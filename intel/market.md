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

#### Eleventh pass, 2026-11-24 — the forge boundary: the "open source map" this KB presents is a North American map

**The structural fact first.** All 314 repository addresses this KB held before this pass were on
`github.com`, a US-domiciled platform. That is not a complaint about GitHub — it is the observation
that when Globant presents "the open source landscape" for a category, it has been presenting the
**North American view of it**, and had never said so. For a North America engagement this is close to
harmless and occasionally an advantage: the client's own engineers live on the same forge, the
licence metadata is in the format their legal team already reads, and `gh api -X GET
search/repositories` gives exact SPDX, stars and `archived` in one call.

**Where it stops being harmless is procurement language.** A claim of the form *"the leading open
source options are X, Y and Z"* is a claim about a search, and this pass established that the search
had one source. Say "the leading options on GitHub" and the sentence becomes defensible at no cost.

**A North American legal instrument showed up inside an open-source licence file, and it is a first
for this KB.** Mayan EDMS — the most-starred enterprise platform found off GitHub this pass
([mayan-edms/mayan-edms](https://gitlab.com/mayan-edms/mayan-edms), GPL-2.0-only, 683★, active
2026-11-24) — states in `LICENSE` both a **US Copyright Office registration** (No. TX 8-577-731) and
**two USPTO-registered trademarks** (Nos. 7,889,160 and 7,889,166), with the explicit note that the
copyright licence *"grants no rights in those trademarks."*

For a North American engagement that matters more than elsewhere, because these are the instruments a
US client's counsel recognises and weighs:

- the copyright registration strengthens the author's **enforcement position on the code**, which
  raises the cost of a sloppy fork;
- the registered marks mean a **white-labelled deployment** — the normal shape of a Globant delivery
  — is governed by a separate trademark policy, not by the GPL;
- and the two questions have **different answers**: you may modify and deploy, and you may not call
  it Mayan.

**The commercial posture for this region.** North America is where the KB's standing adoption numbers
say the ceiling is organisational, not technical: a 2026 Gartner survey of **1,303 enterprises with
at least $50M revenue** found only **22% had scaled AI across multiple business units**, and a much
larger survey (**120,000+ respondents**) found **8.6% with agents in production** against **63.7%
with no formal AI initiative at all**. NVIDIA's *State of AI 2026* puts agentic adoption highest in
**telecom at 48%**. Dentons reports that, absent universal regulation, companies are **writing their
own AI governance frameworks** — and one analysis argues it is regulatory **fragmentation, not
strictness**, that slows scale-up.

Read together with this pass's finding, the sellable North American work is unchanged in shape but
better justified: **the client's blocker is an internal evidence and governance artefact, not a model
choice** — and now one of the artefacts Globant can produce is the *provenance of the shortlist
itself*: which forges were searched, which refused, and what that leaves unmeasured. A governance
framework a client wrote themselves has no such section, which is precisely why it is easy to add.

*(All adoption figures in this subsection are search-listed at snippet level and not verified against
the primary reports; attribute them, do not adopt them.)*

#### Twelfth pass, 2026-11-24 — the weights boundary in North America

**The region owns both sides of this layer: the licences and the body that refuses to bless them.**
OpenMDW-1.1 — the first licence instrument written for model weights, and the eleventh licence class
in this KB — is stewarded by the **Linux Foundation**, with contributors from **Amazon, Meta, IBM,
Microsoft and NVIDIA** named in its own repository. Meta's Community Licenses are the de facto
default for enterprise open-weights deployment. And the **OSI**, which has **not** approved
OpenMDW-1.1 (review still open at the last traced message, 2026-08-29), is the gatekeeper whose
verdict client security teams will cite.

Adoption context, all search-listed at snippet level: a 2026 Gartner survey of 1,303 enterprise
respondents at $50M+ revenue found only **22% had scaled AI across multiple business units**; a
separate survey of 120,000+ respondents found only **8.6% with agents in production**; Dentons
reports **31% of AI initiatives reaching full production against 88% of organisations using AI**.
MarketsandMarkets values the North America AI market at **$254.86B in 2026**; BCC Research puts the
region at **38.5% of global share**. Named players in a market-research summary: Google, Microsoft,
IBM, AWS, NVIDIA, Oracle, Salesforce, OpenAI, Meta.

**The sellable work here is a licence audit of the model layer, and it is new because nobody's
scanner covers it.** Dentons' finding that US companies are **writing their own AI governance
frameworks** absent federal regulation is the opening: a framework a client wrote themselves has no
weights-licence section, because the tooling that would have prompted one reads `LICENSE` files and
models do not keep their terms there. Two concrete offers:

1. **The weights register (Receta 23)** — four licence facts per model, the base-model edge made
   explicit, and the acceptable-use policy read as part of the licence. Days, not weeks.
2. **OpenMDW migration advisory for model-shipping ISVs.** A North American ISV that publishes
   weights has a genuine reason to adopt OpenMDW-1.1 — one grant over model, data, docs and code,
   with **outputs explicitly unrestricted**. The counterweight is that it has **no SPDX identifier**,
   so their customers' SBOM tooling will report it as unlicensed. **That trade is a consulting
   conversation, and right now almost nobody is having it.**

*(Adoption and market figures in this subsection are search-listed at snippet level and not verified
against the primary reports; attribute them, do not adopt them. Licence facts are byte-verified.)*

#### Thirteenth pass, 2026-11-24 — the erasure boundary in North America: deletion became an inbound API poll

**The regulatory shape changed, and it changed into something engineers build rather than lawyers
answer.** California's DELETE Act (SB 362) created a central **Delete Request and Opt-Out Platform
(DROP)**, and since **1 August 2026** registered data brokers must **access it at least once every
45 days and process the deletion requests they find there**. That is not a web form and not a
mailbox: it is a **queue the obligated party must poll on a fixed cycle**, with the penalty
structure of a machine obligation — reported at **$200 per deletion request per day** of
non-compliance, **with no cure period**. More than **300,000** Californians had filed through DROP
by spring 2026, so the first poll was never going to be empty.

Enforcement arrived in the same month as the deadline: on **11 August 2026** the agency announced
its **first enforcement action against a data broker**, a **$116,490** penalty against
**LocateSmarter LLC**, with a further order against **Cybba, Inc.** reported on 13 August 2026. The
first **independent compliance audit** is due **1 January 2028** and recurs every three years.

**Why this is the region's opportunity rather than its risk.** Every other erasure regime in this
KB is request-driven and human-paced. This one has a **polling interval, a per-item penalty, an
enforcement record and a scheduled audit** — which makes it the first jurisdiction where the
erasure cascade is unambiguously a **system with an SLA** instead of a policy document. The
engagement is concrete: a DROP poller, an identity-resolution step against the client's estate
(this KB already holds entity resolution from the sixth pass, and matching is where these
programmes actually fail), the seven-place cascade from `repos/foundations.md`, and an evidence
artefact sized for the 2028 audit.

**And it lands precisely on the region's measured gap.** Dentons' North American survey found
companies building their own AI governance frameworks in the absence of a single federal rule, but
**few with an integrated, auditable management system** — auditable being the operative word. The
adoption numbers say the same thing from the other side: a 2026 Gartner survey puts only **22%** of
enterprises at AI scaled across multiple business units, and a separate survey of 120,000+
respondents found just **8.6%** with AI agents in production. The constraint is not capability, it
is evidence — which is this KB's most-repeated finding, now reproduced in the erasure layer.

> **Sourcing, stated honestly.** `oag.ca.gov` and the other primary legal hosts do not resolve from
> this session. **Every regulatory figure in this subsection is search-snippet-level, not
> primary** — including the $200/day amount, the 45-day interval, the LocateSmarter penalty and the
> audit date. Verify against the CPPA/CalPrivacy DROP pages before putting any of it in a client
> document. The repository and licence facts elsewhere in this pass are byte-verified; these are
> not, and the distinction is deliberate.

#### The accessibility gate, and the date that moved (fourteenth pass, 2026-11-24)

- **The deadline every 2026 roundup quotes is no longer the deadline.** A DOJ **interim final rule
  published 2026-04-20** extends each ADA Title II web and mobile accessibility compliance date by
  one year: public entities of **≥ 50,000 population move from 2026-04-24 to 2027-04-26**, and
  entities **< 50,000 plus all special districts move from 2027-04-26 to 2028-04-26**. The comment
  period closed 2026-06-22. **The standard did not change: WCAG 2.1 Level A and AA**, and
  enforcement of Title II was not altered.
  > **Secondary-sourced.** Four independent legal sources agree (Duane Morris, Reed Smith, Davis
  > Wright Tremaine, National Law Review). `federalregister.gov` **does not resolve** from this
  > session, so this is **not** primary-verified. Quote it as "DOJ interim final rule, April 2026",
  > never as a citation to the Federal Register this KB has read.
- **Sources in direct conflict — recorded, not reconciled.** Other 2026 vendor material still
  describes the April 2026 date as binding or already passed. Both readings are live on the open
  web right now. **Do not build a pitch on urgency against the old date**; a client's own counsel
  will have the extension.
- **Litigation volume, two incompatible numbers.** Level Access, citing Seyfarth Shaw's March 2026
  analysis: **3,117** federal website accessibility suits in 2025, **+27%** year on year, the
  highest since 2022, and **36%** of all ADA Title III federal filings. A NASCIO-linked source puts
  **digital accessibility lawsuits above 5,000** in 2025. These measure different scopes — use one,
  name it, and never average them.
- **The procurement mechanics are the actual buying trigger.** A VPAT becomes an **Accessibility
  Conformance Report** once completed. One university's rule: the ACR must be **under two years
  old and match the product version being purchased**. State guidance warns that a VPAT is
  **self-reported** and recommends independent validation, and states are tightening vendor
  accessibility requirements ahead of the DOJ dates (Davis Wright Tremaine, September 2026).

**Opportunity.** The one-year extension turns a missed deadline into a **fundable 2027 programme**,
and the sellable unit is not a scan report — it is an **independently validated ACR for the agent
UI**, versioned to the release, with the manual screen-reader evidence an automated scan cannot
produce (`compose/patterns.md`, Receta 27). Every agent a client buys for a covered entity inherits
that entity's obligation, so this attaches to **existing** agent engagements rather than competing
with them.

**Explicit gap.** **Section 508** (federal agencies, as distinct from Title II state and local) did
not appear in any source this pass returned. Not covered — do not assume the Title II dates apply
to federal procurement.


#### El límite del consumo en NA — el mandato se estrechó por vía judicial (added fifteenth pass, 2026-11-24)

> **Aviso de verificación, y vale para las cuatro regiones de este pase.** `arxiv.org` y los *hosts*
> legales y de analistas **no resuelven desde esta sesión** (comprobado una vez y no se volvió a
> sondear, por política). Por eso **los hechos de código y licencia de este pase son más fuertes que
> sus hechos regulatorios**: todo lo normativo y toda cifra de mercado de abajo queda **a nivel de
> snippet de búsqueda**, nunca como bibliografía. Las licencias y repos de `repos/foundations.md`,
> en cambio, están leídos byte a byte.

**Lo que está en vigor y lo que no** (fuentes: despachos y consultoras; se contradicen entre sí y se
registra la contradicción en lugar de resolverla):

- **SB 253 (Alcances 1 y 2): vigente.** La Oficina de Derecho Administrativo aprobó el reglamento
  inicial de CARB el **12-oct-2026**, y el Noveno Circuito **dejó en pie** la obligación de
  Alcances 1 y 2. Umbral: ingresos **> 1 000 M USD**.
- **SB 253 (Alcance 3): frenado.** El Noveno Circuito consideró el Alcance 3 **"probablemente
  inconstitucional"** por la Primera Enmienda y devolvió al juzgado de instancia la cuestión de si
  es **separable** del resto de SB 253.
- **SB 261 (informe de riesgo climático): suspendido.** Medida cautelar desde el **18-nov-2025**
  mientras se resuelve la apelación. Umbral: **> 500 M USD**. **Las fuentes discrepan** sobre el
  estado más reciente: un despacho dice que una resolución del **9-nov-2026** mantuvo la suspensión;
  otro afirma que al **28-jul-2026** no había resolución. Sin acceso al primario, **no se afirma
  ninguna de las dos**.

**Por qué esto cambia el argumento comercial, y no en la dirección obvia.** El Alcance 3 es
precisamente donde caerían las emisiones del proveedor de IA **dentro del inventario del cliente**.
Si el Alcance 3 queda enjuiciado fuera, en California **desaparece el mandato** que obligaba a pedir
ese dato aguas arriba. Conclusión: en NA **no se vende contra una fecha límite** — se vende contra
**presión contractual de cliente y de inversor**, que es un argumento más débil y hay que decirlo
antes de construir una propuesta sobre una obligación que un tribunal acaba de recortar. Es el
segundo caso que esta red de KBs registra de una norma climática estatal **litigada hasta quedar sin
efecto** (el primero fue Colorado, en `energy-kb`), y confirma el patrón: **en NA, cite la norma con
su estado procesal o no la cite.**

**La restricción física, que sí es firme y es la mejor puerta de entrada:** la limitación de la IA
pasó de **suministro de chips a disponibilidad de energía**; una casa de análisis sitúa el déficit
de potencia **2026-2028 en 57 GW**, y el *capex* de los mayores operadores de centros de datos
**ronda los 750 000 M USD en 2026** (BNEF), con **1,5 billones USD** de nueva emisión de deuda
proyectada a tres años. Cifras de analistas, atribuidas, no adoptadas.

**La oportunidad, en una frase:** el entregable no es un modelo, es **la cañería de medición y el
expediente**: Kepler por *pod* → atribución por unidad de negocio → `Green-Software-Foundation/if`
como cálculo auditable → salida en XBRL con `Arelle/Arelle`. Es la **misma forma** que `energy-kb`
documentó para el expediente tarifario y `legal-kb`/`enterprise-kb` para OSCAL: **el producto es el
expediente, no el modelo.** Quinta confirmación independiente de esa tesis en esta red.

#### The language boundary — sixteenth pass, 2026-11-24 (North America)

**The duty: Quebec's Charter of the French Language (as amended by Bill 96).** This is the hardest
language obligation in the region and it lands squarely on software, not just on marketing copy.
Per a 2026 law-firm guide, where a **French-language version of a software product exists and has
been made commercially available**, non-French versions may be sold in Québec only if a
**functionally equivalent French version** is offered. Read for employee-facing tools, the operative
test reported is simpler still: **if the vendor offers French, the employer must make it available to
Québec employees.** The final provisions came into force **2025-06-01**, and reported penalties for
organisations are **CAD 3,000–30,000** per offence.
⚠️ **Secondary-sourced** — law-firm and vendor commentary, not the Charter text or the OQLF. Verify
against the statute before it reaches a contract. The *existence and direction* of the duty is well
corroborated across independent sources; the **numbers** are the part to check.

**Why this is an agent problem and not a translation-budget problem.** An agent UI is software with a
user interface. A conversational agent deployed to a client's Québec employees or customers, that
answers in English because the model defaulted to the language of its system prompt, is the exact
failure this rule addresses — and it fails **per conversation**, not once at release. Three
consequences for scoping:
1. **Functional equivalence is the bar, not availability of a translation.** A French UI that loses a
   feature, degrades the answer, or falls back to English mid-conversation is not equivalent.
2. **Language detection becomes a compliance control**, which makes `pemistahl/lingua-py`
   (Apache-2.0) a governed component — and makes the archived state of `fastText` (26,502★, archived
   2024-03-22) and `cld3` (archived 2023-05-24) a live risk, not trivia.
3. **The federal layer is separate.** Canada's *Official Languages Act* duties bind federal
   institutions and their suppliers; Québec's Charter binds commerce in the province. An engagement
   can be subject to one, the other, or both.

**US federal and state:** this pass found **no language-specific AI obligation** — the regional
picture remains governance frameworks built voluntarily against fragmented federal rules, with
**regulatory fragmentation rather than strictness** reported as the brake on scale-up. Sector
language-access duties (healthcare, benefits, voting) exist but are **not AI-specific** and were not
verified in this pass. **Recorded as an informed gap, not as absence of risk.**

**Opportunity, placed:** a **French-equivalence audit of an agent estate** is a short, well-bounded,
legally motivated engagement with a named deadline already past — the strongest kind of door-opener.
The deliverable is the measured subset in Receta 30 plus a per-locale conformance record. The
permissive stack for it — Pontoon (BSD-3-Clause), CTranslate2 (MIT), Opus-MT (CC-BY-4.0 models),
COMET (Apache-2.0), lingua-py (Apache-2.0) — is in `repos/foundations.md`.

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

#### Eleventh pass, 2026-11-24 — the forge boundary: the sovereign estate is on a forge this session cannot reach

**The finding that should change an EMEA conversation.** The German public-sector forge
**openCoDE** (`gitlab.opencode.de`) **refuses connection from this session** — `CONNECT tunnel
failed, response 403`. So does `foss.heptapod.net`, the canonical home of the Tryton ERP. This KB
therefore cannot currently assess the code published by the one procurement programme EMEA clients
raise by name when they say "sovereign". That is stated as a **declared gap**, not a finding: no
claim is made here about openDesk's licence, components, version or activity, and an engagement lead
who hears the name from a client should know the KB has not assessed it.

**What *was* reachable turns out to make the EMEA case better than the sovereignty rhetoric does.**
The workplace estate added this pass is almost entirely European in origin and all of it is
inspectable:

| Component | Origin | Licence | Stars | Last push |
|---|---|---|---|---|
| [nextcloud/server](https://github.com/nextcloud/server) | Germany | AGPL-3.0 | 37,621 | 2026-11-24 |
| [opf/openproject](https://github.com/opf/openproject) | Germany | GPL-3.0 | 17,676 | 2026-11-24 |
| [xwiki/xwiki-platform](https://github.com/xwiki/xwiki-platform) | France | **LGPL-2.1** | 1,336 | 2026-11-24 |
| [dokos/dokos](https://gitlab.com/dokos/dokos) | France | GPL-3.0-or-later | 39 | 2026-11-24 |

**The argument to make:** sovereignty in this region is usually sold as *where the data sits*. The
table above lets Globant sell it as *what the client can read, fork and audit* — a files platform, a
project platform, a wiki and an ERP, all European-authored, all with the licence read from the
repository, all pushed the day they were verified. That is an **operational** sovereignty claim and
it survives a procurement challenge in a way a hosting-region claim does not.

**And the licence gradient inside one deployment is the billable detail.** AGPL-3.0 for files,
GPL-3.0 for project, LGPL-2.1 for wiki. An agent spanning the suite crosses **three copyleft regimes
in one engagement**, so the only safe architecture is one external service over three documented
APIs. XWiki is the outlier worth noticing: **fewest stars, most permissive licence** — LGPL permits
linking, so a genuine extension is possible there and nowhere else in the suite.

**The demand numbers this region now carries, and they point at the same deliverable.** IDC reports
**58% of EMEA organisations using sovereign AI for all or critical workflows**, while only **33% say
they could govern hundreds of AI agents with today's tooling** — and, separately, that only **9% have
delivered measurable business outcomes from most of their AI projects over the past two years**. Veeam
finds **88% already operating AI agents** against **7% who believe they are fully prepared to manage
them**. With most high-risk obligations of the EU AI Act applying from **August 2026**, the reported
shift is from *how* AI is deployed to **where it runs**.

**Put the two halves together and the EMEA offer writes itself.** Demand for sovereign deployment is
already majority (58%); the capability to *govern* it is a third (33%); the capability to *show
outcomes* is under a tenth (9%). The gap between the first number and the other two is the
engagement. The components are the European stack above, the governance layer is the four boundaries
this KB already documents, and the one thing this pass adds is the honest sentence that goes in the
proposal: **the sovereign forge itself could not be inspected from here, so the assessment covers the
components, not the programme.** Clients in this region reward that sentence.

*(IDC, Veeam and EU AI Act timing figures are search-listed at snippet level and unverified against
primary sources; attribute, do not adopt. Repository rows are verified.)*

#### Twelfth pass, 2026-11-24 — the weights boundary in EMEA, and the clause that makes this region different

**This is the subsection where the pass has a hard, actionable finding rather than a trend.**

`meta-llama/llama-models` → `models/llama4/USE_POLICY.md:71`, read 2026-11-24, states that for
**multimodal models in Llama 4** the Section 1(a) rights *"are not being granted to you if you are an
individual domiciled in, or a company with a principal place of business in, the European Union"*,
and that the restriction *"does not apply to end users of a product or service that incorporates any
such multimodal models."* `grep -c 'European Union'` over the Llama 4, 3.3, 3.2 and 3.1 **licence**
files returns **zero** in every case: the clause is in the acceptable-use policy, which no licence
scanner reads.

**Consequences for an EMEA engagement, in order of urgency:**

1. **Multimodal Llama 4 is the highest-risk default in this region**, and the risk is contractual,
   not technical. The clause turns on **the licensee's** domicile, and expressly spares **end
   users**. So the determining question is *which entity exercises the rights* — a question for
   counsel, answered in week one, in writing. Globant S.A.'s Luxembourg incorporation is a matter of
   public record; whether it brings the contracting entity within the clause is **for legal to
   determine, and this KB states the question rather than answering it.**
2. **Verified permissive European alternatives exist.** **Salamandra**
   ([langtech-bsc/salamandra](https://github.com/langtech-bsc/salamandra), **Apache-2.0**, `LICENSE`
   11,357 bytes) is the clean option: no AUP, no gate, no inherited base licence. **Apertus**
   (EPFL + ETH Zurich + CSCS; v1.5 released 2026-07-24) is reported Apache-2.0 **plus a separate
   acceptable-use policy**, with **v1.5 weights gated behind login and acceptance** — a procurement
   fact that matters for any air-gapped build.
3. **OpenMDW-1.1 has a specifically European value that Apache-2.0 lacks.** Its grant runs under
   *"all copyright, patent, **database**, and trade secret rights."* The EU *sui generis* **database
   right** is a real encumbrance on training corpora, and Apache-2.0 does not address it. For a
   client worried about the provenance of a European training set, that clause is worth explaining.

Regional context, search-listed at snippet level: the AI Act's **high-risk provisions apply from
2 August 2026**, with penalties cited up to **€35M or 7% of global revenue**; IDC reports only **9%
of EMEA organisations** delivered measurable outcomes from most AI projects over two years, and
frames execution — not ambition — as the blocker; OECD finds **half of surveyed SMEs** name a skills
shortage as the primary barrier, with one analysis arguing regulation is **not** the main brake and
citing Denmark's enterprise adoption as above the US enterprise average; a Veeam-linked report claims
**88% already operating AI agents against 7% feeling prepared to manage them**. HSBC's partnership
with Mistral AI for enterprise-wide deployment **with full data ownership** remains the reference
deployment this KB already records.

**The offer that follows:** the AI Act deadline has arrived, every client needs an evidence artefact,
and **the model layer is the part of their estate with no licence evidence at all.** Receta 23
produces it in under a week, and Receta 24 turns it into the machine-readable record the Annex IV
discussion keeps asking for and the standards keep making optional.

*(Adoption, penalty and survey figures are search-listed at snippet level and unverified against
primary sources; attribute, do not adopt. All licence facts and byte counts are verified.)*

#### Thirteenth pass, 2026-11-24 — the erasure boundary in EMEA: the model itself may be the personal data, and the logs may not be deleted

**This is the sequel to the twelfth pass, and it inverts its conclusion.** That pass established
that the weights carry a **licence** independent of the code. This one records the harder claim:
in this region the weights may carry **personal data**, which makes the model a data store subject
to a right of erasure.

**EDPB Opinion 28/2024** holds that AI models trained with personal data **cannot in all cases be
considered anonymous**; anonymity is assessed case by case, and a model is anonymous only where the
training data cannot be obtained from it **"through means reasonably likely to be used."** The
Board is explicit that **a mere assertion of anonymity is not enough** to take the model outside the
GDPR, and it points to post-training measures to remove or suppress personal data — with, in the
worst case, erasure of the unlawfully processed dataset **"and/or the AI model itself."**

**That clause is the commercial fact.** The remedy of last resort is deletion of the model, and
this pass measured — in repositories, not opinions — that **there is no production-grade unlearning
tooling to avoid it**: two-digit-star research code, with the best-known benchmark idle 21 months.
So the EMEA architectural commitment writes itself, and it is defensible to a supervisory authority
precisely because it does not depend on an unproven technique: **personal data goes in retrieval
over deletable stores, never into a fine-tune.**

**The second half of the finding is the opposite obligation.** Under the **EU AI Act Article 19**,
providers of high-risk systems must retain automatically generated logs within their control for
**at least six months** (longer where other Union or national law requires), with a parallel duty on
**deployers under Article 26**; Article 18's documentation retention is a separate and much longer
period, reported at ten years, and **must not be conflated with the six-month log floor**. Per
**Regulation (EU) 2026/1744**, the instrument this KB already holds in `intel/trends.md` §4, these
obligations apply from **2 December 2027** (Annex III) and **2 August 2028** (Annex I).

So one regime compels erasure and another forbids it, and **the reconciliation is a schema
decision, not a legal one**: the Act prescribes **no log format at all**, which is the freedom that
makes this solvable. Keep identifiers out of the log body, log a pseudonymous reference, hold the
mapping in a store that *is* in the erasure cascade — and the log can then be retained at full
fidelity for six months or ten years without being a surviving copy of what was erased. Done after
the fact it is a migration; done now it is a field name.

**The market reads the same way.** IDC reports only **9%** of EMEA organisations delivering
measurable business outcomes from most of their AI projects over two years, and **12%** with
dedicated governance structures. Veeam reports **88%** of organisations already operating AI agents
against **7%** who believe they are fully prepared to manage them. That 88/7 split is the
addressable market for an evidence-shaped deliverable.

> **Sourcing.** `eur-lex.europa.eu`, `ai-act-service-desk.ec.europa.eu`, `gdpr-info.eu` and
> `artificialintelligenceact.eu` all fail to resolve from this session (probed once each). Article
> 19's wording, the Article 18 ten-year figure and the EDPB quotations are **search-snippet-level**.
> **One disagreement resolved rather than recorded:** several live 2026 articles still state that
> high-risk obligations apply from **August 2026**. They are stale — this KB holds the naming
> instrument for the deferral. **Two left open:** the status and adoption dates of **Guidelines
> 02/2026** (anonymisation — reportedly requiring *periodic reassessment* of anonymity, since
> re-identification risk grows over time) and **Guidelines 03/2026** (web scraping for generative
> AI) conflict across sources between "adopted 7 July 2026" and "draft for consultation"; and a
> reported Council position of 21 October 2026 on the Digital Omnibus could not be verified.

#### Accessibility is an AI Act obligation, not only a web one (fourteenth pass, 2026-11-24)

- **The finding that reframes the whole layer: AI Act Article 16(l).** Providers of **high-risk** AI
  systems must comply with the accessibility requirements of **Directive (EU) 2016/2102** (Web
  Accessibility Directive) and **Directive (EU) 2019/882** (European Accessibility Act). **Recital
  80** carries the reasoning: providers must ensure *full* compliance with those requirements.
  Hogan Lovells reads this as an obligation that existing EU accessibility legislation be
  **reflected in the design and development** of high-risk AI systems, where those systems fall
  within the accessibility directives' scope. **Accessibility therefore sits inside the AI Act
  conformity file, not beside it.**
  > **Timing is in conflict and is left unreconciled.** One source dates Article 16's application
  > to **2027-12-02** for Annex III high-risk and **2028-08-02** for Annex I, per Article 113(c);
  > another states the high-risk regime applied from **2026-08-02**. Check Article 113 before
  > quoting either. **One source flagged unreliable:** a DisabilityWorld article describes Article
  > 16 as covering *general-purpose* AI providers, which contradicts the high-risk-provider text in
  > every other source — do not cite it.
- **The EAA itself has applied since 2025-06-28**, and it reaches **non-EU providers** that supply
  covered products or services to consumers in the EU — the same extraterritorial shape as the AI
  Act, and the reason a LATAM or APAC delivery centre building for an EU client is in scope.
- **The conformance baseline is moving to WCAG 2.2.** **EN 301 549 V4.1.1** is reported published
  **2026-09-02**, incorporating **WCAG 2.2 Level AA** and its six additional success criteria, and
  described as the first version built to support EAA implementation. Conformance to EN 301 549
  gives a **presumption of conformity** with the EAA (Article 15).
  > **Secondary-sourced, two independent sources** (a Davis Wright Tremaine ICT-standards update of
  > September 2026 and a Deque Australia post citing the same date). **`etsi.org` does not resolve
  > from this session**, and some sources still describe V4.1.1 as merely *expected*. Treat the
  > date as well-attested but unverified at the standard body.

**Opportunity.** The AI Act conformity work EMEA clients are **already funding** (Annex IV
documentation — `compose/patterns.md` Receta 3) has an **unpriced accessibility line item** inside
it by virtue of Article 16(l). That is a cross-sell onto a budget that exists, not a new budget.
And the same structural gap this KB recorded for Annex IV applies here: **there is no EU-mandated
machine-readable format for an accessibility conformance claim either**, so the OSCAL work from the
eighth pass has a second application — and no ready accessibility catalog to adopt
(`repos/foundations.md`, open item).

**Regional asset worth naming.** The best-tested accessible component set in the open is
**EMEA-origin and MIT**: `alphagov/govuk-frontend`, Crown Copyright/GDS
(`verticals/solutions.md`, this pass).


#### El límite del consumo en EMEA — y una corrección a la hipótesis con la que empezó este pase (added fifteenth pass, 2026-11-24)

> **Corrección, registrada porque es exactamente la clase de error que esta KB documenta.** Este
> pase empezó buscando la obligación de eficiencia energética en el **artículo 40 del AI Act**. **No
> está ahí**: el artículo 40 trata de **normas armonizadas y presunción de conformidad** para
> sistemas de alto riesgo. El deber de reportar energía de centros de datos vive en la **Directiva de
> Eficiencia Energética (EED)** y su **Reglamento Delegado (UE) 2024/1364**. Se deja escrito el error
> y su corrección: **atribuir una obligación al instrumento equivocado es tan falsable como inventar
> un repo**, y aquí se iba a publicar como noticia.

**El deber que de verdad existe, y tiene umbral y fecha** (nivel snippet):

- **Reglamento Delegado (UE) 2024/1364**: reporte a nivel de instalación para centros de datos con
  **≥ 500 kW** de potencia TI instalada. Los Estados miembros pueden **bajar** el umbral, no subirlo.
- **Informe anual antes del 15 de mayo** sobre el año natural anterior.
- **El incumplimiento está medido:** en la primera ronda reportaron **770 centros de datos**,
  aproximadamente el **36 %** de los que la Comisión estima obligados. **Dos tercios no reportaron.**
- **PUE**: obligaciones a cumplir **antes del 1-jul-2027**; los centros que **inicien operación el
  1-jul-2026** cumplen **de inmediato**.
- El paquete de la Comisión de **septiembre de 2026** incluye un **esquema de calificación** para
  centros individuales de más de 500 kW.
- **Las fuentes discrepan** en el número de indicadores (una dice 7 datos de instalación + 18 KPI;
  otra, 24 KPI). No se adopta ninguna cifra.

**Ese 36 % es el dato comercial más fuerte de la región en este pase.** No describe una obligación
futura: describe un **incumplimiento presente y cuantificado** sobre una obligación **ya vigente y
anual**. Es un *engagement* de instrumentación con fecha de entrega recurrente (15 de mayo) y una
población identificable (≥ 500 kW).

**CSRD después del Ómnibus I — el mandato se encogió ~90 %:**

- **Directiva (UE) 2026/470** publicada en el DOUE el **26-feb-2026**, en vigor el **18-mar-2026**,
  transposición hasta el **19-mar-2027**.
- Prueba **única** de alcance: **> 1 000 empleados Y > 450 M EUR** de facturación neta (antes era
  "dos de tres").
- Matrices no-UE: **450 M EUR** en la UE más filial o sucursal con **> 200 M EUR**.
- Alcance estimado: de ~**50 000** a ~**5 000** empresas (≈ **90 %** menos).
- **Las fuentes discrepan** en el primer ejercicio reportado bajo el nuevo alcance (FY2027 vs 2028).
  Se registra la discrepancia.
- **Tope de información en la cadena de valor**: limita lo que un obligado puede exigir a socios
  menores — **recorta justamente la vía por la que una pyme proveedora recibía la presión de dato**.
- ESRS revisados **adoptados por la Comisión el 3-jul-2026**; Taxonomía art. 8 **no cambia**.

**Y aquí está la asimetría que hay que llevar a una reunión:** el **CSRD se encogió** mientras el
**deber EED siguió intacto y con un 64 % de incumplimiento**. Quien venda "proyecto CSRD" en EMEA en
2026 está persiguiendo un mandato que acaba de perder nueve de cada diez obligados; quien venda
**instrumentación EED de centro de datos** persigue una obligación vigente, anual y masivamente
incumplida. **Es la misma capa técnica y dos conversaciones comerciales opuestas.**

**El formato, con fechas:** EFRAG publicó el **borrador de taxonomía XBRL de los ESRS revisados el
17-sep-2026**, consulta cerrada el **11-nov-2026**, entrega prevista a ESMA y a la Comisión **antes
de fin de 2026**. **El estado del *tagging* obligatorio está en disputa** entre fuentes: una sostiene
que aún no es obligatorio y que irá por ESEF, otra que está **suspendido por la Directiva (UE)
2026/470** a la espera de actualizar el Reglamento Delegado ESEF 2019/815, y una tercera que es
obligatorio desde 2026. **No se adopta ninguna.** Lo que sí es sólido: el formato de salida será
XBRL, y el procesador open source permisivo para eso es **`Arelle/Arelle` (Apache-2.0, byte-read)**.

**Soberanía del dato, que en esta capa es un problema de licencia y no de nube:** los factores de
intensidad de red de la vía más usada (`co2.js` → Electricity Maps) son **ODbL con *share-alike***.
Para un cliente europeo que quiera el número **sin** heredar obligaciones sobre su base de datos
derivada, la salida es un factor de fuente propia o de operador nacional. Ver la trampa completa en
`repos/foundations.md`.

#### The language boundary — sixteenth pass, 2026-11-24 (EMEA)

**The duty that is confirmed: EU AI Act Article 50 transparency.** Obligations became applicable
**2026-08-02**, with reported penalties up to **€15 million or 3% of global turnover**. The chatbot
limb (Art. 50(1)) requires disclosure that the user is interacting with an AI system, **except where
that is obvious from the circumstances and context**. The Commission published **non-binding
guidelines on 2026-07-20**, which national market-surveillance authorities and the AI Office are
expected to follow closely.

**The clause that decides who pays, and it is a contracting question.** A company that **commissions
and brands** a chatbot can itself become the **provider** under Art. 50, which means the disclosure
duty does not stay with the model vendor by default. For Globant this cuts both ways and must be
written down: in a white-labelled agent the **client** is likely the provider, and the statement of
work should say which party carries each Art. 50 duty rather than leaving it to be discovered by a
regulator. The voluntary Code of Practice covers machine-readable marking under 50(2) and labelling
under 50(4) — **not** chatbot disclosure under 50(1), so there is no safe-harbour text to point at
for the chatbot case.

**The explicit gap — and it is the most useful thing in this subsection.** This pass searched
specifically for whether an Art. 50 disclosure must be given **in the official language(s) of the
member state** and **found no evidence either way**. The searches returned the disclosure duty in
detail and nothing on its language. What the sources do support is that **multiple national
authorities will interpret Art. 50 and their readings may not always align**, which makes national
variation plausible but is **not** evidence of a language rule. Closing this needs the Commission
guidelines text and a specific member state's market-surveillance guidance, neither of which this
session could reach. **Written down as an informed gap: do not tell a client the disclosure may be
English-only, and do not tell them it may not be.** The question is open and it is cheap to ask
their counsel.

**Consumer-protection law is the likelier source of a language duty than the AI Act**, since
several member states require consumer-facing information in the local language under general
consumer and contract rules. Not verified in this pass — **a lead, not a finding.**

**The regional execution picture, for sizing.** Only **9% of EMEA organisations** report measurable
business outcomes from most AI projects over the past two years; the blocker is reported as
execution capability rather than ambition, with **half of surveyed SMEs** citing a skills shortage.
One vendor survey reports **88% already operating AI agents** while **only 7%** believe they are
fully prepared to manage them. Regulation is framed by analysts as **both** constraint and catalyst
for trusted adoption.

**Opportunity, placed:** an **Art. 50 disclosure and language conformance review** across an
agent estate, delivered as a record rather than an opinion — who is the provider for each agent,
what the disclosure says, in which locales, and the evidence it rendered. EMEA is also the region
where the permissive stack matters most: `langtech-bsc/salamandra` (Apache-2.0, Iberian languages)
and Opus-MT's CC-BY-4.0 pairs allow a **wholly self-hosted** language layer, which is the answer to
the data-sovereignty concern the region's own surveys keep reporting. ⚠️ Regulatory figures here are
**secondary-sourced** from law-firm and analyst commentary; `artificialintelligenceact.eu` and the
legal hosts did not resolve from this session.

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

#### Eleventh pass, 2026-11-24 — the forge boundary: this region's inventory is unmeasured, and that is now written down

**This is the most consequential regional statement in this pass, and it is an admission.** The two
forges on which a large share of Chinese enterprise and AI projects publish — **`gitee.com`** and
**`atomgit.com`** — both **refuse connection from this session**: `curl (56) CONNECT tunnel failed,
response 403`. They were never searched in any earlier pass either, and until now that was not
visible anywhere in this KB.

So every APAC inventory claim this KB has made rests on `github.com` alone. The correct
characterisation of APAC coverage is **"unmeasured"**, not "sparse" and certainly not "empty**"**.
The distinction is not pedantry: *sparse* invites the conclusion that the region builds less, which
is both insulting and, on the available evidence, unsupported. **A `403 CONNECT` tells you about the
network policy, not about the region.**

**What this changes in practice:**

1. **Never present a category shortlist to an APAC client as exhaustive.** Say which forges were
   searched. A client in Shenzhen or Hangzhou may well name a Gitee project in the first meeting, and
   the right response is "we have not assessed that forge", not surprise.
2. **The gap is delegable and cheap to close.** It needs a network policy change, not research
   skill — one allowlist entry turns an unmeasured region into a measured one. Recorded as the
   highest-value open item from this pass.
3. **The one APAC-origin platform the KB does hold is on GitHub and remains correct**: ERPNext
   (Frappe, Mumbai). This pass added its **EMEA sibling**, Dokos (France) — which incidentally shows
   the pattern to look for on the unreachable forges: not new frameworks, but **regional derivatives
   of platforms already held**.

**The demand side, which is the strongest of any region.** Lenovo's CIO Playbook reports **96% of
APAC organisations planning to raise AI investment, by about 15% on average, in 2026**. Forrester puts
**APAC ahead of both North America and Europe on genAI use, at 63%**, and predicts **sovereignty will
shape infrastructure choices for half of firms**. AlphaSense notes the region is not moving in
lockstep, with **Japan notably cautious**. On rules: **Singapore** is consulting on AI use in
financial institutions, **China's "AI Plus" programme** pairs adoption targets with governance
measures, and BSA warns that **new rules in India and Vietnam** could slow adoption and raise costs.

**The commercial read, and it is uncomfortable in a useful way.** APAC leads on adoption and
investment intent, leads on sovereignty as an infrastructure driver — and is the region where this
KB's evidence base is weakest, *because of the toolchain rather than the market*. The honest offer is
therefore the one that does not depend on an inventory: **the governance and industrialisation
work** — the four boundaries, the air-gap method from this pass (MIT, and transferable to any
self-hosted platform), the evidence dossier. Those travel without a component catalogue. Selling a
"best open source options in APAC" deck from this KB's current contents would be selling a GitHub
search result as a regional analysis.

*(Lenovo, Forrester, AlphaSense and BSA figures are search-listed at snippet level and unverified
against primary sources; attribute, do not adopt. The forge probe results are measured in this
session.)*

#### Twelfth pass, 2026-11-24 — the weights boundary in APAC: the most permissive option and the least measurable region

**The finding that should change a shortlist:** **Qwen3** is **Apache-2.0** — stated by the vendor at
[QwenLM/Qwen3](https://github.com/QwenLM/Qwen3) `README.md:397`, *"All our open-weight models are
licensed under Apache 2.0"* — while the repository carries **no `LICENSE` file at all** (404 at both
`main` and `master`). It is the most permissive frontier-class family verified this pass, and the
most likely to be **wrongly rejected** by a client's licence scanner, which sees an unlicensed
repository. The counter-evidence is one line of vendor prose; keep it in the engagement file.

**The inheritance finding, with APAC's own honest example.** **SEA-LION** (AI Singapore),
`aisingapore/sealion` → `README.md:88`: releases *"embrace an open-source ethos under the MIT license
as much as possible; however, the exact licensing terms may vary depending on the underlying base
model's restrictions… it may be bound by the Llama3 License… Similarly, the Gemma-based variants may
carry different terms."* Its own arXiv paper (2504.05747) claims the team *"release our models under
the fully open MIT license."* **The paper and the shipped artefact disagree, and the README sides with
the artefact.** For Southeast-Asian language coverage SEA-LION is still the right answer — but
**resolve the specific checkpoint, never the project.**

Regional context, search-listed at snippet level: Lenovo's CIO Playbook reports **96% of APAC
organisations planning to raise AI investment by ~15% in 2026**; Forrester finds APAC **leading on
enterprise AI use**, with Singapore, Australia, New Zealand and South Korea ahead of most North
American and European countries, and expects **sovereignty to shape AI infrastructure choices for
half of firms**; IDC frames unified AI governance as moving from optional to mandatory; Singapore is
consulting on AI use in financial institutions; BSA warns of divergence costs in **Vietnam and
India**; China's national **"AI Plus"** programme pairs adoption targets with extensive governance.
The ADB's AI Preparedness Index (April 2026) records a gap between advanced and developing economies
in the region.

**The measured limit, carried forward from pass 11 and re-confirmed here.** `gitee.com` is
unreachable from this session, so **Chinese-hosted model repositories were never enumerated** —
Qwen3's licence had to be recovered from GitHub prose rather than from a registry. **The APAC weights
inventory is therefore under-measured, not scarce.** Any claim about "the best open-weights options
in APAC" from this KB should read *"the best we could reach on GitHub."*

**The offer:** sovereignty is the regional buying motive, and **Qwen3 under Apache-2.0 is the
strongest sovereignty-plus-permissive combination verified anywhere this pass.** Pair it with Receta
23 so the client's own scanner does not veto it on a filing convention, and with Receta 24 so the
base-model edge of any fine-tune is recorded before it becomes an inherited obligation.

*(Investment and adoption figures are search-listed at snippet level and unverified; attribute, do
not adopt. Licence facts are verified from the repositories named.)*

#### Thirteenth pass, 2026-11-24 — the erasure boundary in APAC: a registered intermediary, and a second retention floor

**The region acquired a role that cannot be filled with software, and it commenced eleven days
before this pass.** Under India's **DPDP Rules 2025** (notified 13 November 2025, G.S.R. 846(E)),
the **Consent Manager** regime began on **13 November 2026**: a consent manager must be an **Indian
company registered with the Data Protection Board**. The substantive fiduciary duties — notice,
consent, safeguards, breach reporting and **rights handling** — follow on **13 May 2027**, eighteen
months after notification. **Rule 8** covers erasure once the purpose is served, and pairs it with
**log retention of at least one year**.

**Two consequences, and the second is the one that generalises.** First, on an India engagement the
consent-capture UI is buildable from the permissive libraries in `repos/foundations.md`, but the
consent-manager *role* is **procurable from a registered Indian entity** — no open-source component
makes an organisation a consent manager, and a delivery plan that assumes otherwise fails a legal
review rather than a technical one.

Second, India's **one-year** log floor sits beside the EU's **six-month** floor. **The retention
floor is jurisdiction-specific, so the log schema must satisfy the longest floor in scope while the
retention *policy* varies per jurisdiction** — which is this KB's trend 4 ("build the obligation set
as configuration — policy-as-code per jurisdiction over one agent implementation") reproduced
exactly in the erasure layer. One log schema, one cascade implementation, per-jurisdiction
retention and erasure policy as data. That is the only shape that survives a multi-country rollout.

**The engineering gap this region has and the others do not.** `data-privacy-stack/presidio`, the
de-identification engine this KB has recommended since the fourth pass, is **English-first in its
recognisers**. For a Taiwan, Japan or Korea engagement that is a measurable quality problem at the
first step of the cascade, and this pass found the first non-English row to put beside it:
**`danyuchn/pii-guard`** (MIT, 257★, 2026-11-15), reversible Traditional-Chinese de-identification
built so documents can be sent to a model safely. Small and single-origin — but on an APAC
engagement, recogniser coverage in the client's own language is the thing to **measure and quote**,
using `presidio-research`, rather than assume.

**Adoption context.** Forrester puts APAC enterprise adoption at **53%** for predictive AI in IT
operations and **63%** for generative AI; Lenovo's CIO Playbook reports **96%** of APAC
organisations planning to increase AI investment, by an average of **15%** in 2026; sovereignty is
reported as shaping AI infrastructure choices for about half of firms. Singapore's regulators are
consulting on AI use in financial institutions around transparency, accountability and risk
oversight. The BSA — an industry group, so read it as advocacy — argues Vietnam's rules could deter
AI investment and that India's approach risks slowing adoption.

> **Sourcing.** `meity.gov.in` and `pdpc.gov.sg` do not resolve from this session. All DPDP dates
> and Rule 8 contents are **search-snippet-level**, and the official gazette text was not read.
> **One disagreement recorded, not resolved:** sources split on whether an individual's right to
> *route* consent decisions through a registered consent manager begins in **November 2026** or
> **May 2027**; the plausible reconciliation — registration opens first, individual routing rights
> follow — could not be confirmed. A second single-source claim, that large platforms must erase
> the data of users inactive for three years after 48 hours' notice, is recorded as **unverified**.

#### Accessibility: three regimes, three different baselines (fourteenth pass, 2026-11-24)

- **Japan — JIS X 8341-3**, and the sources disagree on its force. One states it is **voluntary for
  the private sector but mandatory in public-sector procurement**; another that compliance is **not
  generally required by law**, though many businesses and public bodies treat it as binding. Its
  technical baseline maps to **WCAG 2.0 Level AA** — an older target than the EU's. The change that
  matters commercially is the **2024 amendment**: a web-accessibility shortfall that prevents a
  disabled person from using a business's services can now be the subject of a
  **constructive-dialogue (reasonable accommodation) request**, which moves accessibility from a
  procurement checkbox to a **customer-facing** obligation for private firms.
- **Australia — Disability Discrimination Act 1992**, enforced by the **Australian Human Rights
  Commission**; the **Digital Transformation Agency's Digital Experience Policy** requires new
  government websites and services to meet digital inclusion, access and performance standards.
  Practice aligns to **WCAG 2.2 AA**, with **EN 301 549** recommended as the test standard.
- **India — RPwD Act 2016**, which mandates accessibility conformance for the **public *and*
  private** sectors, operationalised through **BIS IS 17802** (parts 1 and 2, 2021) and
  **GIGW 3.0**.
- **Several APAC jurisdictions are reported to be developing EAA-inspired legislation** (Australia,
  Japan, Singapore named).

> **Source-concentration warning, and it is severe.** Almost all of the above traces to **one
> vendor** (Deque), read across several language localisations of the same pages — which looks like
> corroboration and is not. **No primary government text was reachable** this pass: JISC, the DTA,
> MeitY/DEPwD and the AHRC were not fetched. Treat this subsection as a **lead list**, verify
> against the official text before any of it reaches a client deck.

**Opportunity.** The spread of baselines — Japan on WCAG 2.0, Australia on 2.2, India on its own BIS
standard — makes **per-country conformance the expensive way to do this**. For any client selling
into more than one of these markets, the engagement is *"one target, mapped"*: build to **WCAG 2.2
AA plus EN 301 549**, the strictest and the forward-compatible one, and produce per-market mappings
from a single evidence set. That is also the answer for an APAC client selling **into** the EU,
where the EAA reaches them extraterritorially.


#### El límite del consumo en APAC — la región donde el dato se pide por contrato, no por ley (added fifteenth pass, 2026-11-24)

**Convergencia ISSB, con fechas que las fuentes no reconcilian** (nivel snippet):

- Primeros informes alineados con ISSB en **2026**: Australia, Hong Kong, Malasia, Sri Lanka,
  Pakistán y Singapur. Detrás: Indonesia, Japón, China continental, Filipinas, Tailandia y Corea
  del Sur.
- **Japón**: obligatorio para empresas del *Prime Market* de más de **3 billones de yenes** desde el
  ejercicio que comienza en **abril de 2026**.
- **Singapur**: una fuente da **FY2025** para obligatoriedad de grandes capitalizaciones. **Esa
  fecha choca** con la lista anterior, que pone a Singapur en 2026. Se registra el conflicto.

**Infraestructura, que en APAC es donde está la norma dura:**

- **Singapur**: el Parlamento aprobó un **Digital Infrastructure Bill el 7-oct-2026**, con
  **licenciamiento obligatorio** para centros de datos de **≥ 3 MW** de carga TI crítica.
  **Fuente única** — se marca como tal y no se afirma sin un segundo testigo.
- **Tailandia**: **aprobaciones de nuevos centros de datos en pausa** mientras define estándares
  nacionales.
- **Malasia**: regulación estricta de **uso de agua** introducida este año, empujada por la escasez
  asociada a la demanda de nuevos centros de datos. **Es el primer caso en esta red de KBs donde el
  insumo limitante declarado es agua y no electricidad.**
- **Australia**: anuncio en **julio de 2026** de la intención de regular centros de datos de IA
  (*snippet* truncado; se registra el anuncio, no su contenido).
- **Industria**: la Asia-Pacific Data Centre Association lanzó en **marzo de 2026** el *Sustainable
  Digital Infrastructure Accord*, con objetivo de **100 % de cobertura con energía libre de carbono
  y renovable al 31-dic-2030** en operaciones APAC. Es un **compromiso voluntario de industria**, no
  una norma.

**El hallazgo regional, y es el que define el entregable:** en APAC la obligación que mueve dinero
hoy **no recae sobre el usuario de IA sino sobre su proveedor de infraestructura** — se espera, de
forma creciente, que el operador del centro de datos **entregue a sus clientes datos precisos de
energía y emisiones para que esos clientes cumplan sus propias obligaciones**. O sea: **la demanda
llega por contrato de suministro, no por regulación de IA.** Eso cambia a quién se le vende: el
comprador natural en APAC es el **operador** que necesita producir el dato para sus inquilinos, y el
entregable es un **sistema de atribución multi-inquilino** — que es exactamente la forma de
`sustainable-computing-io/kepler` (Apache-2.0, 1606★) más la atribución por clave virtual del plano
de control que esta KB ya tiene en `Receta 9`.

**Sigue sin establecerse** (y es el cuarto pase de esta red que lo declara, aquí para enterprise):
**ninguna norma de APAC encontrada obliga específicamente a declarar el consumo energético de un
sistema de IA**. Lo que existe es (a) divulgación financiera de sostenibilidad vía ISSB y (b)
regulación de la **instalación** física. **El hueco entre ambas es donde cae el agente**, y hoy nadie
lo cubre por mandato.

#### The language boundary — sixteenth pass, 2026-11-24 (APAC)

**The duty: India's DPDP Act §5(3) — the notice must be available in 22 languages.** A data
principal must have the option to view the privacy notice **in English or in any of the 22 languages
listed in the Eighth Schedule to the Constitution of India**. The DPDP Rules were notified in
**November 2025**; **Consent Manager** provisions commence **November 2026**, and the **remaining
operational provisions in May 2027** — so the notice-and-consent machinery is **phasing in now, not
retrospective**, which is exactly the window in which a platform project gets funded.

**This KB already held DPDP and had missed this.** The measurement at the top of this pass found
`DPDP` with **10 pre-existing hits** — all treating it as a **privacy and erasure** instrument
(Rule 8 retention, the Consent Manager registration requirement). Its **language** duty appeared
nowhere. The lesson generalises past this row: **a statute read for one boundary yields only the
clauses that boundary was looking for.** Four of the five regional duties in this pass come from
laws this KB had already cited for other reasons.

**The asset that makes it feasible, and it has 500 stars.**
[`AI4Bharat/IndicTrans2`](https://github.com/AI4Bharat/IndicTrans2) is **MIT**, and covers
**translation for all 22 scheduled languages of India** — the same set §5(3) names. It is the
lowest-starred and highest-leverage row in this pass: a permissively licensed, self-hostable path to
a 22-language notice obligation, against a statutory clock. Last push **2025-10-03**, so confirm
maintenance before it becomes a dependency rather than a starting point.

**Regional picture, for sizing.** **96% of APAC organisations** plan to increase AI investment, by
an average of **15%** in 2026. Forrester reports APAC leading on some genAI adoption, with
**Singapore, Australia, New Zealand and South Korea** ahead of most North American and European
countries. The region is reported as **five distinct adoption stories rather than one**, with some
jurisdictions advanced on AI regulation and others nascent; **sovereignty is predicted to shape AI
infrastructure choices for half of firms**, and **security** tops the barrier list. Singapore's
consultations on AI in financial institutions are the named example of a regulator shaping
enterprise boundaries; **Vietnam and India** are flagged as markets whose rules could raise costs,
with **training-data disclosure** the sharpest live issue for enterprise software.

**Other language-relevant assets, placed:** `aisingapore/sealion` (Southeast Asian languages,
already in this KB as a sovereign model) and `SakuraLLM/SakuraLLM` (**GPL-3.0** — recorded and
**not** recommended; copyleft, and its domain is light novels).

**Opportunity, placed:** a **22-language notice and consent layer** for an India-exposed client,
built on IndicTrans2 + a TMS approval gate, with the phase-in dates as the project plan. This is the
clearest statute-to-stack mapping in the whole pass: the law names a list of languages, and an
MIT-licensed project covers exactly that list. ⚠️ Statutory detail is **secondary-sourced** (law-firm
and advisory summaries). Verify against the Gazette text of the DPDP Rules, 2025 and any 2026 MeitY
notifications before it reaches a contract.

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

#### Eleventh pass, 2026-11-24 — the forge boundary: the first non-GitHub LATAM finding, and what its licence says

**A measured zero turned into a measured something, and the reason is vocabulary.** Probing the one
reachable alternative forge in Spanish produced a split result:

| Spanish probe | Result |
|---|---|
| `agente IA`, `empresa gestion`, `nomina` | **Measured zero** — nothing above 5 stars, top hits are coursework; `nomina` collides with `nominatim` because the search is accent-insensitive |
| `facturacion` | **Not a zero** — a live cluster of fiscal-localisation projects |

| Repo | Licence | Stars | Last activity | What it is |
|---|---|---|---|---|
| [dansanti/facturacion_electronica](https://gitlab.com/dansanti/facturacion_electronica) | **GPL-3.0** | 11 | **2026-10-31** | *"Librería para la facturación Electrónica Chilena"* — **Chile**. The first LATAM-origin, licence-resolved, non-GitHub repository in this KB |
| [odoocoop/facturacion_electronica](https://gitlab.com/odoocoop/facturacion_electronica) | **unresolved** — `429` after backoff, twice | 4 | 2026-11-01 | Odoo-cooperative LATAM localisation. **A rate limit is not a licence verdict**, so nothing is claimed |
| [torresoftware/apidian2020](https://gitlab.com/torresoftware/apidian2020) | **NONE** | 11 | 2026-06-23 | **Colombian DIAN** e-invoicing validation API — no licence file, therefore **not proposable** |

**Why eleven stars is worth a paragraph.** This file already argues that regional fiscal
localisation is what makes a business suite actually deployable. This pass found that the Chile and
Colombia localisation work sits **on a forge this KB had never looked at**, at star counts a
GitHub-calibrated filter would discard, and that **one of the three is unusable for want of a licence
file** rather than for want of quality.

The commercial conclusion is therefore specific and actionable: LATAM localisation is **a
relicensing and stewardship conversation with named authors**, not a greenfield build. There is a
working Chilean library under GPL-3.0 (usable as a stock dependency, containment rule as ever) and a
working Colombian DIAN implementation that **cannot be proposed until its author adds a licence** —
which is an email, not an engineering programme. *The energy KB reached the identical conclusion about
its own LATAM layer in an unrelated pass; two KBs converging independently on "the blocker is a
licence file, not a capability gap" makes it a regional pattern worth naming in a proposal.*

**The demand numbers, and the one that matches this finding exactly.** RSM's *AI Readiness in Latin
America 2026* (**400+ business leaders**) reports **~40% of organisations already implementing AI**
and **68% of those adopters planning to expand within 12 months** — against **fewer than one in five
with a formal AI governance framework**. Investment remains thin: **$8.2B of the $190B** allocated
globally to private AI opportunities in 2025. Baker McKenzie describes the regulatory map as
fragmented, with **no country yet holding a fully mature, harmonised regime**, while the IBA notes the
region broadly **follows the EU model** — consistent with the Uruguay Council of Europe signature and
the Peru Law 31814 implementing regulation this KB already records (**confirmations, not new facts**).

**So the LATAM offer has two halves that fit together.** Demand is real and scaling (40% / 68%),
governance maturity is the lowest of any region (<20%), and the open-source base layer has a *legal*
blocker rather than a technical one. **Globant's differentiated move here is to be the party that
fixes the licence** — stewarding a localisation component into a clean permissive or copyleft state
with its author, in the open — and then to sell the governance layer the 80% do not have. That is a
credible regional contribution and it costs one conversation per repository.

*(RSM, investment and regulatory figures are search-listed at snippet level and unverified against
primary sources; attribute, do not adopt. Repository rows are verified, with the one unresolved
licence marked as unresolved.)*

#### Twelfth pass, 2026-11-24 — the weights boundary in LATAM: the sovereign model carries someone else's licence

**The headline, and it is this pass's most consequential regional finding.** **Latam-GPT** — the
region's AI-sovereignty flagship, launched by **CENIA (Chile) on 2026-02-10** — is published as
`latam-gpt/Llama-3.1-70B-LatamGPT-SFT-1.0`: continued pretraining and supervised fine-tuning **on
Llama 3.1 70B**, with its model card stating that use is **subject to the Llama 3.1 Community License
Agreement**. Reported at **>300B tokens**, free to companies and public institutions, first trained
on AWS with future training planned at **Universidad de Tarapacá**.

**So the sovereignty is real — and it is linguistic and in the data, not legal.** A Chilean ministry,
a Brazilian bank or a Colombian retailer that adopts Latam-GPT inherits **Meta's acceptable-use
policy, Meta's "Llama" naming obligation and Meta's 700-million-MAU clause**. That is not a criticism
of the project, which is the strongest Spanish- and Portuguese-language option in the region. **It is
a fact that belongs in the statement of work**, and today it is in almost none of them.

*(Latam-GPT's licence and launch details are secondary-sourced: the model card lives on a host that
returns `CONNECT tunnel failed, 403` from this session. Flagged, not laundered.)*

Regional context, search-listed at snippet level: RSM's survey of 400+ business leaders finds **~40%
already implementing AI** and **68% of adopters planning to scale within 12 months**, with efficiency
the leading motive at 67% — **and fewer than one in five holding a formal AI governance framework**.
Baker McKenzie describes a patchwork with **no country yet holding a fully mature, harmonised
regime**; the IBA notes the region broadly **follows the EU model**, consistent with **Uruguay's
Council of Europe signature** and **Peru's Law 31814 implementing regulation** that this KB already
records. WEF with McKinsey estimates AI could lift regional productivity by **1.9–2.3% annually** and
generate **$1.1–1.7T** in additional value per year. Chile is repeatedly named as the regional leader
on the back of Latam-GPT.

**The offer, and the two halves fit together unusually well.** Demand is scaling (40% / 68%),
**governance maturity is the lowest of any region (<20%)**, and the regional flagship model has a
**legal** dependency rather than a technical one. So the LATAM pitch is not "we will help you comply"
— it is:

> *"The model your sovereignty programme is built on is licensed by Meta. Here is the register that
> says so, the clauses that travel with it, and the permissive alternatives if any of them bite."*

That is Receta 23, it takes under a week, and it is the rare governance deliverable a client finds
genuinely informative rather than procedural. Where a client's requirement is strictly permissive
weights, the verified alternatives are **Salamandra (Apache-2.0)** for Iberian languages and
**OLMo (Apache-2.0)** where training-data openness must also survive scrutiny — with the honest
caveat that neither matches Latam-GPT's regional data coverage.

**Measured gap:** **no LATAM-origin base model with a permissive licence was found this pass.** The
region's flagship is a Llama derivative. That is a measured finding about the **licence** layer and
says nothing about capability — and it is the same shape as this KB's earlier measured zero for
LATAM-origin agent repositories.

*(RSM, WEF/McKinsey and regulatory figures are search-listed at snippet level and unverified against
primary sources; attribute, do not adopt.)*

#### Thirteenth pass, 2026-11-24 — the erasure boundary in LATAM: the obligation arrives before the enforcer does

**Chile's data protection law enters into force on 1 December 2026 — seven days after this pass.**
**Ley 21.719**, published in the Diario Oficial on 13 December 2024, takes effect on that date per
its *artículo primero transitorio*, and creates an **Agencia de Protección de Datos Personales**
with inspection and sanction powers. Two qualifications, and this KB's most-repeated error is to
omit exactly this kind of one:

1. **A postponement bill exists and is not law.** *Boletín 18.623-07* would move entry into force to
   1 December 2027. Until a superseding law is published, **the legal date remains 1 December
   2026** — record the proposal's existence, never its effect.
2. **The regulator may not be staffed when the obligation lands.** On a single source, the Senate
   rejected the proposed slate (*terna*) in May 2026 for failing to reach two thirds, leaving the
   Agency's first council unseated. Treated as a lead, not a finding.

**That gap is the commercial opening, and it inverts the usual pitch.** When an obligation takes
effect before its enforcer is operational, the client's exposure is not an imminent fine — it is
that **the obligation is live, retroactive in its subject matter, and there is no authority to give
guidance.** What sells into that is not a defence strategy, it is the **evidence artefact**: a data
map, a working cascade and a dated record of what was erased and when, produced before the Agency
has an opinion about it. The window is now and it is short.

**Brazil moved from "the law exists" to "the regulator has named AI as a target."** *Resolução
CD/ANPD nº 30/2025* sets four supervisory priorities for the **2026–2027** biennium, and **two of
them are this layer**: **data-subject rights** and **artificial intelligence and emerging
technologies** (the others are children and adolescents online, and public-sector processing).
Critically, the ANPD already supervises AI under **LGPD Article 20** (automated decisions) — it does
not need the *Marco Legal da IA*, still before the Câmara, to act. The sanction ceiling is **2% of
revenue, capped at R$50 million per infraction**, and the authority can order the **immediate
suspension** of an AI tool or a database as a preventive measure, before a sanctioning process
concludes.

**That suspension power is an architecture requirement, not a legal footnote.** In Brazil the
cascade has to be **demonstrable before deployment**, because the downside is the tool being
switched off rather than a penalty negotiated afterwards. It is the strongest argument in the
region for building the evidence artefact first.

**Adoption context.** RSM's survey of 400+ regional business leaders puts about **40%** of
organisations already implementing AI, with **68% of those adopters** preparing to scale within
twelve months and **67%** citing efficiency as the driver — while governance and employee-use
policies lag adoption. That ordering is the regional sales motion: capability is being bought, the
controls are not yet, and the erasure cascade is a control with a date attached to it in two
countries.

> **Sourcing and one unresolved contradiction.** `planalto.gov.br` and `www.gov.br` do not resolve
> from this session; everything above is **search-snippet-level**. On ANPD enforcement volume the
> sources **directly contradict each other**: one states that up to 2026 the ANPD had issued a
> single pecuniary fine of **R$14,400** (July 2023), while another claims **120+ concluded
> sanctioning processes in the first half of 2026, up 280%** year on year. These cannot both be
> true and neither carries a primary citation here — **do not quote either number to a client.**
> The claim of 75 inspections for the biennium with 20 targeting AI systems is also single-source.
> The *Resolución* number, the four priorities and the Article 20 basis are consistent across
> sources and are the parts worth repeating.

#### Accessibility: one regulator-grade mandate, and one litigation channel (fourteenth pass, 2026-11-24)

- **Argentina — the sharpest commercial hook in the region.** Beyond **Ley 26.653** (web
  accessibility, referencing WCAG 2.0), the **BCRA's Comunicación "A" 7517/2022** establishes that
  **all financial entities must comply with digital accessibility requirements**. That is a
  **sector regulator** imposing accessibility on exactly the client type Globant serves most in the
  region — not a general non-discrimination statute, and not a deadline that can be deferred.
- **Brazil — the trigger is a lawsuit, not a deadline.** The framework is the **LBI (Lei
  13.146/2015)**, with **Decreto 5.296/2004**, the **e-MAG** federal web standard and the Libras
  Law; the LBI mandates universal design in digital as well as physical environments, and WCAG is
  referenced. Enforcement runs primarily through the **Ministério Público's civil class actions on
  behalf of persons with disabilities** — the most active enforcement actor. There is no
  administrative date to plan against, which is precisely why the deliverable is **evidence held in
  advance**.
- **Chile — Ley 20.422** plus the Digital Transformation Law, with WCAG-aligned standards that are
  **not formally adopted**; legal backing exists, implementation is inconsistent.
- **Colombia — Ley Estatutaria 1618 (2013)**, focused in practice on digital government services,
  with limited enforcement mechanisms.

> **Two measured gaps, written down rather than left silent.**
> 1. **`NBR 17060` could not be confirmed at all.** It was searched for by name as a Brazilian
>    technical accessibility standard and **no source returned its content or status**. **Do not
>    cite it** until it is verified.
> 2. **Zero LATAM-origin accessibility tooling** was found, using the short Spanish and Portuguese
>    instruments as well as English — consistent with the engine/testing layer being entirely
>    US-origin (`repos/foundations.md`).
>
> All sources for this subsection are **law-firm and vendor pages**; `planalto.gov.br` does not
> resolve from this session, as the thirteenth pass also recorded. Nothing here is primary.

**Opportunity.** Two different products for two different triggers, and conflating them is the
mistake: in **Argentina** the buyer is a **regulated financial entity** with a supervisory
requirement, so the engagement is conformance work with a named regulator attached; in **Brazil**
the buyer is any consumer-facing firm whose risk is a **class action**, so the product is an
**Accessibility Conformance Report plus a re-runnable test suite** — evidence that exists before the
claim arrives, not a remediation sprint after it. Both attach to agent UIs the client is already
building, which is what makes this sellable without a new budget line.


#### El límite del consumo en LATAM — *** BRASIL DEROGÓ SU PROPIO MANDATO ISSB, Y ESO INVIERTE LA VENTA *** (added fifteenth pass, 2026-11-24)

**El hecho, y contradice lo que sigue publicado en todas partes** (nivel snippet; fuentes
secundarias de despachos y consultoras, con discrepancias que se registran):

- **Resolución CVM 193 (2023)** hizo **obligatorios IFRS S1 e IFRS S2** para compañías abiertas
  brasileñas **desde el 1-ene-2026**, con **aseguramiento razonable**. Brasil fue citado
  internacionalmente como **el primer país en obligar al estándar ISSB**.
- **Resolución CVM 244 (mayo de 2026) modificó la 193 y revocó la obligatoriedad futura**,
  estableciendo un modelo de **adhesión voluntaria** con requisitos de transparencia tanto para
  quien divulga como para quien decide no divulgar.
- **La condición que importa:** la compañía que **opte** por reportar debe aplicar **CBPS Nº 01 y
  CBPS Nº 02**, obtener **aseguramiento razonable** y **publicar durante al menos tres ejercicios
  consecutivos**.
- **Discrepancias registradas, no resueltas:** una fuente fecha la derogación el **29-may-2026** y
  sitúa un régimen de *comply-or-explain* desde el **1-ene-2027**, y en el mismo texto afirma que el
  cambio alcanza al ejercicio ya en curso, lo que no encaja con esa fecha. Sin acceso al texto de la
  CVM, **la fecha efectiva se declara incierta**.

**Dato explícitamente retirado de circulación:** la cifra de que **el 65 % de las empresas
brasileñas no estaba preparado** para IFRS S1/S2 es de **2024**, **anterior a la reversión**, y se
sigue citando como actual. **No la use.** Es el mismo fallo que esta red documentó en `energy-kb`
con un borrador federal citado como ley: **una cifra correcta en su fecha es desinformación fuera de
ella.**

**Por qué esto invierte el argumento comercial, y es el hallazgo del pase para la región.** La
lectura perezosa es "se cayó el mandato, se cayó el mercado". Es al revés, y la razón está en la
letra de la propia resolución: **quien se adhiere voluntariamente queda atado a tres ejercicios
consecutivos con aseguramiento razonable.** Eso no es una carrera de cumplimiento de un año: es un
**compromiso plurianual auditado y verificable**, asumido por elección y por lo tanto defendido por
alguien dentro de la compañía. Comercialmente es **mejor cliente** que el obligado a regañadientes:
población más pequeña, intención demostrada, horizonte de tres años y una auditoría externa que
exige trazabilidad del dato — es decir, exige exactamente la cañería de medición de
`repos/foundations.md` y no un PDF.

**Lo que no hay, medido y no supuesto.** Sonda en **español y portugués** sobre nombre, descripción
y README de GitHub (`huella de carbono`, `emisiones gases efecto invernadero`, `pegada de carbono`,
`inventario de emisiones`): los primeros resultados por estrellas son **listas *awesome*, catálogos
de datos abiertos y proyectos de curso**. **No existe un motor de contabilidad de carbono de origen
LATAM, mantenido y con licencia permisiva.** Cero **medido**, no silencioso — y el instrumento queda
registrado para repetirlo.

**Lo que sí hay, y es la pieza aprovechable de la región:** **`EquipoAnaliticaXM/API_XM`** — **MIT,
75★, push 2026-11-10, `default_branch=master`** — librería Python de acceso a **SIMEM.co** y
**SINERGOX/XM**, los sistemas de información del operador del sistema eléctrico **colombiano**. No
es contabilidad de carbono: es **dato de red nacional con licencia permisiva**, y por eso resuelve
el problema que la trampa ODbL de este pase deja abierto — permite construir un **factor de
intensidad local** sin heredar *share-alike* sobre la base de datos derivada. Para un cliente andino
es el punto de partida correcto, y es MIT.

**El techo de la región, heredado de `energy-kb` y aplicable aquí sin cambios:** la capacidad
instalada de centros de datos en LAC es de aproximadamente **2 340 MW** a comienzos de 2026,
creciendo **15-20 % anual**, con el crecimiento de IA limitado **más por suministro eléctrico, red e
inversión que por demanda**. Para esta capa eso significa que **el consumo del agente es un problema
de costo y de licencia social antes que de reporte regulatorio** — no hay un mandato LATAM de
declaración energética de IA encontrado en este pase, y se declara como **hueco medido**.

#### The language boundary — sixteenth pass, 2026-11-24 (LATAM)

**The duty: Brazil's new SAC decree — Decree No. 13,135/2026.** It regulates the Consumer Protection
Code, replaces Decree No. 11,034/2022, was published **2026-10-13** and takes effect **20 days
later (≈2026-11-02)** — i.e. **three weeks before this pass**. The finding that matters for an agent
engagement: **the use of AI and automated technologies does not remove the consumer's right to
real-time human customer service** during the hours the decree sets. Chatbots must be **free and
available 24/7** where telephone service is limited to 8 hours. Scope covers regulated sectors,
Central Bank-supervised digital financial services, digital intermediation platforms, ride-hailing
and delivery. Accessibility of SAC channels is **delegated to the relevant sector regulator**.

**Why this belongs in the language boundary even though it is not a language rule.** It is the
**escalation duty** that every conversational agent in Brazil must now implement: a verifiable,
always-available path from the agent to a human, which is a **product requirement, not a policy
page**. It pairs directly with the human-approval layer this KB already holds
(`humanlayer/humanlayer` in `repos/foundations.md`) and with the approval gate in Receta 30 — the
same control, one for *wording* and one for *handoff*.

**The explicit gap.** This pass searched specifically for a **Portuguese-language requirement** for
digital services or chatbots and **found none** in the decree coverage. Brazil's Consumer Protection
Code is generally understood to require Portuguese for consumer information, but **that was not
verified here** and the decree results do not address it. **Recorded as an informed gap.**
`planalto.gov.br` returned **HTTP 000** from this session, so the decree's own text could not be
read — all of the above is **secondary-sourced** from law-firm and trade coverage, and one source
gives a conflicting adoption date of 2026-11-02 that appears to be an error for the entry-into-force
date. **Verify against the Senate or Planalto text before quoting.**

**Regional picture, for sizing.** About **40% of LATAM organisations** are already implementing AI
and **68% of those adopters plan to expand within 12 months** (survey of 400+ business leaders) —
but **fewer than one in five have a formal AI governance framework**. WEF/McKinsey estimate AI could
lift regional productivity by **1.9–2.3% a year** while describing the region as lagging in
capturing it. On regulation: **no LATAM country yet has a fully mature, harmonised AI regime**, the
regional approach largely **follows the EU model**, regulated sectors face heightened accountability,
**Uruguay** was the first in the region to sign the Council of Europe AI treaty (2025), and **Peru**
published the regulation for its AI law in September 2025.

**The measured tooling gap, stated because silence would look like coverage.** **No LATAM-origin
translation or localisation project surfaced in this pass.** The region's open-language assets
already in this KB — `latam-gpt/language_identifier`, `latam-gpt/anonymization-filter`,
`latam-gpt/toxicity-classifier` — are **corpus-cleaning tools, not translation tooling**, and
Chile's **Latam-GPT** (launched February 2026) is a base model, not a localisation stack. For
Spanish and Portuguese the honest recommendation is **Opus-MT's pairs (CC-BY-4.0 models, MIT code)
plus a client-owned glossary and a TMS approval gate** — not a regional project that does not exist.
This is the second consecutive pass in which the LATAM row is a **real gap rather than a thin
finding**, and writing it down is what keeps the next pass from re-searching it blind.

**Opportunity, placed:** a **human-escalation conformance build** for a Brazil-exposed client —
agent plus a provable 24/7 handoff, with evidence per conversation — against a decree that took
effect three weeks ago and whose sector regulators have not yet issued accessibility rules. First
mover advantage here is measured in months, and the compliance deadline has already passed.

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
