# Product Requirements Document (PRD)
# AiGovOps Global Inclusion Matchmaker

**Version:** 1.0.0 | **Date:** 2026-03-15 | **Status:** Draft
**Author:** Bob Rapp, AiGovOps Foundation | **Contact:** bobrapp@hotmail.com

---

## 1. Executive Summary

The AiGovOps Global Inclusion Matchmaker is an open-source, single-page web application that connects Indigenous communities, rural populations, and traditionally disadvantaged groups across G20 nations with organizations, funders, and collaborative project opportunities focused on AI governance, digital inclusion, and policy-as-code implementation.

The platform operationalizes the AiGovOps Foundation's core belief: **when governance ships as code -- transparent, testable, and auditable -- the communities with the least are positioned to gain the most.**

## 2. Problem Statement

### 2.1 The AI Governance Gap
- 575+ federally recognized tribal nations in the US alone lack technical capacity to translate values into executable AI governance
- Rural communities (Eastern WA poverty rate 22.4%, median income $28,254) are excluded from AI policy discussions
- Indigenous languages, cultural protocols, and data sovereignty requirements are absent from mainstream AI governance frameworks
- G20 nations collectively represent 370M+ Indigenous people with minimal AI governance representation

### 2.2 The Matchmaking Problem
- Organizations doing this work are fragmented across countries and silos
- Funders (Microsoft, AWS, OpenAI, Anthropic, BIA, NTIA) have programs but discovery is difficult
- No centralized tool connects causes, communities, funders, and project collaborators across borders

## 3. Target Users

| User Type | Description | Primary Need |
|-----------|-------------|-------------|
| Indigenous/Tribal Organizations | Tribal governments, First Nations councils, Maori trusts, Aboriginal land councils | Find funding, partners, governance templates |
| Rural Community Groups | Rural development orgs, community colleges, agricultural cooperatives | Access AI training, certification, mentorship |
| Grant Writers/Program Managers | Foundation staff, nonprofit program leads | Match projects to funders efficiently |
| Tech Company CSR/Grant Teams | Microsoft AI for Good, AWS Imagine, OpenAI People-First | Discover high-impact grantees |
| Academic Partners | CWU, tribal colleges, rural universities | Find research collaborators |
| Policy Makers | G20 digital policy advisors, tribal council members | Access governance-as-code templates |

## 4. Product Vision

A world where every community -- regardless of geography, language, income, or ancestry -- has the sovereign capacity to shape, govern, and benefit from artificial intelligence.

## 5. Product Mission

Ship policy-as-code for AI that turns ethical principles, regulatory compliance, and community values into automated, open-source, and auditable governance frameworks accessible to all -- starting with Native and First Peoples, tribal communities, rural Washington, and rural Portugal, then scaling across the Indigenous and rural poor of the G20.

## 6. Core Features

### 6.1 Dashboard (Tab 1)
- Foundation vision/mission display
- Interactive world map with 13 target countries highlighted
- Six governance pillars visualization
- Key statistics cards (organizations count, funders count, countries covered)
- Quick-start matchmaking prompt

### 6.2 Organizations Database (Tab 2)
- 100+ organizations across 13 countries (US, Canada, NZ, Australia, Brazil, Mexico, South Africa, Japan, Korea, Thailand, Turkey, Spain, Portugal)
- Filterable by: Country, Region/State/Province, Topic, Organization Type
- Each entry includes: Name, Country, Region, URL, Contact Email, Phone, Mission (short), Topics/Tags
- Card and table view toggle
- Export to CSV
- Heavy weighting: US (30+), Canada (15+), NZ (10+), Australia (10+), others (5+ each)

### 6.3 Funders Database (Tab 3)
- 50+ tech company and government grant programs
- Filterable by: Funding Range, Topic, Geographic Focus, Deadline
- Each entry includes: Funder Name, Program Name, URL, Funding Range, Topics, Geographic Focus, Deadline, Description
- Deadline calendar view

### 6.4 Matchmaker Engine (Tab 4)
- Free-text project description input
- Keyword extraction and scoring algorithm
- Multi-factor matching: Topic overlap, Geographic alignment, Funding range fit, Organization type compatibility
- Ranked results with relevance scores (0-100)
- Side-by-side organization and funder matches
- Save/bookmark matches

