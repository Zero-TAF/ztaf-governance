# ADR-ZTAF-0002 — Zero-TAF Is a Polyrepo Estate Across Six Waves

| Field | Value |
|---|---|
| Status | Accepted |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Supersedes | — |
| Cross-references | ADR-ZTAF-000 · `ztaf-governance` README estate table · AOP `aop-governance` ADR-0001 (polyrepo precedent), CR pattern |

## Context

The programme must decide its landing shape. The options were: a landscape comparison plus one candidate ADR inside the AOP governance estate, or a dedicated estate. The seed's ruling 4 deferred to evidence. The evidence: the gap is architectural and estate-wide (it serves AOP, the enterprise catalogs, autonomy measurement, and government scenarios — not AOP alone); the AOP estate itself is the proven polyrepo pattern (fourteen repositories across eleven tiers, wave-gated); and ADR-0004 of the AOP programme is the wrong hook (it is the decision that AOP needs no separate *security* repository; Zero-TAF is not an AOP security repository — it is a separate framework. Its trigger is not tripped, and citing it would misrepresent both programmes).

## Decision

Zero-TAF is its own organisation (`github.com/Zero-TAF`) with a polyrepo estate of fifteen repositories across six waves:

- **W1 (launched):** `.github`, `ztaf-governance`, `ztaf-foundations`, `ztaf-landscape`, `ztaf-adoption` — the owner's 2026-11-22 ruling moves adoption into Wave 1 as the practice methodology.
- **W2:** `ztaf-spec`, `ztaf-architecture`.
- **W3:** `ztaf-evidence`, `ztaf-mandate`.
- **W4:** `ztaf-reference-harness`, `ztaf-registry`.
- **W5:** `ztaf-conformance`, `ztaf-evaluation`.
- **W6:** `ztaf-examples`, `ztaf-bindings`.

Naming uses the `ztaf-` prefix. The authority ladder descends: a repository depends on the tier below it, never on the tier above it. Every repository creation, retirement, renaming, or tier reassignment after Wave 1 is a CR. No Wave-2 repository is created before Wave 1 is Accepted.

## Consequences

- The estate grows only as fast as the content that justifies it — the discipline that prevents premature sprawl.
- Cross-referencing follows the estate conventions: org-qualified URLs, `ZT-` prefixed identifiers (ADR-ZTAF-0003), "owns / does not own" README sections.
- The estate map in `ztaf-governance/README.md` is the authoritative wave/tier table; drift between it and GitHub reality is a finding.

## What this decision is not

- Not an AOP estate extension — Zero-TAF is a separate framework; the relationship is a profile mapping (ADR-ZTAF-0006), recorded by CR in the AOP programme.
- Not a monorepo — sibling-programme precedent (and weekly register reconciliation in the OpenDEA programme) demonstrates the polyrepo model is governable at this scale.
- Not a commitment to all fifteen repositories — every wave after W1 is gated by a CR and may be reshaped by evidence.
