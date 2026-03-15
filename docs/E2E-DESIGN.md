# End-to-End Design Document
# AiGovOps Global Inclusion Matchmaker

**Version:** 1.0.0 | **Date:** 2026-03-15

---

## 1. User Journeys

### Journey 1: Tribal Organization Seeking Funding
```
1. Open index.html in browser
2. Read Dashboard -- understand AiGovOps mission
3. Click Matchmaker tab
4. Type: "We are a tribal nation in Washington state seeking funding for AI governance training and broadband-connected policy automation"
5. Review matched organizations (NCW Tech Alliance, CWU, etc.)
6. Review matched funders (NTIA TBCP, Microsoft AI for Good, etc.)
7. Click Proposal Generator tab
8. Select: Country=US, Topic=Indigenous Governance, Funder=NTIA TBCP
9. Add context about their specific tribe and needs
10. Copy generated proposal to clipboard
11. Paste into grant application
```

### Journey 2: Tech Company Grant Manager
```
1. Open index.html
2. Click Funders tab -- find their own program listed
3. Click Organizations tab -- filter by topic "indigenous" + country "Australia"
4. Browse matching organizations with contact details
5. Click Matchmaker tab
6. Type: "Looking for Indigenous AI governance projects in APAC region"
7. Review ranked organizations with relevance scores
8. Contact top matches directly
```

### Journey 3: Rural Community College Partnership
```
1. Open index.html
2. Click Organizations tab -- filter by type "academic" + topic "training"
3. Find peer institutions doing similar work
4. Click Matchmaker tab
5. Type: "Rural community college wanting to create AI governance certification for first-generation students"
6. Review org matches (CWU, tribal colleges) and funder matches (AWS Imagine, Anthropic)
7. Generate proposal for cross-institutional certification program
```

### Journey 4: International Researcher
```
1. Open index.html
2. Click Dashboard -- review country coverage
3. Click Organizations tab -- filter by country "New Zealand"
4. Browse Maori AI governance organizations
5. Click Organizations tab -- filter by country "Canada"
6. Browse First Nations technology organizations
7. Use Matchmaker to find cross-border collaboration opportunities
8. Generate proposal for comparative Indigenous AI governance research
```

## 2. Data Flow

```
[Embedded JSON Data]
       |
       v
[App Initialization] --> [Populate Filter Dropdowns]
       |                        |
       v                        v
[Dashboard Stats]    [Organizations Tab: Render Cards]
       |                        |
       v                        v
[Country Map]        [Funders Tab: Render Cards]
                                |
                                v
                     [Matchmaker: User Input]
                                |
                                v
                     [Keyword Extraction]
                                |
                                v
                     [Score Organizations] + [Score Funders]
                                |
                                v
                     [Ranked Results Display]
                                |
                                v
                     [Proposal Generator]
                                |
                                v
                     [Template Population]
                                |
                                v
                     [Copy/Export Output]
```

## 3. UI Wireframes (Text)

### 3.1 Dashboard Tab
```
+------------------------------------------------------------------+
| [Logo] AiGovOps Global Inclusion Matchmaker                       |
| [Dashboard] [Organizations] [Funders] [Matchmaker] [Proposals]   |
+------------------------------------------------------------------+
|                                                                    |
| VISION: A world where every community...                          |
| MISSION: Ship policy-as-code for AI...                            |
|                                                                    |
| +----------+ +----------+ +----------+ +----------+               |
| | 100+     | | 50+      | | 13       | | 6        |               |
| | Orgs     | | Funders  | | Countries| | Pillars  |               |
| +----------+ +----------+ +----------+ +----------+               |
|                                                                    |
| Six Pillars:                                                       |
| [Governance] [Sovereignty] [Rural Access]                         |
| [Multilingual] [Workforce] [Open Source]                          |
|                                                                    |
| Country Cards:                                                     |
| [US] [CA] [NZ] [AU] [BR] [MX] [ZA] [JP] [KR] [TH] [TR] [ES] [PT]|
+------------------------------------------------------------------+
```

### 3.2 Organizations Tab
```
+------------------------------------------------------------------+
| Filters:                                                          |
| Country: [All v]  Topic: [All v]  Type: [All v]  Search: [____]  |
|                                                                    |
| Showing 100 of 100 organizations                                  |
|                                                                    |
| +-----------------------------+ +-----------------------------+   |
| | AiGovOps Foundation         | | NCW Tech Alliance           |   |
| | US - Washington             | | US - Washington             |   |
| | nonprofit                   | | nonprofit                   |   |
| | Ships policy-as-code...     | | 23-org digital equity...    |   |
| | [governance] [indigenous]   | | [digital-equity] [tribal]   |   |
| | URL | Email                 | | URL | Email                 |   |
| +-----------------------------+ +-----------------------------+   |
+------------------------------------------------------------------+
```

