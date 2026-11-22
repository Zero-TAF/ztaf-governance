# AOP Recognition CR — FILED as CR-038

> **FILED and merged 2026-11-23:** [CR-038 in `agentic-operating-procedure/aop-governance`](https://github.com/agentic-operating-procedure/aop-governance/blob/main/change-requests/CR-038-recognise-zero-taf-trust-framework.md), merged via PR [#22](https://github.com/agentic-operating-procedure/aop-governance/pull/22) with the repository map §5 "Trust framework" bullet and the register row. The pre-filing draft is preserved below for the record; the filed text differs only in scope wording adapted to the AOP CR template and cascade checklist.

---

# Draft — CR for lodging in `agentic-operating-procedure/aop-governance`

> **Status: DRAFT — not filed.** Filing this CR in the AOP programme's governance repository is an outward-facing action and proceeds only on the owner's explicit call, per the AOP programme's contributions convention. The text below follows the AOP CR template (fields: Status | Date | Owner | Layer | Depends on; sections 1–6). On approval, it is filed as the next free CR number in `agentic-operating-procedure/aop-governance/change-requests/` and registered in their CR register.

---

# CR-0XX — Recognise Zero-TAF as the Trust Framework Whose Runtime Realisation AOP Profiles

| Field | Value |
|---|---|
| Status | Draft (held in the Zero-TAF programme at `Zero-TAF/ztaf-governance/docs/aop-cr-draft.md`) |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Depends on | ADR-0001 (polyrepo estate), ADR-0006 (decision-rights ladder), ADR-0007 (standards sourcing) |

## 1. Problem statement

The AOP estate formalises decision rights, authority checks outside the model context, escalation with evidence bundles, and the append-only case record — but has no recognised counterpart framework for the trust architecture those mechanisms operationalise. The Zero-Trust Agent Framework programme (`github.com/Zero-TAF`) now exists, defining that architecture: no agent, tool, delegation, or action implicitly trusted; the protected unit is the decision; identity minted per task under signed mandate chains; the decision point outside the model context; per-action enforcement; capability containment; graded assurance (Tough Grades TG-0..TG-4, scored on the same five risk axes as ADR-0006). Absent a recorded relationship, the estates risk silent divergence and duplicative claims.

## 2. Objective

The AOP repository map (§5, Relationship to sibling organisations) and the governance README's cross-references record Zero-TAF as the trust framework that AOP procedures, harnesses, and conformance profiles realise as a profile — with the mapping direction stated one-way from each side and neither estate copying the other.

## 3. Scope

- `plans/` repository map: add Zero-TAF to §5 with the profile-realisation statement and org-qualified URL.
- `README.md` cross-reference block: add the Zero-TAF organisation link.
- No specification, architecture, or clause text changes in this CR. The detailed ZT↔SEC↔TG clause binding lands later, in the Zero-TAF programme's `ztaf-bindings` (Wave 6), mirrored by a future AOP-side CR when it exists.

## 4. Acceptance criteria

- The repository map records the relationship and the direction-of-authority statement.
- ADR-0004 remains in force and untouched: Zero-TAF is a distinct framework, not an AOP security repository; ADR-0004's revival trigger is not tripped by this CR.
- No AOP clause text is altered by this CR.

## 5. Cascade audit

- Zero-TAF ADR-ZTAF-0006 declares this CR as the formalisation instrument and references it by final number once filed.
- The Zero-TAF estate map and programme plan reference the filed CR number.

## 6. What this CR is not

- Not the creation of any repository in the AOP estate.
- Not a conformance change — no AOP document profile or harness behaviour changes.
- Not a merge of programmes — Zero-TAF remains a separate organisation; this CR records consumption and realisation direction only.
