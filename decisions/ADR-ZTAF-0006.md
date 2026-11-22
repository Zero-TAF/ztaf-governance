# ADR-ZTAF-0006 — AOP Realises Zero-TAF as a Profile

| Field | Value |
|---|---|
| Status | Proposed |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Governance |
| Supersedes | — |
| Cross-references | ADR-ZTAF-0001 · ADR-ZTAF-0002 · `docs/aop-cr-draft.md` (the CR to be lodged in `agentic-operating-procedure/aop-governance`) · AOP `aop-spec` SEC-1..SEC-17, `aop-foundations` glossary AOP-024/030–034, `aop-governance` ADR-0006 |

## Context

The Agentic Operating Procedure programme already realises four of Zero-TAF's nine components natively: the outside-model authority check (AOP-030; SEC-1, SEC-2), the guardrail (AOP-031; SEC-5, SEC-17), escalation with evidence bundles (AOP-032/033; SEC-9), and the append-only tamper-evident case record (AOP-034; SEC-8), with zero standing privilege via post-approval scoped credentials (SEC-3) and workload identity (SEC-16). Its decision-rights ladder over five risk axes (ADR-0006) is the seed of Zero-TAF's Tough Grades (ADR-ZTAF-0005). The relationship needs to be formalised in both directions without either programme absorbing the other.

## Decision

1. Zero-TAF is the trust framework: the portable architecture and assurance model. AOP is a **realisation**: AOP procedures, harnesses, and conformance profiles implement Zero-TAF as a profile, exactly as the seed's placement ruling recommended (option C, hybrid).
2. The mapping is **one-directional from each side**: Zero-TAF defines the trust semantics; AOP binds them into procedural execution. Neither programme copies the other's clauses. The binding map (clause-to-clause, ZT↔SEC↔TG) is a Wave-6 `ztaf-bindings` deliverable; until then the correspondence is recorded only at the level of this ADR and the AOP CR.
3. The recognition is recorded in the AOP programme by a CR in `agentic-operating-procedure/aop-governance` (draft: `docs/aop-cr-draft.md`, filing requires owner sign-off as an outward-facing action).
4. ADR-0004 of the AOP programme remains in force and untouched: Zero-TAF is a distinct framework, not an AOP security repository; its revival trigger is not tripped.
5. Zero standing privilege, per-action enforcement, and evidence semantics added by Zero-TAF beyond AOP's current clauses (mandate chains, capability containment, behavioural verification, transparency anchoring, grades) are AOP profile extensions to be developed under Wave 2–5, never patches to AOP repos from this programme.

## Consequences

- The AOP reference harness is the first real Zero-TAF decision-point implementation; its evidence and evaluation work feeds `ztaf-reference-harness` (Wave 4) and `ztaf-evaluation` (Wave 5).
- Divergence between AOP clauses and Zero-TAF semantics is a finding in either programme, not a silent fork.

## What this decision is not

- Not an AOP repository change from this programme — the only AOP-side artefact is the CR itself, filed by the AOP programme's own process.
- Not a claim that AOP is the only possible realisation — it is the first; other harnesses may conform independently.
