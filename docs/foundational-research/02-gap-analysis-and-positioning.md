# Zero-TAF Gap Analysis and Positioning

**Status:** Working research record (pre-founding). Companion to [01-landscape-dossier.md](01-landscape-dossier.md); feeds the org plan (`../../plans/programme-plan.md`).
**Date:** 2026-11-22.

---

## 1. Corrections register — seed document `ADR-ZTAF-000.md` vs verified reality

These must be carried into the formal founding ADR (ADR-ZTAF-0001) so the programme's own claims discipline starts clean.

| # | Seed says | Verified reality | Consequence |
|---|---|---|---|
| 1 | NIST "agent identity design tenets" white paper, Oct 2025 | NOT FOUND as titled/dated. Actual artifacts: NCCoE concept paper **Feb 2026** (comments due Apr 2, 2026) and NIST blog **"Design Tenets for Agent Identity Management Systems", 2026-10-27** with ten tenets | Fix citation everywhere; the tenets are *newer* than we assumed and already claim adjacent ground (see #2) |
| 2 | NIST tenets are "a checklist, not an architecture" — implies wide-open ground | Substantially correct but narrower: tenet #7 already asserts separation of policy from reasoning (our break #3), tenet #6 names cryptographically signed mandate statements, tenet #10 asserts immutable append-only evidence | Zero-TAF cannot claim breaks #3 or C9 *as propositions*. The claim must be the **runtime binding** — the architecture that operationalizes tenets 2/6/7/10 with per-task minting, verified attenuation, action-level linkage, evidence and grades |
| 3 | C6 (capability containment) covered by NIST tenets | **Not covered by any NIST artifact** (verified term/tenet analysis) | C6 remains a clean Zero-TAF claim |
| 4 | Landscape = NIST + OWASP + CSA ATF + DrZeroTrust | Add three 2026 artifacts the seed did not know: **OVERT v1.1** (AAL-1..4 attestation standard, Jun 2026), **Proof-of-Control** (LF Decentralized Trust draft, Sep 2026), **IETF TxT-for-agents** (`agentic_ctx`, `min_assurance_level`, Oct 2026); plus **MAS SAFR** (Jul 2026) and **Singapore MGF-Agentic** (Jan 2026) | Landscape and differentiation docs must engage all; OVERT is the single closest artifact to the gap |
| 5 | (implicit) identity-chaining standard exists as "RFC 10043" | RFC 10043 does not exist; correct cite: **draft-ietf-oauth-identity-chaining-17** (RFC Editor queue, final approval pending) | Use the I-D cite |
| 6 | "AgentIsolation" (academic isolation work) | NOT FOUND; verified referents: **IsolateGPT/SecGPT** (arXiv 2403.04960), E2B | Fix cites |
| 7 | "CaMeLs — contextual integrity for agent memory" | **CaMeL** (arXiv 2503.18813) is control/data-flow IFC with capability marks, not memory contextual integrity | Fix gloss |
| 8 | Macaroons lineage assumed usable | Verified, but **NDSS 2014** (commonly misattributed to USENIX); Biscuit (Eclipse) is the shipping descendant | Cite correctly |
| 9 | ADR-0004 revival trigger: "a repository is the ADR-0004 revival trigger" | ADR-0004 is specifically *Security and Trust Live in Specification and Architecture, Not a Separate Repository*, trigger = "an independent security review body takes ownership... or the threat model outgrows a single chapter of the architecture repository" | Zero-TAF as a *separate framework org* is a different decision; formalize via AOP governance CR, don't cite ADR-0004 as the trigger |
| 10 | "AOP-030 outside-model authority check, AOP-024/031/032/033/034" as spec clauses | AOP-024/030–034 are **glossary concept identifiers** in `aop-foundations`; the normative counterparts are **SEC-1..SEC-17** in `aop-spec` (SEC-1 outside-model check, SEC-2 no self-authorisation, SEC-3 post-approval scoped credentials, SEC-5 fail-closed, SEC-8 append-only tamper-evident case record, SEC-9 approver rules on a case, SEC-11 harness-as-AOP, SEC-16 workload identity, SEC-17 declared egress) | Cross-reference at both levels going forward (concepts + clauses) |
| 11 | EU AI Act pressure framed for 2026 | Digital Omnibus (EU) 2026/1744 moved high-risk duties to **Dec 2, 2027 / Aug 2, 2028** | Frame assurance/evidence value for 2027–2028 readiness |
| 12 | Vendor names: "Zscaler Agent Security Service", "Okta Frontier" as products | NOT FOUND as brands. Correct: Zscaler "zero trust for agentic AI" (Zero Trust Exchange); Okta product = "Okta for AI Agents" (Frontier is their research strand) | Fix in any landscape output |

---

## 2. The verified gap, stated precisely

**Claim survives in this form:**

> No published or shipped framework binds, in one runtime architecture for acting agents: (a) **per-decision delegated authority** via signed mandates minted per task and attenuated down a verifiable chain; (b) a **decision point architecturally outside the model context** that evaluates every action against that mandate and fails closed; and (c) **independent append-only evidence** at decision granularity feeding a **graded assurance scheme** for delegated decisions.

What exists nearby, and why each stops short:

| Framework | Has | Missing from the binding |
|---|---|---|
| NIST tenets (Oct 2026) | All tenets as *assertions* (identity, attenuation, zero standing, policy/reasoning separation, mandates, immutable evidence) | No architecture, no mandate semantics, no C6, no grades — "guideposts" pending an NCCoE SP 1800 build |
| CSA ATF (Feb 2026) | Governance maturity L1–L4, promotion gates, 25 requirements, crosswalks | No runtime decision architecture; per-task identity explicitly open; mandates undefined; no evidence plane |
| DrZeroTrust v3.0 (May 2026) | PEP outside context window; token-exchange delegation; behavioral identity; token isolation; zero standing | Access-frame (protected unit = tool access); per-instance not per-task identity; tokens not mandates; evidence = logs, not independent verification; governance imported from ATF; no grades; vendor-entangled |
| OVERT v1.1 (Jun 2026) | AAL-1..4 assurance grades; non-egress attestation; independent attestation providers; agentic controls incl. delegation-chain attestation | Attestation-first: verifies controls ran; does not define the decision architecture, per-task minted identity, mandate schema, or decision-point placement |
| Proof-of-Control (Sep 2026 draft) | Tamper-evident evidence an agent stayed within granted controls; tier up to "actions cannot run without evidence" | Evidence-first; authority grants are inputs, not per-task minted mandate chains; no identity, no behavioral verification, no grades |
| IETF TxT-for-agents (Oct 2026 draft) | `agentic_ctx` chain claims, monotonic attenuation, `min_assurance_level`, tokens out of LLM reach | Token profile, not architecture; deployment-defined levels; no behavioral verification or oversight layer |
| MAS SAFR (Jul 2026) | Policy-bound execution, real-time validation, auditability — the only regulator naming runtime enforcement | Finance-specific; no mandate-chain model; no graded scheme; no open architecture |
| Singapore MGF-Agentic (Jan 2026) | National governance framework, human accountability core | Voluntary governance; no runtime mechanics |
| Progent / CaMeL / FIDES / AgentSpec | Per-action, out-of-model enforcement (academic) | No identity/minting, no cryptographic delegation, no evidence plane, no grades |
| Entra Agent ID / AgentCore / Okta / gateways | Instance identity, vaults, PEPs | Decision-blind; per-instance identity; no chains; closed |

**The five clean residual claims (defensible, in priority order):**
1. **The decision is the protected unit** — delegation of *decision rights*, not access to resources; architecture evaluates actions-as-decisions under mandate, not requests-under-token.
2. **Signed mandate chains as first-class artifacts** — per-task minted identity, offline-verifiable attenuation (macaroon/Biscuit-style) carrying RFC 8693/9396-grade semantics, bound to the action record. Nothing ships this; SentinelAgent (preprint) is the only academic relative; DrZeroTrust/TxT use tokens, not discrete signed mandates.
3. **Capability containment as a named construct** — absent from NIST tenets entirely; present only as product features (token isolation, sandboxes) and threat catalogues.
4. **The binding** — per-decision authority + evidence + assurance grade operationalized together at runtime (SCITT/RFC 9943-style signed decision statements bound to mandate hashes, receipts verifiable by third parties).
5. **A graded assurance scheme for delegated decisions** — generalizing AOP ADR-0006's five-axis decision-rights ladder into public grades (working name: **Tough Grades, TG-0..TG-4**), keyed to mandate blast radius × evidence depth × verification modality. No scheme for agent-decision assurance exists (EU Act is binary and deferred; ISO 42001 grades management systems; OVERT grades control attestation, not delegated decisions).

---

## 3. Component-by-component coverage matrix (nine components × landscape)

| Component | NIST 800-207 family | NIST agent corpus | AI RMF/600-1 | EU AI Act | ISO 42001 | OWASP ASI | CSA ATF | DrZeroTrust | OVERT | TxT | Singapore MGF | MAS SAFR | Vendors | Academic |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C1 agent identity | stable principal | ✔ (tenet 1) | — | implicit | org-level | ASI03 risk | stable IDs | per-instance | attested ops | proximate_agent | identity recurs | "identified" | instance IDs | DIDs/LOKA |
| C2 signed mandate chain | — | tenets 2,6 (assertion only) | — | — | — | — | named, undefined | token attenuation | attested | chain claims | — | "on behalf" | — | SentinelAgent (preprint) |
| C3 zero standing privilege | per-session | ✔ (tenets 3,4) | — | — | — | ASI03 risk | least privilege | ✔ | — | attenuation | — | least privilege | partial | MiniScope |
| C4 decision point outside model | PDP ≠ model | ✔ tenet 7 (assertion) | — | — | — | — | — | **✔** | — | "out of LLM reach" | — | real-time validation | gateways | CaMeL/Progent/AgentSpec |
| C5 per-action enforcement | per-session access | implied by tenet 8 | — | — | — | — | — | ✔ | top tier (PoC) | per-token | — | ✔ | ✔ products | ✔ papers |
| C6 capability containment | — | **—** | — | partial | — | ASI02/04 risk | segmentation | ✔ | capability control | — | — | transaction limits | token isolation | sandbox/IFC |
| C7 oversight w/ evidence | monitoring | tenet 5 partial | governance | Art.14 (deferred) | org-level | ASI09 risk | HITL by level | partial | HITL attestation | — | accountability core | "owned" | approval UX | WYSIWYS |
| C8 behavioural verification | posture | tenet 9 partial | MEASURE offline | — | — | ASI10 risk | Behavior element | **behavioral identity** | drift attestation | — | — | monitored | ID Protection | AgentDojo et al. |
| C9 independent append-only evidence | logs | tenet 10 (assertion) | incident records | Art.12 (deferred) | records | — | implied logs | write-once logs | **✔ core** | TTS logs | — | auditability | — | SCITT-unbound survey gap |

Legend: ✔ substantive treatment. Read column-wise: no column binds all nine; read row-wise: no row is fully served at *runtime architecture* level anywhere.

---

## 4. Differentiation one-liners (for `ztaf-landscape` and external comms)

- **vs NIST SP 800-207:** same discipline, new protected unit — ZT secured *access to resources per session*; Zero-TAF secures *exercise of delegated decision rights per action*.
- **vs NIST agent tenets (Oct 2026):** we agree with all ten tenets and claim nothing they assert; Zero-TAF is the runtime architecture that *binds* them — mandates as verifiable artifacts, decisions as enforced events, evidence as third-party-verifiable records, grades as the output.
- **vs CSA ATF:** ATF governs *maturity of oversight over agents*; Zero-TAF specifies *the runtime those maturity levels govern*. Profile/crosswalk partner, not rival.
- **vs DrZeroTrust:** convergent on the enforcement point; divergent on the protected unit (access vs decision), identity (instance vs task-minted), and evidence (logs vs independent verification). Cite honestly; differentiate on the mandate.
- **vs OVERT / Proof-of-Control:** they answer "did the controls run and can you prove it"; Zero-TAF answers "what authority did this decision carry and how was it bounded." Complementary layers; pursue crosswalk (TG ↔ AAL).
- **vs IETF TxT-for-agents:** token-transport concretization of one Zero-TAF mechanism; Zero-TAF adds the mandate artifact semantics, the decision point architecture, evidence, and grades. Feed requirements into the draft rather than fork it.
- **vs MAS SAFR / Singapore MGF:** regulatory and governance demand-side validation; Zero-TAF is an implementable open architecture those regimes can cite; finance exemplar aligned to SAFR is an early deliverable candidate.
- **vs vendor PEPs (Entra Agent ID, Prisma AIRS, Zscaler, Okta):** they ship enforcement fragments; Zero-TAF is the open, auditable reference architecture those fragments can be assessed against. Integration/conformance partner posture.
- **Naming posture (ruling 2, restated):** do not contest "Agentic Zero Trust" (DrZeroTrust) or "Agentic Trust Framework" (CSA) — both verified and occupied. Zero-TAF keeps its own name, slogan **"Zero Tough"**, and claims the substance: **"In agentic systems, the trust boundary is the decision."**

---

## 5. Threat-model hooks (for `ztaf-architecture`)

Map OWASP ASI01–ASI10 + MITRE ATLAS agent techniques (AML.T0110/.001/.002, AML.T0080/.000, AML.T0099) onto the nine components as *controls-to-threat* traceability. Verified incident exemplars per component:

- C2/C5 failures → CurXecute CVE-2025-54135 (one approval, silently rewritten trust), tool rug pulls.
- C3 failures → ROME inherited-credential insider case; Replit prod-DB wipe (no zero standing privilege, dev/prod inside agent reach).
- C4 failures → tool poisoning/shadowing (trust decided inside the context window); Lies-in-the-Loop (approval dialog narrated by the agent).
- C6 failures → mcp-remote CVE-2025-6514; cross-server tool shadowing.
- C9 failures → Shai-Hulud worm (no attested action evidence during propagation); Arup deepfake (social enforcement defeated; cryptographic enforcement required).

---

## 6. Standards-engagement traceability (for governance and landscape)

| Body / artifact | Status 2026-11-22 | Zero-TAF action |
|---|---|---|
| NIST AI Agent Standards Initiative | Post-RFI; NCCoE SP 1800 practice guide build starting ("iterative release model") | Participate as implementer; map nine components ↔ ten tenets; submit evidence-plan input |
| NIST tenets blog | Published 2026-10-27 | Cite as the assertion layer; publish the binding as the contribution |
| IETF OAuth identity chaining I-D | Final approval pending | Track; align mandate claims vocabulary |
| IETF TxT-for-agents draft | -03, Oct 2026 | Track; align `agentic_ctx`/`min_assurance_level` with mandate semantics; consider contribution |
| IETF SCITT (RFC 9943 + receipts) | Architecture published Jun 2026 | Adopt as the C9 substrate (Signed Statement = decision record bound to mandate hash) |
| MCP SEPs | No per-task identity/delegation SEP exists | Name the gap; candidate SEP after spec stabilizes |
| A2A v1.0 | Signed agent cards; no delegation primitive | Cite gap; mandate chain positioned as the layer above A2A |
| CSA ATF v0.9.1 | Public review | Produce ZTAF↔ATF crosswalk (maturity levels ↔ TG grades) |
| OVERT v1.1 | Published; shared stewardship (CHAI/AIGovOps) | Produce TG ↔ AAL crosswalk candidate |
| EU AI Act (Omnibus timeline) | High-risk duties Dec 2027 / Aug 2028 | Position evidence plane as pre-compliance instrument (Art. 12/14/43) |
| MAS SAFR | Published Jul 2026 | Finance exemplar alignment candidate |
