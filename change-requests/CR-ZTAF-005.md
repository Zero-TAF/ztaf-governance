# CR-ZTAF-005 — Land Wave 5: Conformance and Evaluation

| Field | Value |
|---|---|
| Status | Implemented |
| Date | 2026-11-24 |
| Owner | Emmanuel A. Otchere |
| Layer | Estate |
| Depends on | ADR-ZTAF-0002, ADR-ZTAF-0005, CR-ZTAF-004, FIND-0001 |

## 1. Problem statement

The grades existed as semantics but nothing could produce a grade card: no must-fail fixture runner, no audit engine, and no behavioural-verification metrics — so TG-3's "behavioural verification operational" (ASM-4) and TG-2's "must-fail fixtures passed" (ASM-5) were unprovable, and grade honesty (ASM-3) had no enforcement tool.

## 2. Objective

`ztaf-conformance` and `ztaf-evaluation` exist: an executable must-fail set, the `ztaf-audit` engine (deployment bundle in → grade card out, clause failures named), and `ztaf-eval` (baseline, drift, off-mandate rates, canary trips, an ACTIVE/INSUFFICIENT-DATA verdict for ASM-4). Both suites green; the audit fails the bundles it should fail and passes the one it should pass.

## 3. Scope

- New repositories: `ztaf-conformance`, `ztaf-evaluation` (public, MIT).
- `ztaf-conformance`: nine checks mapped to ZT-CC clauses; **grade honesty spine** (claimed > evidenced → CC-13 failure; TG-3 claim without receipts → CC-12 failure); the must-fail runner (mandate vectors + three evidence tampers + three config rejections; a single MUST-FAIL VIOLATION fails the set — and a blind verifier makes it fail, the FIND-0001 lesson encoded as a test); `ztaf-audit` CLI; the certification-process outline (stages and non-goals; the programme certifies no one).
- `ztaf-evaluation`: `baseline()` / `check()` over evidence exports — per-class rates, rule-distribution TVD, off-mandate rate, canary trips via `parameters_hash`, `ACTIVE`/`INSUFFICIENT DATA` honesty; `ztaf-eval` CLI; `docs/metrics.md` (formulas, SHOULD-level thresholds, operational rules).
- Both consume exactly what Wave 4's demo writes — the toolchain is one continuous path: card → bootstrap → demo → export → audit → grade card → baseline → check.

Out of scope: fixture certification itself (the outline only; standing up a scheme is owner-gated); TG-4 third-party attestation (human process); new metric research beyond the defined set.

## 4. Acceptance criteria

- [x] Both repositories live, public, MIT, owns/does-not-own READMEs.
- [x] Conformance: 8 tests green — compliant TG-2 bundle passes; grade inflation fails CC-13; TG-3 claim without receipts fails CC-12; unpassed fixtures fail CC-13; tampered evidence fails CC-11; the must-fail set passes honestly and fails against a blind verifier.
- [x] Evaluation: 6 tests green — counts, nominal, drift alarm, off-mandate alarm, canary trip, insufficient-data honesty.
- [x] Discovered test counts stated with the discovery invocation (FIND-0001 lesson).

## 5. Cascade audit

- ADR-ZTAF-0005 — Tough Grades are now auditable: the grade card is the grade's public surface.
- ADR-ZTAF-0001 — the binding's third leg (grade) is enforced by tooling, not prose.
- CR-ZTAF-003/004 — fixtures consume the mandate vectors; audit consumes the harness's artifacts.
- ztaf-adoption — Stage 4's "must-fail runs" and Stage 5's "grades earned continuously" now have their tools.

## 6. What this CR is not

- Not a certification scheme — the programme certifies no one; TG-4 attestation remains a human process outlined, not operated.
- Not new metric research — the metric set is deliberately small and legible (ASM-4's point is existence and actionability, not sophistication).
- Not a gate on Waves 6 — bindings and examples proceed on their own CR.
