# ztaf-governance

The governance repository for the Zero-Trust Agent Framework programme: architectural decision records, change requests, findings, the lifecycle model, the release policy, contributor rules, and the programme plan.

| Field | Value |
|---|---|
| Authority | Normative for Zero-TAF programme governance |
| Tier | W1 (foundations) |
| Version | 0.1.0 |
| Status | Active |
| Licence | MIT |

## What this repository owns

- `decisions/` — the ADR-ZTAF series. ADR-ZTAF-000 is the promoted seed record (verbatim, with a corrections appendix). ADR-ZTAF-0001..0007 are the founding decisions.
- `change-requests/` — CR-ZTAF records and the CR register. Structural estate change, including repository creation, retirement, renaming, and tier reassignment, is a CR.
- `docs/foundational-research/` — the verified research dossier and gap analysis that back the founding decisions.
- `docs/aop-cr-draft.md` — the draft change request to be lodged in `agentic-operating-procedure/aop-governance`, pending owner sign-off.
- `plans/` — the programme plan.
- `templates/` — the ADR and CR templates.

## What this repository does not own

- The definition of Zero-TAF — that is [ztaf-foundations](https://github.com/Zero-TAF/ztaf-foundations).
- Positioning against the landscape — that is [ztaf-landscape](https://github.com/Zero-TAF/ztaf-landscape).
- Adoption practice — that is [ztaf-adoption](https://github.com/Zero-TAF/ztaf-adoption).
- Normative clauses — `ztaf-spec` (Wave 2, gated by CR).

## The estate

| Repository | Tier | Wave | Status |
|---|---|---|---|
| `.github` | T0 | W1 | Active |
| `ztaf-governance` | T0 | W1 | Active |
| `ztaf-foundations` | T0 | W1 | Active |
| `ztaf-landscape` | T0 | W1 | Active |
| `ztaf-adoption` | T1 | W1 | Active |
| `ztaf-spec` | T2 | W2 | Gated by CR |
| `ztaf-architecture` | T2 | W2 | Gated by CR |
| `ztaf-evidence` | T3 | W3 | Gated by CR |
| `ztaf-mandate` | T3 | W3 | Gated by CR |
| `ztaf-reference-harness` | T4 | W4 | Gated by CR |
| `ztaf-registry` | T4 | W4 | Gated by CR |
| `ztaf-conformance` | T5 | W5 | Gated by CR |
| `ztaf-evaluation` | T5 | W5 | Gated by CR |
| `ztaf-examples` | T6 | W6 | Gated by CR |
| `ztaf-bindings` | T6 | W6 | Gated by CR |

The authority ladder descends: a repository depends on the tier below it, never on the tier above it.

## Change model

This programme follows the established ADR, change-request and finding pattern used by the sibling discipline organisations (lineage: the World Semantic Foundation governance model, carried into the Agentic Operating Procedure programme). Records carry the `ZTAF` namespace (`ADR-ZTAF-NNNN`, `CR-ZTAF-NNN`) so citations remain unambiguous across the estate.

Decisions start as **Proposed** and are marked **Accepted** by the owner. A record is never edited silently after acceptance; it is superseded.
