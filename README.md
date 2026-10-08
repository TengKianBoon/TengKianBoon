# Kian Boon (John) Teng

**AI Solutions Architect · business builder, operator and investor · hands-on AI delivery** · Singapore–Indonesia

Boardroom to codebase. I build businesses and the AI systems that help them work. My starting point is the customer or investment decision, the economics behind it and the operating model needed to deliver it. I then connect those needs to workflows, data, people and working technology.

I am Co-Founder and COO of 180Climate. I build with Claude Code, Claude Cowork and Codex, working through architecture, implementation, review, browser QA and release corrections. My portfolio connects working tools to decisions, source, tests and my contribution.

## Business and investment experience

- **PT Ocean Metal Indo — Chief Operating and Commercial Officer, 2011–2023.** Originated and led investment, financing, development and operations for the regulated 11,260-hectare PT Tuhup asset in Kalimantan, from greenfield into production and a managed divestiture process. Built infrastructure, operating functions and teams, and coordinated regulators, communities, customers and delivery partners.
- **Gemalto Indonesia — President Director and Country Manager.** Led country operations and executive customer relationships; formed and led multi-vendor consortia for national eID and ePassport tenders, aligning technical, commercial and government stakeholders.
- **180Climate — Co-Founder and COO.** Lead screening, commercial preparation, fundraising strategy and partner coordination for four direct Indonesian REDD+/IFM development opportunities. Built the commercial and financing model for phased capital, landholder/community economics, investor returns and offtake pathways.
- **Aserra Partners — Vice President of Business Development.** Coordinate sustainable-infrastructure opportunities and waste-to-energy consortium work; advanced a heavy-haulage electrification pilot in Indonesia.

## From business case to working solution

My approach connects the whole decision cycle:

1. **Evaluate the opportunity:** the user or buyer, the problem, the commercial proposition and the evidence needed to proceed.
2. **Design the business and operating model:** capital and cost assumptions, value to stakeholders, partners, responsibilities and delivery dependencies.
3. **Map the workflow:** who decides, which information they need, how it moves and where AI, deterministic logic or human judgment belongs.
4. **Build and test:** architecture, data contracts, implementation and release, with controls that fit the operating use.
5. **Learn and improve:** use feedback, operating observations and commercial requirements to decide what to change, expand or stop.

## Applications built around business decisions

| Application | What I built and why | Explore |
|---|---|---|
| **Carbon Pre-Feasibility Screening — live** | Qualify early development opportunities: turn investment questions into explicit assumptions, traceable calculations and reviewable screening results before further diligence and capital commitment. | [Try Carbon](https://carbon.180climate.net/) · [Architecture and contribution](https://github.com/TengKianBoon/180climate-app) |
| **EUDR Plot Check — live** | Prioritise export due-diligence work: connect geospatial inputs, typed APIs and explicit evidence states to the plots and evidence needing review. | [Try EUDR](https://eudr.180climate.net/) · [Decision logic](https://github.com/TengKianBoon/180climate-app/blob/main/engines/eudr/triage.py) |
| **Fieldwork — native controlled public beta** | Connect project demand with field-service capability: private intake and operator review, SQLite records, consent before contact sharing and recovery procedures. | [Public entry](https://eudr.180climate.net/fieldwork) · [Dated verification](https://github.com/TengKianBoon/180climate-app/blob/main/docs/data-control/controlled-beta-status-2026-09-24.md) |

## How I build

1. **Business to architecture:** define the user, decision and commercial purpose; map the workflow to data, interfaces and operating responsibilities.
2. **Appropriate AI boundaries:** use models where interpretation helps; retain reproducible calculation and screening logic where traceability matters.
3. **Governance in the workflow:** design access controls, private/public data boundaries, consent and human-review points into the application.
4. **Agent-assisted implementation:** configure roles, context, acceptance criteria and bounded retries; inspect code and results, run browser QA and resolve release defects.
5. **Inspectable delivery:** connect demonstrations to decisions, implementation and tests. The screening platform uses FastAPI/Python; Fieldwork adds structured SQLite records.

### Two architecture decisions to inspect

**Traceable Carbon results:** I designed the requirement for visible inputs and intermediate calculations, connecting an early investment question to an inspectable output. [ADR-0014](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/docs/adr/ADR-0014-derivation-trace.md).

**Explicit EUDR evidence states:** I shaped and approved typed contracts that expose insufficient evidence and keep screening decisions reproducible. [ADR-0018](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/docs/adr/ADR-0018-eudr-contracts.md) · [Decision logic](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/engines/eudr/triage.py#L45-L79) · [Tests](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/tests/test_eudr_triage.py#L50-L90).

The documented **1 July 2026 public CI result is 461 passed tests and 2 skipped**. The repository provides architecture decisions and release references alongside the source.

## Evaluation, knowledge and automation

| Project | Mechanisms and contribution | Evidence |
|---|---|---|
| **LLM Decision Lab** | Browser workspace for supplied model answers: weighted criteria, blind labels, claim comparison, local heuristic scoring, disagreement views and two-pass human review. Exported judge prompts support a separate model-assisted assessment. | [Project](https://github.com/TengKianBoon/llm-decision-lab) · [Evaluation logic](https://github.com/TengKianBoon/llm-decision-lab/blob/main/assets/app-core.js) |
| **Governed Audio Learning Pipeline** | Transcription, synthesis, review and export connected to private source storage, reusable tool contracts, cost/retry controls and reviewed public release. MCP-ready interfaces and runbooks make the stages inspectable. | [Project](https://github.com/TengKianBoon/governed-audio-learning-pipeline) · [Operating controls](https://github.com/TengKianBoon/governed-audio-learning-pipeline/blob/main/docs/enterprise-readiness.md) |
| **AI Vendor Presentation Monitor** | Configuration-driven discovery, trusted-source filtering, deduplication, optional transcript processing and digest preparation. | [Project](https://github.com/TengKianBoon/ai-vendor-presentation-monitor) |
| **APMA multilingual audio workflows** | Regional speech and long-file processing, including Qwen for Hokkien and MERaLiON for Singlish; conversion, chunking, stitching, provider comparison and speaker review. | [Project](https://github.com/TengKianBoon/apma-singapore-asr) |

## Commercial and technical foundations

Earlier enterprise work includes 13 years of IT consulting, presales and channel responsibilities, including Oracle business-process solutioning and solution architecture. My operating and investment experience gives those technical choices a business context: capital, customers, delivery, people and stakeholder commitments.

**NTU FlexiMasters in Business AI and Technology (2026)** · 15 Academic Units · CGPA 4.80/5.00. Executive Mentor, Singapore Leaders Network · co-inventor on a telecom-security patent family.

**Hiring for AI solution architecture, forward-deployed AI delivery, business transformation or executive operating leadership?** [Connect on LinkedIn](https://www.linkedin.com/in/kian-boon-teng-7aa84933/).
