---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 🗺️ Mapa de mercado — Enterprise

> Key players, market map and opportunities. Figures are attributed to their source
> because they disagree with each other; where they conflict, that is stated rather than
> averaged away.

> **Second pass, 2026-11-20 (later same day):** NVIDIA added to the player map (it now
> ships the agent-governance toolchain, Apache-2.0); new 2026 evidence added to all four
> regions; the LATAM open-source gap re-measured to repository level. Market statistics in
> this file come from WebSearch result summaries — attributed, but **not read at source**,
> because this session's network policy reaches GitHub only. Repository facts are
> first-hand. See the verification note at the end of `intel/trends.md`.

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
| **NVIDIA** | Silicon + now the agent *governance* toolchain | Ships [SkillSpector](https://github.com/NVIDIA/SkillSpector) (Apache-2.0, 27,027 ★), [SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator), [NemoClaw](https://github.com/NVIDIA/NemoClaw), [NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay), [auto-ontology](https://github.com/NVIDIA/auto-ontology) and the [OpenShell](https://github.com/ai-openshell/OpenShell) runtime — **all Apache-2.0** | New entrant in this map, and the most consequential one for Globant. NVIDIA is giving away exactly the agent-governance layer this KB positions Globant to sell, which **lowers Globant's build cost and raises the bar on pure tooling plays**. Note the vendor-concentration risk: OpenShell's neutral `ai-openshell` org carries an NVIDIA copyright, so a "governed agent" stack assembled naively is an NVIDIA stack. Mitigate by pairing it with non-NVIDIA controls (OPA, Cerbos, Keycloak, OpenSandbox, Giskard). |
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
- **New evidence this pass — production rates, from four angles.** **Gartner 2026: only 22%
  of respondents have successfully scaled AI across multiple business units.** A US survey
  puts **31% of AI initiatives at full production while 88% of organisations use AI**.
  Digitate's study of North American IT leaders — and a separate survey of 120,000+
  respondents — both land on **8.6% of companies with AI agents actually deployed in
  production**. Digitate also finds NA has moved from process automation toward agent-based
  operation since 2023, i.e. the *intent* is agentic while the *installed base* is 8.6%.
- **New evidence this pass — governance is bought here as an advantage, not a cost.**
  Dentons' survey of North American legal and business leaders found organisations
  **selectively apply AI governance guidance but few have an integrated, auditable AI
  management system**; separate reporting frames compliance as a market advantage that builds
  trust with customers and partners. Commentary on US fragmentation argues that it is
  **fragmentation, not strictness, that slows enterprise scale-up** — which is the precise
  argument for a policy-as-code layer that satisfies several state regimes from one build.
- **Market-share note:** this pass found NA at **38.5% of the global enterprise AI market**
  (one market report) against the **~39.6% of the enterprise AI *agent* market** already
  recorded above. Different denominators, not a contradiction — quote whichever matches the
  question, and say which.

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
- **New evidence this pass — the value gap is the sharpest in any region.** IDC's March 2026
  survey: **only 9% of EMEA organisations have delivered measurable business outcomes from
  most of their AI projects over the past two years.** IDC's own framing is that the blocker
  "is almost never ambition — it is the ability to execute", and that organisations which
  integrate governance *early* are better positioned to scale. The single best statistic for
  an opening slide comes from Veeam: **88% of EMEA organisations are already operating AI
  agents, but only 7% feel fully prepared to manage them.**
- **New evidence this pass — sovereignty is being traded away under delivery pressure.**
  Veeam's research frames EMEA companies as **sacrificing data sovereignty in the race to
  deploy AI** — which is a remediation engagement, and one with a regulatory deadline
  attached. Reference deployments to cite: **HSBC partnered with Mistral AI** for
  enterprise-grade AI with full data ownership, and **Siemens** automated operations across
  **11 global locations while keeping data in sovereign environments**. Both are the shape of
  deal Globant should be quoting.
- **New evidence this pass — the SME barrier is skills, not regulation.** An OECD report
  finds **half of surveyed SMEs cite a skills shortage as their primary barrier to
  adoption**, and TechNext argues directly that regulation is *not* the main brake on
  European AI adoption. That reframes the 38-point large/small enterprise gap recorded above
  as a capability-delivery opportunity rather than a compliance one.
- **Stale-date warning, still circulating in November 2026.** A source surfaced in this
  pass's own search still states the EU AI Act high-risk deadline as **2 August 2026 with
  penalties up to €35M or 7% of global revenue**. The penalty figures are real; **the date is
  superseded** by Regulation (EU) 2026/1744 (Annex III → **2 December 2027**). Expect clients
  and competitors to be working from the old date — correcting it is a credibility moment,
  and the deferral is the thing that makes a conformity-readiness programme sellable now.
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
- **New evidence this pass — APAC is the highest-adoption region and the budget is committed.**
  Forrester reports **APAC generative-AI adoption at 63% and predictive AI in IT operations
  at 53%, both substantially above North American and European rates.** Lenovo's CIO Playbook
  finds **96% of APAC organisations plan to increase AI investment, by ~15% on average, in
  2026.** IDC describes the region as moving from experimentation to **industrialisation with
  governance built in** — which is the phase Globant sells into.
- **New evidence this pass — the barrier is infrastructure, specifically real-time data.**
  **49% of APAC businesses cite insufficient infrastructure for real-time data processing as
  a barrier to AI adoption.** Combined with the BCG finding above (~30% of workflows mature
  enough), the APAC engagement is a *data platform* engagement with an agent on the end of
  it, not an agent engagement. [kestra-io/kestra](https://github.com/kestra-io/kestra)
  (Apache-2.0) and [dbt-labs/dbt](https://github.com/dbt-labs/dbt) (Apache-2.0) belong in
  that proposal; see `repos/foundations.md`.
- **New evidence this pass — China's programme pairs targets with governance.** China's
  national **"AI Plus"** programme sets adoption targets alongside extensive governance
  measures, on top of the existing generative-AI, algorithmic-recommendation and deepfake
  rules. Commentators expect APAC to **harmonise on principles (safety, transparency,
  accountability) while implementation stays local** — exactly the case for one agent
  implementation with a jurisdiction-switchable policy layer.
- **Reference deployment to cite:** Australia's **Woolworths Group** is extending its digital
  shopping assistant "Olive" on Google Cloud's agentic AI platform. **MAS** (Singapore)
  continues to consult on AI risk management for financial institutions, including
  third-party AI providers. The **Asian Development Bank's AI Preparedness Index** shows a
  clear gap between advanced and developing APAC economies — relevant to where delivery
  capacity, not just demand, exists.
- **Open-source note:** the **DeepSeek Harness**
  ([deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness), MIT,
  284,581 ★) is APAC-origin and now one of the three largest agent harnesses on GitHub. APAC
  open source is no longer a follower in this category — it is setting it.

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
- **New evidence this pass — the governance gap is now quantified, and it is the pitch.**
  RSM's *AI Readiness in Latin America 2026* survey (400+ business leaders) finds **~40% of
  organisations already implementing AI and 68% of those adopters planning to expand within
  12 months**, with efficiency the top driver (**67%**). Against that: **only 18% have formal
  AI governance frameworks and only 17% have established employee AI policies.** That is the
  cleanest number in this entire KB — a region scaling AI fast with four out of five
  organisations having no governance framework at all. The EU-AI-Act-shaped conformity work
  described above has an addressable market of roughly 82% of LATAM adopters.
- **New evidence this pass — Peru's law has implementing regulation, with a date.** The
  regulation of **Law No. 31814 was published on 9 September 2025**: risk-based structure,
  prohibited practices, and **human oversight required for high-risk uses**. Uruguay's
  signature of the Council of Europe Framework Convention is dated **2025**. So LATAM's
  leading regime is no longer "a law exists" — it is a risk-based regime with an obligation
  Globant can design to, and it looks like the EU AI Act because it was built to.
- **New evidence this pass — infrastructure and a regional model are arriving.**
  Hyperscalers are building large regional data centres across **Argentina, Brazil and
  Mexico**; **Latam-GPT**, a regional model led by Chile's **CENIA**, is the output of a
  two-year regional effort. The UN's **ILIA 2025** index names weak talent pipelines and
  uneven data readiness as the binding constraints. On enterprise provider share, one B2B
  source puts **IBM, Microsoft and Google** as dominant in the region — note the absence of
  a LATAM-origin platform vendor, which is the same finding as the repository evidence below.
  BCG's 2026 piece on **Brazil turning AI ambition into reality** is the best single
  country-level reference to cite.
- **The LATAM open-source gap, re-measured precisely this pass.** Last pass recorded "one
  repository, 0 stars". The number moved, and the conclusion did not:
  [whitebeardit/agents-team-crafter](https://github.com/whitebeardit/agents-team-crafter) is
  now **38 ★** but carries **NOASSERTION — no usable licence** and was last pushed
  **2026-06-23**. Newly located: the **`latam-gpt` GitHub organisation**, the public code
  footprint of the CENIA-led initiative — **8 repositories**, all data-preparation tooling
  ([llm-data-eval](https://github.com/latam-gpt/llm-data-eval) 16 ★,
  [toxicity-classifier](https://github.com/latam-gpt/toxicity-classifier) 5 ★,
  [language_identifier](https://github.com/latam-gpt/language_identifier) 3 ★,
  [anonymization-filter](https://github.com/latam-gpt/anonymization-filter) 1 ★,
  [data-deduplication](https://github.com/latam-gpt/data-deduplication) 0 ★ and three more).
  **Only one of the eight carries a licence** (`anonymization-filter`, MIT, 1 ★), and most
  were last pushed in **2024–2025**. So: LATAM-origin open source in this category exists,
  is sovereign-model data plumbing rather than agent infrastructure, and is **almost entirely
  unlicensed — therefore unusable in a Globant deliverable.** Stated at this level of detail
  so no future pass has to re-run the search to find out whether it was checked.
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