## 4. Country Data Model

| Country | Code | Indigenous Peoples | Key Issues | Primary Orgs |
|---------|------|--------------------|------------|-------------|
| United States | US | 574 federally recognized tribes, 5.2M Native Americans | Tribal sovereignty, broadband, ICWA | AiGovOps, NCW Tech, CWU |
| Canada | CA | 634 First Nations, Metis, Inuit | OCAP principles, UNDRIP, digital equity | FNTC, Mila, FNIGC |
| New Zealand | NZ | Maori (17% pop) | Te Tiriti, Maori data sovereignty | Taiuru, Te Hiku Media |
| Australia | AU | Aboriginal/Torres Strait Islander (3.8% pop) | Closing the Gap, NT intervention | inDigiMOB, Indigital |
| Brazil | BR | 305 Indigenous groups, 274 languages | Amazon protection, Quilombola rights | Instituto Nupef, CONAQ |
| Mexico | MX | 68 Indigenous peoples, 364 language variants | INPI, digital inclusion | INPI, Rhizomatica |
| South Africa | ZA | Khoisan, Zulu, Xhosa + rural poor | Digital inequality, language diversity | Deep Learning Indaba |
| Japan | JP | Ainu, Ryukyuan peoples | Recognition, language revitalization | Ainu Association, AIST |
| South Korea | KR | Rural elderly, multicultural families | Rural depopulation, digital divide | NIA, KISA |
| Thailand | TH | Hill tribes, rural northeast | Language barriers, agricultural AI | Kenan Foundation |
| Turkey | TR | Kurdish, rural Anatolian communities | Infrastructure gaps, language rights | BTK, Habitat Association |
| Spain | ES | Roma, rural depopulation (Espana Vaciada) | Empty Spain, digital divide | Fundacion Secretariado Gitano |
| Portugal | PT | Roma, rural interior communities | InCode2030, digital skills gaps | INCoDe.2030, FCT |

## 5. Matching Weights Configuration

```javascript
const MATCH_WEIGHTS = {
  organization: {
    topicOverlap: 0.40,      // 40% weight
    geographicMatch: 0.25,   // 25% weight
    typeCompatibility: 0.20, // 20% weight
    sizeFit: 0.15           // 15% weight
  },
  funder: {
    topicOverlap: 0.40,      // 40% weight
    geographicCoverage: 0.30, // 30% weight
    fundingRangeFit: 0.20,   // 20% weight
    deadlineProximity: 0.10  // 10% weight
  }
};
```

## 6. Proposal Templates

Each generated proposal follows this structure:

### Executive Summary Template
```
[Project Name] is a [duration]-month initiative by [matched orgs]
to [topic description] in [country/region]. With support from
[funder program], we will [3 key activities] reaching [target
number] participants and producing [3 key deliverables].
```

### Problem Statement Template
```
In [country], [indigenous/rural group] faces [specific challenges].
[Statistical evidence]. Current AI governance frameworks
[gap description]. Without intervention, [consequence].
```

### Measurable Outcomes Template
```
- Train [N] participants in AI governance within [timeframe]
- Deploy [N] policy-as-code templates for [specific use case]
- Establish [N] cross-border partnerships
- Publish [deliverable] for community replication
- Achieve [certification/recognition milestone]
```

## 7. Testing Strategy

### Unit Tests (Browser Console)
- Matchmaker scoring returns expected ranges
- Filter combinations produce correct subsets
- Proposal generator populates all sections
- Data integrity: all orgs have required fields
- Data integrity: all funders have required fields

### Accessibility Tests
- axe-core audit passes with 0 violations
- Keyboard navigation through all tabs
- Screen reader announcement of dynamic content
- Color contrast ratios meet WCAG 2.1 AA

### Cross-Browser Tests
- Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Mobile viewport (375px width)
- Tablet viewport (768px width)
- Desktop viewport (1280px width)

### Offline Test
- Download HTML file
- Disconnect network
- Verify all features work

## 8. Deployment

### Phase 1: Static File
- Host on GitHub Pages (free)
- Direct download from repository
- Share via email/USB for offline communities

### Phase 2: GitHub Pages
- Enable GitHub Pages on main branch
- Custom domain: matchmaker.aigovopsfoundation.org
- Automated deployment on push to main

## 9. Contribution Workflow

```
1. Fork repository
2. Add organization/funder to embedded JSON
3. Verify required fields are complete
4. Submit Pull Request
5. Maintainer reviews data accuracy
6. Merge to main
7. GitHub Pages auto-deploys
```

## 10. Metrics and Analytics

No built-in analytics (privacy-first). Success measured by:
- GitHub stars and forks
- Pull Requests adding organizations
- Issues requesting features
- Grant applications citing the tool
- Community testimonials
