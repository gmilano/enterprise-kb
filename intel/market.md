---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 🗺️ Mapa de mercado — Enterprise

> Key players, market map and opportunities. Figures are attributed to their source
> because they disagree with each other; where they conflict, that is stated rather than
> averaged away.

## The 2026 frame in one paragraph

Enterprise AI spend is real and large — Menlo Ventures puts enterprise AI deployment
spend at **$176.8B as of September 2026, up 5.4x year on year** (single-vendor estimate,
treat the precision with care). Gartner's forecast, widely cited, is that **40% of
enterprise applications will embed task-specific agents by end of 2026, up from under 5%
in 2025**. But the binding constraint has moved from capability to **governance and
production-readiness**: IBM's October 2026 EMEA study found 80% of surveyed executives had
an AI incident escalate to board or C-suite in the past year while only 40% changed
governance policy in response, and Cognizant launched a dedicated EMEA AI unit on
28 July 2026 explicitly because agent pilots were failing to reach scale. The commercial
opening is therefore **not** "build an agent" — it is "make an agent auditable, identity-bound
and recoverable enough to go to production."

## Players globales

| Company | Type | Strength | Weakness / opening for Globant |
|---------|------|----------|-------------------------------|
| Microsoft | Hyperscaler + framework | Copilot distribution, M365/Azure estate, Semantic Kernel (MIT) | Framework story is in flux — AutoGen deprecated and the Agent Framework repo is currently unreachable (see `agents/top.md`). Clients need a stable migration path. |
| AWS | Hyperscaler | Bedrock, enterprise data gravity | Weaker opinionated agent layer; integration work is the gap. |
| Google | Hyperscaler + models | Gemini, A2A protocol origin | Enterprise change-management depth. |
| OpenAI | Model + SDK | Agents SDK (MIT), AGENTS.md donation | Not a systems integrator; no vertical delivery. |
| Anthropic | Model + protocol | Claude; **donated MCP to the Linux Foundation** | Deliberately partner-led delivery — **Globant has a multi-year alliance (30 Jun 2026)**. |
| Salesforce | SaaS incumbent | Agentforce, CRM data | Lock-in and per-agent pricing resistance; open alternatives (Twenty) gaining mindshare. |
| ServiceNow | SaaS incumbent | Workflow system of record | Expensive to extend; agent layer over it is an integration play. |
| SAP | ERP incumbent | Core ERP estate | Slow agentic surface; the S/4 estate is the single biggest agent-enablement backlog in the market. |
| Databricks | Data platform | Data + model proximity | Needs delivery partners for vertical outcomes. |
| ClickHouse | Data platform | **Acquired Langfuse 16 Jan 2026** ($400M Series D same day) | Signals observability consolidating into the data layer — a stack decision clients will ask about. |
| Mistral | EU sovereign model | Sovereignty positioning; capacity reservation deals | Narrower ecosystem than US hyperscalers. |
| Cognizant | SI competitor | **Launched EMEA AI unit 28 Jul 2026** | Direct competitor on exactly the pilots-to-production pitch. |
| UiPath / Automation Anywhere | RPA incumbents | Installed automation base | Agentic transition is their existential risk and a migration opportunity. |

**Open-source governance shift to watch:** the Linux Foundation's **Agentic AI Foundation
(AAIF)**, formed 9 Dec 2025, now stewards MCP (Anthropic), goose (Block) and AGENTS.md
(OpenAI). Visible in the repos: `block/goose` → `aaif-goose/goose`, and
`modelcontextprotocol/servers` relicensing MIT → Apache-2.0. For a CTO worried about
single-vendor protocol risk, **"the protocol is foundation-governed, not vendor-owned"**
is now a true and checkable statement. Adoption scale: by mid-2026 over **10,000 MCP
servers** reported in production, with MCP SDKs downloaded ~97M times/month.

## Opportunities by region

### North America

- **Regulatory shape: state patchwork, no federal law.** Five state AI laws already bind
  companies as of August 2026 — including California's frontier-model law **SB 53**, Texas
  **TRAIGA**, and Illinois' rules on AI in employment. Colorado repealed and replaced its
  original AI Act (signed 14 May 2026) before it ever took effect. A White House national
  AI legislative framework (20 Mar 2026) asked Congress to preempt state law; the
  bipartisan preemption draft released in June 2026 has since stalled.
