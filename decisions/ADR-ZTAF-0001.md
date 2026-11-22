# ADR-ZTAF-0001 — The Trust Boundary Is the Decision

| Field | Value |
|---|---|
| Status | Proposed |
| Date | 2026-11-22 |
| Owner | Emmanuel A. Otchere |
| Layer | Model |
| Supersedes | — |
| Cross-references | ADR-ZTAF-000 · foundational research dossier (`docs/foundational-research/`) · [ztaf-foundations](https://github.com/Zero-TAF/ztaf-foundations) · [NIST: Design Tenets for Agent Identity Management Systems (2026-10-27)](https://www.nist.gov/blogs/cybersecurity-insights/design-tenets-agent-identity-management-systems) · AOP `aop-spec` SEC-1/SEC-2, `aop-governance` ADR-0006 |

## Context

Verification of the seed concept (2026-11-22, see the foundational research dossier) established:

- Enterprise zero trust (NIST SP 800-207 and its whole applied family, including SP 1800-35) protects *access to resources per session* and contains no AI content.
- NIST's agent-identity tenets (2026-10-27) assert, as tenets: distinct agent identification; delegation and attenuation; least and zero standing privilege; signed mandate statements; architectural separation of policy from reasoning; deterministic access decisions; continuous monitoring; immutable evidence. They are guideposts pending an NCCoE practice-guide build — no architecture exists behind them.
- The 2026 field has converged on fragments: governance maturity models (CSA Agentic Trust Framework, Singapore MGF-Agentic), threat catalogues (OWASP ASI, MITRE ATLAS, MAESTRO), token/permission protocols (OAuth token exchange, identity chaining, Transaction Tokens for Agents), attestation standards (OVERT AAL-1..4, Proof-of-Control), and enforcement products (identity platforms, agent gateways, network controls).
- No published or shipped framework binds per-decision delegated authority, a model-external per-action decision point, and independent append-only evidence feeding a graded assurance scheme into one runtime architecture.
- Deployment incidents (CurXecute CVE-2025-54135, MCP tool poisoning, the Replit production-database deletion, the Shai-Hulud worm) each map onto missing components: standing privilege, in-context trust decisions, one-time approvals, no independent evidence.

## Decision

Zero-TAF's protected unit is the **decision**: the exercise of delegated decision rights by an agent, not the access request that precedes it. In agentic systems, the trust boundary is the decision.

Three breaks from enterprise zero trust:

1. **The protected unit moves from access to decision.** Agents do not request resources; they exercise delegated authority to take decisions. The architecture evaluates actions-as-decisions under mandate.
2. **Agent identity is minted per task and delegated down a chain of signed mandates**, not held as a stable principal with a stable perimeter.
3. **The decision point sits outside the model context**, not merely outside the network. An enforcement point that reads the context, or is reasoned about by the model, is not a decision point.

The architecture binds nine components: agent identity; delegation chain with signed mandate; zero standing privilege; decision point outside the model; per-action enforcement; capability containment; oversight with usable evidence; behavioural verification; independent append-only evidence.

**Claims discipline.** Zero-TAF agrees with the NIST ten tenets and claims nothing they assert. The residual claims are the binding: (a) mandates as first-class signed artifacts with per-task minting and offline-verifiable attenuation; (b) capability containment as a named construct; (c) the runtime binding of per-decision authority, evidence, and assurance grade; (d) a graded assurance scheme for delegated decisions (ADR-ZTAF-0005).

## Consequences

- `ztaf-spec` (Wave 2) must define the mandate format, the decision record, and the grade semantics; this ADR is its upstream requirement.
- `ztaf-landscape` must engage OVERT, Proof-of-Control, Transaction Tokens for Agents, and DrZeroTrust claim-by-claim, and refresh quarterly by CR.
- AOP realises this architecture as a profile (ADR-ZTAF-0006): SEC-1/SEC-2 (out-of-model authority check, no self-authorisation) and ADR-0006's five risk axes already realise components 4/5 and the grade axes respectively.

## What this decision is not

- Not a claim over the NIST tenets — we bind them, we do not own them.
- Not a governance maturity model — CSA ATF governs maturity over agent oversight; Zero-TAF specifies the runtime that maturity governs.
- Not an enforcement product — it is the reference architecture products can be assessed against.
- Not a network zero-trust deployment — SP 800-207 remains the authority for that domain.
