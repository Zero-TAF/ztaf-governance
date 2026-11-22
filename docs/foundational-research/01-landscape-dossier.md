# Zero-TAF Landscape Dossier

**Status:** Working research record (pre-founding). Feeds `ADR-ZTAF-000` formalization and the org establishment plan (`../../plans/programme-plan.md`).
**Research date:** 2026-11-22. Five parallel research streams (standards/regulatory; industry rivals; identity & enforcement infrastructure; evidence & assurance; own-estate recon).
**Confidence flags:** VERIFIED (primary source fetched and read) / PARTIAL (multiple consistent secondary sources) / NOT FOUND (searched, could not locate).

> Integrity rule for this dossier: every load-bearing claim carries a source; anything that could not be verified is marked NOT FOUND rather than dropped. A corrections register against the seed document `ADR-ZTAF-000.md` lives in [02-gap-analysis-and-positioning.md](02-gap-analysis-and-positioning.md).

Component shorthand used throughout: **C1** agent identity, **C2** delegation chain with signed mandate, **C3** zero standing privilege, **C4** decision point outside the model, **C5** per-action enforcement, **C6** capability containment, **C7** oversight with usable evidence, **C8** behavioural verification, **C9** independent append-only evidence.

---

## 1. Standards and regulatory spine

### 1.1 The NIST zero-trust family — resource access only