- **Opportunity: multi-state compliance as a product.** Because preemption failed, a US
  national rollout must satisfy several different state regimes at once. Build a
  **policy-as-code compliance layer** (OPA/Cerbos + Giskard evidence capture) that proves
  per-state conformance from one deployment. Standards to anchor on: **NIST AI RMF** and
  **ISO/IEC 42001**.
- **Adoption: saturated at the top, so differentiate on production.** Stanford's 2026 AI
  Index reports North America at 90% organisational AI use; NVIDIA's data says 70% active
  usage; the US Census BTOS figure is far lower (5.4–19.8%) because it asks about a short
  recent window. These are not contradictory — they measure "any use" vs "current use".
  **Takeaway: the pitch is not adoption, it is getting the 40% of enterprises stuck in
  pilots into production.** NA holds ~39.6% of the enterprise AI agent market.
- **Competitive note:** Anthropic reportedly surpassed OpenAI in US business adoption for
  the first time (secondary, Forbes-sourced — verify). Relevant to Globant given the
  Anthropic alliance.

### EMEA

- **Regulatory shape: one regime, and the deadline moved.** The **Digital Omnibus on AI,
  Regulation (EU) 2026/1744**, deferred the AI Act's high-risk obligations:
  **Annex III (standalone high-risk — recruitment scoring, credit assessment, biometrics,
  education) moved from 2 Aug 2026 to 2 December 2027**, and **Annex I (AI embedded in
  regulated products) from 2 Aug 2027 to 2 August 2028**. Annex III *scope* did not change,
  only the date. National regulatory sandboxes move to 2 Aug 2027; the content-marking
  grace period for systems already on market runs to 2 Dec 2026.
  *Confidence: high — independently corroborated by this KB's energy pass, which recorded
  the same regulation and dates from different sources.*
- **Opportunity: the deferral is a sales window, not a reprieve.** IBM reports **41% of EU
  executives are accelerating governance investment ahead of the high-risk obligations**,
  with a further 35% on structured compliance plans. Clients have ~12 months of slack and
  budget already allocated — the right offer is a **conformity-readiness programme** that
  produces the Annex III technical documentation as a by-product of building the agent.