### 6.5 Proposal Generator (Tab 5)
- Country, Topic, and Funder selection dropdowns
- Custom context text area
- Auto-generated proposal sections: Executive Summary, Problem Statement, Solution Framework, Matched Partners, Funder Alignment, Measurable Outcomes, Budget Framework
- Copy-to-clipboard functionality
- Export as Markdown

## 7. Data Architecture

### 7.1 Organizations Schema
```json
{
  "id": "string",
  "name": "string",
  "country": "string",
  "countryCode": "string",
  "region": "string",
  "type": "enum[indigenous, rural, academic, government, nonprofit, tech]",
  "url": "string",
  "email": "string",
  "phone": "string",
  "mission": "string (max 200 chars)",
  "topics": ["string"],
  "founded": "number",
  "size": "enum[small, medium, large]"
}
```

### 7.2 Funders Schema
```json
{
  "id": "string",
  "name": "string",
  "program": "string",
  "url": "string",
  "fundingMin": "number",
  "fundingMax": "number",
  "currency": "string",
  "topics": ["string"],
  "geographicFocus": ["string"],
  "deadline": "string",
  "description": "string",
  "type": "enum[tech_company, government, foundation, multilateral]"
}
```

## 8. Technical Requirements

### 8.1 Architecture
- **Single HTML file** -- zero external dependencies, runs offline
- Pure HTML5, CSS3, JavaScript (ES6+)
- No build step, no npm, no framework dependencies
- All data embedded as JSON in `<script>` tags
- Responsive design (mobile, tablet, desktop)
- Accessible (WCAG 2.1 AA compliant)
- Print-friendly proposal output

### 8.2 Performance
- Initial load < 2 seconds on 3G connection
- Search/filter response < 100ms
- Total file size < 500KB

### 8.3 Browser Support
- Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Graceful degradation for older browsers

## 9. Success Metrics

| Metric | Target (Year 1) |
|--------|------------------|
| Organizations cataloged | 200+ across 13 countries |
| Funders cataloged | 75+ programs |
| Proposals generated | 500+ |
| Successful grant matches | 25+ funded projects |
| Community contributors | 50+ |
| Countries with active orgs | 13 |
| Languages with governance templates | 5+ |

## 10. Roadmap

### Phase 1: MVP (Q1 2026) -- Current
- Single-page HTML app with all 5 tabs
- 100+ orgs, 50+ funders
- Basic keyword matchmaking
- Proposal generator

### Phase 2: Community (Q2 2026)
- GitHub Pages deployment
- Community contribution workflow (PR-based data additions)
- API endpoint for data access
- Multilingual UI (English, Spanish, Portuguese, French, Maori)

### Phase 3: Intelligence (Q3 2026)
- AI-powered matchmaking (optional LLM integration)
- Grant deadline notifications
- Success story tracking
- Impact dashboard

### Phase 4: Scale (Q4 2026)
- Full G20 coverage
- Regional chapter support
- Certification pathway integration
- Policy-as-code template marketplace

## 11. Non-Functional Requirements

- **Open Source:** Apache 2.0 license, community contributions welcome
- **Privacy:** No tracking, no cookies, no analytics by default
- **Sovereignty:** All data publicly auditable, no vendor lock-in
- **Accessibility:** Screen reader compatible, keyboard navigable
- **Offline:** Fully functional without internet after initial load

## 12. Stakeholders

| Stakeholder | Role |
|-------------|------|
| Bob Rapp | Co-Founder, AiGovOps Foundation; CWU Mentorship Lead |
| AiGovOps Foundation | Sponsor organization |
| NCW Tech Alliance | Regional implementation partner |
| Central Washington University | Academic partner, certification pathway |
| Tribal Broadband Initiatives | Infrastructure and governance partner |

## 13. References

- AiGovOps Foundation: https://www.aigovopsfoundation.org/
- NCW Tech Alliance: https://ncwtech.org/
- NTIA Tribal Broadband: https://broadbandusa.ntia.gov/tribal-broadband-connectivity-program
- OpenAI People-First AI Fund: https://openai.com/index/people-first-ai-fund/
- Microsoft AI for Good: https://www.microsoft.com/en-us/ai/ai-for-good
- AWS Imagine Grant: https://aws.amazon.com/government-education/nonprofits/aws-imagine-grant-program/
