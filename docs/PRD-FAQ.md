# PRD - Frequently Asked Questions
# AiGovOps Global Inclusion Matchmaker

**Version:** 1.0.0 | **Date:** 2026-03-15

---

## General Questions

### Q1: What is the AiGovOps Global Inclusion Matchmaker?
**A:** A free, open-source, single-page web application that connects Indigenous communities, rural populations, and disadvantaged groups across G20 nations with organizations, funders, and project opportunities focused on AI governance and policy-as-code. It runs entirely in a browser with zero dependencies.

### Q2: Who built this and why?
**A:** The AiGovOps Foundation, co-founded by Bob Rapp, built this to solve a fundamental matchmaking problem: organizations working on Indigenous and rural AI inclusion are fragmented across countries and silos, while funders with relevant programs are difficult to discover. Bob's decades of mentorship at CWU -- serving first-generation, rural, and underrepresented students -- demonstrated that structured connections between communities, resources, and opportunities produce outsized impact.

### Q3: What does "policy-as-code" mean?
**A:** Policy-as-code means expressing governance rules, ethical guidelines, and compliance requirements as executable, testable, version-controlled code (using tools like OPA/Rego, Terraform, Kubernetes YAML) rather than PDF documents. This makes AI governance auditable, reproducible, and deployable by any community with basic technical capacity.

### Q4: Why focus on Indigenous and rural communities specifically?
**A:** G20 nations collectively represent 370M+ Indigenous people. Rural communities face compounding disadvantages: lower broadband access, fewer tech jobs, less representation in AI policy discussions, and higher poverty rates. Eastern Washington alone has a 22.4% poverty rate. These communities are most at risk of being governed BY AI systems they had no role in designing -- policy-as-code gives them tools to govern AI on their own terms.

### Q5: Which countries are covered?
**A:** 13 countries across G20 and allied nations: United States, Canada, New Zealand, Australia, Brazil, Mexico, South Africa, Japan, South Korea, Thailand, Turkey, Spain, and Portugal. The US, Canada, NZ, and Australia have the deepest coverage due to established Indigenous digital rights movements and Bob Rapp's direct partnerships.

## Technical Questions

### Q6: Why a single HTML file instead of a full web application?
**A:** Intentional design for maximum accessibility. Rural and tribal communities often have limited bandwidth, intermittent connectivity, and constrained IT infrastructure. A single HTML file can be downloaded once, emailed, shared on USB drives, and run offline on any device with a browser. Zero npm installs, zero build steps, zero server requirements.

### Q7: How does the matchmaker algorithm work?
**A:** Keyword extraction from free-text input matched against organization and funder topic tags, geographic alignment scoring, and organization type compatibility weighting. Each match receives a 0-100 relevance score based on multi-factor overlap. The algorithm is transparent and runs entirely client-side.

### Q8: Can I contribute data to the organizations or funders database?
**A:** Yes. Submit a Pull Request to the GitHub repository adding entries to the embedded JSON data following the schema in the PRD. Community contributions are reviewed and merged by maintainers. The goal is 200+ organizations and 75+ funders by end of 2026.

### Q9: Is there an API?
**A:** Not in Phase 1 (MVP). Phase 2 (Q2 2026) plans include a JSON API endpoint and GitHub Pages deployment. For now, all data is embedded in the HTML file and can be extracted programmatically from the source.

### Q10: How is data quality maintained?
**A:** All organization and funder entries require: verified URL, confirmed contact information, published mission statement, and at least one topic tag. Community contributions go through PR review. Stale entries (broken URLs, outdated contacts) are flagged quarterly.

## Funding and Partnership Questions

### Q11: Which tech company grant programs are most aligned?
**A:** Top-tier alignment:
- **OpenAI People-First AI Fund** ($50M, unrestricted grants for community-led innovation)
- **Microsoft AI for Good** ($5K-$15K in-kind, WA State focus)
- **AWS Imagine Grant** (up to $200K + $100K credits, GenAI Pathfinder track)
- **Anthropic Economic Futures** ($10K-$50K + API credits)
- **Google.org AI Opportunity Fund** ($15M+ APAC focus)
- **Salesforce Agents for Impact** ($200-300K + products)

### Q12: What government grants apply?
**A:** Key programs:
- **NTIA Tribal Broadband Connectivity Program** ($500M+ new NOFO spring 2026)
- **BIA Living Languages Grant Program** ($200K-$300K)
- **NTIA Digital Equity** (tribal set-asides, $45M)
- **BIA Native Broadband** (NTBG)
- **USDA Rural Development** (distance learning, telemedicine)
- **EU Horizon** programs for Spain/Portugal
- **Australia NIAA** Indigenous Digital Inclusion
- **NZ Digital Equity Coalition** funding

### Q13: How does this tool help grant writers?
**A:** The Proposal Generator tab auto-drafts grant proposals with: executive summary, problem statement, solution framework, matched local and cross-border partners, funder-specific alignment language, measurable outcomes, and budget framework. Copy-to-clipboard and Markdown export make it paste-ready for applications.

### Q14: What is the relationship with NCW Tech Alliance and CWU?
**A:** NCW Tech Alliance is the regional implementation partner -- their 23-org digital equity coalition, AI Youth Corps (20 students, 3 school districts, Microsoft-backed), and tribal broadband work provide the on-the-ground delivery infrastructure. CWU provides the academic pathway -- stackable certifications targeting their 40% first-generation, 21% Hispanic student body, building on Bob Rapp's proven mentorship pipeline that produced students who built enterprise applications for Fortune 500 companies.

## Impact Questions

### Q15: What measurable outcomes are targeted?
**A:** Year 1 targets: 250 rural/tribal participants trained in AI governance, 25 community mentors/fellows deployed, 10 open policy-as-code templates for tribal data governance, 3 multilingual AI pilots, 1 regional certification pathway through CWU, and a published Rural & Tribal AI Governance Playbook for G20 adoption.

### Q16: How does this address Indigenous data sovereignty?
**A:** Three ways: (1) The Tribal Data Sovereignty Audit Toolkit helps tribes vet AI vendors for data residency and consent compliance; (2) governance-as-code templates encode OCAP principles (Ownership, Control, Access, Possession) into executable policy; (3) the Indigenous AI Ethics Review Board model ensures AI models are reviewed by tribal elders and cultural knowledge keepers before deployment.

### Q17: What about Indigenous languages?
**A:** The Multilingual AI Governance initiative translates governance frameworks into Indigenous languages, co-developed with native speakers. BIA Living Languages grants fund this directly. Phase 2 adds multilingual UI for the matchmaker itself (English, Spanish, Portuguese, French, Maori).

### Q18: How does the Portugal/rural Europe connection work?
**A:** Rural Portugal faces the same digital skills gaps as rural WA -- high NEET rates, limited broadband, agricultural economies transitioning. The cross-continental peer network connects Eastern WA practitioners with rural Portuguese counterparts, sharing governance templates, training materials, and meetup formats. EU Horizon and Portugal's InCode2030 programs fund this work.

### Q19: What is the G20 scaling strategy?
**A:** Prove the model in US (tribal + rural WA), Canada (First Nations), NZ (Maori), and Australia (Aboriginal), then replicate across G20 using the published playbook and open-source templates. Each country chapter adapts templates to local legal frameworks, languages, and cultural protocols while maintaining interoperable governance-as-code standards.

### Q20: Is this just another directory?
**A:** No. Directories are passive. This tool actively matchmakes by scoring alignment between project descriptions, organizational capabilities, and funder priorities. The Proposal Generator goes further -- producing draft grant applications that position matched partners for collaborative funding. The goal is funded projects, not bookmarks.
