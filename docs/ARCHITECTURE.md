# Architecture Document
# AiGovOps Global Inclusion Matchmaker

**Version:** 1.0.0 | **Date:** 2026-03-15

---

## 1. Architecture Overview

```
+------------------------------------------------------------------+
|                    Single HTML File (~400KB)                       |
|                                                                    |
|  +--------------------+  +--------------------+  +--------------+  |
|  |    HTML Layer       |  |    CSS Layer        |  |  JS Layer    |  |
|  |                    |  |                    |  |              |  |
|  | - Semantic HTML5   |  | - CSS Variables    |  | - ES6+       |  |
|  | - ARIA labels      |  | - Flexbox/Grid     |  | - No deps    |  |
|  | - Tab navigation   |  | - Responsive       |  | - Client-    |  |
|  | - Form elements    |  | - Print styles     |  |   side only  |  |
|  | - Data templates   |  | - Dark/Light mode  |  | - Modular    |  |
|  +--------------------+  +--------------------+  +--------------+  |
|                                                                    |
|  +------------------------------------------------------------+    |
|  |                   Embedded JSON Data Store                   |    |
|  |  organizations[]  |  funders[]  |  countries[]  |  topics[]  |    |
|  +------------------------------------------------------------+    |
+------------------------------------------------------------------+
```

## 2. Design Principles

1. **Zero Dependencies** -- No npm, no CDN, no build tools, no frameworks
2. **Offline-First** -- Fully functional after single download
3. **Progressive Enhancement** -- Works without JS (data visible), enhanced with JS
4. **Sovereignty by Design** -- No tracking, no cookies, no external calls
5. **Accessibility-First** -- WCAG 2.1 AA, keyboard navigable, screen reader compatible
6. **Data Transparency** -- All data visible in source, JSON-extractable

## 3. Component Architecture

### 3.1 Application Shell
```
index.html
|
+-- <head>
|   +-- Meta tags (charset, viewport, description)
|   +-- <style> (all CSS inline)
|
+-- <body>
    +-- Header (logo, title, nav tabs)
    +-- Tab Container
    |   +-- #dashboard    (Tab 1: Overview)
    |   +-- #organizations (Tab 2: Org Database)
    |   +-- #funders       (Tab 3: Funder Database)
    |   +-- #matchmaker    (Tab 4: Matchmaker Engine)
    |   +-- #proposals     (Tab 5: Proposal Generator)
    +-- Footer (license, links, version)
    +-- <script> (all JS inline)
        +-- DATA_ORGANIZATIONS[]
        +-- DATA_FUNDERS[]
        +-- DATA_COUNTRIES[]
        +-- App initialization
        +-- Tab management
        +-- Filter/search engine
        +-- Matchmaker algorithm
        +-- Proposal generator
        +-- UI utilities
```

### 3.2 Data Layer

All data is embedded as JavaScript constants in `<script>` tags at the bottom of the HTML file.

**Organizations Array** (~100+ entries):
```javascript
const DATA_ORGANIZATIONS = [
  {
    id: "us-aigovops",
    name: "AiGovOps Foundation",
    country: "United States",
    countryCode: "US",
    region: "Washington",
    type: "nonprofit",
    url: "https://www.aigovopsfoundation.org/",
    email: "info@aigovopsfoundation.org",
    phone: "",
    mission: "Ships policy-as-code for AI governance...",
    topics: ["governance", "policy-as-code", "indigenous", "rural", "standards"],
    founded: 2024,
    size: "small"
  },
  // ... 100+ more entries
];
```

**Funders Array** (~50+ entries):
```javascript
const DATA_FUNDERS = [
  {
    id: "openai-people-first",
    name: "OpenAI",
    program: "People-First AI Fund",
    url: "https://openai.com/index/people-first-ai-fund/",
    fundingMin: 10000,
    fundingMax: 500000,
    currency: "USD",
    topics: ["community", "ai-literacy", "innovation"],
    geographicFocus: ["Global"],
    deadline: "Rolling",
    description: "Unrestricted grants for community-led AI innovation",
    type: "tech_company"
  },
  // ... 50+ more entries
];
```

### 3.3 Matchmaker Algorithm

