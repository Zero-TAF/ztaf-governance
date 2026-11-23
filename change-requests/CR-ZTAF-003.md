# CR-ZTAF-003 — Land Wave 3: Mandate and Evidence

| Field | Value |
|---|---|
| Status | Implemented |
| Date | 2026-11-23 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate, Model |
| Depends on | ADR-ZTAF-0002, CR-ZTAF-002, ADR-ZTAF-0003 |

## 1. Problem statement

Wave 2 made the mandate format and the decision record normative on paper, but registered nothing that proves the semantics executable: the constraint comparison rules of MAN-4 ("implied by") were undefined, no chain-verification algorithm existed in runnable form, no golden vectors existed to detect divergence between spec and code, and the evidence store's chain, batch-root, and third-party verification semantics were unstated.

## 2. Objective

`ztaf-mandate` and `ztaf-evidence` exist: a reference implementation of the mandate chain with golden vectors, and a reference implementation of the evidence store with its verification protocol and the anchoring profile. The spec registers the constraint comparison rules. Both suites run green.

## 3. Scope

- New repositories: `ztaf-mandate`, `ztaf-evidence` (public, MIT).
- `ztaf-spec`: the mandate format document gains §3a — the registered constraint comparison rules (per-type ⊑ definitions; parameter-bound grouped by (field, op) pair; refinement vs violation rules; grade ordering; validity containment). One normative refinement, landed with this CR.
- `ztaf-mandate`: canonical serialisation/hashing; Ed25519 keys; mint; chain verification (signatures, validity containment, attenuation per §3a, chain integrity, revocation, subject binding); signed status-list revocation; **ten golden vectors** (valid chain; broken signature; validity escape; loose budget; revoked intermediate; grade descent; parent-hash mismatch; unknown constraint type; subject mismatch; dropped parent constraint), deterministically regenerable from fixed seeds; unit tests mirroring §3a.
- `ztaf-evidence`: hash-chained store (transparency-attachment-safe record hashing, `zt-genesis` linking), RFC 6962-style batch roots, exports with checkable heads, evidence-bundle assembly (OVR-1 complete-context enforcement); store-export and bundle schemas; the store-semantics document (including the independent-verification protocol and the AOP SEC-8 compatibility note); the transparency anchoring profile (SCITT/RFC 9943 mapping, informative on the wire).

Out of scope: the decision-point integration (`ztaf-reference-harness`, Wave 4); registries (`ztaf-registry`, Wave 4); must-fail fixtures and certification (`ztaf-conformance`, Wave 5); a JSON-Schema validator (deferred by CR-ZTAF-002, unchanged); production persistence and network I/O (both references are explicitly reference-only).

## 4. Acceptance criteria

- [x] Both repositories live and public; MIT; owns/does-not-own READMEs.
- [x] `ztaf-spec` §3a registered; implementation matches it (unit tests mirror the table).
- [x] ztaf-mandate: 15 tests green — 10 vector replays (all failures carry the registered reason class) + comparison-rule units.
- [x] Vectors regenerate byte-identically from the fixed seeds.
- [x] ztaf-evidence: 13 tests green — chain verify, payload tamper, history splice, forged head, required-field enforcement (approver, bundle reference), transparency-attachment hash stability, bundle tamper, incomplete-context rejection.
- [x] Both references run with declared dependencies only (`cryptography` for mandate; none for evidence).

## 5. Cascade audit

- ADR-ZTAF-0001 — residual claim (a), mandates as first-class signed artifacts with offline-verifiable attenuation, is now executable and vector-pinned.
- ADR-ZTAF-0003 — the `ZT-MND-` identifier pattern is exercised by vectors; no new identifier kinds.
- CR-ZTAF-002 — its deferred items (validator, fixtures) remain deferred; this CR's scope was the substrate, not conformance.
- ztaf-spec — §3a added; no existing clause text changed; the spec README's clause conventions unchanged.
- Wave 4 dependencies — `ztaf-reference-harness` now has a chain verifier and an evidence store to integrate.

## 6. What this CR is not

- Not production software — both repositories are labelled reference-only in their READMEs; no CLI, persistence, or network.
- Not the SCITT wire format — the anchoring profile pins the mapping, not the bytes; byte-pinning lands when the IETF receipts profiles publish.
- Not a conformance claim — golden vectors are divergence detection between spec and code, not certification fixtures.
