# CR-ZTAF-002 — Land Wave 2: Specification and Architecture

| Field | Value |
|---|---|
| Status | Implemented |
| Date | 2026-11-23 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Depends on | ADR-ZTAF-0002, CR-ZTAF-001, ADR-ZTAF-0001, ADR-ZTAF-0003, ADR-ZTAF-0005 |

## 1. Problem statement

The framework is definitional only: the founding paper states the claim, the breaks, and the nine components, but there is no normative clause text, no mandate format, no decision-record schema, no grade semantics, and no reference architecture or threat model. Per the founding paper §7 and ADR-ZTAF-0002, these land in `ztaf-spec` and `ztaf-architecture` (Wave 2). Neither repository existed.

## 2. Objective

`ztaf-spec` and `ztaf-architecture` exist and are seeded: the eight trust dimensions with their normative clauses (`ZT-NM`), the trust clauses (`ZT-SEC`), the conformance clauses (`ZT-CC`), the mandate-chain format with a normative JSON Schema, the decision-record schema, the Tough Grades semantics; and the layered view, the trust boundaries, the decision-point runtime loop, the deployment topologies, the architecture clauses (`ZT-ARC`), and the threat model mapped to the agentic threat catalogues. The estate tables carry the two repositories as Active.

## 3. Scope

- New repositories: `ztaf-spec`, `ztaf-architecture` (public, MIT).
- `ztaf-governance`: this CR, the register, the estate table rows for Wave 2.
- `.github`: the org-profile estate table refresh.

Out of scope: the mandate reference implementation and test vectors (`ztaf-mandate`, Wave 3); a schema validator implementation (the JSON Schemas are the normative reference; a validator is candidate tooling for a later wave); must-fail fixtures and certification (`ztaf-conformance`, Wave 5); any change to AOP repositories (the clause-level AOP binding lands in `ztaf-bindings`, Wave 6, per ADR-ZTAF-0006).

## 4. Acceptance criteria

- [x] Both repositories live and public; READMEs carry owns / does-not-own sections; MIT licensed.
- [x] Clause identifiers follow ADR-ZTAF-0003; the area register is fixed by the specification (IDE, MAN, AUT, ENF, CON, OVR, EVD, ASM).
- [x] Each of the nine components is carried by at least one normative clause; a coverage table in the spec records the mapping.
- [x] Every `ZT-SEC` clause cites the `ZT-NM` clauses that realise it; every `ZT-CC` clause cites the clauses it operationalises.
- [x] The mandate and decision-record schemas are valid JSON Schema (draft 2020-12).
- [x] The threat model maps OWASP ASI01–ASI10 and the MITRE ATLAS agent techniques to controls, with verified incident exemplars.
- [x] The estate tables in `ztaf-governance/README.md` and the org profile agree with GitHub reality.

## 5. Cascade audit

- ADR-ZTAF-0001 — the residual claims are now carried by normative clauses; the ADR itself is unchanged.
- ADR-ZTAF-0003 — the scheme is exercised; the area register is fixed by the specification (the ADR's parenthetical area list was illustrative; the spec registers the full set of eight).
- ADR-ZTAF-0005 — the Tough Grades are normative-ised in the spec's assurance dimension and grades document; the ADR is unchanged.
- ADR-ZTAF-0006 — the AOP profile mapping is unaffected; the specification is now the target AOP binds to.
- CR-ZTAF-001 — the estate table rows for Wave 2 move from "Gated by CR" to "Active" through this CR.

## 6. What this CR is not

- Not the mandate reference implementation — the format is normative here; code and vectors are Wave 3.
- Not a conformance programme — no fixtures, no certification, no grade assignments to real deployments.
- Not an AOP change — Zero-TAF does not patch AOP repositories; the profile binding is a Wave-6 deliverable.
- Not a threat catalogue — the threat model cites OWASP, MITRE ATLAS and MAESTRO; it does not restate them.
