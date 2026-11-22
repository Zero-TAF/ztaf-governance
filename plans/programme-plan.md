# Zero-TAF GitHub Org Establishment Plan

**Status:** Draft plan for owner approval. Backed by the research dossier (`../docs/foundational-research/01-landscape-dossier.md`), gap analysis (`../docs/foundational-research/02-gap-analysis-and-positioning.md`), and the estate map (estate-sensitive: held in the programme workspace, not published).
**Date:** 2026-11-22. Target org: `github.com/zero-taf` (exists; `.github` repo created but empty; org description null).

---

## 1. Mission statement (for the org profile)

> **Zero-Trust Agent Framework (Zero-TAF)** — slogan: **"Zero Tough."**
> An architecture and assurance model for agentic systems in which **no agent, tool, delegation, or action is implicitly trusted**. Three breaks from enterprise zero trust: the protected unit is the **decision**, not the access; agent identity is **minted per task** and delegated down a chain of signed mandates; the decision point sits **outside the model context**, not merely outside the network. **In agentic systems, the trust boundary is the decision.**

Org description (short, for the GitHub org field): *"Zero-Trust Agent Framework: an architecture and assurance model where no agent, tool, delegation, or action is implicitly trusted. The trust boundary is the decision."*

---

## 2. The four seed rulings, resolved by the research

| Ruling (ADR-ZTAF-000) | Resolution | Evidence basis |
|---|---|---|
| **Placement** — A (inside AOP estate) / B (separate) / C (leverage NIST/OWASP/CSA) | **C-hybrid, as the seed recommended — now strengthened**: Zero-TAF is its own org (B) because the gap is architectural and estate-wide (serves AOP, OpenDEA agent-foundry, MAMA, government scenarios), while explicitly leveraging NIST tenets as the assertion layer, OWASP ASI/ATLAS as threat vocabulary, CSA ATF as governance-maturity peer, OVERT/Proof-of-Control as assurance peers. AOP realizes Zero-TAF as a profile (spec clauses + trust boundaries + conformance) | No framework binds authority+evidence+grades into one runtime architecture (gap analysis §2); ADR-0004's trigger does not apply (Zero-TAF is not an AOP *security* repo — corrections register #9) |
| **Naming** | Keep **Zero-TAF** / "Zero Tough"; do not contest "Agentic Zero Trust" (DrZeroTrust, verified) or "Agentic Trust Framework" (CSA, verified). Claim the substance: **"the trust boundary is the decision"** | Both rival phrases verified occupied; our name/slogan verified unused anywhere |
| **NIST engagement** | RFI (due 2026-03-09) and concept-paper comments (due 2026-04-02) are closed — **the live window is the NCCoE SP 1800 practice-guide build** ("iterative release model"). Position as implementer: publish the nine-components ↔ ten-tenets map, feed mandate/evidence/grade design as implementation input | Initiative page last updated 2026-11-09; 600+ responses received; no standards published yet |
| **Landing shape** | **Dedicated org + polyrepo estate** (not a single repo, not an ADR inside aop-governance). Formalize with ADR-ZTAF-0001/0002; lodge a CR in `aop-governance` declaring the relationship (not citing ADR-0004 as trigger — it is the wrong decision) | Estate recon: AOP CR pattern requires structural change to go through CR; Zero-TAF is estate-wide, not AOP-internal |

---

## 3. Repo map — six waves, mirroring the proven AOP tier model

Authority ladder descends (a repo depends on the tier below, never above) — same rule as AOP. Naming: `ztaf-` prefix (AOP precedent: `aop-`). Total at maturity: 14 repos; **launch is Wave 1 only (4 repos)**, each later wave gated by a CR.

### Wave 1 — Foundations (launch set)