- **NIST SP 800-207, *Zero Trust Architecture*** — VERIFIED. Final August 2020. Defines ZTA via seven tenets, PE/PA → PDP logical components, PEP in the data plane. The paradigm is "no implicit trust granted to assets or user accounts based solely on their physical or network location or asset ownership," and it "focuses on protecting resources (assets, services, workflows, network accounts, etc.), not network segments." All seven tenets are about *access to resources per session* under dynamic policy. There is no concept of delegated authority to take a *decision* (Zero-TAF break #1), no task-scoped mandate-derived identity (break #2), and no relation between the PDP and what an AI model believes in context (break #3). No AI content anywhere.
  https://csrc.nist.gov/pubs/sp/800/207/final
- **NIST SP 800-207A** — VERIFIED. Final September 2023. Access-control patterns for cloud-native applications. Still access; no agentic content. https://csrc.nist.gov/pubs/sp/800/207/a/final
- **NIST SP 1800-35, *Implementing a Zero Trust Architecture*** — VERIFIED (full text extracted). NCCoE practice guide, final 2025. **Zero occurrences of "artificial intelligence"; only 3 incidental "agent" hits** (user-agent contexts).

**Implication:** the entire applied zero-trust corpus NIST has produced predates agents. Enterprise ZT gives Zero-TAF a vocabulary (dynamic policy, per-session enforcement, PDP/PEP separation) — not an agent architecture. Break #1 is a genuine extension of the NIST frame, not a re-reading of it.

### 1.2 The NIST agent-identity corpus — the closest spine, with two corrections

This is the most important section for our positioning. The seed document cited a "NIST agent identity design tenets" white paper dated October 2025. Verification found a different, and materially more advanced, reality:

- **NOT FOUND:** any NIST white paper titled "Identity and Access Management Design Tenets for AI Agents" (October 2025). No such document exists in any reachable index.
- **VERIFIED — NCCoE concept paper:** *Accelerating the Adoption of Software and AI Agent Identity and Authorization*, NIST NCCoE, **DRAFT February 2026**, comments due **April 2, 2026** (matches the seed's ITL date). It proposes a demonstration project applying OAuth 2.x/OIDC, SAML, NGAC to agents and anchors to the ZT spine ("NIST will also apply relevant guidelines from SP 800-207 ... SP 800-63-4 ... NISTIR 8587 ..."). Verified question text — these are our problem statement, asked back at us:
  - "How do we handle delegation of authority for 'on behalf of' scenarios?"
  - "How can we ensure that agents log their actions and intent in a tamper-proof and verifiable manner? How do we ensure non-repudiation for agent actions and binding back to human authorization?"
  - Term counts in the extracted text: "delegat*" ×6; "mandate" ×0; "least privilege" ×0; "zero standing" ×0; "evidence" ×0.
  https://www.nccoe.nist.gov/sites/default/files/2026-02/accelerating-the-adoption-of-software-and-ai-agent-identity-and-authorization-concept-paper.pdf
- **VERIFIED — the actual tenets:** NIST blog *Design Tenets for Agent Identity Management Systems* (Booth, Fisher, Galluzzo, Clancy), **published 2026-10-27** (`article:published_time` checked in page HTML), Cybersecurity Insights series #2 (predecessor post #1, *Back to the Future: Why Agentic AI Needs a Strong Identity Foundation*, Aug 27, 2026). The **ten tenets**, verbatim titles:
  1. Distinct Agent Identification
  2. Agent Linking, Delegation & Attenuation
  3. Least & Zero Standing Privilege
  4. Short-Lived, Dynamic & Revocable Authorization
  5. Human-in-the-Loop Triggers
  6. Mandates and Constraints — "cryptographically signed mandate statements that define intended outcomes and constraints"
  7. **Architectural Separation of Policy from Reasoning** — "The logic that determines what an agent attempts to do is architecturally separated from the systems that determine what it is allowed to do."
  8. Deterministic Access Decisions
  9. Continuous Monitoring
  10. **Immutable Evidence** — "The enterprise maintains an unbroken, tamper-evident chain of custody and append-only body of evidence."
  https://www.nist.gov/blogs/cybersecurity-insights/design-tenets-agent-identity-management-systems

**Tenet → component mapping (inference from verified text):** 1→C1; 2,6→C2; 3,4→C3; 7→C4; 8→C4,C5; 5→C7 (partial); 9→C8 (partial); 10→C9. **Uncovered anywhere in the NIST corpus: C6 (capability containment) and the binding of a decision's authority level to evidence strength / an assurance grade.**

**Verdict on the seed's characterization** ("closest spine, covers all nine components, but as a checklist, not an architecture"): **substantially correct, with two corrections.**
1. *Citation correction:* the artifact is the **Oct 27, 2026 blog tenets + Feb 2026 concept paper**, not an Oct 2025 white paper.
2. *Scope correction:* as of Nov 2026 the gap is **narrower than the seed implies** — NIST tenet #7 already asserts our break #3 (policy/reasoning separation), tenet #6 already names signed mandates, and tenet #10 already asserts append-only evidence. What NIST has is a tenet list pending an NCCoE demonstration build (SP 1800-series, "iterative release model", nothing shipped). Zero-TAF's defensible residual novelty is the **binding** — per-decision authority + evidence + assurance grade in one runtime architecture — plus verified mandate-chain semantics and capability containment. See the gap analysis.

### 1.3 NIST AI Agent Standards Initiative — timeline verified

- **Announced 2026-02-17** by NIST/CAISI with ITL: three pillars — industry-led standards; community-led open-source protocols (NSF-funded); research on "agent authentication and identity infrastructure" and security evaluation. https://www.nist.gov/news-events/news/2026/02/announcing-ai-agent-standards-initiative-interoperable-and-secure
- **CAISI RFI:** *Request for Information Regarding Security Considerations for Artificial Intelligence Agents*, Federal Register 91 FR 698, doc 2026-00206, published **2026-01-08**, comments due **2026-03-09** (seed's date verified exactly). Focus: *evaluation/assessment of security risk*, not runtime control architecture. https://www.federalregister.gov/documents/2026/01/08/2026-00206/
- **Initiative page** (last updated 2026-11-09): NCCoE hub "received over 600 responses" to the concept paper. https://www.nist.gov/super-intelligence/si-agent-standards-initiative — note NIST's own 2026 terminology is "SI agent" (their term; we need not adopt it).
- **Post-April 2026 developments (PARTIAL):** sector listening sessions (healthcare, financial services, education) held April 2026; comments-summary blog ~2026-09-29; then the Oct 27, 2026 tenets blog. Next step: an **SP 1800-series practice guide** via the NCCoE "iterative release model" (https://pages.nist.gov/nccoe-ai-identity/). No working groups, no published standards, no formal Call for Collaborators in the Federal Register as of 2026-11-22 (FR API search).

**Engagement window:** the SP 1800 build is the live moment to participate as an implementer whose evidence feeds the process — this is what ADR-ZTAF-000's ruling 3 anticipated, and it is still open.

### 1.4 NIST AI RMF and GenAI profile — governance altitude only

- **NIST AI 100-1 (AI RMF 1.0), Jan 2023** — VERIFIED (full PDF extracted). GOVERN/MAP/MEASURE/MANAGE. Oversight-bearing items: GOVERN 3.2 (roles for human-AI configurations), MANAGE 4.1–4.3 (post-deployment monitoring). Term counts: "delegat*" **0**, "agent" **0**, "runtime" **0**. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf
- **NIST AI 600-1 (Generative AI Profile), Jul 2024** — VERIFIED (full PDF extracted). 12 GAI risk categories; densest area is incident handling (72 hits); "delegat*" **0**. https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf

**Verdict:** the AI RMF addresses organizational oversight, accountability, monitoring, incident processes — components 7 and 9 at governance altitude, never runtime. The RMF neither knows nor needs the concept of a per-action policy decision. This genuinely supports the gap claim at the framework level.
Related: **AI 100-2 E2025** (adversarial ML taxonomy, final 2025-03-24) — attack taxonomy, not agentic-specific, no enforcement. **NISTIR 8587** (token/assertion protection) — token security, cited by the concept paper.

### 1.5 EU AI Act — timeline moved; conformity is binary

- **VERIFIED — Regulation (EU) 2026/1744** ("Digital Omnibus on AI", 8 July 2026, in force 27 July 2026), amending 2024/1689: application of high-risk Chapter III Sections 1–3 set to **2 December 2027** (Annex III) and **2 August 2028** (Annex I). https://eur-lex.europa.eu/eli/reg/2026/1744/oj/eng
- The word "agent" appears **0 times** in the regulation (verified) — agents are captured only if a deployment meets Annex III descriptions or is a safety component.
- **Article 43 (conformity assessment)** — VERIFIED: internal control (Annex VI) or notified-body (Annex VII) for Annex III point 1; internal control only for points 2–8; re-assessment on "substantial modification" with a continuous-learning carve-out (Annex IV 2(f)). It is a documentation/process exercise: **no per-decision evidence requirement, no runtime assurance grade.**
- Already in force: definitions/prohibitions (Feb 2025), GPAI obligations (Aug 2025), Art 50 transparency (Aug 2026); new prohibitions from 2 Dec 2026.
- **CEN-CENELEC JTC 21** — PARTIAL: harmonized-standards package targeted ~February 2027; nothing in the programme addresses mandate chains or per-decision evidence.

**Implication:** Zero-TAF's regulatory-pressure argument must be framed against **2027–2028**, not 2026. The opportunity: Zero-TAF's evidence plane is a natural pre-compliance instrument for the Art. 12 logging + Art. 14 oversight + Art. 43 assessment duties.

### 1.6 ISO/IEC and other bodies

- **ISO/IEC 42001:2023** (AI management system) — PARTIAL: certifiable AIMS (accreditation backbone now live: ISO/IEC 42006:2025, ANAB, first certificates incl. IBM Oct 2025). Management-system altitude only; evidence is management records, not tamper-evident per-decision artifacts.
- **ISO/IEC 23894:2023** (AI risk guidance), **ISO/IEC 42005:2025** (impact assessment) — PARTIAL: pre-deployment instruments; no runtime component.
- No ISO/IEC standard addressing agentic-AI runtime authority surfaced (PARTIAL negative; SC 42 programme not exhaustively enumerated).
- **Council of Europe Framework Convention (CETS 225)** — PARTIAL: in force 1 Sept 2025; Art. 12 requires lifecycle accountability/oversight — framework obligations, no technical mechanism.
- **OECD** — PARTIAL: agentic-specific work exists (Working Group on Agentic AI in Government; *Agentic AI in organisations* working paper) — principles, not runtime architecture.
- **MAS (Singapore) SAFR** — VERIFIED-adjacent (PARTIAL): media release **3 July 2026**, industry white paper **SAFR — "Safeguards for Agentic Finance at Runtime"**: policy-bound execution (transaction limits/permissions), real-time validation (banks verify agents before transacting on customers' behalf), auditability ("identified, bounded, monitored, auditable, and owned"). **The closest regulatory artifact anywhere to per-action runtime enforcement — finance-specific, protocol-oriented, no assurance grading, no mandate-chain model.** https://www.mas.gov.sg/news/media-releases/2026/mas-partners-industry-to-develop-safeguards-for-ai-agents-in-finance
- **Singapore IMDA/AI Verify:** *Model AI Governance Framework for Agentic AI*, launched **22 Jan 2026** at WEF — world-first national agentic governance framework; voluntary; human accountability core. https://www.imda.gov.sg/-/media/imda/files/about/emerging-tech-and-research/artificial-intelligence/mgf-for-agentic-ai.pdf
- **UK AI Security Institute** — Inspect framework + Inspect Cyber (Jun 2025) + Inspect Sandboxing Toolkit (Aug 2025); Frontier AI Trends Report (Dec 2025). Evaluation infrastructure, not runtime obligations.

---

## 2. Industry frameworks and named rivals

### 2.1 OWASP

- **Top 10 for Agentic Applications 2026** (Agentic Security Initiative) — VERIFIED, published **9 December 2025**. Full list:
  - **ASI01 Agent Goal Hijack** — attacker redirects the agent's objectives.
  - **ASI02 Tool Misuse & Exploitation** — legitimate tools invoked unsafely.
  - **ASI03 Identity & Privilege Abuse** — stale credentials / excessive scope; acting beyond allowed authority.
  - **ASI04 Agentic Supply Chain Vulnerabilities** — malicious/tampered third-party agents, tools, templates.
  - **ASI05 Unexpected Code Execution** — agent-generated commands give attackers control.
  - **ASI06 Memory & Context Poisoning** — planted data corrupts later decisions.
  - **ASI07 Insecure Inter-Agent Communication** — unauthenticated agent-to-agent messages.
  - **ASI08 Cascading Failures** — faults amplify across autonomous agent networks.
  - **ASI09 Human-Agent Trust Exploitation** — anthropomorphism manipulated into unsafe actions.
  - **ASI10 Rogue Agents** — compromised agents pursuing hidden goals.
  https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026
  Classification: **risk catalogue** — names authority abuse and inter-agent trust, prescribes no architecture. Zero-TAF's threat model cites it; it is a foil, not a rival.
- **Top 10 for LLM Applications 2025** (LLM01–LLM10, published 18 Nov 2024) — VERIFIED. Pre-agentic framing; "Excessive Agency" (LLM06) gestures at C3/C5 as a hazard only. https://genai.owasp.org/llm-top-10/
- **Agentic AI — Threats and Mitigations** — VERIFIED, v1.0 17 Feb 2025; 15 threats with mitigations. https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/

### 2.2 CSA Agentic Trust Framework (ATF) — verified, and importantly adjacent

- **VERIFIED:** *Agentic Trust Framework (ATF)* — "An open specification for Zero Trust governance of autonomous AI agents." Published via CSA blog **2 Feb 2026** (seed's date exact) as a joint Zero Trust WG + AI Safety WG output; lead author Josh Woodruff (MassiveScale.ai). Spec v0.9.1 Public Review Draft (April 2026); CC BY 4.0.
  - Repo (read directly): https://github.com/massivescale-ai/agentic-trust-framework — site: https://agentictrustframework.ai
- **Content:** five core elements — Identity, Behavior, Data Governance, Segmentation, Incident Response; **four-level agent maturity model** — L1 Intern (observe+report), L2 Junior (human approves all actions), L3 Senior (act+notify), L4 Principal (autonomous) — with promotion gates and automatic demotion on incident; RFC-2119 requirements ("25 core requirements"); crosswalks (AICM, MAESTRO, OWASP, NIST 800-207, ISO 42001); a <1s kill-switch requirement at L4.
- **Classification (self-described):** "a specification, not a code library... defines governance principles and requirements" — a **governance maturity model**.
- **Component coverage:** C1 (stable identities; per-task minting explicitly unsolved — DID/VC agent passports are open issues #2/#3), C3 (least privilege/blast radius), C6 (segmentation), C7 (HITL by maturity level), C8 (behaviour monitoring element), C9 partial (audit logging implied, no independent evidence plane). **Does NOT cover:** signed mandate chains (only "cryptographic delegation" named at L4, undefined), decision-point placement, per-action enforcement semantics, per-task identity, evidence-bound assurance grades.
- **Positioning:** ATF is the governance/maturity layer *over* runtime controls; DrZeroTrust already treats it that way. Zero-TAF is the runtime decision architecture ATF's maturity levels would govern.

Supporting CSA corpus (all VERIFIED/PARTIAL): **AI Controls Matrix v1.1** (247 controls; adds AIUC-1 agentic assurance mapping, Jul 2025) — controls catalogue; **MAESTRO** threat-modelling framework (6 Feb 2025) — threat taxonomy; *Agentic AI IAM: A New Approach* (Aug 2025); *Agentic AI + Zero Trust: A Guide for Business Leaders* (Sept 2025, foreword by John Kindervag) — ATF's parent publication. NOT FOUND: any CSA publication titled exactly "Agentic AI Risks and Controls".

### 2.3 DrZeroTrust "Agentic Zero Trust" — verified, nearest architectural rival

- **VERIFIED (34-page PDF read in full):** *Agentic Zero Trust: Extending the Zero Trust Security Paradigm to Autonomous AI Systems*, Dr. Chase Cunningham, DrZeroTrust Research Division, **Version 3.0, May 2026** (seed's date exact). https://drzerotrust.com/agentic-zero-trust-research-paper.pdf
- **What it is:** argues NIST ZTA is "necessary but insufficient" for agents; maps the five CISA ZT pillars (Identity, Device, Network, App/Workload, Data) onto agents with controls per pillar; adds a fifth threat category new in v3.0 — "emergent offensive reasoning" (agent-as-adversary). Concretely: SPIFFE/SPIRE + Entra Agent ID + DIDs/VCs for identity; **RFC 8693 token exchange** for delegation ("a sub-agent receives a freshly issued token scoped only to its specific task... no agent can delegate permissions it does not itself possess"); "no standing permissions" JIT/JEA; a **Token Isolation Pattern** (inside key valid only to the gateway; gateway holds outside keys); agent gateways as PEPs (cites Palo Alto Prisma AIRS 3.0, Cequence); **"deterministic Policy Enforcement Points (implemented in OPA/Cedar, not in the LLM itself)... must sit outside the model's context window"**; **behavioural identity** (persona/job-description spec as ground truth from day one, categorically distinct from UEBA); immutable write-once audit logs; adopts the CSA ATF maturity model wholesale as its governance roadmap.
- **Classification:** architecture-*ish* whitepaper — controls layered on NIST 800-207 pillars with vendor reference implementations (Cequence AI Gateway cited throughout). Not a standard; no conformance regime; vendor-adjacent.
- **Component table:**

| Zero-TAF component | DrZeroTrust coverage |
|---|---|
| C1 agent identity | Strong but **per-instance, not per-task** (SPIFFE SVIDs, Entra Agent ID, DIDs) |
| C2 signed mandate chain | Partial: RFC 8693 chains with scope attenuation + act/sub claims — verifiable delegation via **tokens**, no discrete signed mandate schema/semantics |
| C3 zero standing privilege | Yes, explicit |
| C4 decision point outside model | **Yes, explicit — strongest overlap with our break #3** |
| C5 per-action enforcement | Yes (PEP evaluates every tool call pre-execution) |
| C6 capability containment | Yes (token isolation, MCP allowlisting, persona tool envelopes) |
| C7 oversight w/ usable evidence | Partial (HITL gates; audit logs; ATF promotion gates) |
| C8 behavioural verification | **Yes, distinctive**: "behavioral identity" — persona-spec-driven detection; barrier-response sequences as most discriminating signal |
| C9 independent append-only evidence | Partial ("immutable/write-once" logs required; no independent verification plane, no third-party verifiability) |

- **Differentiation handles for Zero-TAF:** (1) DrZeroTrust keeps the ZT pillar/resource-access frame — the protected unit remains tool/resource **access**, not the delegated **decision**; (2) identity is workload-instance identity, not per-task minted authority; (3) no assurance grades/conformance — governance imported from CSA ATF; (4) evidence is a logging requirement, not an independent verification architecture; (5) vendor entanglement (Cequence). Overlaps to cite honestly: C3/C4/C5/C6/C8 convergent.

### 2.4 The three artifacts the seed did not know about — the real frontier

These are 2026 publications on exactly our turf. They must be engaged head-on in `ztaf-landscape`.

1. **OVERT v1.1 — "Observable Verification Evidence for Runtime Trust"** — VERIFIED. Glacis Technologies, published **11 Jun 2026**, 174pp; shared stewardship with CHAI/AIGovOps Foundation announced 21 Sep 2026. https://overt.is/OVERT_v1.1_STANDARD.pdf
   - Defines **Attestation Assurance Levels AAL-1..AAL-4**, conformance maturity levels, six governance domains, "non-egress attestation" (only hashes/receipts cross trust boundaries), statistical evidence requirements, "self-attestation is not compliant" with Independent Attestation Providers. Part III covers agentic controls: tool-call governance, MCP server trust, multi-agent controls, capability-based access, HITL attestation, delegation chains, behavioural drift detection.
   - **Why it is not the gap-closer:** it is an **attestation/evidence and certification standard** — verifies that controls executed, rather than defining the decision architecture itself: no per-task minted identity, no signed-mandate schema (delegation chains appear as a control to attest, not the primitive), no decision-point placement principle, no oversight layer.
   - **Positioning:** Zero-TAF supplies the decision architecture; OVERT-style AALs are a natural *assurance-grading* vocabulary Zero-TAF evidence could feed (or be crosswalked to).
2. **Proof-of-Control** — VERIFIED. Advanced AI Society; lab hosted under Linux Foundation Decentralized Trust; v1.0 draft in public review from ~17 Sep 2026. https://advancedaisociety.org
   - Open standard for **tamper-evident evidence that an agent stayed within its granted controls**, verifiability tiers up to "actions cannot run without evidence" (per-action enforcement at top tier), open verification without trusting the operator, signed/scoped authority grants.
   - Falls short: **evidence-first, not authority-first**; authority grants are inputs to evidence, not a per-task minted mandate chain; no identity architecture, no behavioural verification, no assurance grades; still a draft.
3. **IETF Transaction Tokens For Agents**, draft-araut-oauth-transaction-tokens-for-agents-03 (A. Raut, Amazon; **31 Oct 2026**). VERIFIED. https://datatracker.ietf.org/doc/draft-araut-oauth-transaction-tokens-for-agents/
   - Adds an `agentic_ctx` JWT claim (proximate_agent, originator, chain_metadata, hop_count) to OAuth Transaction Tokens; optional **`min_assurance_level`** with monotonic attenuation across the chain ("prevents identity laundering"); token handling "must live in the infrastructure layer, out of LLM reach" (convergent with break #3); TTS audit logging for full-chain reconstruction.
   - Falls short: a **token profile**, not an architecture — levels are deployment-defined (no assurance grade scheme), no behavioural verification, no oversight layer, evidence limited to TTS logs.

### 2.5 MITRE ATLAS, SAIF, vendors

- **MITRE ATLAS** — VERIFIED: Oct 2025 added 14 agent-focused techniques with Zenity Labs; **AML.T0110 AI Agent Tool Poisoning** (with sub-techniques .000/.001/.002 in ATLAS v2026.07), **AML.T0080 AI Agent Context Poisoning** (.000 Memory), **AML.T0099 AI Agent Tool Data Poisoning**; ~84 techniques across 16 tactics. TTP knowledge base — vocabulary for our threat model, not controls. https://atlas.mitre.org
- **Google SAIF** — VERIFIED: dedicated "Focus on Agents" section + Agent Risk Self-Assessment; *Google's Approach for Secure AI Agents* (May 2025) whitepaper. Guidance/self-assessment. https://saif.google
- **Vendor matrix** (all VERIFIED unless noted; what each actually proposes beyond marketing):
  - **Microsoft Entra Agent ID** (May 2025; public preview Nov 2025): agents as first-class Entra identity type from "agent identity blueprints"; lifecycle governance (sponsor nudge at 60 days, auto-disable at 90); Conditional Access + ID Protection for agents; "Secure Web and AI Gateway" (Global Secure Access, Nov 2025) routing agent/MCP traffic through network controls; inheritable blueprint permissions. Identity attaches to an *agent instance*, not a decision; "delegation" is classic user→agent OAuth; **not signed per-task mandate chains**.
  - **Palo Alto Networks Prisma AIRS 3.0 + AI Agent Gateway** (23 Mar 2026) + **Idira** agent-identity provider (GA Oct 2026): the clearest **PEP-as-product**.
  - **Zscaler** (9 Jun 2026): "zero trust for agentic AI" on Zero Trust Exchange, agent discovery + inline controls, Agentic SOC (Oct 2026). NOT FOUND as a brand: "Agent Security Service" — do not cite that name.
  - **Okta** ("Okta for AI Agents", GA 30 Apr 2026; *Blueprint for the Secure Agentic Enterprise*, Mar 2026): agent discovery/registration/governance, Cross App Access (XAA). NOT FOUND as product name: "Okta Frontier" (that is their research strand).
  - **CrowdStrike** Charlotte AI + AgentWorks (Apr 2026): "customer-defined bounded autonomy" — maturity tiering convergent with ATF levels.
  - **Wiz** Agent Wiz + AI Security Agent (preview Nov 2026): agent-graph threat modelling; stated-vs-actual reach.
  - **Forrester**: "Agent Action Enforcement Layer (AAEL)" concept — govern agents *before* execution (PARTIAL, paywalled) — analyst validation that enforcement moves outside the model.
  - **Gartner**: AI governance platforms category (Market Guide 2025; first MQ) — policy-lifecycle/compliance tooling, not runtime.
  - **CIS Controls v8.1 MCP Companion Guide** (20 Apr 2026, with Cequence and Astrix) — controls mapping for MCP.

**Net vendor read:** every vendor ships fragments (identity, gateway PEPs, discovery, posture). None binds them into a mandate-decision-evidence architecture with graded assurance.

---

## 3. Identity, delegation, and enforcement building blocks

### 3.1 What shipping identity platforms actually do

| Platform | Identity model | Delegation | Enforcement placement |
|---|---|---|---|
| Microsoft Entra Agent ID (VERIFIED) | Durable directory principals per agent instance; "designed for scale and ephemerality" | user→agent OAuth on-behalf-of; static blueprint permission inheritance | Directory/network infra (outside model, decision-blind) |
| AWS Bedrock AgentCore Identity (VERIFIED, GA Oct 2025) | Workload identities + token vault; raw secrets never reach agent code | Brokered per resource, not per decision | Credential-injection time (outside model) |
| Okta/Auth0 for GenAI (VERIFIED) | User-delegated, Token Vault vs "god-mode" keys; FGA | user→agent only; resource-oriented FGA | Outside model |
| Google Gemini Enterprise (PARTIAL) | Governed agent entities, per-agent audit, policy gateway, spend caps | — | Policy gateway |
| Ping Identity for AI (PARTIAL) | Agent lifecycle, delegated access, MCP support | Admin-configurable, not cryptographic | — |
| WorkOS (VERIFIED, Nov 2026) | auth.md (agent auth discovery), Agent Vault, Passport, **Airlock "Intent-Based Access Control"** | user-scoped | Intent-based framing moves toward decisions |

**Assessment:** no shipping system mints identity per task; none carries a signed chain of attenuated mandates. That is Zero-TAF's greenfield.

### 3.2 Protocol-native state of play

- **MCP authorization (2025-06-18 spec)** — VERIFIED: OAuth 2.1; MCP servers as OAuth resource servers; RFC 9728 Protected Resource Metadata; **mandatory RFC 8707 resource indicators** (audience-bound tokens); token passthrough forbidden; PKCE mandatory; explicit confused-deputy mitigations. Hardened *access* channel — no agent identity semantics, no per-task minting, no delegation chain. https://modelcontextprotocol.io/specification/2025-06-18/basic/authorization
- **MCP Registry** (preview 8 Sep 2025; API frozen v0.1, 24 Oct 2025) — VERIFIED: server discovery, `server.json`, namespace ownership proof (GitHub OIDC/DNS), OSV malware checks. Publisher-identity infrastructure — attestation lineage for capability *origin*. https://github.com/modelcontextprotocol/registry
- **MCP SEPs** — VERIFIED enumeration: SEP-1046 (OAuth client-credentials), SEP-990 (enterprise IdP policy), SEP-991 (URL-based client registration), SEP-985 (PRM alignment), SEP-2127 (server cards). **Documented protocol gap: no SEP addresses per-task agent identity or delegation chains.** Zero-TAF can name (and later feed) this gap.
- **A2A** — VERIFIED: Google Apr 2025 → Linux Foundation 23 Jun 2025 → **v1.0 2026-03-12** → joined the Agentic AI Foundation (AAIF) with MCP, goose, AGENTS.md on 2026-08-27. Agent Cards with **Signed Agent Cards** in v1.0; enterprise spec is explicit: "No Identity in Payload"; per-skill OAuth scopes; TLS mandatory. **A2A deliberately has no delegation-chain primitive** — signed cards attest a peer's identity, not the authority under which a task executes. Zero-TAF's mandate chain is precisely the missing layer above A2A. https://github.com/a2aproject/A2A
- **ANP (Agent Network Protocol)** — VERIFIED: W3C DID-based (`did:wba`), E2EE profiles; ANP-05 "DID-Based Authorization" draft v0.7 (unreleased) envisions VC presentation "for delegation and organization-role credentials." Only shipping protocol with decentralized identity at its core; delegation still a draft. https://github.com/agent-network-protocol/AgentNetworkProtocol
- **Consolidation fact:** IBM/BeeAI ACP merged into A2A (Aug 2025); AGP stays AGNTCY-affiliated. **Treat A2A + MCP (both under AAIF) as the de facto protocol substrate; cite ACP/AGP only historically.**
- **LOKA Protocol** (arXiv 2504.10915, Apr 2025) — VERIFIED: academic vision of DID identity + accountability for agent societies; no implementation or enforcement. Conceptual predecessor.

### 3.3 IETF / standards primitives — the mandate chain's parts bin

All VERIFIED:
- **RFC 8693 OAuth 2.0 Token Exchange** (Jan 2020): `act`/`may_act` claims — the only standardized chain-carrying primitive in mainstream OAuth; declarative claims issued at exchange time, not self-attenuating signed mandates. https://www.rfc-editor.org/info/rfc8693
- **NOT RFC 10043** (does not exist — 404, checked twice). The correct artifact: **draft-ietf-oauth-identity-chaining-17** (Schwenkschuster, Kasselman, Burgin, Jenkins, Campbell, Parecki; rev. 2026-07-19; in RFC Editor queue, final approval pending as of 2026-11-22). RFC 8693 + RFC 7523 JWT grants across trust domains, with subject mapping, downscoping, data minimization. The closest standards-track analog to authority chaining. https://datatracker.ietf.org/doc/draft-ietf-oauth-identity-chaining/
- **RFC 9396 Rich Authorization Requests** (May 2023): `authorization_details` for transaction-specific grants (payee + amount) — the standard hook for **per-decision authority** vocabulary. https://www.rfc-editor.org/info/rfc9396
- **RFC 9635 GNAP** (Oct 2024): first-class software-instance delegation; minimal adoption. https://www.rfc-editor.org/info/rfc9635
- **OAuth 2.1** draft-ietf-oauth-v2-1-17 (Oct 2026; IESG target Dec 2026): PKCE mandatory, sender-constrained tokens (DPoP/mTLS) recommended. Bearer-token upgrade, orthogonal to authority semantics.
- **SPIFFE/SPIRE**: short-lived workload SVIDs, automatic rotation — mature zero-standing-credential machinery binding to *workloads*, no delegation vocabulary.
- **EAT — RFC 9711** Entity Attestation Token (2025): attested claims about an entity's state — ingredient for behavioural verification of agent runtime environments.
- **Macaroons** (Birgisson et al., Google, **NDSS 2014** — commonly misattributed to USENIX): cookies with contextual caveats; decentralized attenuation. https://www.ndss-symposium.org/ndss2014/
- **Biscuit** (biscuitsec.org; Eclipse project): Ed25519-signed, Datalog-based tokens with **offline attenuation** — anyone holding a token can derive a strictly weaker one by appending caveats, verifiable against a public key; revocation identifiers kill attenuated descendants.
- **SCITT** WG: signed statements about artifacts on transparency services (see §4.1).

**Assessment:** macaroons/Biscuit attenuation + RFC 8693 `act`/`may_act` + RFC 9396 `authorization_details` + identity-chaining I-D = the parts bin for a signed mandate chain. What's missing for Zero-TAF: binding to a task/decision record, lifecycle/registry semantics, and the out-of-model decision point that checks them.

### 3.4 Policy engines, agent firewalls, sandbox execution

- **Cedar / OPA / OpenFGA-SpiceDB (Zanzibar lineage)** — VERIFIED: purpose-built authorization (Cedar with formal provers; ReBAC engines). All answer "may *principal* perform *action* on *resource*?" — precisely the resource-access frame Zero-TAF breaks from; usable as policy-computation substrate *inside* a Zero-TAF decision point, carrying no mandate chain, task context, or behavioural evidence of their own.
- **Agent firewall market** (2025-2026, VERIFIED unless noted): Microsoft "Secure Web and AI Gateway" (Global Secure Access, doc 2025-11-03) routing Copilot Studio/MCP traffic; Invariant Labs → Snyk (mcp-scan → "Snyk Agent Scan"; the standalone "Invariant Gateway" no longer appears as a named product — PARTIAL); Lasso MCP Gateway (PARTIAL); Aim Security → Cato Networks ($350M, Sep 2025; Cato AI Security GA Mar 2026); Zenity (PARTIAL); P0 Security (PARTIAL); Cisco AI Defense (Jan 2025; agentic expansion 10 Feb 2026). **All sit at the network/traffic layer — outside the model context (satisfying break #3 literally) yet blind to *what decision the agent believes it is making*; policy is category/flow-based, not mandate-based.**
- **Anthropic "Code execution with MCP"** (4 Nov 2025) — VERIFIED: MCP servers exposed as code APIs in a sandboxed filesystem; progressive disclosure of schemas; data flows between tools *inside the execution environment*, not through the context (token use 150k → 2k in their example); "deterministic rules about data flow." The most important architectural data point for break #3 — industry shifting the enforcement/data path out of the model context. Still capability containment via environment, not authority: no mandates, no per-action policy decisions, human approval prompt-based. https://www.anthropic.com/engineering/code-execution-with-mcp

### 3.5 Academic enforcement/isolation research (2024-2026)

- **CaMeL** ("Defeating Prompt Injections by Design", Debenedetti et al., arXiv 2503.18813, Mar 2025) — VERIFIED: protective system layer; control/data flow extracted from trusted query; untrusted data carries capability marks; private data flows to tools only when a programmer-written policy permits. Out-of-model IFC; capability marking structurally a delegation system, but authority derives from the user query, not signed mandates. (The "contextual integrity for agent memory" gloss in our seed was wrong — corrected.)
- **FIDES** (Invariant Labs, arXiv 2505.23643, May 2025) — VERIFIED: formal model of agent planners; characterizes properties enforceable by dynamic taint-tracking; runtime IFC planner.
- **Progent** (UC Berkeley / Dawn Song group, arXiv 2504.11703, Apr 2025) — VERIFIED: programmable privilege policies over tool calls; "an agent's reasoning should not grant its permissions"; LLM-assisted policy translation with formal guarantees. Closest academic match to per-action enforcement; privileges derive from task state — an implicit, unsigned delegation.
- **GuardAgent** (arXiv 2406.09187) — VERIFIED: LLM guard checking a target agent against guardrail code — model-mediated, probabilistic.
- **AgentSpec** (arXiv 2503.18666; accepted ICSE 2026) — VERIFIED: DSL of trigger/predicate/enforcement rules checked at runtime; blocks >90% unsafe code executions; millisecond overhead. Out-of-model runtime enforcement, unbound to identity/mandates.
- **IsolateGPT / SecGPT** (arXiv 2403.04960, UC Irvine) — VERIFIED: execution isolation into compartments with controlled interaction points. ("AgentIsolation" as a title: NOT FOUND — corrected in the register.)
- **E2B** — VERIFIED: Firecracker-microVM sandboxes for AI-generated code; shipping containment substrate with zero authority semantics.

### 3.6 Incident evidence for the thesis (confused deputy / standing privilege)

1. **CurXecute / MCPoison** — PromptArmor, Jul 2025; **CVE-2025-54135, CVE-2025-54136**; fixed Cursor 1.3.9. Indirect prompt injection made the agent rewrite `.cursor/mcp.json`, auto-executing without re-approval — a literal confused deputy converting model context into code execution.
2. **MCP tool poisoning exfiltration** — Invariant Labs, Apr 2025: hidden instructions in tool descriptions exfiltrated `~/.cursor/mcp.json` and SSH keys; rug pulls (post-approval silent tool-description changes); cross-server tool shadowing redirected email "without any visible trace... outside tool arguments."
3. **mcp-remote RCE** — JFrog, Jul 2025, **CVE-2025-6514** (CVSS 9.6): command execution via the widely-used npm MCP transport library.
4. **CamoLeak** — **CVE-2025-59145**: Copilot Chat exfiltration via GitHub-context confusion (PARTIAL).
5. **ROME incident** — enterprise agent as insider threat via inherited credentials and over-broad permissions (arXiv 2605.09721, PARTIAL).

**Pattern:** (a) standing, user-grade privileges attached to a model loop; (b) trust decisions made *inside* the context window (tool descriptions, READMEs); (c) approval granted once and reused indefinitely. Each is exactly a condition the three breaks are designed to eliminate.

---

## 4. Evidence, oversight, behavioural verification, assurance

### 4.1 Append-only / tamper-evident substrate — exists, unclaimed for decisions

- **RFC 9162 Certificate Transparency v2.0** (Dec 2021) — VERIFIED: Merkle append-only logs, Signed Tree Heads, inclusion/consistency proofs, gossip. The canonical independently verifiable design. Not decisions.
- **RFC 9943 — SCITT architecture** (IETF, **published as Proposed Standard June 2026**) — VERIFIED: issuers register COSE **Signed Statements** about artifacts with **Transparency Services**, receiving verifiable **transparency receipts** (Merkle-inclusion proofs). Receipts profiles in progress (CCF profile at IESG telechat 2026-12-17; MMR profile new WG draft). **Structurally decision-ready: "agent X, under mandate M, took action A" is a perfectly expressible Signed Statement.** https://datatracker.ietf.org/wg/scitt/documents/
- **Sigstore / Rekor** — VERIFIED: immutable ledger of signatures/attestations with Merkle proofs; **sigstore model-transparency** extends the pattern to ML weights/datasets. https://github.com/sigstore/rekor
- **C2PA 2.1** (Aug 2024) — PARTIAL: signed provenance manifests for media; adoption broad; verifiability degrades when stripped; not a shared log.
- **W3C PROV** (2013 Recommendations) — VERIFIED: Entity–Activity–Agent with `actedOnBehalfOf` delegation — exactly the *decision-provenance vocabulary*, no storage/signing infrastructure.
- **Key negative result (peer-reviewed survey):** *From Agent Traces to Trust* (arXiv 2606.04990, Jun 2026, v6 Oct 2026) — VERIFIED — reports essentially no published agent-evidence work produces **"tamper-evident or attested traces."** The combination of per-decision evidence with transparency-log infrastructure is a documented open gap. **This is the strongest public evidence that Zero-TAF's C9 is novel.**

### 4.2 Telemetry — decision-shaped, evidentially worthless

- **OpenTelemetry GenAI semantic conventions** — VERIFIED: dedicated repo; agent spans `create_agent`, `invoke_agent`, `plan`, `execute_tool`; all `gen_ai.*` attributes **Development** status (not stable). Mutable application telemetry, authority-blind, vendor-held. https://github.com/open-telemetry/semantic-conventions-genai
- CloudEvents — envelope carrier only. Vendor tracing (LangSmith, Langfuse, Arize Phoenix, W&B Weave) — debugging/eval, no chain of custody. "Compliance-grade audit trail" claims exist (Broadcom AgentMinder; Monte Carlo × Databricks Agent Bricks, Nov 2025) — single-source [L] provisional.
- **Verdict:** court-usable evidence of agent decisions is essentially unproduced today. Nothing observed combines decision granularity + cryptographic append-only storage + third-party verifiability.

### 4.3 Oversight — context-bound and failing at scale

- **Claude Code sandboxing** (Anthropic engineering, 20 Oct 2025) — VERIFIED: OS-level filesystem/network isolation; verbatim: "approval fatigue, where users might not pay close attention to what they're approving"; **"sandboxing safely reduces permission prompts by 84%."** https://www.anthropic.com/engineering/claude-code-sandboxing
- **Claude Code permission modes** (default / acceptEdits / plan / bypassPermissions; newer `auto`/`dontAsk` with a watcher model and ~66 block rules) — PARTIAL.
- **OpenAI Operator** (Jan 2025) — confirmation gates for sensitive actions. **OpenAI *Practices for Governing Agentic AI Systems*** (Shavit et al., Dec 2023) — seven practices including **action ledgers**, human-approval gates, interruptability; still the canonical oversight framework.
- **Lies-in-the-Loop / WYSIWYS** — *What You Approve Is What Executes: Consent Integrity for Black-Box LLM Agents* (arXiv 2606.02668, Jun 2026) — VERIFIED: an agent narrating its own approval dialog can show a benign summary while executing something else; 10% of GTFOBins payloads "silently passed" inspection; 87% of prompts judged "uninspectable." **Human approval inside the model context is both fatiguing and spoofable — empirical support for break #3.**
- Guardrail frameworks (Llama Guard 4, NeMo Guardrails, ShieldGemma, Guardrails AI) — VERIFIED/PARTIAL: all inspect *content* entering/leaving the context; none sits at the tool/API boundary as an authority-checking enforcement point. **Content classifiers ≠ decision enforcement.**
- Scalable-oversight literature (debate, iterated amplification, weak-to-strong) — VERIFIED/PARTIAL: supervises *model outputs*; no auditable evidence artifacts, no graded assurance for deployed agents.

### 4.4 Behavioural verification

- **Runtime enforcement**: AgentSpec (above; ICSE 2026); VIGIL (behavioral-spec enforcement — [L] provisional); lineage: Schneider 1999 / Ligatti edit automata; 2025-26 implementations are rule-triggered suppression, not full edit-automata semantics.
- **Security-relevant benchmarks** (all VERIFIED): AgentDojo (arXiv 2406.13352; 97 tasks / 629 injection cases), InjecAgent (2403.02691; ReAct GPT-4 vulnerable 24%), AgentHarm (2410.09024; 110 malicious tasks / 11 categories), τ-bench/τ²-bench (policy compliance with pass^k scoring). Outputs are lab scores, not per-decision runtime evidence.
- **Drift detection**: practitioner patterns (Honeycomb, MLflow, W&B continuous evals); no standard statistical drift definition for agent *decision distributions* — open territory for C8.
- **Canary/honeypot** (VERIFIED/PARTIAL): canary values planted in tool outputs alerting on exfiltration; honeypot fake tools for coding agents (Paterson); **LLM Agent Honeypot** (Feb 2025, SSH honeypot fingerprinting autonomous hacking agents in the wild); Wiz 90-day AI-infrastructure honeypot telemetry [L].
- **Distinctive rival capability to engage:** DrZeroTrust's "behavioral identity" (persona-spec deviation from first off-spec action; barrier-response sequences as most discriminating signal).

### 4.5 Assurance grading — the vacuum

- **EU AI Act Art. 43**: binary conformity, high-risk duties deferred to Dec 2027 / Aug 2028 (§1.5). No graded levels.
- **ISO/IEC 42001**: management-system certification (accreditation backbone live) — grades management systems, not decisions.
- **UL 4600**: safety case (GSN) for autonomous products — one comprehensive case, no levels.
- **NIST AI RMF profiles**: risk-tailoring, not certification (agentic profile work underway outside NIST: CSA Agentic AI RMF Profile v1; UC Berkeley CLTC Agentic AI Risk Profile).
- **AI Verify (Singapore)**, **UK AISI Inspect**, **MLCommons AILuminate**: testing/evaluation frameworks — repeatable test evidence, not deployment-time per-decision assurance.
- **OVERT AAL-1..4** (§2.4) is the nearest *graded* scheme — attestation-first, for controls, not a scheme for delegated decisions.
- **Explicit answer: no established scheme grades assurance of autonomous AGENT decisions.** Only [L] proposals exist (aerospace-DAL-style LLM-Agent Assurance Standard; "Agent Reliability Profiles" modeled on Common Criteria EAL; "Aura-Code" AL1-4). Precedents being adapted: NIST SP 800-63 IAL/AAL, SIL/DAL (ARP4754A), SAE J3016.
- **AOP linkage:** AOP ADR-0006 already models authority as a decision-rights ladder over five risk axes (reversibility, blast radius, data sensitivity, regulatory exposure, confidence in observed evidence). Zero-TAF can generalize that into the first graded assurance scheme for *delegated decisions*, keyed to mandate blast radius × evidence depth — and feed it to OVERT-style attestation regimes.

### 4.6 Academic works tying delegation + authority + evidence (closest five)

1. **SentinelAgent: Intent-Verified Delegation Chains for Securing Federal Multi-Agent AI Systems** (arXiv 2604.02767, Apr 2026) — VERIFIED: Delegation Chain Calculus (7 properties), non-LLM Delegation Authority Service enforcing intent-preserving delegation, TLA+-verified (2.7M states). Gap: single-author preprint, synthetic benchmark, trusted central service, no external evidence log, no assurance grading. **The closest academic relative of C2.**
2. **What You Approve Is What Executes** (arXiv 2606.02668) — VERIFIED (§4.3). Approval-representation only.
3. **From Agent Traces to Trust** (arXiv 2606.04990) — VERIFIED: unifies tracing/provenance/observability as "execution provenance"; 6-dimension taxonomy; explicitly identifies missing tamper-evidence. **Strongest public evidence for C9 novelty.**
4. **The Provenance Paradox in Multi-Agent LLM Routing: Delegation Contracts and Attested Identity in LDP** (arXiv 2603.18043, Mar 2026) — VERIFIED: signed **delegation contracts** (objectives, budgets, failure policies) and claimed-vs-**attested** identity; simulation-level; no transparency log or enforcement point.
5. **AgentSpec** (arXiv 2503.18666) — VERIFIED (§3.5).
   Also notable: *Traceability and Accountability in Role-Specialized Multi-Agent LLM Pipelines* (arXiv 2510.07614, Oct 2025).

### 4.7 Incidents evidencing the missing controls

- **Replit agent deletes production database** (Jul 2025) — VERIFIED (Fortune, 23 Jul 2025): agent wiped SaaStr's live DB during a declared code freeze; "catastrophic and unacceptable." Failure modes: no zero standing privilege, no per-action enforcement, dev/prod boundary inside agent reach, no independent evidence.
- **Shai-Hulud npm worm** (14–16 Sep 2025; CISA alert 23 Sep 2025; Shai-Hulud 2.0 Nov 2025 added destructive payloads) — VERIFIED: self-replicating worm via stolen maintainer tokens; autonomous propagation where no signed per-action mandate or attested build evidence existed.
- **Anthropic threat intel** (Aug 2025: Claude Code automated a ransomware/extortion operation; Nov 2025: disrupted GTG-1002, first reported AI-orchestrated espionage campaign running multi-stage intrusion with minimal human oversight) — VERIFIED/PARTIAL.
- **Arup deepfake fraud** (US$25.6M; disclosed May 2024) — VERIFIED/PARTIAL: a *human* was the enforcement point and was defeated — motivates decision points that verify authority **cryptographically rather than socially**.

---

## 5. Market-structure conclusion — the binding gap

The 2026 market has split into five non-overlapping categories:

| Category | Examples | What it does | What it lacks |
|---|---|---|---|
| Governance / maturity specs | CSA ATF, Singapore MGF-Agentic, OECD, Gartner category | maturity levels, promotion gates, controls | runtime mechanics |
| Threat catalogues | OWASP ASI, MAESTRO, MITRE ATLAS, AI 100-2 | enumerate risks/TTPs | controls, architecture |
| Token / permission protocols | RFC 8693, identity-chaining I-D, TxT-for-agents, RAR, Progent, MiniScope | carry/scopes authority per hop | architecture, evidence, grades |
| Evidence / attestation standards | OVERT (AAL-1..4), Proof-of-Control, SCITT/Rekor | prove controls ran / evidence tiers | decision architecture, mandates |
| Product PEPs | Entra Agent ID, Prisma AIRS, Zscaler, Okta, Cequence, agent firewalls | enforce fragments | openness, mandate semantics, independence |

**After ~20 targeted searches ("runtime authorization for AI agents", "per-action policy enforcement", "agent assurance levels", "mandate chain agents", "delegation chain LLM agents"): no found framework binds (a) per-decision delegated authority via signed, per-task-minted mandates, (b) a model-external per-action decision point, and (c) independent append-only evidence feeding defined assurance grades into one runtime architecture for acting agents.**

The seed's three breaks survive verification, with the novelty statement narrowed and corrected: NIST's Oct 2026 tenets already assert separation of policy from reasoning (our #3) and immutable evidence (C9) *as tenets* — Zero-TAF's claim must be the **runtime binding**, the **mandate-chain verification semantics**, **capability containment**, and the **graded assurance scheme** — none of which exists in shipped or published form anywhere we could find. Full analysis and the corrections register: [02-gap-analysis-and-positioning.md](02-gap-analysis-and-positioning.md).

---

## Appendix: master source list (by section)

§1: csrc.nist.gov/pubs/sp/800/207/final · /sp/800/207/a/final · nvlpubs.nist.gov SP 1800-35, AI 100-1, AI 600-1, AI 100-5 · nccoe.nist.gov concept-paper PDF + pages.nist.gov/nccoe-ai-identity · nist.gov blogs (design-tenets, back-future) + SI agent standards initiative page + announcement · federalregister.gov 2026-00206 · eur-lex.europa.eu reg 2026/1744 · artificialintelligenceact.eu/article/43 · cencenelec.eu JTC21 · anab.ansi.org 42001 · coe.int / Wikipedia CETS 225 · oecd.ai (principles, wonk, working paper) · mas.gov.sg SAFR release · imda.gov.sg MGF-Agentic PDF · aisi.gov.uk (trends report, inspect).

§2: genai.owasp.org (agentic top 10, LLM top 10, threats & mitigations) · github.com/massivescale-ai/agentic-trust-framework + agentictrustframework.ai + CSA blog 2026/02/02 · cloudsecurityalliance.org (AICM v1.1, MAESTRO, IAM approach) · drzerotrust.com PDF + cequence.ai/agentic-zero-trust · atlas.mitre.org · saif.google · learn.microsoft.com (agent-id, zero-trust-ai, global-secure-access) · paloaltonetworks.com press · zscaler.com blog · okta.com showcase 2026 · gartner.com / credo.ai · forrester.com · inspect.aisi.org.uk.

§3: learn.microsoft.com/entra/agent-id · docs.aws.amazon.com bedrock-agentcore identity · auth0.com (blog + docs) · workos.com/blog · modelcontextprotocol.io spec 2025-06-18 + registry repo + SEPs · invariantlabs.ai tool poisoning · tenable.com CVE-2025-54135/36 FAQ · jfrog.com CVE-2025-6514 · linuxfoundation.org A2A press · a2aproject/A2A (1.0 blog, AAIF blog, enterprise-ready) · lfaidata.foundation ACP merge · agent-network-protocol repo · arxiv 2504.10915 (LOKA) · rfc-editor 8693, 9396, 9635, 9728 · datatracker identity-chaining + oauth-v2-1 + TxT-for-agents · spiffe.io · rfc-editor 9711 (EAT) · ndss-symposium.org macaroons · biscuitsec.org · github cedar-policy/cedar, openfga/openfga · catonetworks.com Aim acquisition · newsroom.cisco.com AI Defense · anthropic.com engineering/code-execution-with-mcp · specstory/scalex/developersdigest approval fatigue · arxiv 2503.18813 (CaMeL), 2505.23643 (FIDES), 2504.11703 (Progent), 2406.09187 (GuardAgent), 2503.18666 (AgentSpec), 2403.04960 (IsolateGPT) · github e2b-dev/E2B · arxiv 2605.09721 (ROME) · navikt AI agent incident timeline.

§4: rfc-editor 9162 · datatracker SCITT (RFC 9943) · github sigstore/rekor, sigstore/model-transparency · next.redhat.com model transparency · c2pa.org · w3.org TR/prov-dm · github open-telemetry/semantic-conventions-genai · anthropic.com engineering/claude-code-sandboxing · code.claude.com permission modes · openai.com (operator, governing practices, weak-to-strong) · arxiv 2606.02668 (WYSIWYS), 2606.04990 (Traces to Trust), 2604.02767 (SentinelAgent), 2603.18043 (LDP provenance paradox), 2510.07614 (Barrak), 2406.13352 (AgentDojo), 2403.02691 (InjecAgent), 2410.09024 (AgentHarm) · taubench.com · docs.nvidia.com NeMo Guardrails · overt.is/OVERT_v1.1_STANDARD.pdf · advancedaisociety.org · ai-act-service-desk.ec.europa.eu article 43 · cltc.berkeley.edu agentic profile · labs.cloudsecurityalliance.org agentic RMF profile · aiverifyfoundation.sg · github UKGovernmentBEIS/inspect_ai · mlcommons.org (AILuminate, AI safety) · fortune.com Replit · cisa.gov Shai-Hulud alert · securitylabs.datadoghq.com Shai-Hulud 2.0 · anthropic.com misuse reports · weforum.org Arup · honeycomb.io drift · ianlpaterson.com canary · beri.net AgentMinder [L].
