# Kian Boon (John) Teng

**I take enterprise AI from executive intent to production systems that hold up under scrutiny.**

C-level operator · Singapore–Indonesia corridor · climate finance and sustainable infrastructure

Most AI projects die in the gap between a convincing demo and a system a regulated business will actually rely on. That gap is where I work. I decide which problems are worth solving, model the domain so the software cannot make a claim the domain forbids, set the evidence standard the output has to meet, and carry it through deployment and adoption.

---

## How I work

**I settle the business question before any model appears.** Which decision is blocked, what the delay costs, build versus buy, and what a good answer is worth. If a rules engine and a form would do the job, I build that instead.

**I design so the system cannot overstate.** Typed domain contracts, deterministic calculation, bounded inputs, uncertainty carried explicitly rather than rounded away, human review at defined gates, and tests that fail the build when the software makes a claim it has no standing to make.

**I own the last mile.** Deployment, versioning, rollback, adoption, and the commercial line back to the business. A system nobody uses is a failed system regardless of its accuracy.

---

## 180Climate — two production systems

**[Carbon Screening](https://carbon.180climate.net)** · **[EUDR Plot Check](https://eudr.180climate.net)** — both live, serving Indonesian concession holders and commodity exporters.

I selected these problems, designed the system, and took both to launch. The decisions that shaped them were mine:

- **One foundation, two products.** I assessed demand on both sides of the corridor and concluded that carbon pre-feasibility and EUDR plot screening are the same geospatial question asked twice. A single typed core and shared satellite-data layer serve both, which is why two products shipped for close to the cost of one.

- **The legal posture, fixed before any code existed.** EUDR output states what was detected — hectares of loss, which dataset, against the 31 December 2020 cutoff — and never returns a compliance verdict. I recorded that as **ADR-0018** and made it structural rather than editorial: the detection states are typed, and a CI test fails the build if output ever contains *compliant*, *deforestation-free* or *DDS-ready*. A marketing instinct cannot reach a user.

- **Uncertainty as a first-class output.** Carbon results are a range with an uncertainty band and an IPCC Tier label, never a single confident number. I required the report to expose its own inputs and intermediate values so a reviewer can audit the arithmetic — recorded as **ADR-0014** and implemented as a typed calculation trace.

- **The calibration trade-off, held deliberately.** A screen tuned for defensibility flags everything and nobody uses it; tuned for usability it clears plots it should not. I set the standard: watch the amber rate on real runs and tune toward green as the evidence supports it, while never letting a genuine loss render green.

- **Distinguishing a confirmed zero from missing data.** The single decision I would put in front of a technical reviewer. Absent optical-loss data must not be read as a clean result. That distinction is enforced in the type system, not in a comment.

- **Cost and schedule.** Subscription tooling, work routed to the cheapest model that could do it, parallel streams capped, delivered inside the window and budget I set.

**On method, plainly.** I designed and ran an agent harness to implement against my specifications — role-separated writer, reviewer, verifier and test-writer sub-agents, a bounded retry budget, evidence-based handoffs, and human sign-off gates I owned. The commits are co-authored and the harness configuration is public in the repository. The problem selection, domain model, architecture, acceptance criteria, legal posture and every gate decision are mine. Directing a harness of that kind to a defensible production result is the engineering judgement I would bring to a team — not a substitute for it.

**Inspect it end to end:** [the product](https://github.com/TengKianBoon/180climate-app#1-see-the-product) → [a meaningful piece of code](https://github.com/TengKianBoon/180climate-app#3-inspect-a-meaningful-piece-of-code) → [the tests](https://github.com/TengKianBoon/180climate-app#4-check-the-tests) → [what I contributed](https://github.com/TengKianBoon/180climate-app#5-my-contribution) → [versioning and recovery](https://github.com/TengKianBoon/180climate-app#6-inspect-versioning-and-recovery). The repository includes a runnable offline example that reproduces one real decision in under a minute, with no API key.

---

## What a technical evaluator can check

| Competency | Where to see it |
|---|---|
| Domain modelling into typed contracts (Pydantic v2) that make an invalid claim unrepresentable | [`core/contracts`](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/core/contracts/__init__.py#L247-L276) |
| Drawing and defending the boundary between deterministic computation and model output | [architecture](https://github.com/TengKianBoon/180climate-app#2-understand-the-architecture) |
| Guardrails enforced as CI gates rather than policy documents | banned-claim assertion in [the test suite](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/tests/test_eudr_triage.py) |
| Geospatial engineering — COG pixel reads over `vsicurl`, rasterio / shapely, JRC GFC2020 + Hansen + RADD | [`engines/eudr/triage.py`](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/engines/eudr/triage.py#L45-L79) |
| Decision records as an architectural control, not documentation theatre | [18 ADRs](https://github.com/TengKianBoon/180climate-app/tree/main/docs/adr) |
| Agent orchestration with separated authorship and review | [role instructions](https://github.com/TengKianBoon/180climate-app#2-understand-the-architecture) |
| Security controls enforced in the toolchain — secret scan over tool output, scoped command allowlist, destructive-operation veto | [`.claude/settings.json`](https://github.com/TengKianBoon/180climate-app/blob/main/.claude/settings.json) |
| Scope discipline — what was deliberately deferred, published rather than hidden | [hardening roadmap](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/docs/production-roadmap.md) |
| Release engineering — tagged releases, traceable source, defined rollback scope | [releases](https://github.com/TengKianBoon/180climate-app/releases) |
| Verified test evidence | [recorded CI run](https://github.com/TengKianBoon/180climate-app/actions/runs/28553478682/job/84655746161) — 463 collected: 461 passed, 2 skipped, 1 July 2026 |

I design against the Singapore governance context I operate in: the IMDA Model AI Governance Framework, including its agentic-AI guidance, MAS FEAT principles where financial decisions are touched, and PDPA obligations on personal data.

---

## What I bring as an operator

**Adoption is a design constraint, not a launch campaign.** A screen tuned so cautiously that it flags everything gets abandoned in a fortnight — that is a product failure, not a safety win. I set the usability standard alongside the rigour standard: findings written in plain language with real numbers, a free screen as the entry point to paid advisory so that usage and revenue pull in the same direction, and a deliberate watch on how often the tool returns an unhelpful *review needed*. In an enterprise seat this is the same job — getting people to actually use the thing, then keeping them using it.

**Safe usage is enforced where people work, not in a policy document.** In this build that means no secrets in the repository, a secret scan over tool output, a scoped command allowlist and a veto on destructive operations — controls that hold whether or not anyone is watching. Where personal data is in scope I separate private raw material from curated output and work to PDPA obligations; the candidate-fit tool scores anonymised CVs and makes no autonomous decision. Running Gemalto Indonesia I was accountable for national-scale identity and transaction infrastructure, which is where I learned what it costs when a control exists only on paper.

**I decide what not to build, and publish that decision.** I assessed demand on both sides of the corridor before committing a line of code, and cut the scope to the two questions people were actually stuck on. What I deliberately deferred — observability, abuse controls, staging, analytics — is published in the repository as a [hardening roadmap](https://github.com/TengKianBoon/180climate-app/blob/b4ac414789659bfbb56f19599a87cbe72a01a2d2/docs/production-roadmap.md) rather than left for a reviewer to discover. Knowing which corners are safe to cut, and being willing to name them in public, is most of the job.

**I supervise engineers and agents with the same discipline.** A written definition of done before work starts. Review separated from authorship so nothing marks its own homework. A bounded number of attempts before the work escalates instead of failing quietly. Evidence assembled at each gate, and a named human who owns the decision. That is how I ran country teams, and it is how I ran the [sub-agents on this build](https://github.com/TengKianBoon/180climate-app#2-understand-the-architecture). The mechanics differ; the management does not. A team of agents needs what a team of engineers needs — a clear brief, an independent reviewer, and someone accountable for the call.

---

## Selected work

**LLM Decision Lab** — I built a decision harness that puts several model answers to the same question under one project-aware rubric, runs two-pass judging and an adversarial review, and routes genuinely uncertain calls to a human instead of resolving them silently. An applied Outcomes → Rubrics → Graders pattern.

**Governed Audio Learning Pipeline** — A local-first pipeline turning spoken material into governed knowledge artefacts: transcripts, quality-scored summaries and a growing concept map. I designed the private-raw / public-curated separation, maker–checker review, cost gates, and a publish gate that stands between any artefact and the outside world.

**AI Vendor Presentation Monitor** — A config-driven pipeline that tracks official vendor sources, filters for credible material, de-duplicates and prepares a digest, under a deliberately conservative source policy.

**Enterprise AI Candidate Fit & Agent Harness** *(private repository — walkthrough available on request)* — Scores anonymised CVs against a job description with explainable evidence and gap analysis. Built as a governance exercise in a high-scrutiny domain: visible rubrics, human-in-the-loop, fair-hiring guardrails, and no autonomous decisions.

---

## Background

- **Co-Founder & COO, 180Climate** (Oct 2023–) — originating and structuring forest-carbon projects: 9 originated, 4 in active fundraising.
- **VP Business Development, Aserra Partners** — structured Aserra–Daaz's entry into two Indonesian city-scale waste-to-energy projects.
- **President Director / Country Manager, Gemalto Indonesia** (now Thales) — national-scale secure identity and transaction infrastructure.
- **NTU FlexiMasters in Business AI & Technology** — CGPA 4.80 / 5.00, 2026.

Two decades of P&L and country-management responsibility in regulated, high-consequence markets. That is the reason I build AI the way I do: I have carried the downside of a system that was wrong in production.

---

## How I handle AI output

No confidential client data appears in these repositories. Public work uses synthetic examples, public sources or redacted templates. Model output is draft assistance until a human has checked it against a source — that rule is enforced in the systems I build, not just stated in them.

I take a small number of AI deployment advisory engagements each quarter.

---

**[LinkedIn](https://www.linkedin.com/in/kian-boon-teng-7aa84933/)**