| Repo | Owns | Key deliverables | Cross-references |
|---|---|---|---|
| `.github` | Org surface | Profile README (mission, slogan, diagram), community files, issue/PR templates, CODE_OF_CONDUCT, CONTRIBUTING, SECURITY.md, LICENSE policy | Links to AOP, WSF, ES, technehub-labs/OpenDEA, MAMA, Source-Engineering, Assessment-Models |
| `ztaf-governance` | Decisions, change control, plans | **ADR-ZTAF-000** (seed, promoted to record), ADR-ZTAF-0001..0007 (below), CR register, findings, templates, programme plan, research/ + this plan/ as founding dossier | AOP `aop-governance` (pattern lineage, CR-ZTAF lodged there), WSF lifecycle lineage |
| `ztaf-foundations` | What Zero-TAF is | Founding paper; the three breaks; the nine components; glossary **ZT-0xx**; non-goals; misconception ladder (AOP-style discipline); parallel principle: *"No agent, tool, delegation, or action is implicitly trusted"* + *"The procedure governs the agent"* (AOP) ↔ *"The mandate governs the decision"* (ZTAF) | WSF concepts specialized (Identity, Action, Event → mandate, decision); ES registry |
| `ztaf-landscape` | Positioning vs the world | Landscape survey (five market categories); claim-by-claim differentiation table (NIST tenets, CSA ATF, DrZeroTrust, OVERT, Proof-of-Control, TxT-for-agents, MAS SAFR, Singapore MGF, OWASP ASI, MAESTRO, vendor PEPs); corrections register (from gap analysis §1); standards-engagement traceability table | Cites every external framework by org-qualified URL |
| `ztaf-adoption` | The practice methodology (owner ruling 2026-11-22: adoption launches in Wave 1, not Wave 6) | The staged adoption methodology by which an organization practices Zero-TAF: inventory → mandates → decision points → evidence → graded operation; roles; anti-patterns; first-90-days quick start | Binds to foundations concepts; methodology-level only (normative clauses land in ztaf-spec, Wave 2) |

### Wave 2 — Normative

| Repo | Owns | Key deliverables |
|---|---|---|
| `ztaf-spec` | The normative specification | Eight-trust-dimension normative model (working set: Identity, Mandate, Authority, Enforcement, Containment, Oversight, Evidence, Assurance); clause IDs **ZT-NM-\<AREA\>-n**; trust/security clauses **ZT-SEC-n**; mandate-chain format (attenuation semantics; RFC 8693 `act`/`may_act` + RFC 9396 `authorization_details` vocabulary; TxT `agentic_ctx` alignment; Biscuit-style offline verification); decision-record schema; **ZT-CC-n** conformance clauses; Agent Skill-contract alignment note (SK-3 "a skill MUST NOT carry authority") |
| `ztaf-architecture` | Reference architecture + threat model | Layered view; the decision-boundary trust model (PDP/PEP outside model context, fail-closed); deployment topologies (sidecar, gateway, harness-embedded); threat model mapped to OWASP ASI01–ASI10 + MITRE ATLAS agent TTPs + MAESTRO surfaces, with controls-to-threat traceability |

### Wave 3 — Substrate

| Repo | Owns | Key deliverables |
|---|---|---|
| `ztaf-evidence` | The evidence plane | Decision record format bound to mandate hash; SCITT/RFC 9943 Signed Statement profile + transparency receipts; Rekor/CT lineage notes; hash-chained case-record compatibility with AOP SEC-8; third-party verification protocol; evidence-bundle schema aligned to AOP-033 |
| `ztaf-mandate` | The mandate chain | Mandate artifact spec + reference implementation (per-task minting, offline attenuation, revocation, chain verification); identity minting protocol; registry interface; test vectors |

### Wave 4 — Realization

| Repo | Owns | Key deliverables |
|---|---|---|
| `ztaf-reference-harness` | The reference decision point | Out-of-model PDP/PEP (fail-closed, per-action), scoped credential broker (issue-after-approval, AOP SEC-3), escalation dispatch, evidence emission; runnable against MCP + A2A examples |
| `ztaf-registry` | Catalogues of mandates/capabilities/decisions | Published-mandate resolution; capability containment catalogue; decision transparency-log bindings; verified provenance chains |

### Wave 5 — Assurance