- **Opportunity: EU-origin assurance stack as sovereignty answer.** A fully EU-origin
  toolchain can be assembled today and is a genuine differentiator against US-stack SIs:
  [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) (Apache-2.0, Paris)
  for evaluation, [deepset-ai/haystack](https://github.com/deepset-ai/haystack)
  (Apache-2.0, Berlin) for orchestration, Mistral for models, vLLM (Apache-2.0) for
  self-hosted serving. Also in play: the **Apertus** sovereign initiative and Aleph Alpha.
- **Adoption: the SME gap is the volume play.** EU enterprise AI adoption benchmarked at
  **19.95% in 2025** (+6.47pp YoY) with a **38-point gap between large (55%) and small
  (17%) enterprises** — far below NA headline figures, which is where the growth is.
- **Competitive note:** Cognizant's EMEA AI unit (28 Jul 2026) targets this exact pitch.

### APAC

- **Regulatory shape: diverging, and binding in several markets.** South Korea's **AI Basic
  Act took effect January 2026** — the region's first comprehensive AI statute, with
  high-impact-system obligations and roughly a one-year implementation runway. **Vietnam's
  AI law is effective 1 March 2026**, described as Southeast Asia's first binding AI law.
  China has the most developed regime, layered across generative AI, algorithmic
  recommendation and deepfakes. Japan's **AI Promotion Act** is deliberately light-touch and
  pro-innovation; Singapore runs sandboxes and voluntary frameworks, with **MAS** still
  consulting on AI risk management guidelines covering third-party AI providers. India
  signalled possible dedicated AI legislation in July 2026; Indonesia's national rules are
  expected as a Presidential Regulation; Taiwan set up a national AI coordinating committee
  in March 2026.
- **Opportunity: per-market compliance, not a regional rollout.** There is no APAC-wide
  regime, so the deliverable is a **jurisdiction-switchable policy layer** — the same agent,
  different obligations per market, evidenced separately. Data sovereignty and localisation
  remain strategic priorities, which favours self-hosted vLLM over API-only designs.
- **Opportunity: the readiness gap is the actual work.** BCG reports APAC is the
  second-fastest region globally for GenAI adoption but **only ~30% of enterprise workflows
  are mature enough to support AI safely at scale**. That 70% is data and process
  remediation — unglamorous, large, and a durable engagement.
- **Opportunity: APAC-origin open source is Tier-1 now.**
  [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) (Apache-2.0,
  36,363 ★) and especially
  [agentscope-ai/agentscope-java](https://github.com/agentscope-ai/agentscope-java)
  (Apache-2.0, 6,435 ★) matter because APAC enterprise cores are JVM. The Frappe/ERPNext
  stack is India-origin and the natural ERP base for an India engagement.
- **Risk to flag:** training-data disclosure is the live flashpoint — Korea decided against
  adding a text-and-data-mining exception to its Copyright Act in February 2026.

### LATAM

- **Regulatory shape: fragmented, privacy law is the real gate.** **Peru enacted the
  region's first AI law**; Brazil and Chile were expected to follow. Colombia adopted
  national AI policy **CONPES 4144** (Feb 2025), a programme through 2030 rather than
  binding obligations. **Uruguay is the first Latin American country to sign the Council of
  Europe's AI treaty.** Mexico still has no AI-specific legislation. In practice the
  binding constraints are **privacy** regimes — Brazil's **LGPD**, Colombian and Argentine
  *habeas data* — and several firms are adopting the **EU AI Act as a de facto standard**.
- **Opportunity: EU-AI-Act-shaped delivery is reusable here.** Because LATAM enterprises are
  voluntarily anchoring on the EU AI Act, the Annex III conformity work built for an EMEA
  client **re-sells in LATAM** without rebuilding the governance layer. This is the single
  highest-leverage cross-region reuse in this KB.
- **Opportunity: the production gap is extreme and named.** One report puts **45% of ML
  models in LatAm never reaching production.** Durable execution and MLOps hygiene
  ([temporalio/temporal](https://github.com/temporalio/temporal), MIT) are therefore a
  sharper pitch here than agent sophistication.
- **Opportunity: ERP localisation is a defensible niche.** The OCA `l10n-*` modules for
  Brazil, Argentina, Mexico and Chile are real, maintained (`l10n-brazil` pushed the day
  this pass ran) and **AGPL-3.0**. Few global SIs can speak to Brazilian *nota fiscal*
  compliance plus an agentic layer; Globant can. See `verticals/solutions.md`.
- **Sector leaders to reference:** financial services, retail, manufacturing and logistics
  lead. Banks in Brazil, Mexico, Colombia and Peru have strong detection capability.
  Retail: **MercadoLibre, Falabella, Magazine Luiza** use AI in pricing and forecasting as
  standard. Mexico led the region on GenAI enrollment growth (**356%**); Brazil has greater
  depth and maturity.
- **Competitors on the ground:** **Softtek** (Mexico), **CI&T** (Brazil/Colombia delivery),
  **Encora** — these, not the global SIs, are who Globant meets in a LATAM enterprise deal.
- **Measured gap — stated so it is not mistaken for coverage:** there is **no LATAM-origin
  enterprise agent framework at any scale.** Spanish and Portuguese vocabulary searches
  (`agente IA empresa open source`, `agentes IA español framework`,
  `ERP brasil open source nota fiscal`) returned exactly one repository, with 0 stars. The
  only LATAM-origin code in this KB is Odoo localisation. **Implication: in LATAM, Globant
  cannot differentiate on local open source — it differentiates on local compliance
  knowledge applied to global open source.**

## Posicionamiento Globant

- **Assets in hand.** Multi-year **Anthropic alliance (30 Jun 2026)** with Claude-powered
  AI Pods and Claude access for 28,500 employees. **Glob.AI** launched 6 Aug 2026 — a
  marketplace shifting billing from labour to **pay-per-output**, which moves execution
  risk onto Globant and so rewards exactly the reliability engineering (durable execution,
  guardrails, evaluation) this KB is built around.
- **Where to play.** Not "build an agent" — **"take the pilot to production and prove it."**
  The market's measured failure mode is pilots that do not scale (Cognizant's own stated
  reason for its EMEA unit) and models that never ship (45% in LATAM). The deliverable is
  the governance substrate: identity-bound agents, policy-as-code tool access, sandboxed
  execution, durable workflows, captured evaluation evidence.
- **Defensible combination.** Permissive-license agent layer (Globant IP, MIT/Apache) +
  copyleft base platform run stock in the client's estate + per-region compliance evidence.
  The licence asymmetry in `verticals/solutions.md` is the moat: it is easy to demo an
  agent and hard to ship one that a regulated client's legal and risk functions will sign.
- **Cross-region leverage.** Build Annex III conformity once for EMEA; resell the same
  governance layer into LATAM (EU Act as de facto standard) and adapt it per-state for
  North America and per-market for APAC.
