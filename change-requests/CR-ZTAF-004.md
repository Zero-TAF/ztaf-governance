# CR-ZTAF-004 — Land Wave 4: Reference Harness and Registry

| Field | Value |
|---|---|
| Status | Implemented |
| Date | 2026-11-24 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Depends on | ADR-ZTAF-0002, CR-ZTAF-002, CR-ZTAF-003, FIND-0001 |

## 1. Problem statement

The framework had normative clauses and verified substrates but no runnable decision point: the runtime loop existed only as a diagram, and the registry/revocation operations existed only as a format. Adoption also had no on-ramp: an organization with agents under Agentic Operations had no path from a discovery card and profile to a governed agent on a Zero-TAF chain.

## 2. Objective

`ztaf-reference-harness` and `ztaf-registry` exist: the nine-step runtime loop as a runnable decision point with a demo CLI, Agentic Operations adapters (discovery card → policy, profile → subject, bootstrap → chain + registry), and a file-backed registry with down-chain revocation and signed status lists. Both suites green; the demo runs end to end and writes exactly the artifacts Wave 5 consumes.

## 3. Scope

- New repositories: `ztaf-reference-harness`, `ztaf-registry` (public, MIT).
- `ztaf-reference-harness`: policy engine + grade register (rejects agent-mutable config, ENF-6); the loop (resolve → verify → grade-sufficiency → evaluate → escalate/bundle → broker single-use credentials → execute-after-record → emit); **AO adapters** (`ztaf_harness/ao.py`): `card_to_policy_fragment` (CON-1 declared capabilities), `profile_to_subject` (IDE-1 subject binding), `bootstrap` (AO onboarding → attenuated mandate + registry entry + grade register); `ztaf-harness demo | bootstrap | audit-store` CLI; example card/profile/actions; 10 tests.
- `ztaf-registry`: FileRegistry (mandates with parent linkage, **revocation propagating down-chain** MAN-6, agents carrying AO bootstrap output, capability provenance CON-4); signed status lists in the exact `StatusChecker` format; `ztaf-registry` CLI (init/publish/revoke/register-agent/add-capability/status-list/resolve/agents); 6 tests.
- Reference card/profile JSON shapes defined here are the programme's **proposal** for the machine-readable layer the `Agentic-Operation` definitions (README-level as of 2026-11-24) call for; lodging upstream is owner-gated (ADR-ZTAF-0004 rule 3).

Out of scope: real side effects (the executor is a pure simulator); production persistence/HA for the registry (fail-closed on unavailability is the reference behaviour); the AOP clause binding (Wave 6).

## 4. Acceptance criteria

- [x] Both repositories live, public, MIT, owns/does-not-own READMEs.
- [x] Harness: 10 tests green (permit; escalation → three records: case, ruling, enforced execution with approver attribution; deny paths; grade insufficiency per SEC-13; shadow mode records-but-does-not-enforce; config-honesty rejection; AO adapters including a chain-verified bootstrap).
- [x] `ztaf-harness demo` runs end to end: bootstrap → permit (€150) → escalation ruled on the bundle (€350) → deny (undeclared tool); evidence chain verifies; registry + signed status list + export written.
- [x] Registry: 6 tests green — publish/resolve, revoke-propagation (descendants fall, ancestors survive), signed status list verified through the real `StatusChecker`, stale-list rejection.
- [x] Discovered test counts stated with the discovery invocation (FIND-0001 lesson).

## 5. Cascade audit

- ADR-ZTAF-0001 — the binding now runs: grade sufficiency denies per action in a real loop (SEC-13 exercised by test).
- ADR-ZTAF-0006 — the AO bootstrap adapter is the first non-AOP on-ramp; the AOP profile relationship is unaffected.
- CR-ZTAF-003 — the substrates are consumed as libraries (mandate chain verification, evidence store, bundles); no substrate changes needed.
- Wave 5 dependencies — the demo's artifacts define the audit bundle; evaluation reads the same exports.

## 6. What this CR is not

- Not production software — simulator executor, JSON persistence, no network.
- Not an AO estate change — the card/profile shapes are proposals held in this programme; lodging them upstream is a separate, owner-gated action.
- Not the conformance programme — Wave 5 owns fixtures and the audit engine.
