# ADR-ZTAF-000 — The Concept Zero-Trust Agent Framework

| Field | Value |
|---|---|
| Status | Accepted |
| Date | 2026-11-22 (promoted verbatim from the programme seed) |
| Owner | Emmanuel A. Otchere |
| Layer | Governance |
| Supersedes | — |
| Cross-references | [ztaf-foundations](https://github.com/Zero-TAF/ztaf-foundations) · [ztaf-landscape](https://github.com/Zero-TAF/ztaf-landscape) · foundational research dossier · ADR-ZTAF-0001 |

This record is the programme seed, promoted **verbatim**. Where later verification corrected its claims, the corrections are recorded in Appendix A and in the living register at [ztaf-landscape/docs/corrections-register.md](https://github.com/Zero-TAF/ztaf-landscape/blob/main/docs/corrections-register.md). The seed text itself is never edited.

---

The Concept Zero-Trust Agent Framework

Zero-Trust Agent Framework is an architecture and assurance model for agentic systems where no agent, tool, delegation or action is implicitly trusted. Three breaks from enterprise zero trust:
1. The protected unit moves from access to decision. Agents do not request resources, they exercise delegated authority to take decisions.
2. Agent identity is minted per task and delegated down a chain, not held as a stable principal with a stable perimeter.
3. The decision point must sit outside the model context, not merely outside the network.

It is framed around Nine components: agent identity; delegation chain with signed mandate; zero standing privilege; decision point outside the model; per-action enforcement; capability containment; oversight with usable evidence; behavioural verification; independent append-only evidence.

Why it is not the same as what exists. NIST SP 800-207 stops at resource access. The NIST agent identity design tenets are the closest spine and cover all nine components, but as a checklist, not an architecture. OWASP's 2026 Agentic Top 10 is a risk catalogue. CSA's Agentic Trust Framework (Feb 2026) is a governance maturity model. DrZeroTrust's Agentic Zero Trust paper (May 2026) is the nearest architectural rival. The gap: nothing binds per-decision authority, evidence and assurance grade into one runtime architecture for the acting agent.
 (1/3)
Where it lands. Three options, C recommended: hybrid. Concept and component model portable outside AOP as a reference architecture; AOP realises it as a profile (spec clauses, architecture trust boundaries, conformance tests). AOP already holds four of the nine components natively (AOP-030 outside-model authority check, AOP-024/031/032/033/034, the procedural hierarchy, and ADR-0006's five-axis ladder). On naming, Itis not contesting the phrase: CSA owns Agentic Trust Framework, DrZeroTrust owns Agentic Zero Trust. Claim the substance instead: in agentic systems the trust boundary is the decision.

Four rulings:
Placement: A (leverged inside AOP estate), B (Exists as a separate framework), and can be C (leverage other framework, like NISTs, OWASP, CSA etc. ).
Naming: Review and contest the phrase, or take the narrower "the trust boundary is the decision" claim.
NIST AI Agent Standards Initiative (CAISI RFI due March 9, ITL concept paper due April 2): does AOP position as an implementer under development whose evidence feeds that process, and do we submit.
Landing shape: landscape comparison plus one candidate ADR inside ADR-0004, or a dedicated repository. A repository is the ADR-0004 revival trigger, so that is an ADR decision, not a layout decision.

Bookkeeping. Kanban Card 900 raised on board 75, now in Review awaiting the ruling; tag thread-1573555769226567751 created (the sub-thread needed its own slice-id tag); ruling question and recommendation recorded as card comment 1172; snapshot sibling written to ~/.hermes/profiles/coder/kanban/aop-kanban-snapshot-2026-11-21.md; the channel reference updated with the new snapshot path and the comment/tag API facts discovered. No repository file touched: workspace still clean at 97b5640.
 (2/3)
One caveat on my own evidence: the OWASP 2026 Agentic Top 10 list itself is behind a page I only partially extracted, so I cited it as a risk catalogue with its December 2025 publication date and did not enumerate ASI items in the thread. If you want the ASI entries mapped onto the nine components, say so and I will pull the full list before it goes into any document. (3/3)

---

## Appendix A — Corrections register (2026-11-22 verification)

The seed's claims were subsequently verified against primary sources. Corrections that matter to downstream decisions; the full register with evidence lives in [ztaf-landscape/docs/corrections-register.md](https://github.com/Zero-TAF/ztaf-landscape/blob/main/docs/corrections-register.md).

| # | Seed said | Verified reality |
|---|---|---|
| 1 | NIST "agent identity design tenets" white paper, Oct 2025 | No such document. Actual: NCCoE concept paper (Feb 2026) and the NIST blog *Design Tenets for Agent Identity Management Systems*, **2026-10-27**, ten tenets |
| 2 | NIST tenets are "a checklist, not an architecture" — wide-open ground implied | Correct but narrower: tenet 7 already asserts separation of policy from reasoning; tenet 6 names cryptographically signed mandate statements; tenet 10 asserts immutable append-only evidence. The Zero-TAF claim is the **runtime binding**, not the tenets |
| 3 | Capability containment covered by NIST | Not covered by any NIST artifact — clean Zero-TAF claim |
| 4 | Landscape = NIST, OWASP, CSA ATF, DrZeroTrust | Add OVERT v1.1 (AAL-1..4, Jun 2026), Proof-of-Control (Sep 2026 draft), IETF Transaction Tokens for Agents (Oct 2026), MAS SAFR (Jul 2026), Singapore MGF-Agentic (Jan 2026) |
| 5 | (implicit) identity chaining is "RFC 10043" | RFC 10043 does not exist; cite draft-ietf-oauth-identity-chaining (RFC Editor queue, final approval pending) |
| 6 | "AgentIsolation" as isolation research | Not found; verified referents are IsolateGPT/SecGPT (arXiv 2403.04960) and E2B |
| 7 | "CaMeLs — contextual integrity for agent memory" | CaMeL (arXiv 2503.18813) is control/data-flow information-flow control with capability marks |
| 8 | Macaroons lineage | Verified, but NDSS 2014 (commonly misattributed); Biscuit is the shipping descendant |
| 9 | "A repository is the ADR-0004 revival trigger" | ADR-0004 is the AOP security-repo decision; its trigger does not apply. Zero-TAF's separation is its own decision, formalised via a CR in `aop-governance` (draft pending sign-off) |
| 10 | "AOP-030 ... AOP-024/031/032/033/034" as spec clauses | They are glossary concept identifiers in `aop-foundations`; the normative counterparts are SEC-1..SEC-17 in `aop-spec` |
| 11 | EU AI Act pressure framed for 2026 | Digital Omnibus (EU) 2026/1744 deferred high-risk duties to 2 Dec 2027 / 2 Aug 2028 |
| 12 | OWASP ASI items not enumerated | Verified and enumerated: ASI01 Agent Goal Hijack through ASI10 Rogue Agents, published 9 Dec 2025 |
