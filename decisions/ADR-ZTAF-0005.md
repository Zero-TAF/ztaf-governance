# ADR-ZTAF-0005 — Assurance Is a Tough-Grade Ladder Over Five Risk Axes

| Field | Value |
|---|---|
| Status | Proposed |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Model |
| Supersedes | — |
| Cross-references | ADR-ZTAF-0001 (residual claim d) · AOP `aop-governance` ADR-0006 (five risk axes, inherited) · `ztaf-conformance` (Wave 5, owns fixtures and certification) · OVERT v1.1 AAL-1..4 (crosswalk candidate) · NIST SP 800-63 IAL/AAL (design precedent) |

## Context

No established scheme grades the assurance of autonomous *agent decisions*. The EU AI Act's conformity assessment is binary and its high-risk duties are deferred to December 2027 / August 2028; ISO/IEC 42001 grades management systems, not decisions; OVERT's AAL-1..4 grades the attestation of controls, not the authority of the decision they bounded. Meanwhile the AOP programme already models authority as a decision-rights ladder scored over five risk axes — reversibility, blast radius, data sensitivity, regulatory exposure, and confidence in the observed evidence — and checks authority coverage as a conformance condition. That ladder is the seed of a public, graded, decision-level assurance scheme. The slogan honours it: **Tough Grades**.

## Decision

Zero-TAF grades assurance of delegated decisions as **Tough Grades TG-0..TG-4**, attached to a mandate or decision class — never to a model, a vendor, or a management system:

| Grade | Name | Meaning |
|---|---|---|
| TG-0 | Unassessed | No verified mandate, no independent evidence. Not deployable for consequential decisions. |
| TG-1 | Asserted | Signed mandate minted per task; decision point deployed by the operator; evidence recorded but operator-verifiable only. |
| TG-2 | Verified | Mandate-chain verification with attenuation; per-action enforcement outside the model context, fail-closed; append-only evidence verifiable by an independent party within the organisation. |
| TG-3 | Attested | TG-2 plus evidence receipts anchored to an independent transparency service; behavioural verification active (drift, canaries); must-fail fixtures pass. |
| TG-4 | Independently attested | TG-3 plus third-party attestation of the decision-point and evidence operations. |

Grade assignment: each decision class is scored on the five risk axes inherited from AOP ADR-0006 — reversibility, blast radius, data sensitivity, regulatory exposure, confidence in the observed evidence. The highest-scoring decision class governed by a mandate sets the minimum Tough Grade that mandate must hold. Axis-to-minimum-grade guidance is SHOULD-level until `ztaf-conformance` (Wave 5) normative it.

The grades are architectural assurance. They are not legal conformity, and they do not certify compliance with any regulation; they produce the evidence regime such assessments consume. A crosswalk to OVERT AAL levels is a candidate Wave-5 deliverable, pursued as a mapping, not a merger.

## Consequences

- `ztaf-spec` must carry grade semantics in clause form (ZT-NM-ASM); `ztaf-conformance` owns fixtures and certification; `ztaf-evaluation` owns the behavioural-verification evidence that TG-3 requires.
- Adoption practice grades honestly: an organisation that cannot evidence TG-2 declares TG-1 (or TG-0) — grade inflation is a conformance failure, not a marketing choice.

## What this decision is not

- Not a certification of safety or alignment — behavioural verification evidences conduct against mandate, not model intent.
- Not a replacement for regulatory conformity assessment — it is the evidence regime those assessments draw on.
- Not a maturity model for organisations — placement of the programme maturity model is deferred (owner ruling, 2026-11-22).
