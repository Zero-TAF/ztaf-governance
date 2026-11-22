# ADR-ZTAF-0004 — Standards Sourcing Cites, Never Copies

| Field | Value |
|---|---|
| Status | Proposed |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Governance |
| Supersedes | — |
| Cross-references | ADR-ZTAF-0003 · ADR-ZTAF-0007 · `ztaf-landscape` standards-engagement traceability · AOP `aop-governance` ADR-0007 (standards-sourcing precedent) |

## Context

Zero-TAF operates in a dense standards field: NIST (SP 800-207, agent-identity tenets, AI Agent Standards Initiative), IETF (OAuth token exchange, identity chaining, Transaction Tokens for Agents, SCITT), OWASP (Agentic Top 10, LLM Top 10), CSA (Agentic Trust Framework, AI Controls Matrix, MAESTRO), ISO/IEC (42001, 23894), regulators (EU AI Act, MAS SAFR, Singapore MGF-Agentic), and adjacent open standards (OVERT, Proof-of-Control). A programme that restates external content as its own loses both authority and traceability, and drifts silently when the sources move. The sibling programmes already run this discipline: AOP's ADR-0007 restricts standards sourcing to named bodies and requires programme reasoning to be marked as such.

## Decision

1. Zero-TAF **cites**; it never copies. External frameworks, standards, catalogues, and protocols are referenced by publisher and org-qualified URL, with their own identifiers. Programme reasoning is marked as programme reasoning.
2. The named citation set for Wave 1: NIST, IETF, OWASP, CSA, ISO/IEC, EU (EUR-Lex), MAS, Singapore IMDA/AI Verify, MITRE, Google SAIF, and the open standards OVERT and Proof-of-Control. The set may be extended by CR.
3. **Independence ruling (owner, 2026-11-22): no external collaboration materials or standards from industry collaborations are used as sources, and none are referenced in Zero-TAF content. All CSP-facing agent-trust scenarios are rebuilt from first principles within Zero-TAF.** Consequential content is developed from the verified open record (the foundational research dossier) or from Zero-TAF reasoning marked as such.
4. The corrections register in `ztaf-landscape` governs citation hygiene: verified dates, real RFC numbers, corrected titles. A claim that cannot be verified is marked as such or removed.
5. Confidence flags (VERIFIED / PARTIAL / NOT FOUND) travel with factual claims in research artefacts; normative clauses do not carry flags, they carry clause numbers.

## Consequences

- `ztaf-landscape` refreshes quarterly by CR, so citations and rival claims stay honest as the field moves (OVERT, Proof-of-Control, TxT-for-agents, and the NCCoE build are all in motion).
- Upstream contributions (to OWASP mitigations, MCP SEPs, NCCoE practice-guide inputs) areZero-TAF *outbound* work, gated by CR and owner sign-off, and always cite Zero-TAF records rather than duplicating them.

## What this decision is not

- Not a ban on engagement — the programme engages standards bodies; it just never absorbs their material as its own text.
- Not an assertion that cited frameworks are endorsed by, or endorse, Zero-TAF.