```
Input: Free-text project description
  |
  v
Step 1: Tokenize and extract keywords
  - Remove stop words
  - Normalize (lowercase, stem)
  - Extract: topics, countries, org types
  |
  v
Step 2: Score each organization
  - Topic overlap:     0-40 points
  - Geographic match:  0-25 points
  - Type compatibility: 0-20 points
  - Size fit:          0-15 points
  |
  v
Step 3: Score each funder
  - Topic overlap:      0-40 points
  - Geographic coverage: 0-30 points
  - Funding range fit:   0-20 points
  - Deadline proximity:  0-10 points
  |
  v
Step 4: Rank and return top matches
  - Organizations: Top 20 by score
  - Funders: Top 10 by score
  - Cross-reference: Suggest org-funder pairs
```

### 3.4 Proposal Generator

```
Inputs:
  - Selected country
  - Selected topic
  - Selected funder
  - Custom context text
  |
  v
Template Engine:
  - Pulls matched organizations for country+topic
  - Pulls funder-specific alignment language
  - Generates structured Markdown:
    1. Executive Summary
    2. Problem Statement (country-specific data)
    3. Solution Framework (AiGovOps methodology)
    4. Matched Partners (org cards)
    5. Funder Alignment (why this funder)
    6. Measurable Outcomes (templated metrics)
    7. Budget Framework (range-appropriate)
  |
  v
Output: Copy-to-clipboard or download as .md
```

## 4. CSS Architecture

```css
/* CSS Custom Properties for theming */
:root {
  --color-primary: #1a5632;    /* Forest green - earth/sovereignty */
  --color-secondary: #c4820e;  /* Amber - warmth/inclusion */
  --color-accent: #2563eb;     /* Blue - trust/technology */
  --color-bg: #ffffff;
  --color-text: #1a1a1a;
  --color-border: #e5e7eb;
  --radius: 8px;
  --shadow: 0 1px 3px rgba(0,0,0,0.1);
}

/* Responsive breakpoints */
/* Mobile: < 640px */
/* Tablet: 640px - 1024px */
/* Desktop: > 1024px */
```

## 5. Accessibility Architecture

- All interactive elements have `aria-label` or `aria-labelledby`
- Tab panels use `role="tabpanel"` with `aria-selected`
- Cards use `role="article"` with descriptive headings
- Filter controls are `<fieldset>` with `<legend>`
- Search inputs have `role="searchbox"`
- Results announce count via `aria-live="polite"`
- Skip navigation link for keyboard users
- Focus management on tab switches
- High contrast mode support

## 6. File Structure

```
aigovops-global-inclusion-matchmaker/
|
+-- index.html                 # The complete application
+-- README.md                  # Project overview and setup
+-- LICENSE                    # Apache 2.0
+-- CONTRIBUTING.md            # How to add orgs/funders
+-- .claude/
|   +-- rules.md               # Claude Code rules
+-- docs/
|   +-- PRD.md                 # Product Requirements Document
|   +-- PRD-FAQ.md             # PRD FAQ
|   +-- ARCHITECTURE.md        # This document
|   +-- E2E-DESIGN.md          # End-to-end design
+-- data/
|   +-- organizations.json     # Extractable org data
|   +-- funders.json           # Extractable funder data
|   +-- countries.json         # Country metadata
+-- demo/
    +-- screenshot.png         # App screenshot
```

## 7. Security Model

- **No server:** Zero attack surface from server-side code
- **No external requests:** No CDN, no API calls, no tracking pixels
- **No data collection:** No forms submit anywhere, no cookies
- **CSP compatible:** Can run with strict Content-Security-Policy
- **Subresource integrity:** Not needed (no external resources)
- **XSS resistant:** All data rendered via textContent, not innerHTML

## 8. Performance Budget

| Asset | Budget | Actual (Target) |
|-------|--------|------------------|
| HTML structure | 15KB | <10KB |
| CSS | 20KB | <15KB |
| JavaScript | 30KB | <25KB |
| Organization data | 150KB | <120KB |
| Funder data | 50KB | <40KB |
| Country/topic data | 10KB | <8KB |
| **Total** | **275KB** | **<218KB** |

## 9. Future Architecture (Phase 2+)

```
Phase 2: GitHub Pages + JSON API
  - Separate data files (organizations.json, funders.json)
  - Fetch API for dynamic loading
  - Service Worker for offline caching
  - i18n support via language JSON files

Phase 3: Optional AI Enhancement
  - Client-side embeddings for semantic search
  - WebLLM integration for proposal generation
  - No required server dependency

Phase 4: Federation
  - Country chapters maintain own data files
  - Aggregator merges across chapters
  - Git-based governance for data changes
```
