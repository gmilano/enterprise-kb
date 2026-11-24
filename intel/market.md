---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 🗺️ Mapa de mercado — Enterprise

> Key players, market map and opportunities. Figures are attributed to their source
> because they disagree with each other; where they conflict, that is stated rather than
> averaged away.

> **Second pass, 2026-11-20 (later same day):** NVIDIA added to the player map (it now
> ships the agent-governance toolchain, Apache-2.0); new 2026 evidence added to all four
> regions; the LATAM open-source gap re-measured to repository level.
>
> **Third pass, 2026-11-20 (later still):** the NVIDIA concentration risk recorded below now
> has a **structural mitigation** — the control plane went to the Linux Foundation (see the
> players table). **Agent FinOps** added as a commercial opening (`intel/trends.md` trend 12).
> New 2026 evidence added to all four regions, including the first figures that quantify
> LATAM's investment gap and a named EMEA governance-structure number. Market statistics in
> this file come from WebSearch result summaries — attributed, but **not read at source**,
> because this session's network policy reaches GitHub only. Repository facts are
> first-hand. See the verification note at the end of `intel/trends.md`.

>
> **Fifth pass, 2026-11-20 (latest):** a new vendor category enters the map — the **interface
> layer** (CopilotKit, Vercel, Google's A2UI, Thesys), the only protocol surface in agentic
> computing with **no foundation steward** and four live competing standards. All four regions
> updated with new 2026 evidence, including a **correction to this KB's own expectation that
> Brazil would pass an AI law**, a refinement on Mexico (no omnibus act, but binding
> automated-decision duties), and the EMEA finding that the region's only interface-layer
> project is **archived**. Caveat strengthened: GitHub's `users/{org}` endpoint is refused from
> this session, so no region-origin claim in this pass rests on repository metadata.

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
| **Linux Foundation / AAIF** | Neutral steward, not a vendor | Stewards **MCP**, **goose**, **AGENTS.md** and — new this pass — **[Agent Router](https://github.com/theagentrouter/agent-router)** (Apache-2.0), the control plane formerly called Envoy AI Gateway | **Not a competitor — the answer to an objection.** It is what lets Globant say the layer holding a client's model credentials is governed by a foundation, not a vendor. Directly mitigates the NVIDIA concentration risk in the row above. |
| **CopilotKit** | Interface-layer vendor (new category) | Authors **AG-UI** (MIT, 20,766 ★), the agent↔user protocol; $27M Series A May 2026; reported support from Google, Microsoft, Amazon and Oracle; named users include Deutsche Telekom, Docusign, Cisco, S&P Global | **The one layer with no neutral steward.** The protocol is MIT and free to implement; the money is in the enterprise product above it. For Globant that is favourable: the standard costs nothing and the integration into a client's own screens is exactly the billable work. Risk to name: a venture-funded company controls the de facto standard, so keep the renderer behind an adapter. |
| **Google (A2UI)** | Protocol publisher | [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) (Apache-2.0, 17,690 ★), announced 15 Dec 2025, 1.0 shipped; UI as data against a client-held catalog of approved components; Gemini support; ByteDance Lynx renderer (Jun 2026) | A second, Apache-2.0 answer to the same problem — and the stronger *security* story, which is what a regulated client will respond to. Google states it was built with partners including the AG-UI/CopilotKit team, so do not frame these as a two-horse race. |

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
- **New evidence this pass — the base of the funnel is much emptier than the headlines.** The
  same 120,000+ respondent survey that produced the 8.6% production figure also finds **63.7%
  of organisations have no formalised AI initiative at all.** Read against Stanford's 90%
  "organisational AI use", that is the clearest statement of the real NA opportunity: wide
  informal usage, almost no formal programme. **The first sellable deliverable in that
  situation is an AI programme and its governance, not an agent.**
- **New evidence this pass — market size, for a proposal's framing slide.** One market report
  puts the **North American AI market at $254.86B in 2026, reaching $1.36T by 2031.**
  Market-research sourced and directional; do not present it as measured.
- **New evidence this pass — agent cost governance is a North American budget problem now.**
  **Gartner: spend on AI models and platforms +63.4% YoY to $64B in 2026**; IDC reports
  token-and-inference-based pricing as the **largest** budgeting barrier organisations cite.
  Combined with the state-patchwork compliance driver above, the NA entry offer is a **single
  control plane that produces both the per-state compliance evidence and the per-team cost
  attribution** — one build, two budget holders. See `compose/patterns.md` Receta 9.
- **Named players in the region** (one market report): Google, Microsoft, IBM, AWS, NVIDIA,
  Oracle, Salesforce, OpenAI and Meta, with AWS, Azure and Google Cloud anchoring generative-AI
  infrastructure. No systems-integration name in that list — which is the opening.
- **New this pass (fourth, 2026-11-20) — ISO/IEC 42001 is turning into an RFP line item.** US
  federal buyers are reported to lean on **NIST AI RMF** as the common checklist, with **ISO/IEC
  42001** adding the auditable governance layer on top; some sources claim certification is
  already scored decisively in major government procurements, without naming a contract. Pair
  this with the **Dentons** finding already recorded above — that few North American
  organisations have implemented an integrated, auditable AI management system — and the offer
  writes itself: **Globant builds the management system, not just the agent.** Certification is
  reported to take **6–18 months**, so a client who wants it for a 2027 bid has to start now.
  Sources disagree on mandatory vs preferred; see `intel/trends.md` §14. All second-hand.
- **New this pass — the agent payments layer is a North American standards fight.** AP2
  (Google-initiated, ~60 organisations), ACP (OpenAI/Stripe lineage) and the x402 rail are all
  US-origin and all permissively licensed, and **none is settled** — the most-starred is five
  months idle. For a NA retail, travel or marketplace client this is a *positioning*
  conversation, not an implementation one: build the signed-mandate and approval step now,
  stay rail-agnostic. See `repos/foundations.md` and Receta 11.

- **New this pass (fifth, 2026-11-20) — the interface layer is a North American industry, and it
  is already inside the Fortune 500.** CopilotKit (Seattle) raised **$27M in May 2026** (Glilot
  Capital, NFX, SignalFire) for the agent-to-user interface layer, and keeps the **AG-UI**
  protocol MIT while monetising an enterprise product above it. Coverage of the round reports
  **Google, Microsoft, Amazon and Oracle supporting AG-UI**, with **Deutsche Telekom, Docusign,
  Cisco and S&P Global** named as users; company-sourced claims range from "tens of millions of
  agent-user interactions weekly" to "a majority of the Fortune 500". **Treat the adoption
  figures as vendor-sourced**; the repository and licence are first-hand
  ([ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui), MIT, 20,766 ★). *Opening:*
  the protocol is free to implement, the integration work is not, and the clients named above are
  exactly the profile that buys integration from a studio rather than building it.
- **New this pass — the US regulatory picture got an active federal counter-move, not just
  absence.** Beyond "no federal statute", this pass's sweep records **Executive Order 14365** and
  a **DOJ AI Litigation Task Force** aimed at state AI laws, with federal preemption legislation
  proposed and not enacted. State law remains the binding layer: **California SB 53** (frontier
  models), **Texas TRAIGA**, and **Illinois** AI-in-employment rules are cited as in force.
  **Colorado is contested across sources** — one account has the state repealing and replacing
  its AI Act in May 2026 before it took effect (after litigation and DOJ intervention), another
  has the original act effective 30 June 2026. **Do not state Colorado's status to a client
  without checking it that week.** *Consequence for proposals:* a US compliance posture is now a
  moving target with an adversarial federal layer, which strengthens the policy-as-code argument
  this KB already makes — encode the obligation set per jurisdiction, because the set changes.
- **New this pass — Canada is a distinct jurisdiction, not "North America".** No AI-specific
  statute; the **"AI for All" strategy (June 2026)** covers AI literacy, content watermarking and
  a **trusted-AI certification programme**, while PIPEDA and Quebec's **Law 25** already bind any
  AI touching personal data. A certification programme is a procurement hook: it creates a
  third-party artefact a bidder can hold, like ISO 42001 in EMEA (§14).


#### The data plane — North America, added sixth pass 2026-11-20

**Regional sizing (analyst, single-source, treat as directional):** North America holds the
largest regional share of the AI market at **38.5%**, with the United States alone drawing
**$159 billion in 2025**; MarketsAndMarkets projects the regional market from **$254.86B to
$1.36T by 2031 (~27% CAGR)**. Named as the region's most influential players: Google,
Microsoft, IBM, AWS, Nvidia, Oracle, Salesforce, OpenAI and Meta — one report's list, worth
cross-checking before it goes in a deck.

**Governance is self-directed, and that is the commercial opening.** Dentons' North American
survey finds that, absent universal regulation, companies are designing their own AI governance
frameworks — but **few have implemented an integrated, auditable AI management system**. US
federal requirements vary by agency and sector.

**What this pass adds specifically: the incumbent NA data stack is the licence-encumbered
one.** Nearly every source-available or copyleft component found in this pass's sweep is
North-American in origin — [airbytehq/airbyte](https://github.com/airbytehq/airbyte) (Elastic
License 2.0), [metabase/metabase](https://github.com/metabase/metabase) (AGPL-3.0 outside
`enterprise/`) — while the permissive substitutes are mostly EMEA-built (see the EMEA section).
A North American client is therefore **disproportionately likely to already run the components
Globant cannot build on**, and not to know it: Airbyte's own marketing page claims Apache-2.0
while its repository `LICENSE` is ELv2.

**Opportunity:** a **data-plane licence review** scoped tightly to ingestion, BI and entity
resolution, delivered as the first two weeks of any data-agent engagement. It is cheap, it is
evidenced by `repos/foundations.md`, and it lands with a US client precisely because there is no
regulator forcing the question — the forcing function is their own counsel and their M&A
diligence. Pair it with the **auditable metric definition** from `compose/patterns.md`
Receta 14: in a region with no federal rule, a signed metric set is the control that passes a
board, and it is a deliverable rather than a policy document.


**Seventh pass, 2026-11-20 — the entitlement boundary, and where this region's numbers actually point.**
The scaling figures have not moved in a direction that helps: a **Gartner survey of 1,303
enterprises with at least $50M revenue** finds only **22% have successfully scaled AI across
multiple business units**, and a separate survey of **120,000+ respondents** puts agents in
production at **8.6%**. Market sizing for the region is **$254,860M in 2026 at a reported 27.0%
CAGR** through 2031, with North America holding **38.5%** of global share — both single-source
market-research figures, quoted for order of magnitude only. The named incumbents are
unchanged: Google, Microsoft, IBM, AWS, Nvidia, Oracle, Salesforce, OpenAI, Meta.

**The regional reading that matters is regulatory, and it is counter-intuitive:** sources
describe US federal requirements as varying by agency and sector, and one May-2026 analysis
argues that **regulatory fragmentation — not strictness — is what slows enterprise scale-up**,
while a Dentons survey finds few organisations have an integrated, auditable AI management
system even where governance guidance is used selectively. **Fragmentation rewards exactly the
control this pass added.** Under sectoral regimes (HIPAA, GLBA, SOX), "who was allowed to see
this" is an auditable question with a per-sector answer, and an entitlement boundary
(`compose/patterns.md` Receta 16) produces the evidence directly: a permission graph plus a
zero-leak adversarial suite is an artefact an auditor can read, in any sector, without a
federal standard existing.

**This is also the region where the delegation standard is being built, vendor-first.** The MCP
Enterprise-Managed Authorization profile's reported early support is US-vendor support — Okta as
first IdP, Atlassian shipping it in Rovo MCP, Microsoft Entra documenting the `act` claim. **The
entry point for an NA engagement is therefore the client's existing IdP**, not a new component:
if they are on Okta or Entra, the delegation chain is a configuration and integration project
rather than a platform build. Confirm which IdP before scoping — it is the single variable that
decides the shape of the work.

#### The write boundary — North America, added eighth pass 2026-11-21

**The region owns the evidence format.** OSCAL is NIST's, its profile ecosystem is
FedRAMP-shaped, and [oscal-compass/compliance-trestle-fedramp](https://github.com/oscal-compass/compliance-trestle-fedramp)
exists specifically for it. This is the only region where "we will hand your auditor
machine-readable OSCAL assessment results" maps onto a programme the client is
**already** required to satisfy. For federal, federal-adjacent and FedRAMP-pursuing
clients that is not a governance nicety — it is the submission format.

**Regulatory shape: still state-by-state, with the operative detail being churn.**

- **No federal AI statute.** Federal action is executive: one overview lists
  **Executive Order 14409, "Promoting Advanced Artificial Intelligence Innovation and
  Security" (2026)**, as in force. A **bipartisan preemption draft released June 2026
  has stalled** since. *Secondary sources; the EO number and title should be checked
  against the Federal Register before it goes in a client deliverable.*
- **Five state AI laws already bind companies** as of August 2026, including
  **California SB 53** (frontier models), **Texas TRAIGA**, and **Illinois**' rules on
  AI in employment. All three were already recorded here; the count is new.
- **Colorado is the cautionary tale and it is new this pass.** Per one source, **xAI
  sued to block the Colorado law in April 2026 and the state repealed and replaced it
  in May, before it ever took effect**, with the rewrite narrowed toward automated
  decisions that carry real consequences for people. *Single secondary source —
  attribute it, and do not build a compliance timeline on it.* The commercial reading
  is durable even if the detail is not: **a US state AI obligation can be litigated out
  of existence between a proposal and a go-live**, so NA governance work must be sold
  as *control architecture* that survives a statute change, never as compliance with a
  named state law.
- **NIST launched a dedicated initiative to develop standards for autonomous AI agents
  in February 2026.** This is the most important NA line in this pass for Globant:
  the standards body that produced OSCAL is now writing agent standards, in the region
  whose evidence format this KB just acquired. Positioning the write-boundary build on
  NIST-shaped artefacts is a bet on the same institution twice.
- **Canada** has no comprehensive AI law. The **June 2026 "AI for All" strategy** covers
  AI literacy, watermarking and a **Canada Trusted AI Certification** programme;
  **PIPEDA** and **Quebec Law 25** already bite on any system touching personal
  information. A certification programme is a procurement gate in waiting — the same
  shape trend 14 describes for ISO/IEC 42001.

**The number to sell against.** In OneTrust's survey, **87% of organisations encourage
the use of AI agents while only 47% say that use is backed by clear governance and
controls.** That 40-point gap *is* the write-boundary engagement, stated as the
client's own self-report rather than as Globant's opinion. Pair it with the census-vs-
Stanford adoption split already recorded here (19.8% of US businesses using AI in any
function, against Stanford's 90% for North America) — the same methodological gap, and
the reason a client's "we have already adopted AI" and a consultant's "you have not
scaled it" are both true.

**Sellable shape in NA:** OSCAL-backed control evidence for the agent estate, with the
authority matrix and segregation-of-duties enforcement in the tool layer (Receta 17),
positioned as *audit-readiness that survives regulatory churn* rather than as
compliance with any one state's statute.

---

#### The provenance boundary — North America, added ninth pass 2026-11-24

**North America sets the *format*, and this year it revised it.** The eighth pass recorded OSCAL as a
North American artefact with no EMEA equivalent. The same holds one layer down: the authority on *what
an SBOM must contain* is a US agency document.

- **CISA published 2026 Minimum Elements for an SBOM on 2026-07-29**, replacing the 2021 NTIA baseline.
  Reported changes: **cryptographic hash and licence become minimum elements**; depth requirements
  dropped in favour of all components including transitive dependencies; **SWID dropped, leaving only
  SPDX and CycloneDX**. Secondary reporting says it covers open-source, **AI software** and SaaS.
- **It is guidance, not law** — which is exactly why it functions as a procurement clause rather than a
  compliance deadline. US federal software attestation and SSDF (NIST SP 800-218) are the binding
  instruments it feeds; **this pass's searches did not return current material on either**, so their
  2026 status is **an open question, not a settled fact**.
- **The verification tooling consolidated onto a US vendor platform in the same year.** The reference
  SLSA tools retired in favour of GitHub artifact attestations and `gh attestation verify`
  (see `repos/foundations.md`). For a North American client already on GitHub Enterprise this is a
  *simplification* — the cheapest provenance story available anywhere, and it is the one region where
  "just use the platform feature" is usually the right advice.

**Opportunity — the OSCAL/SBOM join, which nobody is selling as one thing.** North America is the only
region where both halves exist: machine-readable **control** evidence (OSCAL, eighth pass) and a
revised machine-readable **component** baseline (CISA 2026). A control narrative that cites an SBOM by
hash, inside an OSCAL assessment document, is buildable **today, only here**, and it is the highest-value
governance deliverable this KB can currently assemble. Lead with the hash requirement: it is the field
that proves an inventory came from artefacts rather than from a questionnaire.

**Second opportunity — the fragmentation that Dentons measured.** With state legislatures as the primary
architects of US AI regulation and few organisations running an integrated, auditable AI management
system, the sellable unit is **one evidence pipeline that satisfies several regimes** rather than a
per-state compliance project.


#### Tenth pass, 2026-11-24 — the containment boundary: this region builds it, and is the only one that can audit it

**The layer is overwhelmingly North American in origin, and that is a procurement fact, not a
compliment.** The stewards of every control verified this pass: **Google** (`gvisor`, and the
initiator of `kubernetes-sigs/agent-sandbox`), **AWS** (`firecracker`), **Microsoft**
(`Azure/kars`, `microsoft/agent-governance-toolkit`), **Sysdig** (`falco`, `prempti`), the
**Cilium** project under CNCF, **Nirmata** (`kyverno`), the **Linux Foundation**
(`agentgateway/agentgateway`). *Corporate headquarters were not verified this pass — `aquasecurity/tracee`
in particular has a non-US corporate parent and is counted here only by repository stewardship.*

**The commercial consequence is sequencing, and it only works in this region today.** Pass 8 put
machine-readable control evidence in this KB (OSCAL, `complyctl`, `compliance-trestle`), and noted
that OSCAL is a North American artefact with no EMEA equivalent. This pass closes the circuit:

- NIST's **AI Agent Standards Initiative** (CAISI, started February 2026) is reported to be
  developing **SP 800-53 control overlays for agentic systems**, with an **AI Agent
  Interoperability Profile** planned for **Q4 2026**; NCCoE published a **concept paper on software
  and AI agent identity and authorization** in February 2026.
- OSCAL encodes SP 800-53. **An agentic overlay on SP 800-53 is therefore the mechanism that turns
  the four containment controls into machine-readable, auditable evidence** — `Sandbox` CRD,
  NetworkPolicy, Kyverno admission policy and Falco ruleset each mapped to a named control and
  emitted as OSCAL by `complyctl`.
- **North America is the only region where that chain exists end to end.** The controls are
  portable everywhere; the *evidence format that a regulator or auditor already accepts* is not.

**Sell:** a four-to-six-week "containment control set + OSCAL overlay mapping" engagement, pitched
at the FedRAMP-adjacent and financial-services buyers that already consume OSCAL. The deliverable is
not the sandbox — it is the **control-to-evidence mapping** that makes the sandbox defensible in an
audit, which is work the client cannot buy as a product.

**Caveats to carry.** The NIST items above are **secondary-sourced** (CSA research notes and a
certification-body summary surfaced by search; `nist.gov` was not fetched in this session) and are
**forward-looking** — one source states plainly that **no enforceable, agent-specific security
controls exist today** and that first substantive deliverables are not expected before late 2026.
Quote the direction, never a date, and never an obligation.

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
- **New evidence this pass — a hard number on governance structures, and it is tiny.** A
  **Gartner figure (cited via WWT): only 12% of organisations have dedicated AI governance
  structures today.** That is the most quotable EMEA statistic in this KB next to Veeam's 88%/7%
  pair, and it sizes the conformity-readiness market directly: the Annex III deadline is binding
  in roughly 12 months and seven out of eight organisations have no structure to meet it with.
- **New evidence this pass — IDC's framing, worth borrowing verbatim.** IDC's September 2026
  piece is titled *"The AI supercycle in EMEA: ambition is funded, capability isn't"* — which is
  the whole EMEA pitch in five words, and it is an analyst saying it rather than Globant.
- **New evidence this pass — the "EMEA is behind" assumption is wrong at country level.** One
  analysis finds **Denmark's enterprise AI adoption now exceeds the US enterprise average
  reported by Stanford, with Finland and Sweden close behind.** So EMEA is not a laggard region;
  it is a region with a very wide country spread and a large/small enterprise gap (55% vs 17%,
  recorded above). **Do not open a Nordics conversation with a catch-up narrative** — there the
  pitch is governance depth and sovereignty, not adoption.
- **New evidence this pass — sovereignty is becoming an infrastructure-placement question.**
  Lenovo's EMEA enterprise-AI lead frames the AI Act as pushing organisations to rethink **not
  just how they deploy AI, but where it runs.** That is the argument for self-hosted vLLM plus
  an EU-origin assurance toolchain — which this pass strengthened: alongside
  [Giskard](https://github.com/Giskard-AI/giskard-oss) (Paris) and
  [Haystack](https://github.com/deepset-ai/haystack) (Berlin), add
  **[Agenta](https://github.com/Agenta-AI/agenta)** (MIT Expat core, copyright **Agentatech UG**,
  a German entity) for agent and prompt evaluation. A credible EU-origin evaluation and
  orchestration stack now exists end to end.
- **Risk to watch:** European executives are reportedly warning that **AI's energy demand puts
  net-zero commitments at risk** — relevant because an EMEA client's sustainability function can
  become an unexpected blocker on a self-hosted GPU proposal. Pair the cost dashboard in
  Receta 9 with energy reporting and it becomes an answer instead of an objection.
- **Competitive note:** Cognizant's EMEA AI unit (28 Jul 2026) targets this exact pitch.
- **New this pass (fourth, 2026-11-20) — 42001 is reported to be moving fastest through European
  procurement.** European buyers are described as folding **ISO/IEC 42001** into vendor due
  diligence, and asking for the **scope statement and sample risk registers**, not merely the
  certificate. Critically, 42001 is reported to **reduce** EU AI Act compliance risk but **not**
  to satisfy the Act — a conflation an EMEA client will make, and correcting it early is free
  credibility. Combine with the EU-origin evaluation stack already recorded above and the AI-Act
  build in Receta 3: the artefacts overlap almost completely, so one engagement can produce both
  the Act evidence and the 42001 scope pack. Second-hand; see `intel/trends.md` §14.
- **New this pass — sovereignty now has a de-identification answer, not just a hosting answer.**
  The EMEA objection recorded above is where data runs. [Presidio](https://github.com/data-privacy-stack/presidio)
  (MIT, 11,989 ★) lets personal data be removed *before* a prompt crosses any boundary, which
  changes the conversation from "which region is the GPU in" to "no personal data left the
  estate". Cheapest credible answer to the first question asked in every EMEA engagement.

- **New this pass (fifth, 2026-11-20) — sovereignty is being deprioritised under delivery
  pressure, and now there is a number for it.** Veeam research (June 2026) reports **99% of EMEA
  enterprise decision-makers calling data sovereignty critical while 72.5% are actively
  deprioritising it to accelerate AI**, with **Germany the most extreme at 82%** putting AI
  development ahead of data governance. Second-hand, single vendor — but it is the most useful
  single sentence in this section, because it names the real objection. *How to use it:* the
  EMEA pitch is **not** "sovereignty or speed". It is **"sovereignty without the delay"** — an
  EU-origin, permissive, self-hostable stack that does not cost a quarter of schedule. That is
  precisely the stack already catalogued above. Also recorded: Forrester predicts **no European
  enterprise will fully exit US hyperscalers in 2026**, so the deliverable is the hybrid
  placement decision, not a migration fantasy.
- **New this pass — the one EMEA-origin project in the agent interface layer is archived.**
  [Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★) was created by
  **Chainlit SAS, Paris**, is the most-recommended Python conversational-AI shell in the market,
  and the GitHub API reports it **archived** (last push 2026-09-18). This is the inverse of the
  pattern this KB records elsewhere: in the metering and assurance layers, EMEA origin is a
  *strength* for a sovereignty pitch; in the interface layer there is **no live EMEA-origin
  option at all** — AG-UI and json-render are US, A2UI is Google, openui is Thesys. *Two
  consequences:* (1) an EMEA client wanting an end-to-end EU-origin stack can have one from data
  to control plane but **not** at the presentation layer, and saying so first is free credibility;
  (2) any EMEA deployment already running Chainlit has an archived dependency in front of
  production — a dated, factual reason to open a modernisation conversation.
- **New this pass — one named EMEA enterprise is already on AG-UI.** Deutsche Telekom appears in
  coverage of CopilotKit's round as a user of the protocol. Second-hand, but it means the
  "in-app agent UI" conversation is already live in a German enterprise, not hypothetical.


#### The data plane — EMEA, added sixth pass 2026-11-20

**The permissive data plane is, to a striking degree, European.** This is the clearest regional
finding of the pass. Of the components in `repos/foundations.md` that Globant can build on
without licence friction:

| Component | Licence | Origin |
|-----------|---------|--------|
| [moj-analytical-services/splink](https://github.com/moj-analytical-services/splink) | MIT | **UK Ministry of Justice** |
| [duckdb/duckdb](https://github.com/duckdb/duckdb) | MIT | Netherlands (Stichting DuckDB Foundation) |
| [dlt-hub/dlt](https://github.com/dlt-hub/dlt) | Apache-2.0 | Germany (Berlin) |
| [debezium/debezium](https://github.com/debezium/debezium) | Apache-2.0 | Red Hat (EMEA engineering) |
| [J535D165/recordlinkage](https://github.com/J535D165/recordlinkage) | BSD-3-Clause | Netherlands |
| [lightdash/lightdash](https://github.com/lightdash/lightdash) | MIT except `/ee` | UK |

**Why that matters commercially rather than as trivia:** the EMEA objection to an AI data
project is almost never capability, it is **where the data goes**. Splink resolves identities
*inside* the client's own warehouse and Debezium reads the database log in place — so the
reference architecture in `compose/patterns.md` Receta 15 **extracts nothing to a third-party
service**, and every component in it is EU- or UK-originated and permissively licensed. That is
a data-sovereignty answer made of facts rather than assurances, and it is available to no
competitor who starts from a US SaaS stack.

**Demand-side numbers:** IDC finds only **9% of EMEA organisations** have delivered measurable
business outcomes from most of their AI projects over the past two years, and frames the gap as
**execution, not ambition**. Veeam reports **88% already operating AI agents while only 7%
believe they are prepared to manage them**; Gartner figures cited by WWT put only **12%** of
organisations with dedicated AI governance structures. Named regional deployment: **HSBC with
Mistral AI**, deploying enterprise-grade AI across global operations **with full data
ownership** — the sovereignty framing, from a bank. Lenovo's EMEA lead frames the AI Act as
forcing a rethink of *where* AI runs, not only how.

**Regulatory hook, and a correction this KB must not lose.** Article 10 of the EU AI Act
governs **training, validation and testing datasets** — data quality criteria, data preparation,
and measures to address bias. Two consequences for this layer:

- Article 10 obligations fall on **providers, not deployers**. A client deploying a third-party
  system should be **obtaining Article 10 documentation from its provider** — and when Globant
  builds the system, Globant is in the provider's seat. The lineage, versioned golden record and
  adjudication trail from Receta 15 are the evidence Article 10 asks for, which turns a
  compliance cost into a deliverable already in the recipe.
- **On the date: this file's existing record stands and is correct.** Regulation (EU) 2026/1744
  (Digital Omnibus) deferred Annex III high-risk obligations to **2 December 2027** and Annex I
  to **2 August 2028**. This pass's searches **again** returned the stale "2 August 2026, €35M
  or 7% of global revenue" framing from secondary sources, alongside newer reporting describing
  the delay. That is the **sixth** independent search to surface the superseded date, so the
  warning already in `intel/trends.md` is load-bearing and should not be trimmed. Per this KB's
  own rule: a fresher secondary source does not beat a verified record, and the discrepancy is
  explained here rather than overwritten.


**Seventh pass, 2026-11-20 — the entitlement boundary is a legal control here, not a security feature.**
This region's execution gap is now measured from several directions and all of them point the
same way: **IDC** (Future Enterprise and Resiliency Survey, Wave 1, March 2026) finds only
**9% of EMEA organisations have delivered measurable business outcomes from most of their AI
projects** over the past two years; a **Veeam** study reports **88% already operating AI agents
while only 7% believe they are fully prepared to manage them**; and **Gartner** projects AI
governance spend of **$492M in 2026** against only **12% of organisations having dedicated
governance structures**. The 88%-versus-7% pair is the most actionable number in this section:
**the agents are already running, and the management layer is not there.** That is a remediation
market, and it matches `compose/patterns.md` Receta 4 (rescue a stalled pilot) more closely than
any greenfield pitch.

**Why the entitlement boundary lands differently in EMEA.** Under GDPR, purpose limitation and
data minimisation make "this employee could retrieve a document they have no business reading"
a **compliance** finding, not merely a security one — so Receta 16 is billable here as
regulatory work rather than hardening. Three supporting facts make it an unusually clean EMEA
story: **Keycloak is Apache-2.0 and Red Hat–originated**, the whole authorization stack
(`apache/casbin`, `authzed/spicedb`, `openfga/openfga`) is permissive and self-hostable, and
therefore **an EMEA client can run the entire entitlement layer on EU-hosted infrastructure
with no US-vendor dependency in the decision path** — the same digital-sovereignty argument the
energy KB found for its metering stack, reproduced in the governance layer. Note the sovereignty
pressure is real and measured: the Veeam work is framed around EMEA companies trading data
sovereignty for deployment speed. Also recorded: **HSBC partnered with Mistral AI** for
enterprise deployment with full data ownership, and **Denmark's enterprise AI adoption now
exceeds the US enterprise average** per Stanford figures cited secondhand — useful because it
breaks the "Europe is behind" frame a client may arrive with.

**A date discrepancy this KB will not resolve by averaging, and must not quietly overwrite.**
Multiple sources read this pass (IDC commentary, WWT, TNW) state the EU AI Act's high-risk
obligations apply from **2 August 2026**, with penalties up to **€35M or 7% of global revenue**.
**That contradicts `intel/trends.md` §4 of this KB, which records the deadline as having
moved.** The sibling energy KB records the same correction in more detail — Reg(EU) 2026/1744,
published in the Official Journal 24 July 2026, moving most Annex III high-risk obligations to
**2 December 2027** and Annex I embedded systems to 2 August 2028. The secondary sources read
this pass are **consistent with the pre-amendment timeline**, which is what a search of
2026-dated commentary would be expected to return. **Per this KB's own rule that a newer
negative does not beat a verified positive merely by being newer, the §4 record stands and
these sources are logged as disagreeing.** The primary register remains unread after four
passes — `eur-lex.europa.eu` was not reachable from this environment either. **Do not put
either date in a client proposal without reading the Official Journal text**; the commercial
risk is symmetrical and real, because the earlier date inflates a compliance budget and the
later one may understate an obligation.

#### The write boundary — EMEA, added eighth pass 2026-11-21

**The honest finding first, because it is a gap and not an opportunity.** The EU AI
Act's **Annex IV technical documentation** obligation has **no machine-readable
canonical format and no equivalent open-source toolchain.** OSCAL is a NIST artefact
with a FedRAMP-shaped profile ecosystem. It is genuinely useful in EMEA as an evidence
*substrate* — a place to keep control definitions, assessment plans and results in a
validatable form — but **it is not an AI Act conformity format and must never be
presented to an EMEA client as one.** Anyone quoting "OSCAL for AI Act compliance" is
selling a substrate as a certificate. Searched for an EU/EN-standard equivalent this
pass and found none; recorded as an informed gap, not as coverage.

**The board-level trigger is now measured, by name, in this region.** An **IBM study
dated 14 October 2026** reports:

- **80% of surveyed EMEA executives** say an AI-related incident reached their **board
  or C-suite** in the past year;
- **only 40% changed AI governance policy or frameworks** in response;
- **41% of EU executives are accelerating governance investment** ahead of the AI Act's
  high-risk obligations in **December 2027**.

The first two numbers together are the single best EMEA sales artefact this KB holds:
**the incident already reached the board, and in 60% of cases nothing changed.** That is
not a client who needs convincing that governance matters — it is a client who has
already had the conversation and lacks the architecture to act on it. Sell the build,
not the problem.

**And the third number settles this KB's most-repeated correction.** December 2027 is
the date this KB has defended for five consecutive passes against searches that keep
returning "2 August 2026": Regulation (EU) 2026/1744, the Digital Omnibus, moved Annex
III high-risk obligations to **2 December 2027** and Annex I to **2 August 2028**. IBM's
figure is the **third independent confirmation and the first from an enterprise survey
rather than from the regulation**, which makes it citable to an executive who will not
read a regulation. *This pass's searches still returned the stale August 2026 date from
other sources in the same result set — the error is not retreating.*

**The delivery-market signal.** **Cognizant launched a dedicated EMEA AI unit on 28
July 2026**, explicitly to move agentic AI from failed pilots into production, citing an
**IDC-documented 88% pilot failure rate**. Two readings, both true and both worth
saying to a client:

1. **Receta 4 (rescue a stalled pilot) is now a contested market in EMEA,** not an
   open one. A competitor has built a regional unit around precisely that motion.
2. **The differentiator cannot be "we move pilots to production"** — that is now the
   category claim. It has to be the thing the 88% actually fail on. This KB's own
   evidence says that is the boundary work: entitlement (Receta 16), the write path and
   the evidence trail (Receta 17). A pilot that was never going to pass a security
   review does not fail at the production step; it fails at the authorisation
   conversation, and it fails late.

**Adoption base rate, for sizing.** EU enterprise AI adoption reached **19.95% in 2025**
(up 6.47pp year on year) with a **38-point gap between large (55%) and small (17%)
enterprises**; OECD firm adoption **more than doubled from 8.7% (2023) to 20.2%
(2025)**. *Desk-research benchmark, not an official statistic.* The large-enterprise 55%
is the segment Globant sells to, and it means the EMEA conversation is rarely
greenfield: there is an existing deployment with an existing governance debt.

**Sellable shape in EMEA:** the write boundary as **Annex IV readiness** — human
authorisation in the path, initiator separated from authoriser in the record, reversal
rather than deletion — built on permissive components with an OSCAL evidence substrate
presented honestly as a substrate. Sovereignty is a live constraint here, which is why
`camel-semantic-wolf-defender` (local prompt-injection inference, no call out) and
self-hostable `block/buzz` matter more in this region than their star counts suggest.

---

#### The provenance boundary — EMEA, added ninth pass 2026-11-24

**EMEA is the only region where this layer has a statutory deadline and a fine, and it is the region
where the consolidation described above does the most damage.**

- **The Cyber Resilience Act is in force and biting in two stages.** Article 14 **reporting obligations
  have applied since 2026-09-11** — covering actively exploited vulnerabilities and severe incidents,
  **including for products already on the market before that date**. The **SBOM generation requirement**,
  conformity assessment, CE marking, secure-by-design requirements and vulnerability handling apply from
  **2027-12-11**. Reported exposure for reporting breaches: up to **€15 M or 2.5 % of worldwide annual
  turnover**, whichever is higher.
- **Two honest caveats to quote.** Article 14 **never mentions SBOM** — the "you need an SBOM by
  September 2026" claim circulating in vendor content is a *practical readiness argument* about the
  24-hour early-warning window, **not a legal requirement**; the legal SBOM date is December 2027. And
  the Commission's **Single Reporting Platform** was reported as still not publicly addressable three
  days before the obligation took effect, per a Cloud Security Alliance note; this pass **could not
  confirm** whether it went live on schedule.
- **Thirteen months is the whole message.** CRA SBOM obligations land 2027-12-11. A client who has not
  started has one budget cycle, and the *hash* requirement means the work is pipeline engineering, not
  documentation.

**Opportunity 1 — the non-GitHub verification gap, which is sharper in EMEA than anywhere.** The
retirement of `slsa-verifier` points every user at **`gh attestation verify`**. European public-sector
and regulated estates are disproportionately **self-hosted GitLab and on-premises CI**, and this pass
searched for a GitLab-native equivalent and **found none**. So the cheapest compliant path in North
America is **unavailable to a large share of EMEA buyers**, who need `cosign` + `in-toto`/`witness` +
`rekor` assembled and operated. **That is a build, it is defensible, and no vendor is offering it as a
product.** It is the single most specific provenance opportunity this pass identified.

**Opportunity 2 — sovereignty makes tool selection a billable decision, not a download.** Veeam's
survey reports **88 % of organisations already operating AI agents while only 7 % believe they are
prepared to manage them**, alongside reporting that EMEA firms are **sacrificing data sovereignty to
deploy AI faster**; IDC puts only **9 % of EMEA organisations** achieving measurable outcomes from most
AI projects. Against that backdrop, two measured facts from this pass are directly monetisable:

1. **`snyk/agent-scan` is Apache-2.0 and still sends MCP configuration to a vendor analysis API, with a
   token and a daily quota.** For a sovereignty-constrained client it is likely **disqualified on
   architecture, not on licence** — and `cisco-ai-defense/mcp-scanner`, whose YARA/static/readiness
   analyzers need **no key** and whose LLM analyzer accepts a **local Ollama endpoint**, is the
   candidate to pilot instead.
2. **The Sigstore trusted root cannot be fetched from an air-gapped network.** Measured here:
   `gh attestation trusted-root` fails closed against `tuf-repo-cdn.sigstore.dev`. Allowlisting that
   host once, pinning the root, shipping it inward as a controlled artefact and **owning its refresh**
   is a concrete work package — and a forgotten refresh is an outage, because verification correctly
   fails closed.

**Still-open gap, carried forward from the eighth pass and unchanged:** the EU AI Act's Annex IV
technical documentation has **no machine-readable format**, so the OSCAL-style evidence story available
in North America has **no EMEA statutory counterpart.** CycloneDX plus CRA's SBOM requirement is the
nearest available substrate — propose it as the Annex IV carrier, and be explicit that this is
Globant's construction, not a regulator's instruction.


#### Tenth pass, 2026-11-24 — the containment boundary: sovereignty is an *operational* property, and the licence is what delivers it

**New regulatory instrument, not previously in this KB.** The European Commission proposed a
**Cloud and AI Development Act on 3 June 2026**, giving cloud sovereignty a **four-level assurance
framework — localisation, independence, EU control, no interference**. It is a **proposal**, with
adoption targeted **around 2027**. Treat it as a direction of travel that is already shaping
procurement language, not as law.

**The four levels map almost one-to-one onto what this pass's controls technically enforce** — and
that mapping is a deliverable in itself:

| Assurance level | The containment control that evidences it |
|---|---|
| **Localisation** | Node placement + `SandboxTemplate` scheduling constraints; where the sandbox actually runs |
| **Independence** | Self-hosted control plane: Kyverno/Gatekeeper admission, Falco rules and the mesh CA are all operated by the client, not called out to |
| **EU control** | Workload identity and mTLS issued by a CA the client holds (Istio ambient / SPIFFE), not by a vendor tenant |
| **No interference** | **Default-deny egress** (Cilium egress gateway or an `egress-guard` iptables container) — the control that demonstrably prevents an outbound path to a non-EU endpoint |

**This is the answer to the region's hardest buying objection, and it is a licence argument.**
Deloitte's 2026 survey is reported to find **83%** of organisations describe sovereign AI as at
least moderately important and **77% factor a solution's country of origin into vendor selection**.
Every control verified this pass is **Apache-2.0 or MIT and self-hostable**. You cannot change where
Cilium or gVisor was written — but under those licences you can change **who operates them, on whose
hardware, under whose CA, with egress to whose endpoints.** **For this layer, sovereignty is an
operational property, not an origin property, and the permissive licence is precisely what converts
one into the other.** That sentence sells an integration engagement to a buyer whose stated filter
would otherwise disqualify the entire stack.

The corollary is the honest limit: **this argument works for the control plane, not for the model.**
A sovereign containment layer around a non-EU model API is a real and defensible posture — it is
also exactly the hybrid shape the region's own guidance describes (non-sensitive scale on global
clouds, "crown jewel" logic on sovereign infrastructure). Say which half you are making sovereign.

**Exposure, and the date that is contested.** Administrative fines reach **€35M or 7% of worldwide
annual turnover** for the gravest breaches. On the AI Act's high-risk obligations, sources
**disagree**: one says they take **full effect 2 August 2026**, another that obligations **may slip
to 2027**. This KB already recorded the deadline moving; this pass adds a second instance of the
ambiguity **and does not resolve it**. In any EMEA deliverable, state the date as contested and
defer to the client's counsel.

**Still true, and still a gap worth naming:** there is no EMEA equivalent of OSCAL. Annex IV has no
machine-readable format. So in this region the containment controls are demonstrable but the
evidence is a document, not a data structure — which is more consulting work, not less, and should
be priced that way.

*Sourcing note: the Deloitte percentages, the sovereign-cloud market figure and the named sovereign
GPU providers were all relayed through vendor and consultancy blogs surfaced by search. The
legislative instrument and its four levels were reported consistently across several such sources
but no primary EU text was fetched in this session. Verify before quoting a number to a client.*

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
- **New evidence this pass — stop selling "APAC" as one region.** AlphaSense's 2026 survey
  describes the region as **"less like one region and more like five distinct AI adoption
  stories", with Japan the most cautious**, and finds **security concerns top the region's
  adoption barriers** — not cost, not skills. That reorders the APAC pitch: lead with
  containment and data residency, not productivity. It also matches the regulatory picture
  already recorded (Korea binding, Vietnam binding, Japan light-touch, Singapore sandboxed).
- **New evidence this pass — directly relevant to Globant's Anthropic alliance.** **Anthropic's
  2025 AI Usage Index ranked four of its top five countries in APAC.** Globant has a multi-year
  Anthropic alliance (30 Jun 2026) and Claude access for 28,500 employees; APAC is where that
  model's per-capita usage is densest. **That is a region-specific reason to lead with the
  alliance in APAC** rather than treating it as a global talking point.
- **New evidence this pass — "sovereign RAG" is the regional vocabulary.** APAC enterprise
  coverage pairs **sovereign RAG with hyperscale AI** as the 2026 shape of demand, and IDC
  describes **unified AI governance moving from optional to mandatory**. Concretely: retrieval
  over client-resident data, self-hosted serving, per-market policy. The stack is already in
  `repos/foundations.md` — vLLM (Apache-2.0) for serving, RAGFlow or Haystack for retrieval,
  Agent Router (Apache-2.0) as the control plane, jurisdiction-switchable policy in OPA/Cerbos.
  Use the client's own words: **sovereign RAG**.
- **New evidence this pass — Thoughtworks places APAC ahead on agentic specifically**, citing
  Asian markets leading on agentic AI adoption, job creation and executive confidence. With the
  Forrester figures above (63% genAI, 53% predictive AI in ITOps), APAC is the region where
  Globant should expect to meet clients who are *already* agentic and need governance retrofitted
  — the opposite of the LATAM and EMEA "get it to production" motion.
- **Fourth APAC-origin harness, new this pass:** [bytedance/deer-flow](https://github.com/bytedance/deer-flow)
  (MIT, 85,545 ★) — a long-horizon SuperAgent harness. Two of the four largest MIT harnesses on
  GitHub are now APAC-origin. **For a Japan or Korea client worried about US vendor dependence,
  an APAC-origin MIT harness on a foundation-governed control plane is a complete answer.**
- **Regulatory risk to watch, sharpened:** a BSA post flags **training-data disclosure as the
  sharpest live issue for enterprise software in Japan**, and warns that **Indian and Vietnamese
  measures could slow adoption** in those markets. Thin sourcing — verify before quoting.
- **Fourth pass, 2026-11-20 — re-searched, and the regional picture did not move.** The
  mandated APAC sweep returned the same body of evidence already recorded in this subsection:
  Forrester on Singapore, Australia, New Zealand and South Korea leading North American and
  European countries on adoption; Lenovo's CIO Playbook on **96%** of APAC organisations planning
  to raise AI investment by an average of **15%** in 2026; Japan as the most cautious market;
  China's national **"AI Plus"** programme pairing adoption targets with governance; IDC on
  unified AI governance moving from optional to mandatory; Forrester predicting **sovereignty
  shapes AI infrastructure choices for half of firms**. **No new APAC-specific finding this
  pass** — recorded explicitly, because a silent subsection looks like coverage.
- **One new named deployment:** **Woolworths** (Australia) is reported running a shopping
  assistant on Google Cloud's agentic platform — useful as the regional retail reference when
  the agent-payments conversation in `intel/trends.md` §13 comes up. Second-hand.
- **Gap that remains open:** this pass again found **no APAC-origin repository in the four new
  layers** (payments, PII, catalog, graph RAG) — unlike the harness layer, where two of the four
  largest MIT harnesses are APAC-origin. The APAC strength is in agent runtimes, not in the
  governance substrate around them.

- **New this pass (fifth, 2026-11-20) — China's filing regime has a volume number now, which makes
  it a measurable gate rather than a described one.** More than **550 generative-AI services had
  been filed by mid-2026**; public-facing services must complete a **security assessment and
  algorithm filing before launch**, and **mandatory AI content labelling has been in force since
  1 September 2025**. Second-hand (law-firm and compliance summaries), but the shape is actionable:
  in China the pre-launch artefact *is* the project plan, so a China-facing engagement is
  scoped backwards from the filing, and labelling is an engineering requirement in the output
  path, not a policy page.
- **New this pass — India signalled it may legislate, so the window to build before the rules is
  closing.** In **July 2026** the Indian government indicated it may pursue dedicated AI
  legislation on a **risk-based model**; until then the **Digital Personal Data Protection Act**
  is the binding constraint on AI data use. One industry body warns dedicated legislation risks
  slowing adoption. *So what:* for an India engagement, build the obligation set as configuration
  now (the same policy-as-code pattern as EMEA) rather than hard-coding "no AI law applies".
- **New this pass — the adoption-versus-scale gap is quantified for the region.** Deloitte-sourced
  figures put APAC enterprise generative-AI adoption at **18% (2024) → 42% (2025)**, with
  **scaled deployment at roughly 12% of enterprises**. That is consistent with the BCG "~30% of
  workflows mature enough" datum already recorded above and with Forrester's higher adoption
  figures: APAC adopts fastest and scales no better than anyone else. The regional pitch is
  therefore **industrialisation**, not evangelism.
- **New this pass — APAC is implementing the interface layer, not just consuming it.** ByteDance
  shipped an **A2UI renderer for Lynx in June 2026**, i.e. an APAC-origin renderer for a
  Google-origin protocol, and Gemini supports A2UI 0.9.1. Together with `bytedance/deer-flow`
  (MIT, 85,545 ★) already in `agents/top.md` Tier 0, the pattern holds: **APAC engineering teams
  are producing permissive agent infrastructure, not only adopting it.** For a Japan or Korea
  client worried about US vendor dependence, the interface layer now has a non-US implementation
  path — and [Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere) (Apache-2.0,
  3,835 ★) gives the JVM core a portable agent runtime (Receta 6).


#### The data plane — APAC, added sixth pass 2026-11-20

**APAC is where the data *agents* come from, as EMEA is where the data *plane* comes from.**
Three of the four live text-to-SQL/data agents found this pass are APAC-origin:
[Canner/WrenAI](https://github.com/Canner/WrenAI) (Apache-2.0, 18.4k ★, Taiwan),
[eosphoros-ai/DB-GPT](https://github.com/eosphoros-ai/DB-GPT) (MIT, 20.3k ★, China) and
[XGenerationLab/XiYan-SQL](https://github.com/XGenerationLab/XiYan-SQL) (Apache-2.0, 1.0k ★,
China, with the serious NL-to-SQL benchmark work in the category). The region's main
entity-resolution project, [zinggAI/zingg](https://github.com/zinggAI/zingg) (India), is
AGPL-3.0. **This is the second time this KB has measured APAC as the origin region for an entire
agent category** — the third pass found `deer-flow` the same way — and it is now a stated
pattern rather than a coincidence. Practical use: in an APAC engagement the agent layer can
credibly be sourced regionally, which matters where sovereignty is a procurement criterion.

**Adoption runs ahead of the West, unevenly.** Forrester reports **Singapore, Australia, New
Zealand and South Korea leading most North American and European countries** in enterprise AI
adoption. Lenovo's CIO Playbook finds **96% of APAC organisations increasing AI investment, by
an average of 15% in 2026**. Against that: AlphaSense describes the region as not moving in
lockstep, with **Japan notably cautious** and **security the top adoption barrier**, and the
Asian Development Outlook's AI Preparedness Index shows a wide gap between advanced and
developing markets. Forrester expects **sovereignty to shape AI infrastructure choices for half
of firms**.

**Regulation relevant to the data plane:** Singapore's consultations on AI use in **financial
institutions** centre on transparency, accountability and risk oversight — all three are
semantic-layer properties in Receta 14, not model properties, which is the argument to make to
a Singaporean bank. IDC reports unified AI governance moving **from optional to mandatory**.
China's national **"AI Plus"** programme pairs adoption targets with extensive governance.
BSA has warned that a recent development risks slowing AI adoption in **India**, including
Indian-language model work. Named regional deployment: **Woolworths Group (Australia)**
extending its digital shopping assistant "Olive" on Google Cloud's agentic platform.

**Opportunity:** the sovereignty-shaped build — an APAC-origin data agent over a permissively
licensed, in-warehouse data plane, with nothing extracted to a US SaaS. **One caution to carry
into the sale:** Zingg's AGPL means the region's best-marketed entity-resolution tool is the one
Globant must contain behind a process boundary; the MIT substitute (Splink) is EMEA-origin, so
an "all-APAC stack" is not achievable at the resolution layer and should not be promised.


**Seventh pass, 2026-11-20 — sovereignty makes the permissive authorization stack the regional advantage.**
The demand signal is the strongest of the four regions: **Lenovo's CIO Playbook** reports
**96% of APAC organisations planning to increase AI investment, by an average of 15% in 2026**,
and **Forrester** finds **Singapore, Australia, New Zealand and South Korea ahead of most North
American and European countries** in enterprise AI adoption. The region is explicitly **not
homogeneous** — AlphaSense's 2026 survey describes **Japan as cautious**, with **security
concerns the region's top adoption barrier**, and **Confluent** reports **49% of APAC businesses
citing insufficient infrastructure for real-time data processing**. Google Cloud's agentic
platform at **Woolworths** is a named regional deployment.

**The regulatory driver points directly at this pass's stack.** Sources describe governments
continuing to refine data-protection, privacy and **cross-border transfer** requirements, which
pushes enterprises toward locally governed systems — regional commentary is already using the
phrase **"sovereign RAG"**. **Singapore** has run consultations on AI use in financial
institutions focused on transparency and accountability; **China's national "AI Plus" programme**
pairs adoption targets with extensive governance measures; and industry group **BSA** warns that
some policy developments risk slowing adoption in **India** and raising costs in **Vietnam**.
**Sovereign RAG is an entitlement problem before it is a hosting problem:** keeping the corpus
in-country is worthless if every in-country user can retrieve all of it. Receta 16 is the part
that makes a sovereign deployment defensible, and because every component is Apache-2.0 or MIT
and self-hostable, **there is no cross-border dependency in the authorization path at all.**

**One concrete regional fit worth naming in a proposal.** `apache/casbin` ships first-party JVM
and .NET ports (`apache/casbin-jcasbin`, `apache/casbin-Casbin.NET`), and this KB's
`compose/patterns.md` **Receta 6** exists precisely because Japanese and Korean enterprise cores
are JVM-heavy. **Authorization that runs in-process on the JVM, with no new network service and
no new vendor, is a materially easier sell into those cores** than a sidecar — and the move to
Apache Software Foundation governance (`repos/foundations.md` rename ledger) is itself an
argument in procurement-conservative markets, where ASF stewardship is a recognised quantity in
a way a single-vendor repository is not.

**Standing gap, carried forward from the sibling energy KB and still unaddressed:** the IEA
*"Energy and AI in East Asia"* report remains unread, and more relevant here, **no APAC-origin
authorization or agent-identity project surfaced in this pass's sweep** — the entitlement layer's
supply is NA- and EMEA-origin (Auth0/Okta, Authzed, Ory, Red Hat), with the ASF now stewarding
Casbin, whose origin is Chinese academic work. That last point is worth stating positively: **the
most-starred component in this layer has APAC origins and now has foundation governance.**

#### The write boundary — APAC, added eighth pass 2026-11-21

**A second binding, dated instrument lands in the region, and this one was not in this
KB.** Alongside **Korea's AI Basic Act (in force 22 January 2026)**, already recorded:

- **Vietnam's AI law took effect 1 March 2026**, with **Decree 142/2026, issued 30 April
  2026**, providing the first implementing detail. A law plus an implementing decree is
  a *filing-shaped* duty, which is the shape that changes an engagement's scope rather
  than its marketing.
- **China** remains the region's most developed binding regime, layering rules on
  algorithmic recommendation, deepfakes and generative AI.
- **Singapore** stays light-touch and sandbox-based, and **MAS is consulting on
  comprehensive AI Risk Management Guidelines**, with a response possibly due late 2026.
  For a financial-services client in Singapore the guidelines are the live document, not
  the AI governance framework.
- **Japan**'s AI Act is principles-based, relying on cooperation and existing law rather
  than penalties — **strategy, not an enforceable duty.** Do not scope Japanese work as
  compliance.
- **India** signalled in **July 2026** that it may pursue dedicated AI legislation, with
  industry groups warning of an adoption slowdown. Sources conflict; **record as in
  transition and do not cite a date.**
- **Korea declined to introduce a text-and-data-mining exception into its Copyright Act
  in February 2026.** Easy to miss and directly relevant: it constrains what a client
  may legally do with their *own* corpus when fine-tuning in Korea, which is a write-path
  question about training data rather than about transactions.

**The adoption constraint is data readiness, not appetite.** One industry analysis puts
APAC as the **second-fastest region globally for GenAI adoption** while only about
**30% of enterprise workflows are mature enough to support AI safely at scale**, naming
siloed systems, inconsistent data quality and an AI-skills shortage; regulated sectors
(healthcare, financial services) are flagged for gaps in **guardrails and
auditability**. *Vendor analysis — directional.*

That 30% is the most useful APAC number in this pass because of what it implies for
sequencing. A write-boundary engagement presupposes a system of record with clean
entities and a working integration layer. **In APAC the honest first deliverable is
more often the data plane (Receta 14, Receta 15) and the integration inventory than the
write boundary itself** — and saying so is a credibility asset, because the client
already knows their workflows are not ready. Compare the energy KB's APAC finding
recorded in `rotation.json`: sell *planning*, not real-time control. The same shape
holds here — sell the layer beneath the one the client asked for.

**APAC-origin permissive supply, byte-read.**
[Tencent/LoopForge](https://github.com/Tencent/LoopForge) — 5,481 ★, **MIT** (GitHub
badge says `NOASSERTION`; resolved by reading the file), pushed 2026-11-21 — self-hosted
workflows for coding-agent delivery. It vendors a Tencent-modified copy of
[obra/superpowers](https://github.com/obra/superpowers), which this KB already tracks.
Also relevant: `agentscope-ai/agentscope-java` and **[google/adk-java](https://github.com/google/adk-java)**
(new this pass) for the JVM-native enterprise cores that dominate the region's banking
and telco estates — see **Receta 6**.

**Sellable shape in APAC:** country-by-country, never a regional platform — the
regulatory instruments are national and do not transfer, and `rotation.json` records
the same conclusion reached independently in the energy rotation. Lead with the data
plane and the integration inventory; land the write boundary second, on JVM-native
components where the core is JVM-native.

---

#### The provenance boundary — APAC, added ninth pass 2026-11-24

**APAC's position in this layer is the one most likely to be misread: it is a co-author of the global
baseline while having almost no domestic mandate.**

- **Japan co-signed the baseline, one day after CISA published it.** METI and Japan's National
  Cybersecurity Office signed the **2026 Minimum Elements for an SBOM on 2026-07-30** (CISA published
  2026-07-29). That makes the document **a shared international baseline, not a US one** — the single
  most useful fact in this subsection, because it removes the "that's an American rule" objection from
  an APAC procurement conversation. The guidance is reported to cover open-source, **AI software** and
  SaaS, and to cite **Japan's SBOM Introduction Guide v2.0** as a national example.
  **Sourcing caveat: this is secondary-sourced.** METI's press release was not read at source in
  this session, and `www.cisa.gov` and `media.defense.gov` do not resolve here, so treat the
  co-signing as well-corroborated reporting rather than a primary-verified fact.
- **Singapore's CSA co-signed the earlier "Shared Vision of SBOM for Cybersecurity" (September 2025)**,
  and is reported to have issued an advisory with OWASP on SBOMs and real-time vulnerability monitoring
  for open-source and third-party dependencies. **This pass found no primary CSA 2026 SBOM document** —
  recorded as a gap in the evidence, not as absence of activity.
- **South Korea:** KISA is reported to have **expanded SBOM-based supply-chain support in 2026**.
- **No mandate anywhere in the region, on this pass's evidence.** Japan's METI guide is **voluntary**;
  the FSA lists SBOMs for in-house software as a **recommended** measure for financial institutions.
  Treat SBOM in APAC as **procurement advantage, not legal exposure.**

**Opportunity 1 — the export argument, which is the strongest provenance pitch in the region and is
cross-regional.** The EU **CRA applies to products placed on the EU market regardless of where they
were built.** An APAC manufacturer, device maker or software exporter selling into Europe inherits the
**2027-12-11 SBOM obligation and the €15 M / 2.5 % exposure** without any domestic law changing. So the
sale in APAC is not compliance — it is **market access**, and it has a date on it. This reframing applies
to LATAM exporters identically, and it is the most portable insight this pass produced.

**Opportunity 2 — sovereign deployment is already the regional default, which suits this layer.**
Forrester predicts sovereignty will shape AI infrastructure choices for **half of firms**; Lenovo's CIO
Playbook reports **96 % of APAC organisations planning to increase AI investment, averaging +15 % in
2026**; IDC frames unified AI governance as moving **from optional to mandatory**. Provenance tooling is
unusually well-suited here because **`cosign`, `syft`, `grype`, `in-toto` and Dependency-Track all run
entirely on-premises** — unlike the metered cloud scanner in `agents/top.md`. Lead with the fact that
**the whole stack can be self-hosted**; it is the regional buying criterion.

**Caveat on maturity, carried from earlier passes:** regional AI-governance maturity is uneven (the ADB
AI Preparedness Index shows a wide gap between advanced and developing APAC economies), and AlphaSense
reports **security concerns as the region's top adoption barrier.** Security-as-the-barrier is the
*reason* a provenance engagement sells here — it answers the stated objection directly rather than
arguing past it.


#### Tenth pass, 2026-11-24 — the containment boundary: the only framework that names delegation chains, and a 28% that dictates how to sell

**Singapore remains the region's agent-specific regulator, and it is the one jurisdiction whose
framework matches this KB's layer model.** IMDA's **Model AI Governance Framework for Agentic AI**
(published January 2026, reported **updated to v1.5 in May 2026** adding multi-agent systems,
third-party risk and automation bias) addresses **delegation chains** — which is pass 7's
entitlement boundary — alongside multi-agent coordination. **No other framework found names
delegation as a governed object.** It is **best-practice guidance, not law**; separately, MAS
guidance on AI in finance is reported to require effectively the same controls a binding law would,
which is why Singapore financial-services buyers behave like regulated buyers regardless.

**Japan stays on the soft-law track:** AI Promotion Act (in force 2025), **AI Basic Plan**
(December 2025), **AI Guidelines for Business v1.2** (March 2026), with companies expected to build
internal AI governance voluntarily. One source (Bloomberg) reports **voluntary adoption of aligned
standards from April 2026 (FY2026) with mandatory reporting phased in from 2027** — **single-sourced,
flagged as such**, consistent with this KB's existing practice of marking Japanese policy claims
that rest on one relay.

**India is principles-based and non-statutory**, with financial regulators signalling expectations
on explainability, governance and human oversight of AI-driven decisions rather than legislating.
Gartner is reported to forecast India IT spending above **$176B in 2026** — the region's volume
argument.

**The number that should change how this layer is pitched in APAC: 28%.** A Cloudera survey is
reported to find **58% of APAC enterprises increased AI investment but only 28% say AI currently
generates more value than it costs**, while **73%** cite governance and compliance as a scaling
constraint. Read those together and the usual containment pitch is wrong here: a buyer who is not
yet value-positive will not fund a security layer presented as additional cost.

**Pitch containment as the thing that makes isolation affordable, not as the thing that makes it
safe.** The lever is concrete and verified: `SandboxWarmPool` in
[kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox) provides
**pre-warmed sandboxes with low-latency claims**, and **gVisor needs no hardware virtualisation**,
so per-task isolation stops requiring a bare-metal or nested-virt node estate. Per-task isolation
was always the correct posture and was always priced out by cold start; these two features are what
change the arithmetic. Tie the proposal to the KB's existing FinOps trend (12) and quote cost per
sandboxed task, not controls implemented.

This is consistent with, and sharpens, the guidance already recorded for this region — workflow
maturity around 30% means **sell the data plane first**. Containment is the second sale, and in APAC
it is a **cost** conversation that happens to produce a **control**.

*Sourcing note: all survey percentages and the Japanese timeline above are relayed through
consultancy, vendor or press summaries surfaced by search; no primary IMDA, METI, MAS or Gartner
document was fetched in this session.*

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
- **Re-measured this pass across six new layers, and the gap holds.** The control plane, metering,
  red teaming, evaluation, sandboxing and document-AI categories added to
  `repos/foundations.md` this pass were each searched for LATAM-origin projects. **Zero appeared
  in any of the six.** The conclusion is now measured across eight categories rather than one,
  so a future pass can stop re-running it and spend the time on compliance depth instead.
- **New evidence this pass — the investment gap, quantified for the first time in this KB.**
  WEF/McKinsey analysis estimates AI could lift LATAM productivity by **1.9–2.3% annually and
  generate $1.1–1.7 trillion in additional economic value per year**, yet the region captured
  **$8.2B of the $190B allocated to private AI opportunities globally in 2025 — about 4.3%.**
  That pair of numbers is the best opening slide for a LATAM enterprise conversation in this
  KB: the value is regional, the capital is not, and the binding constraint is execution
  capacity, which is exactly what a delivery partner sells. WEF's January 2026 piece
  *"Latin America lags in unlocking AI value"* carries the roadmap framing.
- **New evidence this pass — the "EU model" claim now has an authority behind it.** The
  **International Bar Association** states the region's approach **follows the EU model** on AI
  regulation, and **Baker McKenzie** states that **no Latin American country currently has a
  fully mature, harmonised AI regime across all sectors.** Together those two make the
  cross-region reuse argument defensible rather than convenient: build Annex III conformity for
  EMEA, re-sell the governance layer in LATAM, and cite the IBA rather than Globant's own
  opinion that it transfers. Baker McKenzie also warns multinationals that the lack of
  harmonisation is the planning problem — i.e. per-country evidence from one build.
- **New evidence this pass — the competitor set includes nearshore specialists.** Nearshore AI
  and software services are a named growth channel, with firms such as **Nisum** already
  established in Colombia and Peru. Add them to **Softtek, CI&T and Encora** as the realistic
  competitive set; the global SIs are not usually who Globant meets here.
- **Reference material to cite:** the **IDB's May 2026 study** on AI adoption among LATAM
  startups, **CEPAL/ECLAC** regional material, and the **ILIA 2025** index (weak talent
  pipelines and uneven data readiness as binding constraints). All second-hand — none read at
  source from this session.
- **Fourth pass, 2026-11-20 — re-searched, nothing new on the market side.** The mandated LATAM
  sweep returned evidence already recorded here: RSM's survey of 400+ leaders (**~40%** already
  implementing, roughly **two-thirds of those** planning to scale within 12 months, efficiency
  the top motivation at **67%**), governance and employee-use policies lagging adoption, Mexico
  and Brazil leading on project volume and funding followed by Chile, Colombia and Argentina,
  **Peru's Law No. 31814** as the most advanced risk-based regime, **Uruguay** as first regional
  signatory to the Council of Europe AI convention, and **Latam-GPT** (Chile/CENIA, 30+
  institutions, eight countries). **No new LATAM finding this pass** — stated plainly rather
  than left silent.
- **Globant is named in the regional player set** alongside IBM México and Nisum, with Rappi,
  Bitso and Clip named on the startup side. Useful in a credentials slide; second-hand.
- **The supply-side gap was measured again, in four new layers, and is still zero.** Payments,
  PII/anonymisation, catalog/lineage and graph RAG were each searched in English, Spanish and
  Portuguese (`pagos agentes IA`, `agente pagamento IA`, `anonimizacion datos IA`). Everything
  returned was **0–3 stars with NOASSERTION — no usable licence**: landing pages, a WhatsApp
  payment-receipt OCR bot, student final-year projects. **Fifth consecutive pass, fifth zero.**
  The strategic reading is unchanged and now very well evidenced: **LATAM is a demand market and
  a delivery market, not a supply market, for agent infrastructure.** Globant's regional moat is
  integration and localisation on top of North American and EMEA-origin open source — not
  regional open source, because there is none to build on.

- **New this pass (fifth, 2026-11-20) — correction to this KB's own expectation: Brazil's AI law
  did not arrive, and there is a named reason.** Earlier passes recorded that "Brazil and Chile
  were expected to follow" Peru. The region's most developed bill, **PL 2338/2023**, has
  **stalled** — reportedly awaiting a rapporteur's opinion in a Chamber committee, with a vote
  possibly not before after the **October 2026 elections**. **Do not tell a Brazilian client a
  national AI law is imminent.** What *is* binding remains **LGPD**. This is not a contradiction
  of the earlier record but a resolution of it: the expectation was reasonable and did not
  happen, which is exactly the kind of thing a KB must say out loud rather than quietly drop.
- **New this pass — Brazil's courts are acting as the interim AI regulator, which is a different
  compliance surface entirely.** The **Superior Electoral Court (TSE)** issued **fourteen
  resolutions** governing the 2026 electoral process, including restrictions on AI use. *So what:*
  in Brazil the near-term binding constraints arrive as **judicial and sectoral acts**, not as a
  statute — so the discovery question for a Brazilian engagement is "which regulator and which
  court have spoken about your sector", not "is there an AI law".
- **New this pass — refinement, not reversal, on Mexico.** This KB records "Mexico still has no
  AI-specific legislation", which remains true of a *comprehensive* law. But sources this pass
  report **2026 amendments already in force that create concrete binding obligations**, and
  Mexico's data-protection law carries an **opt-out right from automated processing that could
  harm the data subject** — an automated-decision constraint that directly governs agents.
  Separately, the federal digital agency **ATDT published a National AI Plan 2026 in September**,
  reported to centre on a **314-petaflop public supercomputer**. *So what:* "Mexico is
  unregulated" is the wrong brief. The right brief is "no omnibus AI act, but binding
  automated-decision duties plus a national compute programme to align with". Sources conflict
  on the detail — verify the amendment text before quoting it.
- **New this pass — named LATAM enterprise adopters, which this section lacked.** **Petrobras,
  Nubank and Embraer** are cited as integrating AI into operations (predictive maintenance, fraud
  detection, customer-service automation), with Brazil the region's largest AI market for 2026.
  Secondary sourcing, but it gives the regional map named references instead of percentages.
- **Measurement caveat worth more than a statistic.** A secondary source cites IDB/McKinsey
  figures of **67% of large regional enterprises with at least one AI project in production but
  only 23% reporting measurable business impact** — while another review in the same sweep found
  **no firm-level adoption data for any Latin American country**. Both cannot be strong at once.
  Use the 67/23 *shape* (production without measured value) and never the decimals; the
  67/23 pairing says the same thing as the RSM governance figures above and is the opening.
- **LATAM open-source supply in the interface layer: not measured, and that is the honest
  statement.** This pass's sweep of the agent-to-user layer returned no LATAM-origin repository,
  but it was run in English only. This KB has measured a Spanish/Portuguese-vocabulary zero for
  *agent frameworks* several times; it has **never** run that vocabulary against the interface
  layer. So the correct record is **"not searched"**, not "zero". A negative is only worth
  recording when it was actually measured — the next LATAM pass should run it before anyone
  quotes a gap. (Note also that org location cannot be read from this environment at all; see
  the verification addendum in `intel/trends.md`.)


#### The data plane — LATAM, added sixth pass 2026-11-20

**Demand is real and ahead of governance.** RSM's survey of **400+ Latin American business
leaders** finds roughly **40% already implementing AI** and **68% of those adopters planning to
scale within 12 months**, with **67% citing efficiency** as the motive. RSM's own framing is
that the next phase depends less on appetite than on closing three gaps: **rules, readiness and
workforce capacity**. Thomson Reuters places **Mexico and Brazil** first on project volume and
funding, followed by **Chile, Colombia and Argentina**.

**Regulatory state:** no Latin American country has a fully mature, harmonised AI regime across
all sectors. **Peru is furthest along** — the regulation of **Law No. 31814** was published in
**September 2025**, setting out prohibited practices and requiring **human oversight for
high-risk uses**. **Uruguay** became the first country in the region to sign the Council of
Europe's Framework Convention on AI (2025). This is consistent with what this file already
records: several regional firms are voluntarily anchoring on the **EU AI Act as a de facto
standard**.

**The repository gap, measured rather than assumed — this is the honest finding.** This pass
searched in Spanish for LATAM-origin work in this specific layer (data agents, semantic layers,
text-to-SQL, entity resolution: *"código abierto agente datos SQL semántica empresa LATAM
Brasil México 2026 repositorio"*) and found **zero LATAM-origin repositories in the data
plane.** What the Spanish-language results actually returned was *coverage* of
[NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) in regional tech press, NVIDIA's
AI-Q blueprint, and Spanish and EU **academic theses** — no regional project. That is consistent
with this KB's standing measurement of no LATAM-origin agent framework of scale, and it now
extends one layer down. **Recorded explicitly so no later pass reads silence as coverage**, and
so nobody re-runs the same Spanish-vocabulary sweep expecting a different answer: this layer has
now been measured at zero once, in Spanish, on 2026-11-20.

**Why the gap does not weaken the LATAM offer — and this is the useful inversion.** Every
component of Recetas 14 and 15 is MIT, BSD-3-Clause or Apache-2.0 and **EMEA- or
APAC-originated**, and the architecture extracts nothing to a third-party service. So the LATAM
engagement is not waiting on a regional stack that does not exist; it is delivering the
permissive in-warehouse stack with **EU-AI-Act-shaped documentation** — which is the standard
regional firms are already choosing voluntarily, and which this file notes Globant can design
to because the conformity work was built for EMEA. The in-warehouse property specifically
answers **Brazil's LGPD** and the regional *habeas data* constraints this file already records:
with Splink and Debezium, personal data never leaves the client's own boundary, so the
cross-border transfer question largely does not arise.

**Opportunity:** lead with **Receta 15 (entity resolution)** rather than the agent. In markets
where the data estate is fragmented across local ERP localisations — which this KB already
catalogues via the OCA `l10n-*` modules for Argentina, Brazil, Chile and Mexico — the
duplicate-rate delta is a measurable, unarguable first win, and it is the prerequisite that
makes a "customer 360" agent buildable at all.


**Seventh pass, 2026-11-20 — the governance gap and the scaling intent are the same number, and that is the opening.**
The two most useful regional figures this pass are from one **RSM survey of 400+ business
leaders**: roughly **40% of organisations are already implementing AI**, **68% of those adopters
are preparing to expand within 12 months**, and **fewer than one in five report having a formal
AI governance framework.** Those are not three facts, they are one: **a region scaling faster
than it is governing.** The oversharing failure mode in `compose/patterns.md` Receta 16 is most
likely to occur first where adoption is accelerating and governance frameworks are absent, which
is precisely this profile. **This makes the entitlement boundary the cleanest first-engagement
offer LATAM has in this KB** — it is concrete, it is cheap relative to a platform build, its
acceptance test is a hard pass/fail (zero leaks on an adversarial set), and it does not require
the client to have an AI strategy first.

**Regulation: fragmented, EU-shaped, and moving.** Baker McKenzie describes the landscape as
fragmented, with **no Latin American country currently having a fully mature, harmonised AI
regime** across all sectors. Dated anchors worth carrying: **Uruguay signed the Council of
Europe's AI treaty in 2025**, and **Peru published the implementing regulation for its AI law in
September 2025**. The IBA's reading is that the region is **following the EU model**, with live
debate over whether over-regulation would hinder innovation. **Commercially this is the
strongest argument for building the entitlement layer on EU-shaped assumptions** — purpose
limitation and data minimisation — because work done to that standard travels to the next LATAM
jurisdiction as those regimes converge on it, instead of being rebuilt per country.

**Two market figures that do not reconcile — recorded, not averaged.** **Thomson Reuters**
reports the region accounted for **1.12% of worldwide AI spending in 2025**. The CEPAL-linked
**ILIA 2025** index states Latin America accounts for approximately **15–20% of the global
market for AI applications**. Those differ by more than an order of magnitude and **cannot both
be describing the same quantity** — almost certainly *spending on AI* versus *addressable market
for AI applications*, but neither source read this pass defines its denominator well enough to
confirm it. **Do not put either number in a client deck without its denominator.** For scale
framing, the **WEF/McKinsey** estimate that AI adoption could lift regional productivity by
**1.9–2.3% annually** is the least ambiguous figure available and the IDB has published a 2026
technical note on startup AI adoption across the region.

**Supply-side zero, re-measured and unchanged in its conclusion.** This pass's authorization and
agent-identity sweep returned **no LATAM-origin project of any scale** — the supply is NA- and
EMEA-origin (Auth0/Okta, Authzed, Ory, Red Hat) with ASF-stewarded Casbin of Chinese academic
origin. This is **consistent with, and does not re-measure, this KB's standing finding** that no
LATAM-origin agent framework of any scale exists (`agents/top.md`), which has now been measured
across multiple passes with Spanish and Portuguese vocabulary. The conclusion carries over
intact: **in this layer there is no regional open ecosystem to compete with, so publishing one
remains the cheapest positioning move available** — and the entitlement boundary is an unusually
good candidate for it, because the hard part is the per-system ACL connector, and the systems
that lack open connectors are precisely the regional ERP localisations this KB already
catalogues through the OCA `l10n-*` modules for Argentina, Brazil, Chile and Mexico.

#### The write boundary — LATAM, added eighth pass 2026-11-21

**Two binding or near-binding instruments, and the region's problem is volume rather
than absence.**

- **Peru has a binding risk-based regime in force since 22 January 2026** — **Supreme
  Decree No. 115-2025-PCM**, the regulation of **Law No. 31814**. This is the region's
  clearest dated, enforceable instrument and it was not in this KB.
- **Uruguay is the first country in the region to sign the Council of Europe's Framework
  Convention on AI.** A treaty signature is not a domestic obligation, but it signals the
  direction of travel and it is the kind of fact a regional CIO has not heard.
- **Brazil is contested and must be recorded as contested.** One source credits Brazil
  with leading the region via a 2024 AI Legal Framework; another, more specific, reports
  the bill **still awaiting the rapporteur's opinion in a Chamber special committee, with
  a vote possibly after the October 2026 elections.** The second is the more precise
  claim and neither was verified against an official source. **Do not tell a Brazilian
  client their AI law is settled.**
- **Mexico is irreconcilable in this pass's sources.** One says Mexico still lacks
  AI-specific legislation as of mid-2026; a Mexican law-firm chapter refers to
  "landmark legislative amendments enacted in 2026". **Recorded as unresolved — check
  Mexican primary sources before any Mexico engagement, and do not quote either claim.**
- **The structural finding: 716 AI-related regulatory instruments, rules and legislative
  proposals across 23 countries and territories.** The LATAM compliance problem is not a
  missing rulebook, it is **fragmentation at a scale no client can track manually** —
  which is itself the argument for machine-readable control evidence. A control
  catalogue expressed once in OSCAL and profiled per jurisdiction is a better answer to
  716 instruments than a document per country, and this is the one region where the
  *volume* argument for the OSCAL layer makes itself.
- **The EU AI Act reaches the region commercially, not legally.** Latin American
  companies that cannot certify their systems risk exclusion from tenders and global
  supply chains. For an exporter, EMEA's Annex IV conversation is a LATAM revenue
  question.

**Adoption: the gap between "in production" and "working" is the whole market.** A
secondary source citing IDB and McKinsey reports **67% of large regional enterprises
already have at least one AI project in production, and only 23% report measurable
impact on business metrics.** *Could not be traced to the original report — attribute
it, do not adopt it.* If directionally right it describes a region of **Receta 4
rescues**: the pilots exist, they are live, and two-thirds of them cannot show a number.
Financial services leads — thin-file credit scoring, real-time fraud, AML,
conversational banking — with **Nubank, Mercado Pago, Bancolombia and Itaú** named as
adopters, and **Softtek** cited for nearshore delivery into Mexican and Colombian
clients. One source records **no firm-level adoption data for any Latin American
country**, which is the more reliable statement about the statistics than any of the
percentages.

**The supply-side gap, now measured with the right instrument — write this down.**
This pass ran the **short Spanish** query `agentes IA empresa código abierto github
2026`, because `rotation.json` flags prior LATAM zeros as having been measured with
long English queries that do not discriminate. Result: **Spanish-language articles
about global repositories** — Peruvian, Spanish and Italian blogs ranking OpenCode,
Codex, Gemini CLI, OpenHands, Dify and Langflow. **Not one LATAM-origin enterprise
agent repository.**

So the zero is now a **measured zero, not an unmeasured silence**, and it is the second
independent measurement for this KB. **The Spanish-language layer of this ecosystem is
commentary and translation, not supply.** What LATAM *does* originate, and what this KB
holds, is the **regulatory and linguistic fitness layer**: `oca/l10n-argentina`,
`oca/l10n-brazil`, `oca/l10n-chile`, `oca/l10n-mexico` and the `latam-gpt/*`
data-preparation tools (anonymisation, deduplication, language identification,
toxicity, data evaluation). That is a real differentiator and it should be sold as
exactly what it is — **fiscal, legal and linguistic fitness that no global framework
ships** — and never dressed up as a regional agent runtime.

**Sellable shape in LATAM:** localisation-plus-agentic (Receta 5) remains the entry
motion; the write boundary attaches to it naturally, because a Brazilian or Mexican
fiscal posting is precisely a write to a system of record that must be reversible,
attributable and auditable under a regime that may change. The 716-instrument number
is the reason to express the controls once, in a machine-readable catalogue, and
profile them per country.

---

#### The provenance boundary — LATAM, added ninth pass 2026-11-24

**Measured result first, because the honest zero is the finding.** This pass searched for LATAM
software-supply-chain mandates in **Spanish and then in Portuguese** — the short native-language
instrument this KB adopted after the eighth pass, precisely because long English queries do not
discriminate.

- **No SBOM or software-supply-chain mandate located in Brazil, Mexico or Chile.** The Spanish query
  returned fintech, crypto, open-finance, ESG and gaming regulation — **adjacent regulatory noise, not
  software supply chain.** The Portuguese query returned Brazilian commentary that **states there is no
  specific Brazilian regulation requiring SBOMs**, with LGPD creating only *indirect* liability via
  breach accountability for an unknown component. That LGPD reasoning is **a blog argument, not a norm**,
  and is recorded as such.
- **One real sectoral anchor, and it is the useful find.** **ANBIMA** — Brazil's capital-markets
  association — publishes secure-application-development guidance that **recommends maintaining an
  up-to-date inventory of all dependencies (SBOM).** That is **industry good practice in the financial
  sector, not law**, and it is the only LATAM instrument this pass located that names the artefact.
  It matters because LATAM's AI lighthouse deployments are concentrated in financial services.
- **Unverified lead, flagged not promoted.** A vendor page attributes software-component control
  requirements to **BACEN Resolution 4.893** and related cyber circulars. **Not confirmed against the
  Banco Central primary text** — do not cite it to a client until someone reads the resolution.
- **LATAM-origin repositories in this layer: zero, and measured.** No LATAM-origin provenance,
  signing, SBOM or attestation project appeared in any search this pass. This is now consistent with
  eight prior passes: **LATAM supply is localisation and data-quality work** (`oca/l10n-*`,
  `latam-gpt/*`), **not infrastructure runtimes.**
- **Regional governance context, unchanged and relevant:** fewer than **one in five** LATAM
  organisations report a formal AI governance framework, while **~40 % are implementing AI and 68 % of
  adopters plan to scale within 12 months** (RSM, 400+ leaders). Baker McKenzie: **no LATAM country has
  a fully mature, harmonised AI regime.** Uruguay remains the first regional signatory to the Council of
  Europe AI treaty; Peru's Law 31814 regulation was published September 2025.

**Opportunity 1 — the export and nearshore argument, which is the whole LATAM case for this layer.**
Since no domestic mandate exists, provenance is **not** a compliance sale in LATAM. It is two other
things, both stronger:

1. **CRA exposure through export.** A LATAM software or device exporter selling into the EU inherits
   the **2027-12-11 SBOM obligation** and the **€15 M / 2.5 %** exposure with no local law changing.
2. **Nearshore supplier credibility.** LATAM's growth position is as a **trusted nearshore partner** to
   North American buyers. Those buyers are being handed **CISA's 2026 minimum elements** as procurement
   language — **hash and licence per component**. A nearshore supplier that ships signed artefacts and a
   conformant SBOM *by default* clears a gate its competitors argue about. **This is Globant's own
   delivery pipeline as a differentiator**, which makes it unusually cheap to prove: build it once
   internally, then sell the evidence.

**Opportunity 2 — governance scaffolding for a region that is scaling without it.** 68 % of adopters
scaling against <20 % with a governance framework is the clearest arbitrage in any region on this page.
The cheapest credible entry remains the AI inventory (`compose/patterns.md` Receta 13); **what this pass
adds is the field that makes it defensible — the component hash** — and the warning that an inventory
built from questionnaires cannot produce one.

**What was NOT found, stated so a later pass does not mistake silence for coverage:** no LATAM national
CERT or regulator document on SBOM; no Mexican or Chilean instrument of any kind; no LATAM equivalent of
OSCAL or of the CRA. Searched 2026-11-24 in Spanish and Portuguese. **Recommended instrument for the
next pass:** query the national agencies directly (`gov.br/anpd`, CERT.br, Chile's CSIRT, Mexico's
agencies) rather than the open web, because this pass's evidence suggests the open-web layer here is
commentary rather than regulation.


#### Tenth pass, 2026-11-24 — the containment boundary: a second measured zero, and why it is an argument rather than an absence

**Measured, with the instrument stated.** A Spanish-language query aimed directly at this pass's
layer — *"aislamiento de agentes IA contenedores egress Kubernetes código abierto LATAM Brasil
2026"* — returned **zero LATAM-origin projects, zero LATAM case studies and zero Spanish- or
Portuguese-language primary documents.** Every result was English and global: Microsoft's
`Azure/kars`, Google's and Kubernetes' own announcements, a Red Hat downstream build, an InfoQ
round-up. **This is the second consecutive pass in which the short Spanish instrument returns a
measured zero for the layer under study** (pass 8 measured the same for agent repositories).

**A measured zero and a silence are different data, and this one is an argument Globant can use.**
The containment layer is **import-and-integrate in every region, including North America** — nobody
buys this as a product anywhere, because no product composes the four controls. So the absence of
LATAM-origin tooling costs a LATAM engagement **nothing**: the billable work is integration against
the client's own Kubernetes estate, network topology and audit requirements, and integration is
irreducibly regional. **For this one layer, LATAM starts level with EMEA and only modestly behind
North America** — the gap is the evidence format (OSCAL), not the controls.

**Regulatory picture, with the disagreement recorded rather than resolved.**

- **Brazil** is the region's most advanced file and the sources conflict. **PL 2338/2023** was
  approved by the **Senate in December 2024**; one analysis says it **remains pending a vote in the
  Chamber of Deputies**, a second describes it as **in final approval**, and a third describes the
  law as **already in an implementation phase with ANPD as the enforcement authority**. **Detailed
  regulation is expected in Q4 2026.** These cannot all be true; **do not pick one in a client
  document.** State that the instrument is PL 2338/2023, that ANPD is the named authority in the
  sources that go furthest, and that detailed rules are expected imminently.
- **Mexico** has **no specific AI law** — two accumulated proposals without *dictamen*, pending
  constitutional reforms, and a sectoral patchwork. One analysis makes the sharper commercial point:
  **data obligations under LFPDPPP are enforced in practice by enterprise customers in contracts
  rather than by the regulator.** In Mexico the buyer *is* the compliance regime.
- **Peru and El Salvador** are reported (July 2026 analysis) as the only LATAM countries with
  specific AI legislation **fully in force**. This KB already holds Peru's SD 115-2025-PCM
  (in force 22 January 2026).

**Why the containment layer is the right thing to sell into Brazil specifically, now.** With
detailed regulation expected in Q4 2026 and **ANPD** named as enforcement authority, the question a
Brazilian client will face is not *which framework did you adopt* but *what can you show*. The
cheapest durable answer is the one `Azure/kars` demonstrates and this KB has now recorded as a
pattern: **a SHA-256 hash-chained audit log of every policy decision**, produced by the containment
layer as a by-product of enforcing it. **An append-only, tamper-evident decision log is defensible
against a rule that has not been written yet** — which is the only control posture that survives a
regulation still in drafting.

**Adoption and governance figures — recorded with their spread, because the spread is the finding.**
Microsoft's Global AI Diffusion report (Q1 2026) is cited as placing **Costa Rica first in the
region at 28.5%** generative-AI adoption among the working population. On governance, one report
claims **92% of LATAM companies use AI but only 8% have formal policies**, while another puts usage
at **78%**. **A 14-point spread on the simplest question in the survey means neither number is
usable**; the directional claim that policy adoption lags usage badly is the only part multiple
sources support. ISO/IEC 42001 certificate counts of **18 (Brazil)** and **11 (Mexico)** appear in
one source — too small a sample to generalise, and consistent with this KB's trend 14 that 42001 is
becoming a procurement gate ahead of being a widely held certificate.

*Sourcing note: every figure in this subsection was relayed through commercial blogs or consultancy
reports surfaced by search. No primary legislative text, no ANPD publication and no Microsoft report
was fetched in this session — `nist.gov`-class primary sources were out of reach for all four
regions this pass. Verify before any of these numbers enters a client deliverable.*

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
- **The sharpest alignment in this KB, found third pass.** McKinsey's position is that the unit
  of AI governance should be **the completed business outcome, not the token cost**. Globant's
  **Glob.AI** (6 Aug 2026) already bills **per output**. The commercial model Globant shipped and
  the governance model the market is converging on are the same model — an argument no
  competitor billing by headcount can make. **Say it in those terms.** The flip side is a margin
  risk, not a talking point: pay-per-output puts the token bill on Globant's side, so the
  metering stack in `compose/patterns.md` Receta 9 protects Globant's own economics before it is
  ever a client feature. Build it internally first and the client reference writes itself.
- **Vendor-neutrality is now an answerable objection.** Until this pass the governed-agent stack
  this KB recommends was overwhelmingly NVIDIA's. With **Agent Router** (Apache-2.0, Agentic AI
  Foundation) at the control plane, **OpenTelemetry GenAI semantic conventions** for telemetry,
  **E2B** as a non-NVIDIA sandbox and **Docling** (MIT, LF AI & Data) for documents, Globant can
  propose a governed stack whose enforcement and telemetry layers are foundation-governed. Keep
  the NVIDIA skill-security tools — they are the best available — but stop letting them be the
  whole architecture.
- **Cheapest credible entry point, any region.** Per IDC, 95% of enterprises already run an
  agent-enabled workflow in production and only 45.4% can see token consumption per workflow.
  A **cost-and-usage control plane** touches no business logic, needs no model work, and produces
  the number that unlocks budget for the governance programme. Lead with it when a client says
  they have "already done AI".