| Repo | Owns | Key deliverables |
|---|---|---|
| `ztaf-conformance` | Conformance + certification | Profiles for documents and harnesses; **must-fail fixture set**; certification process; **Tough Grades TG-0..TG-4** — the graded assurance scheme for delegated decisions, scored on the five axes generalized from AOP ADR-0006 (reversibility, blast radius, data sensitivity, regulatory exposure, confidence in observed evidence) × evidence depth × verification modality; TG↔OVERT AAL crosswalk candidate |
| `ztaf-evaluation` | Behavioural verification | Metric definitions (decision-level drift, off-mandate action rate, barrier-response discrimination — engaging DrZeroTrust's behavioral identity); benchmark bindings (AgentDojo, τ²-bench, InjecAgent, AgentHarm); canary/honeypot guidance; shadow-mode evaluation; reproducibility protocol |

### Wave 6 — Adoption + bindings

| Repo | Owns | Key deliverables |
|---|---|---|
| `ztaf-adoption` (extension) | Adoption engineering beyond the Wave-1 methodology | Full playbook; enterprise / government scenarios (**CSP-facing scenarios are rebuilt from first principles inside Zero-TAF — no external collaboration materials are used as sources; scoped as a later task**); maturity model (placement decision — this repo vs `Assessment-Models` — **explicitly deferred, scoped as a later task**) |
| `ztaf-examples` | Worked exemplars | At least two: **AOP-profiled exemplar** (extend the 5G RAN anomaly exemplar with mandate/evidence/grade); **finance exemplar aligned to MAS SAFR** (policy-bound execution + real-time validation + auditability) |
| `ztaf-bindings` | Cross-org mapping assertions | ZT↔AOP clause map (SEC-1↔ZT-SEC-*, SEC-8↔evidence record, ADR-0006 axes↔TG); ZT↔OpenDEA catalog bindings (guardrails/controls/digital-identities/risk-register/agent-foundry); ZT↔WSF/ES concept specializations; ZT↔MAMA autonomy rungs; ZT↔SE COTS evidence chains. Predicate vocabulary + statuses reused from ES mappings ("assertions, not copies") |

---

## 4. Identifier scheme (estate-consistent, collision-free)

| Kind | Format | Example |
|---|---|---|
| Glossary concept | `ZT-0xx` | ZT-007 Mandate chain |
| Normative model clause | `ZT-NM-<AREA>-n` (areas: MAN mandate, AUT authority, ENF enforcement, CON containment, EVD evidence, ASM assurance) | ZT-NM-MAN-3 |
| Trust/security clause | `ZT-SEC-n` | ZT-SEC-1 decision point outside model context |
| Conformance clause | `ZT-CC-n` | ZT-CC-9 |
| Architecture clause | `ZT-ARC-n` | — |
| ADR | `ADR-ZTAF-NNNN` | ADR-ZTAF-0001 |
| Change request | `CR-ZTAF-NNN` | CR-ZTAF-001 |
| Assurance grade | `TG-0..TG-4` ("Tough Grades") | TG-3 |
| Cross-org citation | org-qualified URL + target's own IDs | `github.com/agentic-operating-procedure/aop-spec` §SEC-8 |

---

## 5. Founding ADR series (ztaf-governance, Wave 1 content)

| ADR | Proposed title | Core decision |
|---|---|---|
| ADR-ZTAF-000 | The Concept Zero-Trust Agent Framework (seed record) | Promote the existing seed file verbatim as the founding record, with the corrections register attached as an appendix (research integrity) |
| ADR-ZTAF-0001 | The Trust Boundary Is the Decision | Formalize the three breaks + nine components with the narrowed novelty claims (binding, mandate semantics, containment, grades); record that breaks #3/C9 *propositions* are shared with NIST tenets 7/10 and the contribution is the runtime binding |
| ADR-ZTAF-0002 | Zero-TAF Is a Polyrepo Estate Across Six Waves | Repo map above; authority-ladder rule; every repo creation after Wave 1 is a CR |
| ADR-ZTAF-0003 | Identifiers Are ZT-Prefixed and Estate-Consistent | Identifier table above; no invented IDs for external concepts — bind or declare a gap |
| ADR-ZTAF-0004 | Standards Sourcing Cites, Never Copies | Cite NIST/IETF/OWASP/CSA/ISO/MAS/IMDA by URL; programme reasoning marked as such (AOP ADR-0007 pattern); Zero-TAF remains separate from all of them; **no external collaboration materials or standards from industry collaborations are used as sources — all CSP-facing agent-trust scenarios are rebuilt from first principles** (owner ruling 2026-11-22) |
| ADR-ZTAF-0005 | Assurance Is a Tough-Grade Ladder Over Five Risk Axes | TG-0..TG-4 defined on the ADR-0006 axes; grades attach to mandates/decision classes, not models |
| ADR-ZTAF-0006 | AOP Realises Zero-TAF as a Profile | One-directional mappings; reciprocal CR to be lodged in `aop-governance`; four-of-nine realization acknowledged (SEC-1/2/3/5/8/9, ADR-0006, harness) |
| ADR-ZTAF-0007 | Naming and Claims Discipline | Zero-TAF / "Zero Tough"; do not contest occupied rival phrases; claim "the trust boundary is the decision"; citation hygiene rules from the corrections register |

---

## 6. Cross-org reference policy (self-reinforcement rules)

1. **Direction of authority** (from estate map §4): WSF owns foundational concepts; ES owns concept registry + mappings; OpenDEA/technehub-labs owns enterprise guardrails/controls/identity catalogs; AOP owns procedural realization; MAMA owns autonomy measurement; SE owns source/evidence integrity; Assessment-Models carries maturity artifacts; **Zero-TAF owns the trust architecture** — and is cited (not copied) by the others wherever agent authority is governed.
2. **Citation unit:** org-qualified GitHub URLs + the target's own identifiers. Never restate external clause text as ours.
3. **No invented IDs:** bind ZT concepts to WSF/ES concepts; bind controls to `dea:` records; where a target lacks a record, declare a gap and lodge a contribution (NM-INT-5 pattern).
4. **Lodging contributions:** prepared in `ztaf-bindings/contributions/`, filed as CRs in the target repo's own change-request shape, executed only with owner sign-off (outward-facing action). First two candidates when Wave 6 lands: reciprocal citation in `dea-catalog-agent-foundry`; concept assertions in `enterprise-semantics-mappings`.
5. **The AOP CR (inbound, Wave 1):** lodged as **CR-038** in `aop-governance` — "Recognise Zero-TAF as the trust framework whose runtime realisation AOP profiles" — filed and merged 2026-11-23 (PR #22); the repository map §5 carries the one-way direction-of-authority statement and ADR-0004 remains in force (Zero-TAF is a distinct framework, not an AOP security repo).
6. **Governance-pattern reuse:** ADR/CR/finding/templates with ZTAF prefixes (pattern lineage cited to WSF→AOP, not reinvented).

---

## 7. Standards-engagement calendar (2026-2027)

| Window | Action |
|---|---|
| Now → Dec 2026 | Publish Wave 1; nine-components ↔ ten-tenets map in `ztaf-landscape`; monitor identity-chaining I-D (final approval pending) and SCITT receipts profiles (CCF telechat 2026-12-17) |
| Q1 2027 | NCCoE SP 1800 build participation (implementer input; the "600+ responses" cohort is the venue); engage CSA ATF public review with crosswalk comments; TxT-for-agents draft feedback |
| Q2 2027 | Wave 2–3; MCP SEP gap statement (per-task identity / delegation chains) as a discussion post toward a candidate SEP; A2A delegation-gap write-up |
| 2027 → Dec 2027 / Aug 2028 | Frame TG + evidence plane as EU AI Act readiness instruments (Art. 12 logging, Art. 14 oversight, Art. 43 conformity); MAS SAFR finance exemplar |

---

## 8. Wave 1 execution checklist (on approval)

1. `zero-taf/.github`: set org name "Zero-Trust Agent Framework", description (§1), profile README (mission, slogan, diagram, estate cross-links), community-health files; push to the existing empty `.github` repo (first branch: `main`).
2. Create `ztaf-governance`, `ztaf-foundations`, `ztaf-landscape`, **`ztaf-adoption`** (public; **MIT** — matches AOP, the direct sibling programme; ES uses Apache-2.0, WSF none detected).
3. Seed each repo: README with "owns / does not own" sections + authority/tier/wave/status table (AOP convention); move `ADR-ZTAF-000.md` + `research/` + `plan/` into `ztaf-governance` (decisions/ and docs/foundational-research/).
4. Draft ADR-ZTAF-0001..0007 from §5 (status: Proposed).
5. Local workspace: `git init`, connect remotes, mirror estate layout under `/Volumes/512GBORICO/Developer/Zero-TAF/`.
6. ~~(Owner sign-off item) Lodge the AOP CR per §6.5.~~ **Done 2026-11-23: filed and merged as CR-038** (agentic-operating-procedure/aop-governance PR #22).

**Explicitly deferred (need their own CRs):** Waves 2–6 repos; any upstream contributions; any MCP SEP / IETF engagement beyond monitoring; NCCoE submission package.

---

## 9. Risks and open questions

- **Rival convergence velocity:** OVERT, Proof-of-Control, TxT, NIST SP 1800 are all moving in 2026–2027; `ztaf-landscape` needs a refresh cadence (quarterly CR) so claims stay honest.
- **Narrowed novelty discipline:** the founding ADR must enshrine that Zero-TAF claims the *binding*, not the tenets — overclaiming would be caught immediately by NIST's Oct 2026 text.
- **Licence compatibility** across the estate (WSF CC BY 4.0 / ATF CC BY 4.0 / AOP practice) — verify AOP's licence at Wave 1 and match.
- **Naming risk:** "Zero-TAF" vs the acronym collision with TAF (Terrestrial Adjacent... / TAID) — low; verified unused in the agentic-security context; slogan "Zero Tough" is distinctive and verified unused.
- **Governance bandwidth:** 14 repos at maturity is AOP-scale; the wave gates prevent premature estate sprawl (the exact failure ADR-0004 guards against inside AOP).
- **Owner rulings recorded 2026-11-22 (execution constraints):** (1) **No external collaboration materials or standards are used as sources, and none are referenced in Zero-TAF content** — all CSP-facing agent-trust scenarios are rebuilt from first principles (scoped as a later task). (2) **`ztaf-adoption` launches in Wave 1** as the practice methodology. (3) **Whether `Assessment-Models` carries the ZTAF maturity model is explicitly deferred** and scoped as a later task; until decided, maturity artifacts stay out of Wave 1.
