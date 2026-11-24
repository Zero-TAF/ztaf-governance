# FIND-0001 — Wave 3 test coverage overstated; two latent defects in ztaf-mandate

| Field | Value |
|---|---|
| Status | Resolved |
| Date | 2026-11-24 |
| Found by | Programme self-review pass (owner-directed) |
| Severity | High (claims accuracy) / High (latent functional defect) |
| Touches | `ztaf-mandate`, CR-ZTAF-003, corrections register #13 |

## Finding 1 — the golden-vector test never ran

`tests/test_vectors.py` declared `class TestGoldenVectors:` without subclassing `unittest.TestCase`. unittest discovery therefore collected **zero** tests from the module: every "tests green" report for Wave 3 (`Ran 15`) counted only the constraint-rule unit tests. CR-ZTAF-003's acceptance criterion "10 vector replays green" was **reported but never executed**. The programme polices exactly this failure mode in others (grade honesty, ASM-3: a claim above the evidence is a failure, not a reporting choice).

**Fix:** the test class subclasses `unittest.TestCase` with per-vector `subTest`; the suite is now 16 tests and the vector replay reports per-vector failures.

## Finding 2 — signature verification silently always failed

`ztaf_mandate.keys.verify` constructed the public key with `Ed25519PrivateKey.from_public_bytes(...)`, the wrong class (public keys load via `Ed25519PublicKey`). The call raised `AttributeError`, which the function's blanket `except Exception` swallowed into `return False`. Consequence: **every** Ed25519 verification — mandates, chains, status lists — returned False. The first real vector replay failed all ten with "status list signature verification failed"; after the one-line class fix, all ten pass and regeneration remains byte-identical.

**Fix:** `Ed25519PublicKey.from_public_bytes`. Lesson recorded: a blanket-except verifier must never be the only guard on a correctness-critical path; the vector suite is that guard, and it had to actually run to matter.

## Resolution state

- `ztaf-mandate` fixed and pushed; 16/16 green; vectors byte-identical under regeneration.
- CR-ZTAF-003 carries a dated correction note (its §4 checklist is otherwise left as written — the correction lives in the finding and the register, not in a silent edit).
- Corrections register row #13 appended in `ztaf-landscape`.

## Process consequence

Every future "tests green" claim in this programme MUST state the collected test count with the discovery invocation (`python -m unittest discover -s tests` from the repository root) and the repos now treat a suite whose count is stable across runs as suspicious. Audit tooling (Wave 5, `ztaf-audit`) checks fixture execution, not just presence — because this programme itself failed that check once.
