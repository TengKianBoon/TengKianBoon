# AI governance in my public projects, mapped to ISO/IEC 42001 themes

A mapping draft: how the controls in my public projects (Fieldwork A2A, FieldProof and the 180Climate screening platform) line up with the themes of ISO/IEC 42001:2023, the standard for AI management systems. It is my own mapping. It is not an audit, a certification or a Statement of Applicability, and it makes no compliance claim. Every row links to public code or records.

Last reviewed: 21 November 2026.

| Control in my projects | How it works | Public evidence | ISO/IEC 42001 theme |
|---|---|---|---|
| **People make the consequential decisions** | In Fieldwork A2A a client's AI agent can only draft a job and read its status; 180Climate reviews each draft with the client, publishes approved jobs and handles cancellation. In FieldProof an AI reads each photographed label and a person accepts or rejects every item. | [How a draft becomes a job](https://github.com/TengKianBoon/fieldwork-a2a#how-a-draft-becomes-a-job) · [FieldProof](https://github.com/TengKianBoon/fieldproof) | A.9 Use of AI systems (A.9.2 processes for responsible use); A.3 Internal organization |
| **Intended use and limits stated** | The Fieldwork Agent Card describes its one skill and its pilot limits; the service README lists exactly what a client receives. | [Agent Card](https://fieldwork-a2a-180climate.netlify.app/.well-known/agent-card.json) · [What a client receives](https://github.com/TengKianBoon/fieldwork-a2a#what-it-does) | A.9.4 Intended use of the AI system; A.8 Information for interested parties |
| **Verified before release** | The public repository contains unit tests, a contract test against upstream validation, and SDK and isolation proof scripts for synthetic clients. | [Tests](https://github.com/TengKianBoon/fieldwork-a2a/tree/main/tests) · [Proof scripts](https://github.com/TengKianBoon/fieldwork-a2a/tree/main/scripts) | A.6.2.4 Verification and validation; A.6.2.5 Deployment |
| **Design decisions recorded** | Public architecture decision records document selected design choices and corrections. | [180Climate ADRs](https://github.com/TengKianBoon/180climate-app/tree/main/docs/adr) | A.6.2.3 Documentation of design and development; A.6.2.7 Technical documentation |
| **Selected service events are logged** | For a rejected requester credential, the handler logs a diagnostic. For an operator queue read, it records the operator identifier and row count. | [Fieldwork A2A source](https://github.com/TengKianBoon/fieldwork-a2a/tree/main/src) | A.6.2.8 Recording of event logs |
| **Client separation and key handling** | Each client has its own key, stored only as a fingerprint; every task is bound to its client, and another client's task answers "not found". Tests fail if a reply leaks a code or a private link. | [Access and isolation](https://github.com/TengKianBoon/fieldwork-a2a#what-it-does) · [Tests](https://github.com/TengKianBoon/fieldwork-a2a/tree/main/tests) | Supporting security measure. No direct Annex A mapping asserted. |
| **Limits on use and spend** | Per-client pilot limits and bounded errors in Fieldwork A2A; a daily model-spend ceiling in FieldProof. | [Pilot limits](https://github.com/TengKianBoon/fieldwork-a2a#pilot-limits) · [FieldProof](https://github.com/TengKianBoon/fieldproof) | A.6.2.6 Operation and monitoring; A.4 Resources for AI systems |
| **A correction held by a test** | An independent review found an unsuitable peat-methodology reference; the routing correction is recorded in ADR-0012 and a named golden-case test stops it returning. | [ADR-0012](https://github.com/TengKianBoon/180climate-app/blob/main/docs/adr/ADR-0012-peat-routing-correction.md) · [Golden-case tests](https://github.com/TengKianBoon/180climate-app/blob/main/tests/test_golden.py) | Clause 10 Improvement |

## Not yet covered

- **A.2 Policies related to AI:** no single written AI policy.
- **A.5 Assessing impacts of AI systems:** no formal, documented impact assessment per system.
- **Measured accuracy (A.6.2.4):** the FieldProof label reader has no labelled evaluation set yet, so its accuracy is not yet measured.
- **Clauses 4 to 9:** no formal AI management system (scope, leadership commitment, risk treatment plan, Statement of Applicability, internal audit).

Next, in order of value: an evaluation set for the label reader that reports correct reads, wrong reads and blanks with their denominators; an impact assessment template; a short AI policy.
