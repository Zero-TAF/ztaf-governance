# ADR-ZTAF-0003 — Identifiers Are ZT-Prefixed and Bind, Never Collide

| Field | Value |
|---|---|
| Status | Accepted |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Model |
| Supersedes | — |
| Cross-references | ADR-ZTAF-0002 · ADR-ZTAF-0004 · `ztaf-foundations` glossary (`ZT-0xx`) · AOP NM-INT-5 (gap-and-contribute rule) · Enterprise-Semantics mapping predicates |

## Context

The estate in which this programme operates already carries identifier namespaces: AOP (`NM-`, `SEC-`, `CC-`, `ARC-`, `SK-`, `AOP-0xx` glossary), WSF (`ADR-WSF-NN`), OpenDEA (`dea:*`, `EGV-`), MAMA, Source-Engineering (`COTS`). A programme that invents colliding identifiers fragments cross-citation across the estate. The established rule in the sibling programmes is that identifiers bind to canonical records or are declared as gaps and lodged as contributions — never invented locally as if canonical.

## Decision

Every Zero-TAF identifier is `ZT`-namespaced:

| Kind | Format | Example |
|---|---|---|
| Glossary concept | `ZT-0xx` | ZT-004 Mandate |
| Normative model clause | `ZT-NM-<AREA>-n` (MAN mandate, AUT authority, ENF enforcement, CON containment, EVD evidence, ASM assurance) | ZT-NM-MAN-3 |
| Trust/security clause | `ZT-SEC-n` | ZT-SEC-1 |
| Conformance clause | `ZT-CC-n` | ZT-CC-9 |
| Architecture clause | `ZT-ARC-n` | — |
| ADR | `ADR-ZTAF-NNNN` | ADR-ZTAF-0001 |
| Change request | `CR-ZTAF-NNN` | CR-ZTAF-001 |
| Assurance grade | `TG-0..TG-4` | TG-3 |

External concepts are cited by their own org-qualified identifiers and URLs. Zero-TAF does not re-identify them. Where an AOP, WSF, ES, or OpenDEA record is the canonical instance of a concept, Zero-TAF binds to it; where no canonical record exists, the gap is declared in the binding repo (Wave 6) and lodged as a contribution to the owning programme, then swapped for the canonical identifier when published.

## Consequences

- Citations across the estate stay unambiguous (`ZT-SEC-1` vs AOP `SEC-1`).
- The glossary in `ztaf-foundations` is the single source of `ZT-0xx` numbers; numbers are never reused, only retired.
- Binding work is deferred to Wave 6 by design; until then, external references are plain citations, not bindings.

## What this decision is not

- Not a claim of authority over external namespaces — the direction is always Zero-TAF consuming theirs.
- Not a mandate to mirror external content — mappings are assertions, not copies.
