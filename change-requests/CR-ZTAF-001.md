# CR-ZTAF-001 — Establish the Wave 1 Estate

| Field | Value |
|---|---|
| Status | Implemented |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Depends on | ADR-ZTAF-000, ADR-ZTAF-0002, ADR-ZTAF-0003, ADR-ZTAF-0004, ADR-ZTAF-0007 |

## 1. Problem statement

The `Zero-TAF` organisation existed with an empty `.github` repository, no org name, no description, and no recorded content beyond the seed file in the programme workspace. The concept, its verified landscape, and the estate plan existed only locally.

## 2. Objective

The Wave 1 estate is live on GitHub: org surface populated; `ztaf-governance`, `ztaf-foundations`, `ztaf-landscape`, and `ztaf-adoption` created, seeded, and cross-linked; the founding decisions and foundational research published; licences in place.

## 3. Scope

- Org: name "Zero-Trust Agent Framework (Zero-TAF)", description per ADR-ZTAF-0001's claim.
- `.github`: org profile README, community health files, MIT licence.
- `ztaf-governance`: README with estate table; ADR-ZTAF-000 (seed promoted verbatim with corrections appendix) and ADR-ZTAF-0001..0007 (Proposed); CR-ZTAF-001 and the CR register; ADR/CR templates; foundational research dossier and gap analysis; programme plan; AOP CR draft (not filed).
- `ztaf-foundations`: founding paper; ZT-0xx glossary; non-goals; misconception ladder.
- `ztaf-landscape`: landscape survey; claim-by-claim differentiation; corrections register; component coverage matrix; standards-engagement traceability.
- `ztaf-adoption`: the five-stage adoption methodology.
- All repositories MIT-licensed (matches AOP; ES uses Apache-2.0, WSF none detected).

Out of scope: Waves 2–6 repositories; normative clause text; filing the AOP CR; any upstream contribution.

## 4. Acceptance criteria

- [x] Org name and description set on `github.com/Zero-TAF`.
- [x] Five repositories exist and are public; each README carries "owns / does not own" sections.
- [x] ADR-ZTAF-000..0007 present; 000 verbatim with Appendix A; 0001..0007 Proposed.
- [x] Every published factual claim traces to the foundational research or carries a confidence flag.
- [x] No external collaboration materials referenced anywhere (ADR-ZTAF-0004 ruling 3).
- [x] MIT licence in every repository.

## 5. Cascade audit

- ADR-ZTAF-0002 estate table — created by this CR's scope and now authoritative.
- ADR-ZTAF-0003 identifiers — `ZT-0xx` numbers minted in the foundations glossary by this CR.
- ADR-ZTAF-0006 — the AOP CR draft is created but NOT filed; filing is a separate, owner-gated action.
- `ztaf-landscape` corrections register — the living register established; ADR-ZTAF-000 Appendix A points to it.

## 6. What this CR is not

- Not the AOP recognition (that is the draft in `docs/aop-cr-draft.md`, awaiting sign-off and the AOP programme's own process).
- Not a specification release — nothing in Wave 1 is normative.
- Not a maturity-model decision — deferred per the owner's 2026-11-22 ruling.
