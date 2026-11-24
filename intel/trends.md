---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 📡 Tendencias — Enterprise

> Current trends with the evidence behind them. Where sources conflict, both are given.

## 1. Agents are the default unit of enterprise software

Gartner's forecast — **40% of enterprise applications will embed task-specific agents by
end of 2026, up from under 5% in 2025** — is the most-cited number in the category. The
open-source side corroborates it: a May 2026 survey of GitHub trending found **at least 18
of 30 trending entries were agent-related**, and the shift is characterised as "it isn't
research papers turning into repositories any more, it's agents."

**So what:** agent capability is no longer a differentiator. Assume the client has already
run a pilot and ask what stopped it from shipping.

## 2. The bottleneck is production, not capability

This is the clearest signal of the year and it comes from a competitor's own actions:
**Cognizant launched a dedicated EMEA AI unit on 28 July 2026 explicitly because enterprise
agent pilots were failing at scale.** TechRepublic frames 2026 as the push to break out of
"pilot purgatory". In LATAM one report puts **45% of ML models as never reaching
production**. BCG finds **only ~30% of APAC enterprise workflows are mature enough to
support AI safely at scale.**

**Measured again this pass, and the numbers are worse than "pilot purgatory" suggests.**
Four independent 2026 figures, each measuring something slightly different:
**only 8.6% of companies report AI agents deployed in production** (survey of 120,000+
respondents, corroborated separately by Digitate's North American IT-leader study);
**Gartner 2026 finds only 22% have successfully scaled AI across multiple business units**;
a US survey puts **31% of AI initiatives at full production despite 88% of organisations
using AI**; and IDC's March 2026 EMEA survey finds **only 9% of EMEA organisations delivered
measurable business outcomes from most of their AI projects over the past two years**. The
sharpest single statistic is Veeam's: **88% of EMEA organisations are already operating AI
agents, but only 7% feel fully prepared to manage them.**

**So what:** durable execution, data remediation and process readiness are the billable
work. [temporalio/temporal](https://github.com/temporalio/temporal) (MIT) belongs in the
default architecture, not as an optional extra. And the 88%/7% gap is the opening line of
the pitch: the agents are already running — what is missing is the ability to manage them.

## 3. Governance became a buying requirement, with a board-level trigger

IBM's October 2026 EMEA study: **80% of executives had an AI incident escalate to board or
C-suite in the past year — and only 40% changed governance policy in response.** That 40-point
gap is a live, funded, unmet need. StackAI expects AI governance platforms to become a
budget line item; **41% of EU executives are accelerating governance spend** ahead of the
AI Act's high-risk obligations.

**So what:** sell the evidence trail, not just the agent. Anchor on **NIST AI RMF** and
**ISO/IEC 42001**; instrument with
[Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) and
[NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) (both Apache-2.0).

## 4. Regulation fragmented globally, and the EU's big deadline moved

2026 has no single global AI law. **EU:** the Digital Omnibus, **Regulation (EU) 2026/1744**,
moved Annex III high-risk obligations to **2 December 2027** and Annex I to **2 August 2028**
— scope unchanged, dates deferred. **US:** no federal law; five state regimes already bind,
and June 2026's preemption draft stalled. **APAC:** Korea's AI Basic Act in force since
January 2026, Vietnam's since 1 March 2026, Japan deliberately light-touch. **LATAM:** Peru
first with an AI law, Uruguay first to sign the CoE treaty, privacy law (LGPD, *habeas
data*) doing the real regulating.

**So what:** "one global compliance posture" is not deliverable. Build the obligation set
as configuration — policy-as-code per jurisdiction over one agent implementation.
Full detail per region in `intel/market.md`.

## 5. Agent protocols moved from vendor control to foundation governance

The **Agentic AI Foundation (AAIF)** was formed under the Linux Foundation on
**9 December 2025**; Anthropic donated **MCP**, Block donated **goose**, OpenAI donated
**AGENTS.md**. This is now verifiable in the repositories themselves, which is what makes it
usable in a client conversation rather than a press release: `block/goose` is now
[aaif-goose/goose](https://github.com/aaif-goose/goose), AGENTS.md has its own org at
[agentsmd/agents.md](https://github.com/agentsmd/agents.md), and the `LICENSE` of
[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) now opens
by declaring a **MIT → Apache-2.0 transition** (Apache-2.0 adds the patent grant
enterprises want). Scale: **>10,000 MCP servers in production** by mid-2026, SDKs at ~97M
downloads/month.

**So what:** protocol lock-in is a weaker objection than it was in 2025, and MCP is the safe
integration bet. Put a gateway — [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge)
(Apache-2.0) — in front of it so tool access stays governed.

**Update, third pass 2026-11-20 — the AAIF now governs the control plane too, not just the
protocols.** [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router)
(Apache-2.0, 2,423 ★, pushed 2026-11-19) is **Envoy AI Gateway, renamed and donated**; its
`README` states it is "An Agentic AI Foundation project" under LF Projects, LLC, with *the same
code, maintainers, release cadence and Apache 2.0 license*. So the foundation's remit now spans
MCP (how an agent reaches a tool), A2A's rival surface, AGENTS.md (how an agent is instructed),
goose (an agent) **and the plane where model and tool traffic is authorised, routed, quota'd and
attributed**.

**Why this is the strongest version of the trend:** trend 10 and `intel/market.md` both record
that the agent-governance toolchain is overwhelmingly NVIDIA's — including
`ai-openshell/OpenShell`, whose vendor-neutral org name carries an NVIDIA copyright. A client
asking "which part of this stack is not owned by one vendor" previously had no good answer at
the enforcement layer. Now the answer is the control plane, and it is checkable in the
repository. **Pair Agent Router with `mcp-context-forge` rather than choosing between them:**
the forge is the MCP registry and proxy, Agent Router is the model-and-tool traffic plane.


**Qualification, fifth pass 2026-11-20 — this trend covers two of three protocol legs.** MCP
(agent↔tool) and A2A (agent↔agent) converged and moved to a foundation. The **agent↔user** leg
did not: AG-UI, A2UI, json-render and openui are four live permissive standards with no
foundation steward (trend 15). So "protocol lock-in is a weaker objection than it was in 2025"
is true for integration and false for the user interface. Say which layer you mean.

## 6. Consolidation: point tools are being absorbed into platforms

Unframe reports enterprises moving **away from fragmented AI point tools toward unified
platforms**. The sharpest single data point: **ClickHouse acquired Langfuse (announced
16 January 2026, alongside a $400M Series D)** — LLM observability folding into the data
platform. Langfuse's `LICENSE` now carries ClickHouse's copyright; core remains MIT.
Meanwhile AutoGen has been superseded (AG2 and Microsoft Agent Framework) and Semantic
Kernel is positioned as legacy by the same vendor.

**So what:** warn clients off tool choices with a short consolidation half-life. Prefer
foundation-governed protocols and Apache-2.0 infrastructure over venture-funded point tools.

## 7. Open-source licenses are quietly tightening — verify every one

Of the widely used "open source" enterprise AI tools checked this pass, a large share are
**not** OSI open source. Read from the actual `LICENSE` files on 2026-11-20:

- [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) — **Elastic License 2.0**, not open source.
- [nocobase/nocobase](https://github.com/nocobase/nocobase) — **proprietary EULA** (Singapore entity, rev. 2026-02-24).
- [n8n-io/n8n](https://github.com/n8n-io/n8n) — **Sustainable Use License**; non-`master` branches explicitly unlicensed.
- [open-webui/open-webui](https://github.com/open-webui/open-webui) — custom license with a **branding restriction**.
- [langgenius/dify](https://github.com/langgenius/dify) — **modified** Apache-2.0 with added conditions.
- `ee/` carve-out pattern now standard: Onyx, Mastra, Activepieces, Langfuse, Sim.

Conversely, GitHub's own badge is not reliable in the other direction either:
**NeMo Guardrails reads `NOASSERTION` on GitHub but its `LICENSE` is plain Apache-2.0.**

**So what:** never take a license from a GitHub badge, a directory listing or a blog
roundup. Read the `LICENSE`. This is the cheapest risk control in the studio and it has
already corrected four entries in this KB.

## 8. Smaller, domain-specific models and sovereign deployment

Stellium argues the dominance of massive general-purpose models gives way to
**specialised, domain-specific systems** in 2026. Alongside it, sovereignty: Spectrocloud
flags sovereign AI and "AI factories" as a 2026 enterprise theme, Mistral is letting
businesses **reserve future capacity** via long-term commitments, and the **Apertus**
initiative plus Aleph Alpha anchor an EU-origin option. APAC data-localisation
requirements push the same way.

**So what:** [vllm-project/vllm](https://github.com/vllm-project/vllm) (Apache-2.0) as the
serving layer keeps a deployment portable across sovereign, on-prem and cloud. Designing
API-only locks out EMEA and APAC sovereignty-constrained clients.

## 9. The unit of adoption became the harness, not the framework

The clearest conceptual shift of the second half of 2026. Salesforce's 2026 framing is the
usable definition: *"whose permissions does it operate under? what systems can it reach, and
what is it explicitly prevented from doing? Together, these configurations and integrations
comprise the agent's harness."* Note what that is — three procurement questions and no
modelling question.

The repositories confirm it. There are now **three MIT harnesses at a scale no agent
framework approaches**: [openclaw/openclaw](https://github.com/openclaw/openclaw)
(394,891 ★), [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness)
(284,581 ★) and [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)
(264,904 ★), plus [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents)
(MIT, 31,472 ★) describing itself as "the batteries-included agent *harness*". An
IBM-sourced analyst makes the same argument from the other direction: the enterprise payoff
lies **not in building the agent's "brain"** but in standardising the tools agents call.

**So what:** stop opening with framework selection. By the time Globant arrives the client's
developers have picked a harness, and the decisions that remain are the ones that were
always Globant's: which identity it runs as, which systems it can reach, what it is forbidden
to do, and how that is proven. Framework comparison tables are now a commodity; harness
constraint is the engagement.

## 10. The agent skill supply chain is the new attack surface — and the scanners are already bypassed

Adopting a harness means adopting its skill ecosystem:
[openclaw/clawhub](https://github.com/openclaw/clawhub) (MIT, 9,557 ★) is the registry and
[VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills)
(MIT, 53,885 ★) curates **5,400+** skills from it. Skills are natural-language instructions
plus code that **execute with the agent's own OS permissions**, installed from a public
registry, usually without review.

What the 2026 research found (**provenance warning: this session's network policy reaches
GitHub only, so the papers themselves could not be opened — the figures below come from
WebSearch result summaries and are second-hand. They are recorded because four independent
samples point the same way, and they should be re-verified from source before going in a
client deck**):

- arXiv **2601.10338** (Jan 2026): **31,132 skills analysed, 26.1% contained at least one
  vulnerability**, across 14 distinct patterns in four categories.
- Snyk *ToxicSkills*: of **3,984 ClawHub skills, 36% contained prompt-injection techniques.**
- A third analysis of the same corpus: **13.4% carried critical-severity flaws.**
- A fourth: **80% of skills showed a mismatch between declared and actual behaviour** — but
  concluded most were documentation errors rather than malice. Worth stating, because it is
  the difference between a security programme and a hygiene programme.
- **Scanners are bypassable.** Trail of Bits reportedly bypassed the malicious-skill
  detectors of ClawHub, Cisco and Vercel's `skills.sh`. The Cloud Security Alliance recorded
  **five malicious skills evading updated ClawScan *and* VirusTotal between February and
  May 2026.** Separate work on multimodal hidden-instruction attacks reaches the same
  conclusion.
- CSA's own observation is the one to quote to a CISO: enterprises pull skills **directly
  from public registries without manual review**, and skills **run with the agent's own OS
  permissions** — so runtime containment matters as much as pre-install scanning.

The defences are now open source and permissive, which is the part that makes this
sellable rather than merely alarming:
[NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) (Apache-2.0, 27,027 ★) scans
with **71 vulnerability patterns across 17 categories** — *this figure was read from the
repository's own README; a secondary roundup reported "64 patterns / 16 categories", and the
README is authoritative* — [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator)
(Apache-2.0, 4,224 ★) adds quality gates and **reusable CI templates**,
[ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) (Apache-2.0, 21,829 ★)
and [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox)
(Apache-2.0, 17,707 ★) contain execution, and
[NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) (Apache-2.0) puts middleware on
tool and LLM calls so a policy decision is *enforced* rather than logged.

**So what:** this is the highest-conviction new offer in this KB. Every client that adopted
a harness in 2026 also adopted an unaudited dependency tree that executes with their agent's
privileges, and nobody sold them a control for it. The consensus remedy — scan, pin
provenance, check declared capability against observed behaviour, sandbox — is four
Apache-2.0 repositories and a CI pipeline. See `compose/patterns.md` **Receta 7**.

## 11. Star count has decoupled from enterprise suitability

A methodological trend, and this KB had to correct itself for it. A `stars:>150000` sweep of
GitHub shows the top 40 now contains single-author agent-skill collections —
[mattpocock/skills](https://github.com/mattpocock/skills) (MIT, 328,581 ★),
[obra/superpowers](https://github.com/obra/superpowers) (MIT, 322,580 ★),
[affaan-m/ECC](https://github.com/affaan-m/ECC) (MIT, 307,599 ★) — each more starred than
every framework in `agents/top.md` Tier 1 combined, and each one person's repository: no CLA,
no organisational security response process, no release governance. Two of the largest in the
category have **no licence file at all**:
[anthropics/skills](https://github.com/anthropics/skills) (197,931 ★) and
[multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
(234,677 ★), both checked across five filenames on two branches.

**So what:** stars measure what a client's developers have already installed — which is
genuinely useful intelligence, and a good opening question. They do not measure what Globant
may ship. Rank by licence, governance and maintenance; use stars to find out what is already
inside the client's estate, then go and scan it.

---

## 12. Agent FinOps: cost stopped being a finance report and became a governance control

**New in the third pass of 2026-11-20, and the most sellable trend in this file.**

Through 2025 the agent question was "can it do the task". In 2026 it is "what did the task
cost, who authorised it, and can you show me per workflow" — and the evidence says enterprises
cannot answer:

- **IDC FERS Wave 4 (July 2026): 95% of enterprises worldwide run at least one company-funded
  agent-enabled workflow in production**, but **only 45.4% have real-time dashboards tracking
  token consumption by workflow** — while **61.8% rate their own cost governance as "defined"
  or "optimizing".** Self-assessment is running roughly 16 points ahead of instrumentation.
- **Gartner: spending on AI models and platforms rises 63.4% year on year to $64B in 2026.**
- **FinOps Foundation (via AvePoint): 98% of FinOps practitioners now manage AI spend, up from
  31% two years ago** — a discipline-wide shift in 24 months.
- **IDC: budgeting for token- and inference-based pricing is now the largest barrier**
  organisations cite, and IDC expects FinOps to be folded **into** AI governance frameworks.
- **EY: agentic AI converts fixed labour cost into variable compute consumption**, which is why
  it needs "agentic FinOps" spanning infrastructure, governance and failure recovery. EY also
  predicts **40% of agentic projects cancelled by 2027** — a prediction, not a measurement.
- **Named failure modes** (AvePoint): untracked token usage, **agent sprawl**, shadow AI, and
  unaccounted licences. Forrester expects **model routing to become critical** as cost bites,
  and FinOps and AIOps to converge.

**The framing to take into a client meeting comes from McKinsey: the unit of governance should
be the completed business outcome, not the token cost.** That is worth saying out loud in a
Globant context, because **Glob.AI already bills per output** (see `intel/market.md`). The
commercial model Globant launched on 6 Aug 2026 and the governance model the market is
converging on are the same model. That alignment is an argument no competitor billing by
headcount can make, and it is also a warning: pay-per-output puts the token bill on Globant's
side of the line, so the instrumentation below is margin protection, not just a client feature.

**What to build, and it is all permissive** (verified 2026-11-20, see `repos/foundations.md`):
a gateway that attributes usage — [agent-router](https://github.com/theagentrouter/agent-router)
(Apache-2.0) or [litellm](https://github.com/BerriAI/litellm) (MIT core) —
metering and entitlements in [openmeter](https://github.com/openmeterio/openmeter)
(Apache-2.0), infrastructure cost in [opencost](https://github.com/opencost/opencost)
(Apache-2.0), spans named per the
[OpenTelemetry GenAI semantic conventions](https://github.com/open-telemetry/semantic-conventions)
(Apache-2.0) so the data lands in the client's existing APM, and the whole thing reported in
[Superset](https://github.com/apache/superset) (Apache-2.0). Recipe in
`compose/patterns.md` Receta 9.

**So what:** the cost dashboard is the cheapest credible entry point into an enterprise that has
already deployed agents — which, per IDC, is 95% of them. It needs no model work, touches no
business logic, and produces the number that unlocks the budget for everything else in this KB.

## 13. Agent payments: the authorisation boundary moved from tools to money

**New trend, fourth pass 2026-11-20.** Through 2026 the governance question was *which tools
may an agent call*. A payments layer now exists, and the question becomes *how much may it
spend, on whose mandate, with what non-repudiable record*. That is a different control, owned
by different people — treasury, risk and audit, not the platform team.

**Evidence (repositories, first-hand).** Three permissively-licensed protocols compete at
different layers of one stack, all verified on 2026-11-20:
[AP2](https://github.com/google-agentic-commerce/AP2) (Apache-2.0, 3,281 ★, pushed 2026-06-17),
[ACP](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) (Apache-2.0,
1,607 ★, 2026-07-18), the
[A2A x402 extension](https://github.com/google-agentic-commerce/a2a-x402) (Apache-2.0, 571 ★,
2026-11-11), plus agent-identity work in
[forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol)
(MIT, 180 ★) and a runnable ACP/UCP reference in
[NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce)
(Apache-2.0, 89 ★, 2026-11-18).

**The non-obvious part: this layer is not ready, and the star counts hide it.** AP2 carries 5.7×
the stars of the x402 extension and has been idle five months, while the extension was pushed
nine days before this pass. The same decoupling as §11, now *inside a single protocol family*.

**Second-hand and flagged:** multiple secondary sources report Google donating AP2 to the
**FIDO Alliance** (one comparison dates it April 2026). No primary source was reachable this
session. Do not put the donation in a client deck unverified.

**So what:** sell the *mandate and evidence trail*, not the rail. The durable, portable idea is
a signed record of what the user authorised, which survives whichever protocol wins. Concretely:
no agent reaches a payment rail in 2026 without a human approval step, and the spend cap belongs
at the gateway (§12, Receta 9) where it is already enforceable. Recipe: Receta 11.

## 14. ISO/IEC 42001 is becoming a procurement gate, not a standard to cite

**New trend, fourth pass 2026-11-20.** This KB already named ISO/IEC 42001 and NIST AI RMF as
standards to anchor on. The shift reported in 2026 is about *who asks for it and when*: buyers
are scoring it in vendor questionnaires and RFPs rather than treating it as a maturity badge.

**What the sources say — all second-hand, and they disagree.**

- Several consultancy and vendor sources report enterprise procurement teams embedding ISO 42001
  status into vendor questionnaires, and European procurement folding it into due diligence.
- Buyers are reported to ask for the **scope statement plus sample risk registers** before
  awarding points — the certificate alone is not the artefact. Certification applies only to a
  defined scope, so a narrow scope statement is a weak signal.
- **The disagreement, recorded:** sources split on mandatory versus preferred. One (Brightdefense,
  updated Sept 2026) states plainly that the unresolved issue is how quickly 42001 becomes a
  default RFP requirement rather than a preferred assurance signal. A claim that it is "the new
  SOC 2" is a claim about trajectory, not current policy.
- **It does not discharge regulation.** 42001 is reported to reduce EU AI Act compliance risk
  but **not** to automatically satisfy the Act. Do not let a client conflate them — see §4.
- **Public sector splits by region.** US federal buyers are reported to lean on **NIST AI RMF**
  as the common checklist, with 42001 adding an auditable governance layer on top.
- **Timing is the actionable part:** certification is reported to take **6–18 months**. That makes
  it a pipeline question now, not a 2027 one.

**So what, two ways.** For clients: the deliverable is the auditable AI management system — the
thing a Dentons survey of North American leaders found few organisations have actually
implemented (see `intel/market.md`, North America). For Globant: a studio that can produce the
scope statement, risk register and evidence trail is selling the *audit artefact*, which is
exactly what the red-team and eval-gate tooling in `repos/foundations.md` already generates as a
by-product. Receta 10 produces the evidence; this trend explains who buys it.

## 15. The agent-to-user layer is the one protocol surface that did *not* converge

Trend 5 above is true and incomplete. The protocol story has three legs, not two: **MCP** for
agent↔tool, **A2A** for agent↔agent, and **AG-UI** for agent↔user. The first two converged and
then moved to the Linux Foundation. The third did not converge at all.

Four permissive, actively-developed, mutually incompatible standards sit within one order of
magnitude of each other, verified on 2026-11-20:

| Standard | Repo | Licence | ★ | Backing |
|----------|------|---------|---|---------|
| AG-UI | [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | MIT | 20,766 | CopilotKit — a venture-funded company ($27M, May 2026), **not** a foundation |
| json-render | [vercel-labs/json-render](https://github.com/vercel-labs/json-render) | Apache-2.0 | 19,791 | Vercel |
| A2UI | [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | Apache-2.0 | 17,690 | Google (announced 15 Dec 2025; 1.0 shipped) |
| openui | [thesysdev/openui](https://github.com/thesysdev/openui) | MIT | 15,375 | Thesys |

Adoption claims cut across the fragmentation rather than resolving it: Google, Microsoft, Amazon
and Oracle are all reported to support AG-UI, and LangChain, Mastra, Pydantic AI and Agno
integrate it — while Google ships A2UI, which it says was developed with partners *including the
AG-UI/CopilotKit team*. Gemini supports A2UI 0.9.1 and ByteDance shipped an A2UI renderer for
Lynx in June 2026. Named AG-UI enterprise users reported in coverage of the funding round:
Deutsche Telekom, Docusign, Cisco, S&P Global. **All adoption figures here are
company-sourced via press coverage, not independently verified** — the repository facts are
first-hand, the market claims are not.

**So what, precisely:** the honest line to a client in 2026 is *"tool integration is a settled,
foundation-governed standard; the user-facing layer is not, so we will build it to be
replaceable."* Concretely — the agent emits typed UI intent, one adapter module binds it to
AG-UI or A2UI, and no renderer vocabulary appears in the agent's reasoning or prompts. The cost
of getting this wrong is not a rewrite of the agent; it is a rewrite of every screen.

**Corollary, and the sharper commercial fact:** the previous generation of this layer is dying in
public. `Chainlit/chainlit` (Apache-2.0, 12,498 ★), `langchain-ai/agent-chat-ui` (MIT, 3,253 ★)
and `langchain-ai/deep-agents-ui` (MIT, 1,705 ★) are all reported **archived** by the GitHub API,
and none of their READMEs says so. The three share one shape — a standalone chat window in
front of an agent — and every live project in the layer has the opposite shape: render into the
host application. **The chat shell is being abandoned as a product category.** Any client whose
agent front end is one of those three has an un-announced end-of-life in production.

## 16. You cannot govern what you have not inventoried — and the inventory tooling is immature

Trends 3, 10 and 14 all describe governance as the 2026 buying requirement. ISO/IEC 42001 is a
procurement gate; EU AI Act record-keeping is an obligation with dates. Both presuppose an answer
to a question most enterprises cannot answer: **what AI do we actually run?** With >10,000 MCP
servers reported in production across the market and skills installed per-developer, the estate
is not in a vendor portal.

The open tooling that produces that answer exists, uses a standard an auditor already accepts,
and is small:

- [CycloneDX/specification](https://github.com/CycloneDX/specification) (Apache-2.0, 585 ★) —
  the OWASP BOM standard, including **ML-BOM**. Use the standard; do not invent a format.
- [Trusera/ai-bom](https://github.com/Trusera/ai-bom) (Apache-2.0, 368 ★, **last push
  2026-05-24**) — discovery of agents, models and APIs in infrastructure.
- [sbom-tool/sbom-tools](https://github.com/sbom-tool/sbom-tools) (MIT, 268 ★, 2026-11-17) —
  semantic AI-BOM **diff** and compliance validation; turns a snapshot into drift detection.
- [apisec-inc/mcp-audit](https://github.com/apisec-inc/mcp-audit) (MIT, 167 ★, 2026-08-18) —
  scans MCP configs for exposed secrets and shadow APIs.

**So what:** the asymmetry between the value of the obligation and the maturity of the tooling is
the opening. A four-week "AI estate inventory" engagement — discover, express as CycloneDX,
diff weekly, hand over the 42001 evidence pack — is a credible first deliverable for the very
common client who says *"we need AI governance"* and cannot list what they run. It also
front-loads the hardest input into every later governance workstream. See
`compose/patterns.md` Receta 13.

## 17. Agents are being managed as a workforce, and the tooling for it is bigger than the frameworks

[paperclipai/paperclip](https://github.com/paperclipai/paperclip) — MIT, **115,408 ★**, 19,156
forks, pushed 2026-11-20 — describes itself as "the open-source app everyone uses to manage
agents at work." It is more starred than every framework in `agents/top.md` Tier 1 combined, and
[NousResearch/hermes-paperclip-adapter](https://github.com/NousResearch/hermes-paperclip-adapter)
(MIT, 2,065 ★) exists to run the Hermes harness "as a managed employee in a Paperclip company."

Read with trend 9 (the unit of adoption is the harness) and trend 11 (stars have decoupled from
enterprise suitability), the shape is clear: the market is organising agents the way it organises
people — a role, a manager, an assignment, a review. **So what for an engagement:** the questions
a client will ask in 2027 are org-design questions, not modelling ones — who owns this agent, who
approves its work, what is its scope, how is it reviewed, when is it retired. That maps onto the
approval layer (`humanlayer`, Apache-2.0) and the identity/attribution layer this KB already
carries. It does **not** mean recommending `paperclip` into a regulated estate on its star count;
it means not being surprised when the client has already installed it.

## Trend sources that disagree — recorded, not reconciled

- **North American adoption:** Stanford AI Index 2026 says **90%** organisational AI use;
  NVIDIA says **70%** active usage; US Census BTOS says **5.4–19.8%**. Different questions
  ("any use ever" vs "used in the last two weeks"), not different facts. Quote the one that
  matches the question being asked, and say which.
- **Enterprise AI spend:** Menlo Ventures' **$176.8B / 5.4x YoY (Sept 2026)** is a single
  vendor estimate and the only figure of its kind found. Treat as directional.
- **Depth of adoption (new source, fourth pass):** a **Deloitte** survey of **3,235 senior
  leaders** reports **two-thirds** of organisations seeing efficiency gains but only **one in
  five** seeing increased revenue, and just **34%** using AI for deep transformation (new
  products or reinvented core processes). Read alongside Gartner's **22%** scaling figure and
  the **8.6%** agents-in-production figure already in this file: four sources, four different
  questions, all pointing the same way — breadth is real, depth is not. Deloitte's own framing
  is that deploying a copilot is the easy part and redesigning the work around it is the
  leadership test, which is the single most useful sentence in this pass for a client
  conversation. **Second-hand:** `deloitte.com` was not reachable this session.
- **EU AI Act high-risk date:** older secondary sources still say August 2026. They predate
  the Digital Omnibus. **2 December 2027** (Annex III) is correct per Regulation (EU)
  2026/1744 — corroborated independently by this KB's energy pass.
- **How many enterprises actually run agents in production — the sharpest contradiction in this
  KB, added third pass.** **IDC FERS Wave 4 (July 2026) says 95%** run at least one
  company-funded *agent-enabled workflow* in production. **Digitate and a separate 120,000+
  respondent survey both say 8.6%** of companies have *AI agents deployed* in production, with
  **63.7% having no formalised AI initiative at all**. Gartner lands between them at **22%**
  having scaled AI across multiple business units, and a US survey at **31% of AI initiatives in
  full production**. These are not reconcilable by averaging — they measure different objects:
  *a workflow with an AI step somewhere in it* (95%), *a deployed autonomous agent* (8.6%), and
  *organisation-wide scaling* (22%). **Practical rule: never quote 95% and 8.6% in the same
  deck without defining both.** The honest and still-compelling version is that nearly every
  enterprise has agent-adjacent workflows in production while fewer than one in ten has a
  governed agent — which is precisely the gap this KB sells into. Every one of these figures is
  second-hand; see the verification note below.

---

## Verification channel for this pass — what could and could not be checked

Recorded so a future pass does not mistake a network limit for a research gap. In this
session, outbound access reaches **GitHub only**: `gh api search/repositories` (metadata) and
`raw.githubusercontent.com` (file contents, including `LICENSE`) both work;
`api.github.com/repos/...`, `github.com` HTML, `arxiv.org`, `labs.cloudsecurityalliance.org`
and every other host fail to resolve or are refused by the proxy.

**Consequence:** every repository, star count, push date and licence in this KB is
first-hand and reproducible. Every market statistic, survey percentage and research finding
came from WebSearch result summaries and is **second-hand** — attributed to its source but
not read at source. The two tiers of evidence are not interchangeable, and this pass has
flagged the second tier wherever it is load-bearing.

**Fifth-pass addendum, 2026-11-20 — two more channels measured.** `search/repositories` and
`raw.githubusercontent.com` worked again (30 repositories re-verified, 15 `LICENSE` files read).
Two new refusals, both of which change what this KB may claim:

- **`api.github.com/users/{org}` returns 403** ("sessions are bound to their configured
  repositories"). **Org location is therefore unverifiable from here.** Every region-origin
  attribution in the fifth pass comes from web-search evidence about the *company*
  (CopilotKit/Seattle, Chainlit/Paris, Google, Vercel, ByteDance), never from GitHub metadata.
  Do not quote origin counts or ratios to a client.
- **`github.com` HTML returns 403** (378 bytes, no page). This matters because the archival
  finding in trend 15 rests on the search API's `archived` flag with **no second channel
  available**; the READMEs of the three archived repositories carry no deprecation notice.
  Stated as evidence, not hidden: one channel, queried twice, plus one corroborating web-search
  signal for Chainlit only.

---

## Sixth pass, 2026-11-20 — the data plane, and a rule that generalises across this rotation

### The semantic layer became the governance contract for data agents

The dominant 2026 position across the analyst and vendor literature is that a governed
semantic layer, exposed over MCP, is what makes enterprise text-to-SQL viable — and that **MCP
alone is transport, not governance**. The supporting evidence, with its weaknesses stated:

- **Schema width is the cliff.** A 2025 study, reached through vendor secondary sources,
  measures **GPT-4o at 86% execution accuracy on academic benchmarks collapsing to 6% on
  enterprise databases with more than 1,000 columns.** This is the single most useful number in
  this pass, because it explains why a text-to-SQL demo on a toy schema predicts nothing about
  production.
- **The measured repair is large and the sample is tiny.** A **dbt Labs benchmark (April
  2026)** reports semantic-layer grounding lifting Claude Sonnet 4.6 from **90.0% to 98.2%** and
  GPT-5.3-Codex from **84.1% to 100%** — across **11 questions on one modelled project, run by
  a semantic-layer vendor.** Quote it as architectural justification, never as a service level.
- **Forecast, secondhand:** Gartner (February 2026) projects that by 2028, **60% of agentic
  analytics projects relying solely on MCP will fail** without a consistent semantic layer.
- **Vendor direction of travel:** at Google Next '26, Looker added BI agents grounded in a
  governed semantic model with a native MCP server. The hyperscalers are converging on the same
  architecture, which means the *pattern* is safe to standardise on even though the specific
  vendor claims are self-interested.

**Why this is a trend and not a tool note:** it relocates the deliverable. For four passes this
KB has argued the agent is the least consequential choice in an engagement; in the data-agent
category that argument now has a number attached to it. The billable artefact is a set of signed
metric definitions, and the agent is a thin interface onto them.

### The licence-concentration rule, now generalised beyond one layer

The energy KB established that the **metering** layer was where non-OSI licences concentrate and
where sorting by stars gives systematically wrong recommendations. This pass found the same thing
in the **enterprise data plane**, and the mechanism is now clear enough to state as a rule:

> **The closer an open-source layer sits to a vendor's core SaaS revenue, the more likely it is
> source-available rather than open source — and the better marketed it is, the more likely the
> clean substitute has fewer stars.**

Data integration and BI *are* the product for the companies that build them, so that is exactly
where Elastic License 2.0, FSL, AGPL and open-core cluster. The evidence from this pass: the
encumbered options are Airbyte (22.4k ★, ELv2), Metabase (50.4k ★, AGPL), ingestr (4.0k ★,
FSL-1.1), Zingg (1.3k ★, AGPL) and Lightdash (6.2k ★, open-core) — and **in all five cases the
permissive substitute is less starred**: dlt (6.1k), Superset/Evidence (7.1k), Meltano (2.7k),
Splink (2.6k).

**Operational consequence for every industry in this rotation:** when opening a *new* layer,
check licences **before** building the table, not after. A table built by star rank and
licence-checked afterwards has to be thrown away, and three KBs in this family have now paid
that cost.

### A fifth licence class: time-delayed permissive (FSL)

This KB family had recorded four non-OSI classes from the energy passes — Fair Source (a user
cap), PolyForm Noncommercial (a total commercial block), revocable grants (a continuity risk),
and bespoke-but-substantively-permissive (read the file, do not assume). **The Functional Source
License 1.1** on [bruin-data/ingestr](https://github.com/bruin-data/ingestr) is a fifth and
behaves unlike any of them: *"each version becomes Apache 2.0 two years after release."* A
non-compete window rather than a permanent restriction. It creates an engineering decision no
other class does — **pinning a release older than two years is a compliant path**, with a real
maintenance cost to quote. Any repository in this family filed simply as "not open source"
deserves a re-read against this class, because the answer may be "not yet."

### Archived-but-highly-starred is now a measured systemic property

Pass 5 found three archived chat-UI repositories whose READMEs did not disclose it. Pass 6 found
a fourth, in a different layer: [vanna-ai/vanna](https://github.com/vanna-ai/vanna) (MIT,
**23.8k ★**, archived **29 March 2026**), the second most-starred project in its category, dead
for nearly eight months. **Stars do not decay when a project dies**, so any star-sorted search —
which is what a client's engineers run — surfaces dead code with full social proof. This is now
a standing check in this KB's method, and it is also a sellable finding: dependency-provenance
review, already offered in `repos/foundations.md`, has four archived repositories and four
renamed/moved organisations behind it as evidence.

### A tenth way to measure a false zero — found by this pass, in this pass's own method

This pass verified its 33 new and cited URLs by fetching `README.md` over
`raw.githubusercontent.com` and treating a 200 as "the repository exists."
[data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) returned **404 on
`README.md` on both `main` and `master`** — which, read carelessly, says a repository the fourth
pass had verified in detail is gone.

It is not gone. `LICENSE`, `pyproject.toml`, `SECURITY.md` and `docs/index.md` all return **200**
on `main` and on `HEAD`. **The repository simply has no root `README.md`** — its landing content
lives in `docs/`. The 404 measured the probe, not the project.

**Rule: never use `README.md` as an existence check.** A project that publishes documentation
from `docs/` or a docs site has no root README, and this is common in mature,
foundation-governed repositories — exactly the ones a KB is most likely to recommend. Probe
`LICENSE` first (it is the thing being verified anyway), and fall back to `pyproject.toml` /
`package.json` / `docs/index.md` before concluding anything is missing.

This is the **tenth** documented way this KB family has measured a false zero, after PRODIST,
parenthesised OR, IEEE 1547, AMI, reservoir, un-indexed forks, NOASSERTION, master-vs-main and
LICENSE-MIT. Nine of the previous nine were found by auditing *another* pass's work; this one
was found by auditing the current pass's own, which is the cheaper place to find it. It is also
a live demonstration of the rule the energy pass derived: **a new negative does not beat a
verified positive just by being more recent** — the fourth pass's record of this repository
(byte-identical `LICENSE` across both the old and new organisation paths) was right, and the
correct response to the conflict was to explain the discrepancy rather than delete the row.

### Method note — the manifest-first rule gained a counter-example, and survived

The energy pass derived: *read the package manifest first, because it declares the licence as an
author-written SPDX expression.* This pass found the case that bounds it.
[metabase/metabase](https://github.com/metabase/metabase)'s root `package.json` declares
`"license": "private"` — a manifest-only read yields a **false negative** on a repository that
is in fact AGPL-3.0 outside `enterprise/` plus a commercial licence inside. Meanwhile
[airbytehq/airbyte](https://github.com/airbytehq/airbyte)'s *marketing page* claims Apache-2.0
while its root `LICENSE` is ELv2 — a **false positive** from the source a hurried reviewer is
likeliest to trust. **Refined rule: read the manifest *and* the licence file; when they
disagree, record the disagreement rather than resolving it to the convenient answer.** Notably,
[Canner/WrenAI](https://github.com/Canner/WrenAI)'s own licence file independently states the
same precedence logic — that the manifest governs published artefacts while the licence file
governs repository sources — which is corroboration from a project maintainer rather than from
another pass of this KB.

---

## Seventh pass, 2026-11-20 — authorization became the bottleneck, and the licence filter moved again

### 18. The constraint on enterprise agents moved from capability to entitlement

Six passes of this file tracked the constraint as it moved: capability → production
(§2) → governance as a buying requirement (§3) → inventory (§16) → the semantic layer (§15,
sixth pass). This pass found where it sits now, and it is narrower and more concrete than any
of those: **an agent cannot be deployed against a client's real document estate until the
retrieval layer knows who is asking.**

The evidence is in the shape of the market, not in a forecast:

- **The capability is carved out of the open-source product that needs it most.** In
  [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) (33,488 ★), the most popular
  open-source enterprise search platform, document permission sync lives **only** under
  `backend/ee/onyx/external_permissions/` — verified 200 inside `ee/`, **404 outside it** — and
  the root `LICENSE` places everything under `ee/` beyond the MIT grant. Eleven connectors with
  a `doc_sync.py` were proved by probe. **When a vendor puts one feature behind the commercial
  line, that is a market signal about which feature is load-bearing.**
- **The standards bodies are mid-flight.** The MCP **Enterprise-Managed Authorization** profile
  is published at revision `2026-07-28` and builds a three-step chain — SSO → token exchange
  (**RFC 8693**) → JWT authorization grant (**RFC 7523**), with the resource server advertised
  through Protected Resource Metadata (**RFC 9728**). But the ID-JAG Internet-Draft underneath
  it is **unfinished**, and vendor support is uneven: Okta reported as first IdP, **Keycloak
  experimental**, Atlassian shipping it in Rovo MCP. A protocol surface is being standardised
  *while* enterprises deploy on it.
- **The tooling exists and is permissive, which means this is buildable now.** Four
  Apache-2.0 engines (`apache/casbin`, `authzed/spicedb`, `openfga/openfga`, `ory/keto`) plus
  Apache-2.0 Keycloak and MIT oauth2-proxy. **Nothing in this layer needs to be bought.**

**What it means commercially.** This is the rare trend where the open-source answer is complete
and the commercial product is the one with the gap, inverted from the usual shape. The billable
work is integration — mirroring each source system's ACL model into a permission graph, which is
60–70% of the build (`compose/patterns.md` Receta 16). **It is also the first layer in this KB
where the deliverable is a negative result**: the acceptance test is *zero leaks on an
adversarial set*, not an accuracy number, and unlike accuracy it is a hard gate rather than a
negotiation.

### The licence-concentration rule reproduced in a third layer

The sixth pass generalised a rule first measured in the energy KB's metering layer: *in some
layers the licence filter must run before the popularity filter.* This pass reproduces it in the
authorization layer, and the mechanism is now clear enough to state as a cause rather than an
observation:

**In any layer where the product category is described by an architectural pattern rather than
by a vendor, the category name carries no licence information.** "Zanzibar-inspired
authorization as a service" describes Apache-2.0 SpiceDB, Apache-2.0 OpenFGA and **AGPL-3.0
Permify** equally accurately. Likewise "modern open-source identity provider" covers
Apache-2.0 Keycloak and **AGPL-3.0 Zitadel**. The pattern name is the thing engineers search
for, so it is the thing that fills the result page, and it is uncorrelated with what Globant
may ship. Three industries, three layers, same finding — treat it as a property of this
rotation, not of one sector.

### A sixth licence class: relicensing in progress

This KB has recorded permissive-OSI, `ee/` carve-out, ELv2, fair-source with a user cap,
Polyform noncommercial, revocable, bespoke-permissive-non-OSI and time-delayed FSL. The MCP
specification repository
([modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol),
9,734 ★) is a class none of those cover. GitHub reports `NOASSERTION`; the manifest says
`"license": "SEE LICENSE IN LICENSE"`, so **the manifest-first rule returns nothing** and the
file must be read. It states the project is *"undergoing a licensing transition from the MIT
License to the Apache License, Version 2.0"*: new code and specification contributions are
Apache-2.0, documentation is CC-BY-4.0, and **contributions whose authors have not granted
relicensing consent remain under MIT**.

**There is no single SPDX identifier that describes this repository**, and which licence applies
depends on the file and on which contributor wrote it. Both licences here are permissive, so
nothing is blocked — but an inventory that records one SPDX value for it records something
false, and **§16's point was that governance begins with an accurate inventory.** The
generalisable rule: *a licence file can describe a process rather than a state, and when it
does, the honest inventory entry is "mixed — see file", not a guess.*

### Method: a new way to be wrong, and it is the opposite of the previous nine

This KB family has nine documented ways to measure a **false zero**. This pass found a false
**positive** with a structural cause. Searching the exact name of an architectural pattern
returned six GitHub repositories **all named essentially the same thing**, with specific,
credible, metric-bearing READMEs — and real star counts of **1, 0, 0, 19, 0, 0**, three with no
licence file. They were personal demonstrations of the pattern, named after it.

**The cause generalises to every industry in this rotation:** web search ranks documents by
semantic match to their text, so when a technical phrase is simultaneously a *pattern name* and
therefore a natural *repository name*, the result page is dominated by projects that match the
words perfectly and carry no adoption at all. The energy KB's rule said the discriminator is
*the proper name of a technical artefact* — a protocol, an ontology, an organisation. This pass
adds the counterpart: **a pattern name is not a proper name**, and a result page whose entries
all share one repository name should be read as a warning rather than as corroboration. The fix
is cheap and unchanged — resolve every candidate through the API before writing it down — but
without naming the trigger, the next pass walks into it again.

---

## Eighth pass, 2026-11-21 — the write boundary, and a licence rule that runs backwards

### 19. The constraint moved again: from what the agent may *read* to what it may *change*

The seventh pass found that the binding constraint on enterprise agents had moved from
capability to **entitlement** — who the agent acts for and what that person may see.
One pass later the same clients are asking the next question, and it is harder:
**what may the agent change in the system of record, and what proves afterwards that
it was allowed to?**

The evidence that this is the live question, not a predicted one:

- **Segregation of duties is the named failure mode.** Practitioner analyses this
  quarter are explicit that an agent wired into every step of a workflow can *initiate*
  an action and then *execute its own approval* inside a single run, collapsing the
  human separation that SoD exists to enforce. The prescribed fix is structural, not
  prompt-based: put a human back in the authorisation step, scope what the agent may do
  alone, and keep an audit trail that **separates who initiated from who authorised**.
- **The enforcement point is the tool, not the prompt.** The pattern being published is
  an `approve_invoice` tool that **refuses any call where `requester_id ==
  approver_id`**, regardless of whether the agent's prompt mentions segregation of
  duties at all. Authority limits are read from the ERP's own authority matrix rather
  than restated in the system prompt.
- **Reversal, not deletion.** The audit guidance is that a wrong posting is corrected
  by an **approved reversal** in the ERP, never by deleting the record. An agent with
  delete capability on a financial record is not a control problem, it is an
  unauditable system.
- **Read-only is the entry point.** Most deployments described start read-only, with
  the agent assembling the case and proposing the action for a person to approve, and
  materiality tiers deciding what it may commit alone.

**Source discipline:** these are vendor, consultancy and practitioner sources — a
finance-automation guide, an ERP-patterns write-up, a SaaS-governance analysis — plus
two arXiv preprints on auditable agent claims. **None of them is an audit standard, and
there is no SoD standard specific to agent write access to an ERP.** The convergence
across independent commercial sources is the signal; the specifics must be checked
against the client's own auditor and SOX scope. Recorded as practitioner consensus, not
as a requirement.

### The protocol-level finding: MCP's only marker for "this changes things" is explicitly untrustworthy

Read from the primary source — `schema/2025-06-18/schema.ts` and
`docs/specification/2025-06-18/server/tools.mdx` in
[modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol),
because **`modelcontextprotocol.io` does not resolve through this session's egress
proxy** (see the verification channel note below).

The `ToolAnnotations` interface carries four behavioural flags, and the schema's own
doc comment opens:

> *"NOTE: all properties in ToolAnnotations are **hints**. They are not guaranteed to
> provide a faithful description of tool behavior (including descriptive properties
> like `title`). Clients should never make tool use decisions based on ToolAnnotations
> received from untrusted servers."*

The specification page states it normatively:

> *"For trust & safety and security, clients **MUST** consider tool annotations to be
> untrusted unless they come from trusted servers."*

**And the defaults are the part nobody quotes:**

| Flag | Default | Meaning of the default |
|---|---|---|
| `readOnlyHint` | **false** | Assume the tool **does** modify its environment |
| `destructiveHint` | **true** | Assume the modification is **destructive**, not merely additive |
| `idempotentHint` | **false** | Assume calling it twice has **additional effect** |
| `openWorldHint` | **true** | Assume it touches an **open world** of external entities |

So the protocol's defaults are correctly conservative: **an unannotated MCP tool is, by
specification, a non-idempotent destructive open-world operation.** But the only party
who can declare otherwise is the server — the party clients are instructed not to
trust.

**The consequence is architectural and it is the whole of Receta 17:** write-path
safety **cannot** live in tool metadata. `destructiveHint` is useful as *documentation*
and as a *default-deny input to a policy decision*; it can never be the enforcement
point. Enforcement has to sit where the call is mediated — the integration route, the
gateway, the policy engine — in something the client controls rather than something the
tool author asserts. Any vendor who tells a client their platform "respects MCP tool
annotations" has described a documentation feature as a security control.

### 20. Compliance evidence became a machine-readable artefact, and the tooling is a decade old

The governance trends in this file (3, 14, 16) all end at the same wall: the client
accepts that governance is a buying requirement, and then asks what they hand the
auditor. Until this pass this KB had **no answer in the form of tooling** — zero
occurrences of OSCAL across all nine files.

NIST's **OSCAL** expresses control catalogs, profiles, component definitions, system
security plans, assessment plans and assessment results as validatable XML/JSON/YAML.
Around it: `compliance-trestle` for authoring with CI, `complyctl` as a runtime that
pulls **Gemara** policy from an **OCI registry** and emits **OSCAL, SARIF, EvaluationLog
and Markdown**, and providers bridging to **OpenSCAP, Ampel and OPA**. Full table in
`repos/foundations.md`.

Three things make this a trend rather than a tool list:

1. **The evidence format is now agent-addressable.**
   [oscal-compass/compliance-trestle-mcp](https://github.com/oscal-compass/compliance-trestle-mcp)
   exposes trestle's operations over MCP. The agent can author the control evidence
   describing its own governance. That is either the most useful closing of the loop in
   this KB or the most obvious conflict of interest in it, **depending entirely on
   whether the evidence is signed by something the agent cannot write to** — which is
   why Receta 17 puts the evidence store outside the agent's own write boundary.
2. **Policy is shipping as an OCI artefact.** complyctl pulls Gemara policy layers from
   a container registry. The client's compliance policy gets the same distribution,
   versioning and signing machinery as their container images — and the same supply
   chain risk, which is trend 10's problem arriving in a new layer.
3. **The surface limiter is in the product, not the proposal.**
   `compliance-trestle-mcp` ships a `TRESTLE_MCP_TOOLS` environment variable; `all`
   exposes every tool and **the default exposes only the authoring lifecycle.** A
   maintainer shipping a narrower-than-maximal default tool surface is the first
   instance this KB has recorded of the write-boundary principle appearing *inside* an
   MCP server rather than in guidance about them. Cite it: it is evidence the practice
   is real.

### A seventh licence class, and the first one that runs in the permissive direction

Every licence trap in the seven previous passes ran the same way: **looked permissive,
was not.** Permify AGPL-3.0 behind SpiceDB-identical marketing copy. `osohq/oso`
archived. FSL's time-delayed permissiveness. BSL 1.1 reading as open source. The "MIT
incipit" impostor whose title said *PROPRIETARY AND NON-COMMERCIAL* above a verbatim
MIT grant sentence. The EUPL enumerating five foreign licence names and defeating every
keyword detector.

This pass found four that run the other way — **looked restricted, were not**:

| Repo | GitHub badge | Byte-read reality | Why the classifier failed |
|---|---|---|---|
| [usnistgov/OSCAL](https://github.com/usnistgov/OSCAL) | `NOASSERTION` | worldwide public domain, 5,254 B | US-Government public-domain dedication — not an SPDX licence at all |
| [usnistgov/oscal-cli](https://github.com/usnistgov/oscal-cli) | `NOASSERTION` | worldwide public domain, 3,540 B | same |
| [usnistgov/oscal-content](https://github.com/usnistgov/oscal-content) | `NOASSERTION` | worldwide public domain, 2,105 B | same |
| [Tencent/LoopForge](https://github.com/Tencent/LoopForge) | `NOASSERTION` | **MIT**, 3,516 B | a corporate preamble above the grant, plus a bundled third-party licence appendix |

**The rule: `NOASSERTION` is not a verdict, it is the absence of one.** It records that
GitHub's classifier did not recognise the file. It must be resolved by byte-read **in
both directions**, and the two commonest causes of a false restriction are a
government public-domain dedication and a vendor preamble above a standard grant.

This matters beyond one KB. `rotation.json` records the energy pass closing with *"4
hard exclusions, all `NOASSERTION`, all with traction"*. Those exclusions may be
correct — but if they were made **on the badge rather than on the file**, some of them
are false, and the method that produced them is the method that hid the entire NIST
compliance stack from this KB for seven passes.

**And the corollary that is easy to miss:** public domain is not strictly more
permissive than Apache-2.0. A US-Government dedication carries **no express patent
grant and no warranty disclaimer**. For redistribution inside a client deliverable, the
Apache-2.0 sibling may be the better legal choice than the nominally freer NIST
original.

### Method — three more ways to be wrong, bringing the count to thirteen

**Eleven. A problem-shaped instrument cannot find a category-shaped object.** This KB
holds 234 distinct repository addresses and, through seven passes, **three of the four**
hyperscaler agent frameworks. `google/adk-python` — 22,295 ★, Apache-2.0, pushed the day
of this pass — was simply never found, because every query this KB runs is shaped like a
*problem* ("the data plane", "the entitlement boundary", "cost governance") and a
general-purpose framework answers no single problem. The `rotation.json` rule *"the
query vocabulary matters more than the query count"* is true and insufficient: a
vocabulary of problems has a blind spot shaped exactly like a product. **Any KB past
its third pass should spend one query per pass on a flat inventory check against the
obvious incumbents.**

**Twelve. The org-named repo is not the product.**
`complytime/complytime` has **1 star** and holds design proposals.
`complytime/complyctl` has 38 ★ and is the runtime. Composing `owner/owner` from an org
name — which looks like the safest possible guess — would have placed a one-star
proposals repository into a foundations table as a flagship. **List the org, read the
descriptions, and never compose a slug.** This is the mirror image of rule twelve's
neighbour: the slug that resolves is not necessarily the slug that matters.

**Thirteen. Read the manifest, not the announcement.** Apache's own blog names the
Camel MCP component "camel-mcp"; the tree contains **`camel-mcp-server`**, and the
blog's name resolves to nothing. The same `components/camel-ai/pom.xml` read revealed
**`camel-a2a`**, which no blog, release note or roundup mentioned at all. The
manifest-first rule already existed in this fleet for *licences*; this pass extends it
to **capabilities**. When a layer is new enough that the vendor is still writing about
it, the build file is more current than the prose — and the prose is where the wrong
dependency coordinates come from.

### Archived-but-recommended: now seven, and the pattern has a tell

[complytime/complyscribe](https://github.com/complytime/complyscribe), 21 ★,
Apache-2.0, **archived** with its last push 2026-05-11 — while a ComplyTime QuickStart
site and a May-2026 write-up both still present it as the way to bring trestle into
CI/CD. That is the seventh instance across this KB and the energy KB.

**The tell, stated so it can be checked in one step:** in all seven cases the project
was *recommended by documentation that shipped alongside it* rather than by an
independent source. Project-adjacent documentation is written once, at the moment of
enthusiasm, and is never revised when the code is abandoned. **A recommendation from a
project's own site or a launch post is not evidence of liveness — only the repository's
`archived` flag and last-push date are.** Check both, every time, even when the
recommending page looks official. Especially then.

### Independent confirmation of this KB's most-repeated correction

This pass's EMEA search surfaced an IBM study dated **14 October 2026** reporting that
**41% of surveyed EU executives are accelerating governance investment ahead of the EU
AI Act's high-risk obligations in December 2027.** This KB has corrected the stale
"2 August 2026" date in five consecutive passes.

That IBM date is now the **third independent confirmation** of the position recorded in
`intel/market.md` — Regulation (EU) 2026/1744, the Digital Omnibus, moved Annex III
high-risk obligations to **2 December 2027** and Annex I to 2 August 2028 — and the
first that comes from an **enterprise survey rather than the regulation itself.** It is
usable in front of a client who will not read a regulation but will read IBM.

**The stale date has not gone away.** This pass's searches *again* returned
"2 August 2026" alongside the correct date, from different sources, in the same result
set. Expect clients to arrive with the wrong deadline for at least another quarter, and
expect it from reputable-looking sources.

### Verification channel for this pass — what could and could not be checked

| Channel | Status | Consequence |
|---|---|---|
| `git ls-remote` | **working** | Every repository in this pass's tables confirmed live on 2026-11-21. |
| `raw.githubusercontent.com` | **working** | All 23 licences byte-read from the repository's own `LICENSE`; four `NOASSERTION` badges resolved. Primary-source reads of the MCP schema and spec, Camel's `pom.xml`, complyctl's and trestle-mcp's READMEs. |
| `gh api search/repositories` | **working, with one blind spot** | Stars, SPDX badge, last push and the `archived` flag — which is how complyscribe was caught. **Blind spot: `ossf/gemara` returns no result at all** (including for `repo:ossf/gemara`, HTTP 422), so **no star count is quoted for it**. A repository absent from the search index is not a repository that does not exist — `git ls-remote` says it is live and its licence was byte-read. |
| `gh api repos/<owner>/<repo>` | **denied by session scope** | Confirmed again. The default branch cannot be queried, so licence probing iterates `main`/`master`/`develop` blind — `dapr/dapr` and `ComplianceAsCode/content` were both found on `master`. Per `rotation.json`: a "no artefact" result from this endpoint is a permission failure wearing the costume of a finding. |
| `modelcontextprotocol.io` | **does not resolve** (`ENOTFOUND`, outside the session's allowed domains) | The MCP specification was read instead from `modelcontextprotocol/modelcontextprotocol` on `raw.githubusercontent.com`, which is the same text at its source of truth. **No loss of primary-source quality** — unlike the arXiv gap the energy pass had to declare, this one was fully substituted. The host should be allowed in the session's network settings if a future pass needs the rendered site. |
| arXiv | **not attempted** | `rotation.json` records arxiv.org as proxy-rejected (403). Two arXiv preprints appeared in this pass's SoD search results and are recorded as **search-listed and unverified**, never as bibliography. |

## Ninth pass, 2026-11-24 — the provenance boundary, and a maintenance rule that runs backwards

### 21. The question moved from "is it safe?" to "can you prove what it is?" — and the reference tooling is retiring

The seventh pass recorded the constraint moving from capability to **entitlement**, the eighth from
reading to **writing**. This pass records the question underneath both: **identity of the component.**

A scan is an opinion, held by one tool, at one moment. **Provenance is a verifiable claim about
origin** — signed by an identity, recorded in a log a third party can check, re-checkable later
without trusting whoever made it. An enterprise asking *"is this MCP server safe?"* wants a scan. An
enterprise asking *"in two years, can you prove the model and tools behind this decision were the ones
we approved?"* wants provenance, and **before this pass the KB held nothing that could answer it**:
`sigstore`, `cosign`, `in-toto`, `SLSA`, `attestation`, `syft`, `grype`, `trivy`, `dependency-track`,
`guac` and `model card` all scored **zero across nine files**, while `SBOM` scored 24 hits purely as a
compliance noun.

**The trend has a direction, and it is consolidation onto one vendor's platform.** Both reference SLSA
tools — [slsa-verifier](https://github.com/slsa-framework/slsa-verifier) (352 ★) and
[slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator) (610 ★) — now declare
in their READMEs: *"This project is no longer actively maintained. We are working on guidance and
simpler tooling to replace it."* Both point users at **GitHub artifact attestations** and
`gh attestation verify`. Neither is archived; both carry recent tags; both look alive on their repo
pages.

So the CI-agnostic, open-source provenance path is being retired in favour of **a platform feature of a
single vendor.** Three consequences to carry into a conversation:

1. **The migration breaks consumers, by the project's own admission:** *"GitHub artifact attestations
   are verified with `gh attestation verify` rather than with slsa-verifier, so migrating changes how
   your consumers verify."* Provenance migrations are not internal refactors.
2. **Non-GitHub estates have no named successor.** This pass searched for a GitLab equivalent and
   **found none**. For GitLab/Jenkins/self-hosted CI the remaining permissive path is
   `cosign` + `in-toto`/`witness` + `rekor`, assembled by hand. That is the single largest unserved
   requirement this pass found, and it is studio work.
3. **The adoption gap is the proportion check.** 352 stars for the reference verifier against **39,670
   for `trivy`.** The primitives an auditor asks about are two orders of magnitude less adopted than
   the scanner the client already runs — so *"we already run Trivy"* is not an answer to *"prove this
   model is the one you approved."*

### 22. Regulation stopped asking for a list and started asking for fields — and AI is now named in it

The AI-BOM trend (#16) said you cannot govern what you have not inventoried. 2026 moved the goalposts
from *having* an inventory to **the inventory's contents**, on two independent tracks:

- **A multinational minimum-elements baseline, revised and now covering AI.** CISA published **2026
  Minimum Elements for an SBOM on 2026-07-29**, replacing the 2021 NTIA baseline — and **Japan's METI
  co-signed it on 2026-07-30**, which makes this a shared international baseline rather than a US
  document. Reported changes: **cryptographic hash and licence become minimum elements**, depth
  requirements dropped in favour of all components including transitive dependencies, and **SWID
  dropped — leaving only SPDX and CycloneDX.** Secondary reporting says the guidance covers
  **open-source, AI software and SaaS**. It is **guidance, not law.**
- **A hard legal deadline with a fine attached.** The EU **Cyber Resilience Act**: Article 14 reporting
  obligations **in force since 2026-09-11** (including for products already on the market), and the
  **SBOM generation requirement, conformity assessment, CE marking and vulnerability handling apply
  from 2027-12-11.** Reported exposure: up to **€15 M or 2.5 % of worldwide annual turnover.**

**The commercially important consequence of "hash and licence are now minimum elements":** both are
*per-component, machine-checkable* fields. An inventory assembled from prose, vendor questionnaires or
a spreadsheet **cannot satisfy them** — a hash can only come from the artefact itself. That is what
converts the AI-BOM engagement from a documentation exercise into a **tooling and pipeline
engagement**, and it is why the consumption half of this layer (`syft` → `grype`, `cdxgen aibom` →
Dependency-Track) now matters more than the format debate. **`protobom` matters for exactly one
reason**: after SWID was dropped, SPDX↔CycloneDX is the only remaining axis of format disagreement.

**Caveat recorded honestly:** the CISA document could **not** be read from primary source in this
session — `media.defense.gov` and `www.cisa.gov` both fail DNS resolution (outside the session's
allowed domains). The July-2026 date, the hash/licence change, the SWID removal **and Japan's
co-signing** are **corroborated across several independent secondary sources that agree**, and are all
recorded as **secondary-sourced, not primary-verified** — the METI press release was likewise not read
at source. Both hosts should be allowed in the session's network settings if a future pass
needs the element list verbatim.

### A method rule that runs backwards — maintenance status must be read in both directions

Passes 3–8 found **seven** archived-but-still-starred projects whose READMEs never said so, and the
eighth pass noted the tell: *all seven were recommended by project-adjacent docs.* The rule that
produced was **trust the repository metadata over the documentation.**

**SLSA is the exact inverse: the repository metadata says alive, the README says unmaintained.** Not
archived, recent tags, active-looking pages — and an explicit retirement notice at line 11 of each
README. Had this pass applied its own rule, it would have shipped two retired tools as current.

**The corrected rule: neither source dominates. Read the repo metadata *and* the README, every pass.**
Metadata catches the projects that go quiet without telling you; the README catches the projects that
tell you while still looking busy.

Two sharper corollaries from this pass:

- **A permissive licence does not imply a runnable tool.** `snyk/agent-scan` is Apache-2.0 and will not
  scan without a vendor token, a network call and a daily quota; `cisco-ai-defense/mcp-scanner` is
  Apache-2.0 and most of its analyzers need no key at all. **Licence governs redistribution rights; it
  says nothing about whether the capability is local.** Same shape as the Onyx `ee/` finding
  (seventh pass) — now a general rule, and the one that decides whether a sovereign client can use a tool.
- **`pushed_at` is not "last commit on the default branch", and the gap is information.** `bomctl` last
  pushed 2025-11-20 over a `main` frozen since 2025-09-10. State which measurement you mean — a push to
  a side branch is how an idle project looks alive.

### An eighth archived-but-recommended project, and the tightest timing yet

[NimbleBrainInc/mpak](https://github.com/NimbleBrainInc/mpak) — MCP package registry with bundle
signing, GitHub-OIDC provenance and an **L1–L4 trust ladder** ending at "Attested" — was **archived by
its owner on 2026-11-23**, *the day before this pass*, and a search engine returned it to this pass as a
live finding. `archived: true` confirmed via `gh api search/repositories`; 163 commits, monorepo, Helm
chart, CI — and **14 stars**. **Adoption killed it, not quality**, which is trend #11
(star count has decoupled from enterprise suitability) running in the other direction: *too few* stars
is a survival risk even for well-built work.

### A refinement to the licence taxonomy — `NOASSERTION` has two distinct causes

The eighth pass established that `NOASSERTION` is the **absence of a verdict**, to be resolved by
byte-reading the `LICENSE` in **both** directions. This pass found that it resolves to two different
situations, and they have different consequences:

1. **Permissive behind a preamble.** `in-toto/in-toto` and `in-toto/attestation` both badge
   `NOASSERTION`; both `LICENSE` files byte-read as Apache-2.0 behind a university copyright line.
   **Outcome: a single, clean SPDX identifier.** (Checked on `develop`, which is in-toto's **actual
   default branch** — a read against `main` is a read of a branch the project does not treat as current.)
2. **Genuinely mixed, mid-transition — and no single identifier exists.**
   [modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry) badges
   `NOASSERTION` because its `LICENSE` *is a transition notice*: new contributions Apache-2.0, but
   contributions whose authors have not consented to relicensing **remain MIT**. Both permissive, so
   **not a blocker** — but *"the MCP registry is Apache-2.0"* is false, and so is *"it is MIT"*. The
   transition is **partial across the organisation**: the same notice sits on
   `modelcontextprotocol/modelcontextprotocol` and `/servers`, while
   [`/python-sdk`](https://github.com/modelcontextprotocol/python-sdk) is **still plain MIT**.

**Operational rule: record licences per repository and per date, never per organisation** — and when a
repository is mid-transition, say so in the cell rather than picking the identifier you prefer.

### Verification channel for this pass — what could and could not be checked

| Channel | Status | Notes |
|---|---|---|
| `git ls-remote --symref` | **working, and upgraded** | Existence, HEAD sha **and the real default branch**. This is what caught `slsa-verifier`'s `HEAD` pointing at `refs/heads/Hayden-IO-patch-1` (a personal patch branch, at a different sha from `main`) and `in-toto`'s default of `develop`. Previous passes probed `main`/`master` blind; **`--symref` removes that guesswork** and is the single most useful instrument added this pass. |
| `raw.githubusercontent.com` | **working** | Every licence in this pass byte-read from the repository's own `LICENSE`. Also the primary-source reads of both SLSA retirement notices, the MCP licensing-transition notice and `snyk/agent-scan`'s DNS-rebinding disclosure. |
| `git clone --bare --depth 1 --filter=blob:none` + `git log -1` | **working, new this pass** | Authoritative **last commit on the default branch** — the measurement `pushed_at` does not give. Cheap: no blobs, one commit. |
| `gh api search/repositories` | **working** | Stars, SPDX badge, **`archived`** and `pushed_at`. This is how `mpak`'s same-day archival was confirmed. |
| `gh api repos/<owner>/<repo>` and raw `api.github.com` | **403 / denied** | Confirmed again, consistent with every prior pass. Use `search/repositories` instead — it carries the `archived` flag, which is the field that matters most. |
| GitHub Atom feeds (`/commits/<branch>.atom`) via `curl` | **blocked (403 via proxy)** | Attempted as a cheap date source for 24 repositories; all returned nothing. The shallow-clone method replaced it. |
| `registry.npmjs.org` and `pypi.org/pypi/<pkg>/json` | **working** | **The decisive channel this pass.** Proved PyPI `mcp-scan` is a redirect shim (`requires_dist: ['snyk-agent-scan']`) and that npm `mcp-scan` is a *different owner's* package. **A name collision across package ecosystems is invisible from GitHub alone** — it can only be seen from the registries. Add this to the standing toolkit. |
| `gh attestation trusted-root` (local execution) | **fails closed, and that is the finding** | `tuf refresh failed: Get "https://tuf-repo-cdn.sigstore.dev/14.root.json": Forbidden`, exit 1, 0 bytes. **Measured, not cited:** the Sigstore trusted root can be *used* offline but not *obtained* offline. |
| `media.defense.gov`, `www.cisa.gov` | **do not resolve** (`ENOTFOUND`, outside allowed domains) | The CISA 2026 SBOM minimum elements are therefore **secondary-sourced, corroborated across several agreeing sources, and explicitly not primary-verified.** Probing stopped after the second failure per policy rather than trying further mirrors. |

---

## Tenth pass, 2026-11-24 — the containment boundary, and a licence class that splits inside one repo

### 23. The four boundaries are now a sequence, and the last one is the only one with no product

Read the last four passes as one argument, because that is how a client experiences it:

| Pass | Boundary | The question | State of the tooling |
|---|---|---|---|
| 7 | **Read** | What may this agent, acting for this person, see? | Mature — Zanzibar-family engines, CNCF-backed |
| 8 | **Write** | What may it change, and what proves it? | Mature — decade-old integration runtimes, OSCAL for evidence |
| 9 | **Provenance** | Are its components what they claim to be? | Mature primitives, **retiring reference tooling** |
| 10 | **Containment** | **What can it reach, and what physically stops it?** | **Primitives mature, composition absent** |

The components are individually excellent and individually CNCF-graduated. What does not exist is a
product that composes them. **Containment is four controls — intercept the request, isolate the
kernel, restrict the egress, detect at runtime — and nothing found provides all four.** The only
verified repo that attempts all four is [Azure/kars](https://github.com/Azure/kars): MIT, **46
stars**, CRDs at `v1alpha1`, and its own README says *"Not an officially supported Microsoft
product."*

**Why this is the most sellable gap in the whole KB:** the other three boundaries can be closed by
adopting something. This one can only be closed by **integrating**, which is billable systems work
on components the client already runs — Kubernetes, a mesh, a policy engine — rather than a licence
purchase they can make without Globant.

### The failure mode is the same one for the third pass running, and it has a name

Three independent sources, each describing the limits of its own control, converge:

- [falcosecurity/prempti](https://github.com/falcosecurity/prempti)'s README: it governs *"the
  commands the agent requests, not the side effects those commands produce at runtime"*, and is
  *"not a sandbox, OS-level security, or a substitute for least-privilege environments."*
- Vercel's gVisor-vs-microVM comparison: neither *"automatically denies outbound network access or
  enforces business permissions."*
- Cloud Security Alliance, October 2026, reviewing a July 2026 incident: **no sandbox was
  technically broken** — an agent **wrote a file that a trusted, unsandboxed component later
  executed.**

That third one is a **confused deputy**, and it is the *same shape* as pass 7's headline (Onyx's
permission sync living only in the enterprise directory, so the MIT build retrieves over a flat
index) and pass 8's (MCP tool annotations are hints the client must treat as untrusted). **Three
consecutive passes, three different layers, one failure mode: the boundary held, and the component
on the other side of it did the work.**

The practical consequence for a design review: stop asking *"is the agent sandboxed?"* and ask
**"what reads what the agent writes, and is that thing inside the boundary?"** A sandbox whose
output directory is consumed by an unsandboxed CI runner, indexer or deploy hook has a boundary
drawn in the wrong place, and no amount of kernel isolation fixes it.

### 24. Agent isolation acquired a Kubernetes standard, and it is already past 1.0

[kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox) (Apache-2.0,
4,703 ★, pushed 2026-11-23) is a **SIG Apps subproject** whose README pins **`v1.0.2`** as the
recommended production/GitOps version. It introduces `Sandbox`, `SandboxTemplate`, `SandboxClaim`
and `SandboxWarmPool` on `agents.x-k8s.io/v1beta1`, and is explicitly a **sandbox orchestrator**
that *delegates* isolation to gVisor or Kata via `RuntimeClass`.

Three consequences worth carrying into a design conversation:

1. **The abstraction boundary is now standard, so the isolation choice is deferrable.** gVisor
   (no hardware virtualisation needed) versus Kata/Firecracker (own guest kernel) becomes a
   `RuntimeClass` value rather than an architecture commitment. Design against the CRD; pick the
   runtime when you know the node estate.
2. **`SandboxWarmPool` is the line item that makes per-task isolation affordable.** Isolation per
   task is the correct security posture and has always been priced out by cold-start cost. A
   pre-warmed pool with low-latency claims is what changes that, and it is the feature to point at
   when a client says strong isolation is too slow.
3. **It is not a CNCF project.** Google's announcement says *"building Agent Sandbox as a CNCF
   project"* — future tense. It is a Kubernetes SIG Apps subproject today, which is a real
   governance status and should be quoted accurately rather than upgraded.

**Not verified, and it matters more than anything above:** a SIG Apps announcement is reported to
say that from v0.4.3 sandboxes **default to strict network isolation, blocking internal cluster IPs
and node metadata endpoints** unless explicitly managed in the `SandboxTemplate`. The node metadata
endpoint is how a sandboxed process reaches **cloud credentials**, so a secure-by-default posture
there would be the single most important default in the layer. **It is not in the byte-read README,
and `kubernetes.io` and `agent-sandbox.sigs.k8s.io` do not resolve under this session's network
policy.** Verify against the `SandboxTemplate` CRD before quoting it.

### A ninth licence class: split by component inside a single repository

The eight classes recorded so far split a licence by **time** (FSL/BUSL), by **version**, by
**revenue**, by **directory** (Onyx's `ee/`), by **relicensing in progress**, by **absent verdict**
(`NOASSERTION`), by **public domain**, and by **permissive-behind-a-preamble**. This one splits by
**component within one repo, with a choice attached.**

[cilium/cilium](https://github.com/cilium/cilium)'s GitHub badge says `Apache-2.0` and is **correct
but incomplete**. Its own `README.rst`, byte-read 2026-11-24: *"The Cilium user space components are
licensed under the Apache License, Version 2.0. The BPF code templates are dual-licensed under the
General Public License, Version 2.0 (only) and the 2-Clause BSD License (**you can use the terms of
either license, at your option**)."* `bpf/COPYING` returns 200; a top-level `LICENSE.BSD-2-Clause`
returns 404 because the files live under `bpf/`. Same shape in `cilium/tetragon`.

**This class resolves in the permissive direction — the second one that does** (pass 8 found four
`NOASSERTION` badges that were all permissive). Take the BSD-2-Clause option and no GPL enters a
client deliverable. But the resolution is an **act**, not an observation: the election has to be
made and **recorded in the SBOM**, because the licence of the artefact shipped is not the licence on
the page describing the repository.

**The generalised rule, now stated for the fifth layer in a row:** a repository-level licence badge
is a claim about the *repository*, never about the *artefact*. Verify at the level you ship.

### Method — three more ways to be wrong, bringing the count to sixteen

**14. A fork inherits everything the page shows except one line.**
[grosser/agent-sandbox](https://github.com/grosser/agent-sandbox) appeared in a web search result
list **beside** the real project: 0 stars, Apache-2.0 badge, first README line byte-identical to
upstream. Licence checks pass, existence checks pass, prose checks pass. **Only the "forked from"
line distinguishes it.** For any repo that arrived via web search, read that line before the
licence.

**15. The verification channel is blind to exactly this risk.**
`gh api search/repositories -f q=repo:grosser/agent-sandbox` returns **nothing**, because forks are
excluded from the search index. So the channel this KB trusts most **raises no flag at all** on a
fork, while the channel that surfaced it (web search) cannot verify anything. **The channel that
finds a risk and the channel that confirms it are not the same channel, and neither covers the
other's blind spot.** Treat "the API returned no result" as *unknown*, never as *does not exist* —
the same repo returns a complete record under `git ls-remote` and `raw.githubusercontent.com`.

**16. A single repo can be refused by one channel and served by every other.**
`gh api search/repositories -f q=repo:google/gvisor` returns **HTTP 422** (*"cannot be searched
either because the resources do not exist or you do not have permission"*) while
`raw.githubusercontent.com/google/gvisor/master/LICENSE` returns the full Apache text and the repo
page renders normally. A 422 from a search endpoint is a statement about the **index**, not about
the repository. Fall through to the next channel; do not record a false absence.

### Sources that disagree, resolved and unresolved — this pass

**Resolved against a primary source.** A 2026 comparison blog states Kyverno **graduated** within
CNCF in March 2026; another lists it **Incubating**.
[kyverno/kyverno](https://github.com/kyverno/kyverno)'s own README says *"CNCF Incubating project"* —
**the repository wins.** Falco and Cilium carry *graduated* badges in their own READMEs, so the
difference is genuine self-description. CNCF maturity gets quoted in procurement documents; quote it
from the README.

**Unresolved, recorded.** The EU AI Act's high-risk obligations: one source says they take full
effect **2 August 2026**, another says obligations **may slip to 2027**. This KB already recorded
that the deadline moved; this pass adds a second independent instance of the ambiguity **without
resolving it**. For any EMEA deliverable, state the date as contested and cite the client's own
counsel rather than a date from a vendor blog.

### Verification channel for this pass — what could and could not be checked

| Channel | Result |
|---|---|
| `git ls-remote --symref` | **Works** — existence and real default branch, including for forks |
| `raw.githubusercontent.com/<repo>/<branch>/LICENSE` and `/README*` | **Works** — the byte-read licence, and the only channel that found the Cilium split |
| `gh api -X GET search/repositories -f q=repo:<o>/<n>` | **Works** — exact stars, SPDX, `archived`, last push. **Excludes forks**; **422** on `google/gvisor` |
| `api.github.com/repos/<o>/<n>` | **403** for every repository not attached to this session, with or without the token |
| `github.com` HTML via `curl` | **403**; the identical URL via the fetch tool **works** — two channels to the same bytes, one blocked |
| `kubernetes.io`, `agent-sandbox.sigs.k8s.io` | **Do not resolve** under this session's network policy — cost one high-value finding, recorded above as unverified rather than dropped |

## Eleventh pass, 2026-11-24 — the forge boundary, and the first finding about the KB rather than the industry

> Passes 7 to 10 each measured a boundary of the agent: what it may **read**, **change**, **prove**
> and **reach**. This pass measured the **instrument**. The result changed what is in the tables, so
> it is a research finding and not a retrospective.

### 25. The inventory had one source, and nobody had ever checked

| Measurement, 2026-11-24 | Value |
|---|---|
| Distinct repository addresses in this KB | **314** |
| …on `github.com` | **314** |
| …on `gitlab.com`, `sourceforge.net`, `codeberg.org`, `bitbucket.org`, `git.sr.ht`, `gitee.com`, `huggingface.co` | **0** |

Ten passes, 8,355 lines, 314 addresses, one forge. **Not 314 of 320 — 314 of 314.**

The reason this is a trend and not an errand is what the single source does to a claim. Every
sentence of the form *"the leading open source options in this category are X, Y and Z"* is a claim
about a search, and the search had one input. The fix is not more humility, it is **four extra
words**: "the leading options **on GitHub**". The claim then becomes true and costs nothing.

**What the correction actually bought, in one pass:** an enterprise DMS at 683 stars active the same
day (Mayan EDMS), a permissive ERP+CRM forge the client already self-hosts (GitLab CE, MIT), a French
ERPNext derivative, six MIT agent components, an MIT air-gap reference implementation from a vendor's
public-sector group, the first LATAM-origin licence-resolved repository in the KB — **and** the most
capable agent-context product found in weeks, which turned out to be proprietary. None of it was
hidden. It was on the forge nobody searched.

### 26. A forge zero has two causes, and conflating them manufactures false findings

Nine alternative forges were probed. **Eight refused at the network layer** before any question
about content could be asked:

| Forge | Probe result, 2026-11-24 |
|---|---|
| `gitlab.com` | **Reachable** — API `200`, unauthenticated, licence + default branch + stars + last activity in one call |
| `gitee.com`, `atomgit.com` | `curl (56) CONNECT tunnel failed, response 403` |
| `gitlab.opencode.de`, `foss.heptapod.net` | `CONNECT tunnel failed, 403` |
| `codeberg.org`, `pagure.io`, `git.openldap.org` | `CONNECT tunnel failed, 403` |
| `invent.kde.org`, `salsa.debian.org` | `CONNECT tunnel failed, 403` |

So the KB's zero decomposes into:

- a **discovery gap** on `gitlab.com` — real, our fault, and **closed this pass**; and
- an **instrument gap** on the other eight — **not closeable by research at all**, only by a network
  policy change.

**The rule, and it corrects a rule this fleet already wrote.** A sibling KB recently established that
forge bias is measurable on URLs and that every KB should grep for alternative forges — correct, and
it is what started this pass. But a grep alone **cannot distinguish the two causes**, and a KB that
greps, sees zero and concludes "nothing there" publishes a false finding dressed as diligence.
**Record the probe result next to the grep result.** The grep says what you cited; only the probe says
whether you could have. Reachability also varies between sessions — the sibling KB successfully read
SourceForge in a pass where this session cannot even open a tunnel to it — so the probe is **per-pass
evidence, not a constant**.

The regional consequence is the sharpest form of this: **`gitee.com` and `atomgit.com` are both
refused, so this KB's APAC inventory is *unmeasured*, not sparse.** "Sparse" implies the region builds
less. A `403 CONNECT` says nothing whatever about the region.

### A tenth licence class: the vendor's own enterprise licence, inside an open-source namespace

The taxonomy in this file ran to nine classes. The tenth was found twice in one pass, in the same
namespace as an MIT project.

| Repo | API licence field | Licence actually in the repo |
|---|---|---|
| [gitlab-org/gitlab](https://gitlab.com/gitlab-org/gitlab) | `mit` | **MIT** |
| [gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph) | `other` | **GitLab Enterprise Edition licence** |
| [gitlab-org/modelops/applied-ml/code-suggestions/ai-assist](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist) | `other` | **GitLab Enterprise Edition licence** |

The EE text: the software *"may only be used in production, if you (and any entity that you
represent) have agreed to, and are in compliance with, the GitLab Subscription Terms of Service …
and otherwise have a valid GitLab Enterprise Edition subscription for the correct number of user
seats."*

**What distinguishes this class from the eight before it.** Not that it is commercial — this KB
already holds Camunda (not open source) and Mattermost (tri-modal). What is new is the **carrier**:
the licence travels by *namespace adjacency*. `gitlab-org/gitlab` is MIT; two siblings require paid
seats; the repositories sit under the same owner, use the same CI, and look identical in a search
result. **The namespace is not the licence**, and a community fork of EE-licensed code carries the EE
terms — the fork changes who may contribute, not what you may deploy.

### `other` now has four documented outcomes, which settles the argument about it

A sibling KB found two `other` verdicts resolving **permissive** (Apache-2.0) and **weak copyleft**
(LGPL-3.0), and concluded that resolving an `other` by default is 50% accurate. This pass adds the
remaining two corners from four byte-reads:

| Resolved value | Example | Cause of the `other` |
|---|---|---|
| Permissive | *(sibling KB)* amiris-py → Apache-2.0 | REUSE layout `LICENSES/<SPDX>.txt`, which the API does not index |
| Weak copyleft | *(sibling KB)* midas → LGPL-3.0-only | non-standard declaration |
| **Strong copyleft** | mayan-edms → **GPL-2.0-only** | licence text wrapped in a bespoke preamble carrying copyright and trademark registrations |
| **Proprietary** | orbit, ai-assist → **GitLab EE** | a vendor's own licence, which no SPDX identifier matches |

**Four outcomes spanning permissive to proprietary from one API value.** `other` is not a weak signal
to be nudged in a hopeful direction — it is **the absence of a verdict**, and it must be resolved by
reading bytes. A fifth cause was also added this pass, and it is the dullest and most preventable:
**a filename the API does not look for.** Orbit's licence is in `LICENSE.md`; the tree had to be
listed to find it. Check `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING`, and the
`LICENSES/` directory before concluding anything.

### The constraint that is not the licence — registered trademarks

Mayan EDMS's `LICENSE` declares a **US Copyright Office registration** (TX 8-577-731) and **two
USPTO-registered trademarks** (7,889,160 / 7,889,166), stating that the copyright licence *"grants no
rights in those trademarks"* and pointing at a separate `TRADEMARK_POLICY.md`.

This is the first platform in this KB where the **brand**, not the code licence, is the binding
constraint on the normal delivery shape. The two questions have different answers: *may we modify and
deploy it?* — yes, under GPL-2.0; *may we call it that?* — separate policy, registered marks. A
white-labelled "our DMS, built on Mayan" proposal needs the second answer, and no licence scanner in
any toolchain will raise it. **Licence compliance and brand compliance are different reviews.**

### Method — three more ways to be wrong, bringing the count to nineteen

**17. A star-ranked forge listing surfaces dead mirrors near the top.** Stars accumulate and never
decay. The second-highest-starred result in this pass's forge sweep was
[meltano/meltano](https://gitlab.com/meltano/meltano) at **554★ and last activity 2024-09-11**, whose
own description reads *"[This project was migrated to GitHub]"* — a corpse this KB already holds at
its live address, which a star sort would have added as a duplicate. A second remnant,
`gitlab-org/duo-workflow/duo-workflow-service`, announces its migration **within** the same forge.
**Both announce their own death in the description field** — the cheapest possible check, and exactly
the one a star-sorted list invites you to skip. Read `last_activity_at` and the description *before*
the star count.

**18. A rename can move the product and leave the path alone.** The ninth pass built a detector for
renames that move **owner and path**; this is the variant that defeats it.
[gitlab-org/cluster-integration/gitlab-agent](https://gitlab.com/gitlab-org/cluster-integration/gitlab-agent)
— MIT, 113★, active 2026-11-24 — still sits at the path of a Kubernetes agent while describing itself
as *"**GitLab Relay** — host for … Workflow Engine (AutoFlow / autocore), GitLab CD, Job Router and
Runner Controller."* URL resolves, licence unchanged, **product replaced**. A link check cannot catch
this. Diff the upstream description against your own one-line summary.

**19. A keyword sweep tuned on one forge under-reports another, and the fix is to search the domain
rather than the technology.** Searching `gitlab.com` for **`agent`** returns, in star order, a browser
user-agent switcher, a Kubernetes cluster agent, `fetchmail`, a network telemetry agent and a VPN
client: on that forge the word still carries its **pre-LLM meaning**. The sweeps that produced every
platform finding this pass were `erp`, `crm`, `facturacion` and `mcp` — **domain** terms, plus the one
technology term new enough to have no homonym. This is the forge-side twin of the language bias
already recorded in this file, and it is worse, because it is invisible: the query returns plenty of
results, all of them wrong.

### Two instruments worth reusing across the fleet

1. **`GET https://gitlab.com/api/v4/projects?search=<term>&order_by=star_count&sort=desc&simple=true`**
   — unauthenticated public project search, star-ordered. This is the discovery instrument the fleet
   did not have; it is what found Mayan EDMS.
2. **`GET https://gitlab.com/api/v4/projects/<url-encoded-path>?license=true`** returns licence,
   **default branch**, stars, forks and last activity **in one call**. Encode the whole path including
   nested subgroups. The default branch matters: across projects verified this pass it was `master`
   (×4), `main` (×7), `develop` and **`3.0`** — the blind `main`→`master` fallback this KB has used
   would have failed outright on Flectra. Rate limits are real: `429` appeared twice under rapid
   probing, and **a `429` is not a licence verdict** — back off and retry, or record the licence as
   unresolved, which is what was done for `odoocoop/facturacion_electronica`.

### Verification channel for this pass — what could and could not be checked

| Channel | Result |
|---|---|
| `gitlab.com/api/v4/projects/…?license=true` | **Works** unauthenticated — licence, default branch, stars, last activity in one call; `429` under rapid probing |
| `gitlab.com/api/v4/projects/…/repository/files/<f>/raw?ref=<branch>` | **Works** — the byte-read that resolved Mayan (GPL-2.0), Orbit (EE) and ai-assist (EE) |
| `gitlab.com/api/v4/projects/…/repository/tree` | **Works** — the only way to prove `lazy-mcp` has *no* licence file and that Orbit's is `LICENSE.md` |
| `gh api -X GET search/repositories -f q=repo:<o>/<n>` | **Works** — exact SPDX, stars, `archived`, last push for the GitHub rows |
| `gh api repos/<o>/<n>` | **403** for every repository not attached to this session — unchanged from prior passes |
| `codeberg.org`, `gitee.com`, `atomgit.com`, `gitlab.opencode.de`, `foss.heptapod.net`, `pagure.io`, `git.openldap.org`, `invent.kde.org`, `salsa.debian.org` | **`CONNECT tunnel failed, 403`** — eight forges unmeasured, declared above |
| Regional adoption and regulatory figures (IDC, Gartner, Forrester, Veeam, Lenovo, RSM, Dentons, Baker McKenzie, BSA, NVIDIA) | **Search-listed at snippet level, not opened at source.** Attribute, never adopt. Several are vendor-sponsored |

### Gaps measured this pass — stated, not left silent

- **Eight forges unmeasured**, listed above. The highest-value is `gitee.com`: it makes the APAC
  inventory *unmeasured* rather than sparse, and closing it needs **one allowlist entry, not research
  effort**. This is the top open item from this pass.
- **openDesk** — the EMEA sovereign-workplace programme — **not assessed**. Its forge is refused; no
  claim is made about its licence, components, version or activity. Named as a lead so a future pass
  knows where to look.
- **Tryton** — a full ERP — **not usable from this session's evidence**. Canonical forge refused; its
  GitHub presence is explicitly *"Mirror of tryton"* (247★) and reports **no licence**, so the mirror
  cannot establish the licence either.
- **`odoocoop/facturacion_electronica`** — licence **unresolved** after two `429` responses. Recorded
  as unresolved rather than guessed.
- **`huggingface.co`: zero addresses, and unprobed.** The KB holds no model-side address of any kind.
  Whether that is a real gap or correct scoping for an infrastructure KB has **not been decided**; it
  is recorded here so the next pass decides it deliberately instead of inheriting it.

---

## Twelfth pass, 2026-11-24 — the weights boundary, and the first licence finding about something that is not code

> Passes 7 to 10 measured four boundaries of the agent: what it may **read** (entitlement), what it
> may **change** (write), what it **is** (provenance), and where it may **reach** (containment).
> Pass 11 measured the **instrument** and found the inventory sat on one forge. This pass points the
> KB's most developed apparatus — eleven passes of licence taxonomy — at the one object it had never
> been pointed at: **the model weights the agent runs on**.
>
> The result is the sharpest commercial finding in several passes. Every licence class in this KB
> was derived from a `LICENSE` file in a code repository. **For weights, that file is the wrong
> document, and reading it produces the wrong answer in both directions.**

### 27. The licence of the code and the licence of the weights are independent, and the clause that matters most is in neither

This KB holds 338 repository addresses and a ten-class licence taxonomy, all of it built by reading
`LICENSE` files. Four model families were probed this pass by raw byte-read. The agreement rate
between *the repository's licence* and *the weights' licence* was **two in four**, and the two
failures run in **opposite** directions:

| Model family | What the code repo's `LICENSE` says | What the weights actually carry | Direction of the error |
|---|---|---|---|
| Gemma (`google-deepmind/gemma`) | **Apache-2.0**, 11,358 bytes | Gemma Terms of Use — bespoke, with a separate prohibited-use policy (**and see the unresolved item below**) | **False positive** — the badge reads permissive, the weights are not |
| Qwen3 (`QwenLM/Qwen3`) | **No `LICENSE` at all** — 404 at both `main` and `master` | Apache-2.0, per the vendor's own `README.md:397`: *"All our open-weight models are licensed under Apache 2.0."* | **False negative** — the repo looks unlicensed, the weights are permissive |
| Llama (`meta-llama/llama-models`) | Root `LICENSE` is **78 bytes containing a URL** and nothing else | Per-model agreements: `models/llama4/LICENSE` is the 7,603-byte **LLAMA 4 COMMUNITY LICENSE AGREEMENT** (effective 2025-04-05); llama3_3 7,909 B, llama3_2 7,669 B, llama3_1 7,680 B | **Scanner blindness** — a licence detector sees a pointer, which is why this repo is commonly reported as `NOASSERTION` |
| OLMo (`allenai/OLMo`, `allenai/OLMo-core`) | **Apache-2.0**, 11,359 bytes | Apache-2.0 | Agreement |

**The rule, and it is new:** `repo_license` and `weights_license` are **two different facts about two
different artefacts**. Neither predicts the other. A permissive badge on an inference-code repository
is not evidence about the model it loads, and a missing licence file is not evidence against it.
This is the same shape as the rules this fleet already carries for `NOASSERTION` and `other`
(a verdict that informs in neither direction) — but one layer up, on an object no SBOM tool in a
normal pipeline even enumerates.

#### The operative clause is in the acceptable-use policy, not the licence — measured, not argued

Several widely-cited 2026 write-ups quote an EU carve-out as **Section 1(a) text of the Llama 4
Community License**. It is not there. Run over the licence files themselves:

```
grep -c 'European Union' models/llama4/LICENSE    → 0
grep -c 'European Union' models/llama3_3/LICENSE  → 0
grep -c 'European Union' models/llama3_2/LICENSE  → 0
grep -c 'European Union' models/llama3_1/LICENSE  → 0
grep -c 'European Union' models/llama4/USE_POLICY.md    → 1
grep -c 'European Union' models/llama3_2/USE_POLICY.md  → 1
```

The clause lives at `models/llama4/USE_POLICY.md:71`, and this is its full text, read from Meta's
own repository on 2026-11-24:

> *"With respect to any multimodal models included in Llama 4, the rights granted under Section 1(a)
> of the Llama 4 Community License Agreement are not being granted to you if you are an individual
> domiciled in, or a company with a principal place of business in, the European Union. This
> restriction does not apply to end users of a product or service that incorporates any such
> multimodal models."*

**A document that is not the licence withdraws the licence grant.** Three consequences, and the
third is the one that costs money:

1. **Licence scanning is structurally incomplete for weights.** Every scanner, every SPDX tool and
   every GitHub badge reads `LICENSE`. None of them reads `USE_POLICY.md`. A clean licence report on
   a Llama-derived model is therefore *not* evidence that the model may be used — it is evidence
   that the scanner looked at the wrong file.
2. **The AUP must be treated as part of the licence** for any weights, and read in full, because it
   is incorporated by reference and can modify the grant itself.
3. **The clause turns on the licensee's domicile, so it depends on which entity signs.** The
   restriction does not reach *end users* of a product incorporating the model — it reaches the party
   exercising the §1(a) rights. For a services company building a multimodal Llama 4 system for a
   European client, the question *"who is the licensee, and where is its principal place of business?"*
   decides whether the rights exist at all. **That question must be asked before a pilot starts, not
   during legal review of the statement of work.** Globant S.A.'s Luxembourg incorporation is a
   matter of public record; whether it makes the contracting entity *"a company with a principal
   place of business in the European Union"* for the purposes of this clause is a question for
   counsel, and this KB states the question rather than answering it.

### 28. The "sovereign" model is a licence question, not a technology question — and it inherits

The strongest regional finding of the pass, and it inverts a conclusion this KB has repeated: at the
*agent* layer the inventory is North-American and APAC-origin with measured zeros for EMEA and LATAM.
At the **weights** layer, EMEA and LATAM are *present and funded* — but what they ship is, in two
headline cases, **someone else's licence**.

- **LATAM — Latam-GPT (CENIA, Chile), launched 2026-02-10.** The region's flagship sovereignty
  project is published as `latam-gpt/Llama-3.1-70B-LatamGPT-SFT-1.0`: continued pretraining and SFT
  **on Llama 3.1 70B**, with the model card stating use is subject to the **Llama 3.1 Community
  License Agreement**. Reported as >300B tokens, free to companies and public institutions, first
  trained on AWS with future training planned at Universidad de Tarapacá.
  **The sovereignty is linguistic and in the data. It is not legal.** A Chilean public body adopting
  it inherits Meta's acceptable-use policy, Meta's naming obligation and Meta's 700-million-MAU
  clause. *(Model-card licence and launch details are secondary-sourced — the model card itself is on
  a host this session cannot reach; see the verification channel below.)*
- **APAC — SEA-LION (AI Singapore).** Its own `README.md:88`, read this pass, is unusually honest and
  should be quoted to any client who asks for "the MIT one":

  > *"All SEA-LION releases will therefore embrace an open-source ethos under the MIT license as much
  > as possible; however, the exact licensing terms may vary depending on the underlying base model's
  > restrictions or requirements. For instance, if the model leverages Meta's Llama3 codebase, it may
  > be bound by the Llama3 License, which places certain restrictions on commercial use. Similarly,
  > the Gemma-based variants may carry different terms."*

  Meanwhile the project's own arXiv paper (2504.05747) states the team *"release our models under the
  fully open MIT license."* **A peer-reviewed paper and the shipped artefact disagree**, and the
  README sides with the artefact. The Gemma-derived variant is listed as Gemma Community License on
  its model card and on Ollama.
- **EMEA — the genuinely permissive options exist and were verified.**
  `langtech-bsc/salamandra` (Barcelona Supercomputing Center) carries a **plain Apache-2.0** 11,357-byte
  `LICENSE`, read this pass. **Apertus** (EPFL + ETH Zurich + CSCS, Swiss AI Initiative; v1.5
  released 2026-07-24) is reported as Apache-2.0 at the licence level **but adds a separate Apertus
  LLM Acceptable Use Policy, and the v1.5 weights are gated** — login and acceptance required before
  download. Sources disagree on whether the AUP binds downstream redistribution of unmodified
  weights; recorded as disagreeing, not reconciled.

**The rule for the shortlist:** *"it is a national or sovereign model"* is a claim about who trained
it and on what data. **It carries no information about the licence.** Resolve the base model first,
then the fine-tune, then the AUP — in that order, because the restrictions compose downward and the
derivative cannot be freer than its base.

### An eleventh licence class — and the first one written for weights rather than code

**OpenMDW-1.1** (Open Model, Data and Weights), stewarded by the Linux Foundation out of the Model
Openness Framework. Verified this pass by byte-read of the canonical text at
`OpenMDW/OpenMDW` → `1.1/LICENSE.OpenMDW-1.1`, **2,619 bytes** — and found **byte-size identical** in
the wild at `NVIDIA/Cosmos` → `LICENSE`, which is how the adoption was confirmed from NVIDIA's own
repository rather than from a press release.

What the text actually does, quoted and paraphrased from the 2,619 bytes:

- **One instrument for four artefacts.** "Model Materials" is defined as *"(1) one or more machine
  learning models (including architecture and parameters); and (2) all related artifacts (including
  associated data, documentation and software)."* This is the first licence in this KB that covers
  weights, data, docs and code in a single grant — the thing pass 9's provenance work kept needing
  and never had.
- **It grants more rights than Apache-2.0 names.** Permission to deal in the materials *"without
  restriction, including under all copyright, patent, **database**, and **trade secret** rights."*
  The **database right** matters specifically in EMEA: the EU *sui generis* database right is a real
  encumbrance on training corpora that Apache-2.0 simply does not address.
- **Outputs are explicitly free.** *"This agreement does not impose any restrictions or obligations
  with respect to any use, modification, or sharing of any outputs generated by using the Model
  Materials."* This is the clause that distinguishes it commercially from the Llama family (naming
  and "Built with Llama" obligations) and from OpenRAIL-style use restrictions.
- **No field-of-use restriction, no acceptable-use policy, no user-count ceiling.**
- **Defensive termination that reaches copyright, not only patents.** All grants terminate if the
  licensee files or voluntarily participates in a suit asserting the materials infringe *"any patent
  or copyright"*, unless responsive to a suit brought first. **This is the clause blocking OSI
  approval** (see below).
- **Rights clearance is pushed onto the licensee, in capitals.** The licensee is *"SOLELY RESPONSIBLE
  FOR (1) CLEARING RIGHTS OF OTHER PERSONS THAT MAY APPLY TO THE MODEL MATERIALS."* **An OpenMDW
  model is a clean licence from the licensor. It is not an indemnity for the training data**, and a
  client who reads "permissive" as "someone else carries the copyright risk on the corpus" has
  misread it.

**Status, and it is the part that breaks pipelines:** OpenMDW-1.1 was submitted to the OSI
license-review list and **the review was still open at the last message traced (2026-08-29) with no
board decision**. Richard Fontana objected that extending termination to copyright claims is *"unlike
any OSI-approved license I can think of"*; at least one reviewer stated it does not provide software
freedom; Pamela Chestek floated falling back to OpenMDW-1.0 to clear the objections. It is
consequently **not OSI-approved and not on the SPDX License List.**

> **The operational consequence, and it connects straight to pass 9.** Because OpenMDW-1.1 has no
> SPDX identifier, every SPDX-based tool in a client's pipeline will emit `NOASSERTION` or a custom
> string for an NVIDIA Cosmos-class model. This KB's own ninth pass established that `NOASSERTION`
> has two causes and resolves in both directions. **Here is a third cause: a real, deliberate,
> foundation-stewarded licence that the identifier list has not caught up with.** Do not let a client's
> scanner downgrade an OpenMDW model to "unlicensed" — and do not let it upgrade one either.

Also recorded: the licence's own `FAQ.md`, which the README points to for details, is a **171-byte
stub**. The documentation for the newest licence class does not exist yet.

### The machine-readable artefact for weights exists in two standards, and both make it optional

Pass 8 found that MCP's `ToolAnnotations` are all hints that clients must treat as untrusted, so
write-path safety cannot live in tool metadata. **The same structural failure reproduces one layer up,
and this pass measured it in the schemas themselves.**

- **CycloneDX 1.6** — `CycloneDX/specification` (Apache-2.0, 11,341-byte `LICENSE`). Byte-read of
  `schema/bom-1.6.schema.json` (**262,666 bytes**) confirms a `machine-learning-model` component
  type, plus `modelCard` and `modelParameters`. ML-BOM is real and in the published schema.
- **SPDX 3.0** — the AI profile is **not** in `spdx/spdx-spec`. It is in `spdx/spdx-3-model`, at
  `model/AI/Classes/AIPackage.md` (1,687 bytes), whose own header reads
  `SPDX-License-Identifier: Community-Spec-1.0`. `AIPackage` is a concrete subclass of
  `/Software/Package` carrying `autonomyType`, `domain`, `energyConsumption`, `hyperparameter`,
  `informationAboutApplication`, `informationAboutTraining` and `limitation`.
- **And every one of those properties is declared `minCount: 0`.** All optional. A fully conformant
  SPDX 3.0 AI SBOM can therefore be **silent about training data, silent about limitations and
  silent about autonomy** — and still validate.

**The rule:** the field existing in the standard is not the same as the field being populated.
**Require the fields in the contract, not in the format.** "Give us an AI-BOM" is not a requirement;
"give us an AI-BOM in which `informationAboutTraining` and `limitation` are non-empty, and the
weights' licence and its acceptable-use policy are both named" is one.

### A licence trap inside the weights tooling itself

The two tools that inspect the serialisation format most weights-adjacent attacks use are **not in
the same licence class**, and the better-known one is the restricted one:

- `trailofbits/fickling` — **LGPL** (7,652-byte `LICENSE`, at `master`, not `main`). Copyleft. Fine
  as a standalone CI binary, a problem if someone links it into a shipped product.
- `mmaitre314/picklescan` — **MIT** (1,072 bytes). The permissive peer, and the one to reach for when
  the scanner has to ship inside a client deliverable.

### Method — three more ways to be wrong, bringing the count to twenty-two

- **T89 — `LICENSE` is the wrong file for a model, and reading it harder does not help.** Resolve
  weights in this order: (1) the weights' own card or registry entry, (2) the vendor's
  `README`/licence directory in the source repo, (3) the **acceptable-use policy as part of the
  licence**, (4) the base model's licence if the artefact is a fine-tune. A clean `LICENSE` read is
  not a verdict on the weights; it is a verdict on the code.
- **T90 — a restriction can live outside the instrument that grants the rights, and it still binds.**
  Measured here as a one-line `grep`: zero hits for `European Union` across four Llama `LICENSE`
  files, one hit in each `USE_POLICY.md`. **Before quoting any weights licence, enumerate the
  documents the licence incorporates by reference and read all of them.** Every KB in this fleet that
  recommends a model should run this `grep` against its own shortlist.
- **T91 — the vendor's own instruction for finding the licence may point at a host you cannot
  reach, and that is not the same as the licence being unknown.** `QwenLM/Qwen3:398` says *"You can
  find the license files in the respective Hugging Face repositories"*; `aisingapore/sealion:88` says
  *"Users should always refer to the Hugging Face model card."* **Both pointers resolve to a host that
  returns `CONNECT tunnel failed, 403` from this session.** The licence was still recoverable — from
  the README prose in one case and from the base model's repository in the other. **Follow the chain
  to a reachable primary rather than recording an unknown**, and when it genuinely cannot be reached,
  say which host refused.

### Sources that disagree — resolved and unresolved, this pass

| Question | State | What to do about it |
|---|---|---|
| Is the EU multimodal carve-out in the Llama 4 **licence**? | **Resolved: no.** It is in `USE_POLICY.md:71`. Multiple secondary write-ups attribute it to licence §1(a); the licence files contain zero occurrences | Cite the AUP, with the file and line. Do not cite the blogs |
| Does NVIDIA ship Nemotron under OpenMDW? | **Resolved as a two-document case, not a contradiction.** The press release describes OpenMDW for the Nemotron *model family*; `NVIDIA-NeMo/Nemotron` → `LICENSE` is **Apache-2.0** (11,358 B) — that is the **code**. `NVIDIA/Cosmos` → `LICENSE` **is** OpenMDW-1.1 (2,619 B) | Exactly trend 27 in the adopter's own repos. Never infer a weights licence from a code repo, including when the vendor announced the weights licence |
| **Gemma 4's licence** | **UNRESOLVED.** Two 2026 secondary sources state Gemma 4 moved to **Apache-2.0** in April 2026 with Gemma 1–3 remaining under the Gemma Terms of Use; another states Gemma ships under the Gemma Terms with a separate AUP. `google-deepmind/gemma`'s `README` contains **no licence statement at all** (grep: zero hits), and its `LICENSE` is Apache-2.0 — i.e. the code. The primary source, `ai.google.dev/gemma/terms`, **does not resolve from this session** | **Do not put a Gemma licence in a proposal this week.** Have legal read the terms page directly. The KB records the disagreement and refuses to average it |
| Does the Apertus AUP bind downstream redistribution of unmodified weights? | **Unresolved.** One source argues redistributing unmodified under Apache-2.0 leaves downstream users with Apache-2.0 obligations only; another characterises the release as carrying a custom AUP | Treat as Apache-2.0 + AUP until read in full. The v1.5 download gate is independently confirmed |
| Is OpenMDW-1.1 OSI-approved? | **Resolved: no, and still under review** at the last traced message, 2026-08-29 | Call it "foundation-stewarded, permissive in substance, **not OSI-approved, no SPDX ID**". Never "OSI-approved" |

### Verification channel for this pass — what could and could not be checked

**What worked.** `raw.githubusercontent.com` is reachable and is the instrument this pass ran on:
every licence claim above with a byte count attached was produced by fetching the file and measuring
it. Licence identity was confirmed by **byte-size comparison** against a known-good copy of the same
text — which is how OpenMDW-1.1 in `NVIDIA/Cosmos` was matched to the canonical 2,619-byte file.

**What was refused, and the consequence for this pass's tables.**

| Host | Result | What it cost |
|---|---|---|
| `huggingface.co` | `CONNECT tunnel failed, 403` via curl; **DNS does not resolve** for the fetch tool | **The canonical weights-licence oracle is unreachable.** Model cards could not be read. Every weights licence here was recovered from a source repository instead, or flagged secondary |
| `ai.google.dev` | **DNS does not resolve** | The Gemma licence question stays open rather than being resolved |
| `api.github.com` | **403 for every repository outside this session's scope** | **No star counts and no last-push dates were obtainable this pass.** New rows therefore carry licence, byte-verified evidence and the verification date, and **omit stars rather than copy them from a blog.** Existing rows were left untouched |

> **This is a declared gap, not a silent one.** A reader comparing this pass's tables to pass 11's
> will see the star column missing and should not read that as the projects being small or new. The
> measurement was refused, and the KB's own rule already covers it: cite the institution and the
> evidence, never the star.

**Repository paths probed and not found** — stated so nobody reads absence as non-existence:
`swiss-ai/apertus`, `utter-project/EuroLLM`, `OpenGPT-X/Teuken`, `sarvamai/sarvam-1`, `lfai/mof`,
and `aisingapore/sea-lion` (the correct path is `aisingapore/sealion`, which was read successfully).
**Apertus, EuroLLM, Teuken and Sarvam are real projects whose repository addresses this pass failed
to locate** — they are an open inventory item for pass 13, not a measured zero.

### Gaps measured this pass — stated, not left silent

- **No LATAM-origin and no EMEA-origin *base* model with a permissive licence was found beyond
  Salamandra (EMEA, Apache-2.0, verified).** Latam-GPT, the LATAM flagship, is a Llama derivative.
  This is a **measured** finding about the licence layer, and it is the opposite of a gap in
  capability.
- **APAC remains under-measured for the same reason as pass 11:** `gitee.com` is unreachable from
  this session, so Chinese-hosted model repositories were never enumerated. Qwen3's licence was
  recovered from GitHub prose, not from a registry.
- **The KB still holds zero machine-readable AI-BOM artefacts for its own shortlist.** The standards
  were verified this pass; no model in this KB has an ML-BOM attached. That is the obvious pass-13
  deliverable and it is now unblocked.

---

## Thirteenth pass, 2026-11-24 — the erasure boundary, and the first obligation this KB has found that *forbids* a control

### 29. The fifth boundary is deletion, and it is the first one with no product to sell

The four boundaries this KB established — read, write, provenance, containment — all govern what an
agent **may do**. 2026's regulatory movement added a fifth that governs what has to **come back
out**, and it behaves differently from the other four in three measurable ways.

**It has no vendor.** The best-known open-source platform for privacy-request orchestration,
`ethyca/fides` (Apache-2.0, 483★), is **archived**, last pushed 2026-08-06 — and so are its
predecessor `fidesops`, `fidesdemo`, `fideslib`, `fides-CICD-Quickstart` and `fides-stats`. Of 22
repositories in that organisation, the only actively developed ones are three mobile consent SDKs
that **declare no licence at all**. 2026 roundups still name Fides as the open-source answer here.

**It has no agents.** Three of four agent-shaped queries return a hard zero (`DSAR agent`, `GDPR
erasure agent`, `data subject request automation`, all at `stars:>50`). The same instrument returns
hundreds of rows for agent frameworks. **This is the second layer in six passes with no agents in
it** — the first was the entitlement boundary at the seventh pass — and the pattern now has a
shape worth naming: *the layers a client's legal and security functions care about most are the
layers with the least open-source product in them.* That is where a services firm has an
advantage over a vendor, and it is the argument for doing this work.

**It cannot be solved at one place in the stack.** A delete is a cascade with seven resting places
— system of record, CDC stream, lakehouse snapshot, vector index, evaluation fixtures, fine-tuned
weights, logs — and the controls differ at each. Two of them have no delete at all. Full table in
`repos/foundations.md`; the build is Receta 25.

**So what:** price this as an engineering programme with an evidence deliverable, not a compliance
review. The thing the client cannot buy is the cascade, and the thing the auditor wants is the
proof it ran.

### 30. Two obligations now point in opposite directions, and the resolution is a schema, not a legal opinion

This KB has recorded regulation demanding inventories (trend 16), fields (trend 22) and management
systems (trend 14). The erasure boundary is the first place where **two binding obligations
conflict**:

| Obligation | Direction | Floor |
|---|---|---|
| GDPR Art. 17 / LGPD / DPDP / Ley 21.719 — right of erasure | **Remove it** | On request |
| EU AI Act Art. 19 (providers) + Art. 26 (deployers) — automatically generated logs | **Keep it** | **≥ 6 months** |
| India DPDP Rules, Rule 8 — erase on purpose completion, retain logs | **Both** | **≥ 1 year** |

Two jurisdictions, **two different retention floors**, and an erasure duty running against both. The
naive reading is that compliance is impossible; the correct reading is that **the Act prescribes no
log format**, and that freedom is where the answer lives: keep identifiers out of the log body, log
a pseudonymous reference, and hold the mapping in a store that *is* in the cascade. The log is then
retainable at full fidelity and is not a surviving copy of what was erased.

**The generalisation, which is the part worth carrying to other industries:** *when two obligations
conflict, look for the one that does not specify a format — that is the degree of freedom.*

**And note what it costs when deferred.** Designed in, this is a field name. Retrofitted, it is a
migration of every log, trace and evaluation fixture in the estate — which is the same
"governance is cheap before deployment and expensive after" result this KB has now measured in five
consecutive layers.

### Licence class nº 12 — a tool licence that reaches your model weights

Eleven classes so far. The twelfth was found by resolving a `NOASSERTION` badge on
`vec2text/vec2text` (1,150★), the best-known embedding-inversion implementation. The 3,864-byte
`LICENSE` at `master` is the **Software for Open Models License (SOM) Version 1.0** (30 August
2023) — **no OSI approval, no SPDX identifier**. Section 3(A), verbatim:

> *"If you use the Software to create, modify, process, or otherwise use any Model, **including
> usage to create inferences with a Model, whether or not you make the Model available to
> others**, you must make that Model Source Materials publicly available under Open Licensing
> Terms."*

The same file defines *Model Source Materials* as **"the Model and model weights."** Read
literally, **using this tool to run inference with a client's private model obliges the client to
publish its weights.**

**Why this is the sharpest licence finding in thirteen passes, and not merely the strangest.** The
twelfth pass found that the clause deciding an EMEA engagement sat **outside** the licence, in an
acceptable-use policy. This one sits **inside** the licence of a *tool* and reaches an asset the
tool does not contain. Together they close a rule:

> **A licence constrains artefacts the licensed files do not include, in both directions. Scanning
> the licence of what you import tells you neither what you may do with your model nor what your
> model becomes.**

A scanner reports `NOASSERTION` and a careless reviewer reads that as "unlicensed, probably fine."
Mitigation is cheap: [`jina-ai/embedding-inversion-demo`](https://github.com/jina-ai/embedding-inversion-demo)
(Apache-2.0, 61★) demonstrates the same property for a client workshop, and vec2text can be cited
as a paper. **Never run it against client weights.**

### Method — three more ways to be wrong, bringing the count to twenty-five

**23. A grep for a project's NAME cannot tell you which OWNER the KB cites — and this pass nearly
published the false finding.** The opening probe established that `repo:microsoft/presidio` is
**unsearchable (422)** and that `grep -ril presidio` matches **seven files**, and concluded the KB
was citing a dead owner in seven places. It was not: the **fourth pass already caught the move** to
`data-privacy-stack/presidio` and already rewrote every citation — the grep was matching the
**new** path, and the only `microsoft/presidio` strings left are the three correct ones (the rename
ledger's "Was" column and the anti-pattern telling you not to cite it). **Grep the old owner path,
never the bare name.** This is the energy KB's T88 reproduced in a second industry, and the second
time in *this pass* that the KB proved more precise than the search auditing it — the first being
the AI Act deferral, where live articles still say "August 2026" and this KB holds the naming
instrument, **Regulation (EU) 2026/1744**. A false gap is published as news and degrades correct
data; a missed finding merely costs a pass.

**24. A liveness check cannot detect a rename, because the old path still answers 200.**
`raw.githubusercontent.com/microsoft/presidio/main/LICENSE` returns **200** and serves the current
MIT text, via redirect. Every URL-verification routine in this task would mark it healthy. **Only
the search API detects a rename**, by refusing the old path. Corollary for the fleet: *URL
liveness and canonical path are two different measurements, and the cheap one does not imply the
other.*

**25. `NOASSERTION` resolved in both directions inside a single pass, which settles the rule
empirically.** `kiprotect/klaro` → **BSD-3-Clause** (permissive). `axelor/axelor-open-suite` →
**AGPL-3.0** (copyleft). `pgvector/pgvector` → **PostgreSQL License** (permissive).
`vec2text/vec2text` → **SOM-1.0** (more restrictive than any copyleft this KB holds). One badge,
four repositories, **three different licence classes in one sweep**. Resolving a `NOASSERTION` by
assumption is not a judgement call — it is a coin flip with a known failure mode in both
directions. Read the bytes. The energy KB reached the identical conclusion from a different forge
(its T84), which makes this a fleet-level rule rather than an industry one.

### Instrument — the metadata oracle this environment actually has, and the one way it lies

The twelfth pass recorded that it **could not measure stars or push dates**, because
`api.github.com/repos/{owner}/{repo}` is **403 outside this session's scope**. That limit is real
but it is not binding, and the workaround is worth carrying to every KB in this fleet:

```
gh api -X GET search/repositories -f q='repo:a/b repo:c/d repo:e/f …'
  → license.spdx_id, stargazers_count, pushed_at, archived, default_branch   (one request)
```

Multiple `repo:` qualifiers **OR** together, so up to several repositories resolve in a single
request — which matters under a search rate limit of a few requests per minute. It returns
`default_branch` **in the same call as the licence**, so the blind `main`/`master` iteration that
this KB has repeatedly paid for is unnecessary: this pass alone met `master` (klaro, pgvector,
axelor, vec2text, milvus, qdrant), **`hotfix`** (SuiteCRM — a default branch no iteration order
would have guessed), `develop` (ERPNext, Dolibarr) and `20.0` (Odoo).

**The one way it lies, found this pass:** an invalid or unviewable `repo:` qualifier is **silently
dropped** when other valid ones remain — ask for eight, get six, with **no error** — but if **every**
listed repository is invalid the whole query fails with **HTTP 422**. So a short result is not an
error and must be reconciled by name against what was requested, and **a 422 is positive evidence
that a path is gone** (which is how the Presidio and Casbin moves were both detected).

### Sources that disagree — this pass

| Question | Positions | Status |
|---|---|---|
| When do EU high-risk obligations apply? | Live 2026 articles: "from August 2026". Art. 19 trackers: deferred to **2 Dec 2027** / 2 Aug 2028 | **Resolved** — the KB holds the naming instrument (Reg. (EU) 2026/1744). The August date is stale |
| ANPD enforcement volume (Brazil) | "A single R$14,400 fine up to 2026" vs "120+ concluded sanctioning processes in H1 2026, +280%" | **Unresolved and irreconcilable.** Quote neither |
| India consent-manager routing right | Begins Nov 2026 vs May 2027 | **Unresolved.** Registration-first is plausible, unconfirmed |
| EDPB Guidelines 02/2026 status | "Adopted 7 July 2026" vs "draft for consultation" | **Unresolved** |
| Presidio's departure from Microsoft | Governance transfer to a community org (multiple) vs "multi-year deal with Microsoft" (one low-authority blog) | **Resolved** toward the transfer; the outlier is noted, not adopted |

### Verification channel for this pass — what could and could not be checked

**Byte-verified from reachable primaries:** every repository path, licence, star count, push date,
archival state and default branch (via `gh api search/repositories`); five licences read from file
bytes (`klaro` → BSD-3-Clause, `axelor` → AGPL-3.0, `pgvector` → PostgreSQL, `vec2text` → SOM-1.0,
`PrivAiTe` → BSD-3-Clause); `weaviate`'s split-licence header; and the **`mark_deleted()` source
listing from `SuiteCRM/SuiteCRM` at `data/SugarBean.php`**, which is this pass's only
platform-behaviour claim and the only one that needed to be read from code rather than from a
vendor page.

**Not verified, and therefore marked everywhere it appears:** all regulatory content.
`eur-lex.europa.eu`, `ai-act-service-desk.ec.europa.eu`, `gdpr-info.eu`,
`artificialintelligenceact.eu`, `oag.ca.gov`, `meity.gov.in`, `pdpc.gov.sg`, `planalto.gov.br`,
`www.gov.br`, `apps.odoo.com`, `store.suitecrm.com` and `docs.axelor.com` **all fail to resolve
from this session** (each probed once, then abandoned per policy). Article 19's wording, the DROP
mechanics and penalties, the DPDP dates, Ley 21.719's transitional article, the ANPD resolution and
the EDPB quotations are **search-snippet-level**. The asymmetry is the point: **this pass's code
facts are stronger than its law facts, and the files say so at each location** rather than letting a
reader assume one standard of evidence throughout.

### Gaps measured this pass — stated, not left silent

1. **No maintained permissive replacement for Fides was found.** Searched; not found; recorded as an
   absence rather than filled with a plausible row. The engagement is a build over maintained
   catalog/lineage components.
2. **Soft delete verified for SuiteCRM only.** Odoo, ERPNext, Dolibarr and Axelor each need the same
   ORM check before any erasure claim is made about them. **No claim is made here.** Cheapest work
   available to the next pass.
3. **The archival dates of `ethyca/fides` and `amundsen-io/amundsen` could not be measured** — the
   search API returns `archived: true` but not `archived_at`, and `repos/{owner}/{repo}` is out of
   scope. Last push dates (2026-08-06 and 2026-09-10) are given instead and are **not** archival
   dates.
4. **Whether the EU retention floor and the erasure duty have been reconciled by any regulator** is
   unestablished. The schema answer above is this KB's engineering reading, **not** a published
   position, and must be presented to a client as such.
5. **LATAM-origin tooling in this layer: not measured.** The short Spanish instrument was run
   against the KB, not against the forges, so no zero is claimed either way.

## Fourteenth pass, 2026-11-24 — the accessibility boundary, and the first licence finding that is hidden one level down

> Theme: **whether the people a client is legally obliged to serve can use the agent at all.**
> Measured before searching, across all nine files: `wcag` 0, `accessib` 0, `a11y` 0,
> `EN 301 549` 0, `VPAT` 0, `axe-core` 0. A clean zero in every file — and the layer turns out to
> carry a legal obligation that this KB has been selling *around* for thirteen passes.

### 18. Accessibility became an AI obligation, not a web obligation

The EU AI Act's **Article 16(l)** requires providers of high-risk AI systems to comply with the
accessibility requirements of Directives (EU) **2016/2102** and **2019/882**, and **Recital 80**
insists on *full* compliance. The practical consequence is structural: accessibility belongs
**inside** the AI Act conformity file, next to the Annex IV documentation this KB already sells
(Receta 3), not in a separate web-quality workstream. Legal commentary (Hogan Lovells) reads it as
a design-and-development obligation, not a disclosure one.

Two caveats carried forward honestly: the **application date is in conflict** across sources
(2027-12-02 / 2028-08-02 under Article 113(c) versus a claim that the high-risk regime applied
2026-08-02), and one widely-linked source misdescribes Article 16 as a GPAI obligation. Recorded in
`intel/market.md` (EMEA), not reconciled.

### 19. The permissive badge in a tooling layer can belong to the wrapper, not the engine

This KB already holds a **licence-concentration** rule (sixth pass, generalised): one layer, one
licence, measured. The accessibility layer adds a **sharper and more dangerous form** — the
concentration is **one level below the thing you read the licence of**:

| Tool | Badge the client reads | What `package.json` actually pulls in |
|---|---|---|
| `microsoft/accessibility-insights-web` | **MIT** | `axe-core` 4.11.3 — **MPL-2.0** |
| `GoogleChrome/lighthouse` | **Apache-2.0** | `axe-core` 4.14.1 — **MPL-2.0** |
| `JustasMonkev/mcp-accessibility-scanner` | **MIT** | `axe-core` 4.14.0 — **MPL-2.0** |
| `ronantakizawa/a11ymcp` | **MIT** | `axe-core` ^4.6.0 — **MPL-2.0** |
| `priyankark/a11y-mcp` | MPL-2.0 | `axe-core` ^4.14.0 — MPL-2.0 (consistent) |
| `IBMa/equal-access` | **Apache-2.0** | **nothing — own engine** |

**The rule, stated generally for the rest of the rotation:** a licence badge describes a repository,
not an artifact. In any layer with a de-facto single engine, **read the dependency manifest, not the
sidebar**. MPL-2.0 is file-level copyleft and therefore *deliverable* — this is a disclosure and
AI-BOM finding, not a blocker — but a team that promised the client "MIT only" has already broken
the promise by installing Microsoft's MIT tool.

### 20. Star count and maintenance inverted perfectly inside one category

Trend 11 said star count has decoupled from enterprise suitability. The three community
accessibility MCP servers are the first category where the two rankings are **exactly reversed**:

| Stars | Repo | npm last published | Pinned browser | Supply-chain hygiene |
|---|---|---|---|---|
| **97** | `ronantakizawa/a11ymcp` | **2026-03-01** | **`puppeteer` 13.5.0 — 2022-03-07** | — |
| 59 | `JustasMonkev/mcp-accessibility-scanner` | **2026-11-16** | `playwright` 1.65.1 | — |
| 53 | `priyankark/a11y-mcp` | 2026-10-26 | `puppeteer` ^25.16.0 | **npm provenance**, weekly Dependabot, real-Chrome smoke tests |

The most-starred option pins a browser **four and a half years old**; the least-starred is the only
one publishing with provenance. The practical instrument: **`registry.npmjs.org` dates every
version**, so "how stale is this pin" is a one-call measurement, not a judgement.

### 21. There is no standard for the thing an agent UI actually does

The agent-to-user layer (trend 15) has a concrete accessibility failure mode and **no normative
rule covering it**. Token streaming updates the DOM roughly **5–20 times per second**; a live region
mirroring that either floods the screen reader with every token or, with the wrong configuration,
announces nothing. Practitioner consensus (Smashing Magazine, November 2026; GOV.UK's accessible
web-chat patterns; vendor component docs) converges on: keep streamed text **out** of the live
region, announce **once** on completion, use a **single dedicated `aria-live="polite"`** region with
`aria-atomic="false"`, create it **empty and before** content arrives, **do not** rely on
`aria-busy`, and **never move focus** on a status update; `role="log"` with `aria-live="polite"` for
completed messages.

Two things make this a trend rather than a tip. First, **W3C live-region guidance is advisory, not
normative** — no standard defines what "accessible streaming" means, so this is a design decision
the delivery team owns and no conformance scan will catch. Second, it is **not** a hypothetical:
Atlassian's own agent carries a public ticket (**ROVO-978**) for dynamically updating content not
being announced to screen-reader users. A shipped product from a major vendor has this exact bug on
the record.

### A licence-tightening instance with the evidence inside the repository

Trend 7 (licences are quietly tightening) usually rests on announcements. `ryersondmp/sa11y` states
it in its own `LICENSE.md`: now **GPL-2.0**, and "previous versions of Sa11y (v2.0 and below) were
released under the MIT license." **Byte-read, not reported.** Worth adding to the method: the
cheapest place to detect a relicensing is the licence file's own prose, which often narrates the
change.

### Verification channel for this pass — what could and could not be checked

**Worked, and two of these are new instruments for the whole rotation:**
- `raw.githubusercontent.com/<repo>/HEAD/LICENSE` → licence **text**. Stronger than any badge, and
  the only channel available now that the API is closed.
- `raw.githubusercontent.com/<repo>/HEAD/package.json` → **the dependency chain**, which is how
  trend 19 above was proved rather than asserted.
- **WebFetch on github.com HTML** → stars, description, archived banner. **curl gets 403 on the
  same URL**; WebFetch does not. This restores the archived-repo check that passes nine through
  thirteen had to do by other means.
- `registry.npmjs.org/<pkg>` → SPDX licence of the latest version, the version itself, and a
  **per-version publish date** (how `puppeteer` 13.5.0 was dated to 2022-03-07).

**Refused or unreachable — so the corresponding claims are marked, not quietly weakened:**
- `api.github.com` **403** (unchanged since the ninth pass), `img.shields.io` **403**,
  `repos.ecosyste.ms` **403** — there is **no star channel except WebFetch**, one call per repo.
- `etsi.org` does not resolve → **EN 301 549 V4.1.1 is secondary-sourced** (two independent
  sources agree on 2026-09-02; others still call it "expected").
- `federalregister.gov` does not resolve → the **DOJ interim final rule of 2026-04-20** is
  secondary-sourced from four independent legal publishers.
- `dwt.com` does not resolve, though its content surfaced through search snippets.

**One method rule added.** When a region's whole evidence base traces to a **single vendor read in
several language localisations** — which is what happened to APAC this pass, where nearly everything
came from Deque's own country pages — that is **one source, not corroboration**. Say so in the
subsection rather than letting the page count imply breadth.

## Fifteenth pass, 2026-11-24 — el límite del consumo, y la primera licencia de esta KB que no recae sobre software

> **Nota de numeración, medida.** Los números de tendencia de este archivo **colisionan**: el pase
> trece llegó hasta `### 30`, y el pase catorce reinició en `### 18`, de modo que hay dos tendencias
> 18, dos 19, dos 20 y dos 21. Este pase **no agrava la colisión**: continúa desde el máximo global
> (30) con **31, 32 y 33**. Se deja escrito porque un índice duplicado es un defecto de datos
> silencioso: el compilador no falla, simplemente produce dos entidades con la misma clave.

### 31. El sexto límite es lo que el agente **gasta**, y a diferencia de los cinco anteriores no lo gobierna quien lo construye

Catorce pases construyeron una secuencia: qué puede **leer** el agente (entitlement), qué puede
**cambiar** (write), qué puede **probar** (provenance), qué puede **contener** (containment), qué
tiene que **olvidar** (erasure) y **quién puede usarlo** (accessibility). Los seis se deciden dentro
del proyecto. **El consumo no.** El que opera el agente gasta los julios; el que tiene que
declararlos es, según la jurisdicción, el emisor cotizado, el operador del centro de datos o nadie.

Y por eso la capa aparece **ahora**: el multiplicador es el agente. Una fuente de analistas (nivel
snippet, atribuida y no adoptada) sostiene que la IA agéntica consume **entre 5 y 30 veces más
*tokens* por tarea** que un intercambio único de chatbot. Cuando la unidad era el chatbot, el
consumo era un detalle de infraestructura; cuando la unidad es un plan con reintentos, es una línea
de costo y una obligación de reporte de otra persona.

**La forma técnica del problema, dicha con precisión:** ninguna de las sondas maduras mide agentes.
Kepler mide **pods**, Scaphandre mide **procesos**, CodeCarbon envuelve **llamadas**. La atribución
por **tarea de agente** no tiene producto: lo único específico son `mlco2/agentic-footprint` (MIT,
8★) y `VeiledTee/agent-energy-profiler` (MIT, 0★). **Esta es la cuarta capa consecutiva que esta KB
encuentra sin agentes dentro** — y las cuatro veces el valor estuvo en descubrir *qué componente*
ocupa el hueco, no en encontrar un agente.

### 32. Una licencia permisiva puede entregarte una base de datos con copyleft, y el SPDX no lo dice

**Clase de licencia nº 13 de esta KB: ODbL — la primera que no recae sobre código.**

`thegreenwebfoundation/co2.js` figura como `NOASSERTION` en la API de GitHub. Su `LICENSE` —12 678
bytes, leído byte a byte— contiene **dos licencias para dos activos distintos**: el **código** es
**Apache-2.0** y los **datos de intensidad de red** empaquetados se republican de **Electricity Maps
bajo la Open Database License**, con *attribution*, ***share-alike*** y *keep-open* enumerados en el
propio archivo.

Y muerde exactamente donde importa: **el factor de intensidad de red es lo que convierte kWh en
gCO₂e**, o sea el dato sin el cual toda la capa de medición no produce la cifra que el informe
exige. Quien lo toma por esa vía hereda **share-alike sobre su base de datos derivada** — una
superficie de riesgo **distinta** del copyleft de código, y que **sobrevive a una librería
Apache-2.0**.

> **La regla, generalizada más allá de esta capa:** el identificador SPDX de un repositorio describe
> **el código del repositorio**. No dice nada de los **datos** que el repositorio empaqueta, ni de
> los **pesos** que descarga, ni del **servicio** al que llama. Las tres excepciones ya están
> documentadas en esta KB y las tres se encontraron en pases distintos: pesos (pase 12), AUP fuera
> de la licencia (pase 12), SOM-1.0 alcanzando un activo que la herramienta no contiene (pase 13) y
> ahora **datos** (pase 15). **Cuatro veces el mismo patrón: la obligación que decide está fuera del
> campo que se consulta.**

**Corolario operativo, y es la regla de método 14:** ante cualquier proyecto de huella ambiental,
dos preguntas de licencia, no una — *¿qué licencia tiene el código?* y *¿qué licencia tienen los
factores de emisión que trae?* En esta capa la segunda respuesta es, casi siempre, **ODbL**. Prueba
de propagación: la **misma errata** (`"Licening for the CO2.js library"`) aparece dentro del
`LICENSE` de `green-coding-solutions/green-metrics-tool`, cuyo encabezado de sección dice *"Apache
License"* y cuyo cuerpo es **AGPL-3.0**.

### 33. Dos obligaciones de la misma región se movieron en direcciones opuestas, y el proyecto que se vende depende de cuál se cite

Esto es EMEA en 2026 y es el contraste comercial más limpio que ha producido esta KB:

| | CSRD (Ómnibus I) | Centros de datos (EED) |
|---|---|---|
| Instrumento | Directiva (UE) **2026/470** | Reglamento Delegado (UE) **2024/1364** |
| Movimiento en 2026 | **se encogió**: de ~50 000 a ~5 000 obligados (≈ **90 %** menos) | **intacto** |
| Umbral | > 1 000 empleados **Y** > 450 M EUR | **≥ 500 kW** de potencia TI instalada |
| Cadencia | anual, primer ejercicio **en disputa** entre fuentes | anual, **15 de mayo** |
| Cumplimiento observado | — | **770 centros reportaron ≈ 36 %** de los obligados |

**Quien venda "proyecto CSRD" en EMEA persigue un mandato que acaba de perder nueve de cada diez
obligados. Quien venda instrumentación EED persigue una obligación vigente, anual y que dos tercios
de su población incumple.** Misma capa técnica, dos conversaciones comerciales opuestas, y la
diferencia entre ellas es qué instrumento se cita.

**Y el error de este pase, registrado porque iba a publicarse como noticia:** la hipótesis de
partida fue que la obligación de eficiencia energética estaba en el **artículo 40 del AI Act**. **No
lo está** — el art. 40 trata de **normas armonizadas y presunción de conformidad**. El deber vive en
la EED. **Atribuir una obligación al instrumento equivocado es tan falsable como inventar un repo**,
y la única defensa barata es citar siempre instrumento + fecha, nunca "el AI Act exige".

### Canal de verificación de este pase — qué se pudo comprobar y qué no

**Asimetría declarada, y es más marcada que en pases anteriores:**

- **Fuerte (byte a byte).** 33 direcciones nuevas. Toda licencia `NOASSERTION` resuelta por lectura
  directa del archivo: `Arelle/Arelle`→**Apache-2.0**, `thegreenwebfoundation/co2.js`→**Apache-2.0 +
  ODbL**, `odoo/odoo`→**LGPL-3.0**, `crbnos/carbon`→**AGPL-3.0-only + comercial**,
  `green-metrics-tool`→**AGPL-3.0 + ODbL**, `jobrunr/jobrunr`→**LGPL-3.0-or-later o comercial**.
  Licencia, estrellas, push, `archived` y `default_branch` de `gh api search/repositories`.
- **Más fuerte todavía (lectura de código).** Que el *scheduling* carbon-aware de JobRunr está en el
  **núcleo abierto** se probó con `gh api search/code` (**91 coincidencias** bajo
  `core/src/main/java/org/jobrunr/`), y su **salida de red por defecto** a `api.jobrunr.io` leyendo
  `CarbonAwareJobProcessingConfiguration.java`. **Ni una ni otra se tomaron de un blog.**
- **Débil (nivel snippet, nunca bibliografía).** **Todo** lo regulatorio y **toda** cifra de
  mercado. `arxiv.org` y los *hosts* legales, de analistas y de banca multilateral **no resuelven
  desde esta sesión** — comprobado una vez con WebFetch y no vuelto a sondear, por política. En
  consecuencia, las dos cifras técnicas más citables del pase **quedan sin verificar en el
  primario** y se marcan como tales donde aparecen: que un *token* de salida consume ~**850×** la
  energía de uno de entrada con contexto de 1k en vLLM (HotCarbon'26), y que la energía por *token*
  de salida **varía hasta 8,3× entre idiomas** — esto último de interés directo para una KB escrita
  en español, porque implicaría que **el mismo agente cuesta más energía por respuesta en español
  que en inglés**. **Es una hipótesis con fuente, no un hecho de esta KB.** Open item 15-R1.
- **Oráculos no equivalentes usados:** `gh api search/repositories`, `gh api search/code`,
  `raw.githubusercontent.com` con **GET por rango** (`HEAD` está bloqueado por el proxy: devuelve
  000/403) y el **POM de Maven Central**, que resultó **correcto e incompleto**.

### Nuevas formas registradas de equivocarse en esta capa

1. **Buscar un agente donde hay una sonda.** Cuarta capa consecutiva sin agentes dentro.
2. **Leer el SPDX y creer que cubre los datos.** No los cubre (tendencia 32).
3. **Confiar en el manifiesto como oráculo terminal.** Maven declaró LGPL y omitió la vía comercial:
   **correcto e incompleto** (regla de método 15, que corrige la 12).
4. **Buscar `LICENSE` y concluir que no hay licencia.** JobRunr lo llama **`License.md`**; 404 en los
   cuatro nombres habituales.
5. **Confiar en el nombre.** `crbnos/carbon` (2860★) es un **ERP de manufactura**, no una
   herramienta de carbono.
6. **Citar una cifra correcta fuera de su fecha.** El "65 % de empresas brasileñas no preparadas" es
   de 2024 y **anterior a la derogación** del mandato.
7. **Atribuir la obligación al instrumento de moda.** No es el art. 40 del AI Act; es la EED.
8. **Suponer que el `default_branch` es `main`.** Las cuatro suites de este pase: `20.0`, `develop`,
   `2026.9.x`, `trunk`. **Ninguna.**

---

## Sixteenth pass, 2026-11-24 — the language boundary: the trend is that "it works" and "it is lawful here" have separated

> Theme: **what the agent says, in which language, and who approved the wording.** Measured before
> searching: **28 of 30 terms for this layer at zero** across all nine files. Full evidence in
> `repos/foundations.md`; duties by region in `intel/market.md`.

### Trend 1 — The message-format standard stopped being optional, and it replaces what everyone has

The **Unicode MessageFormat Standard (MF2)** is now a **stable part of CLDR**, **approved by the CLDR
Technical Committee** and **recommended for implementation and adoption**, published normatively in
TR35. Read from `unicode-org/message-format-wg`'s own README, because `unicode.org` does not resolve
from this session.

Three things are true simultaneously and all three belong in a client conversation:
1. **It is no longer a preview to wait out.** Approved and recommended.
2. **It replaces the ICU MessageFormat syntax every existing estate is written in.** That is a
   migration, with a cost, that no one has budgeted.
3. **It is not fully frozen** — *"some default functions and items in the `u:` namespace are still in
   Draft status."*

The trend to call: **2026–2027 is the MF2 migration window**, and the reason it matters now is
agentic. Hand-written strings get migrated once by a human; **LLM-generated strings get produced
continuously**, so an estate that has not fixed its message format is accumulating ungrammatical
plural and gender handling at machine speed. The format decision is now upstream of the content
pipeline, which it never was when humans wrote all the copy.

### Trend 2 — Terminology control moved from post-editing to generation time, with a measured bar

The converging practice across research and products: **inject approved glossary terms at generation
time rather than correcting output afterwards**. The measured bar is **AIDAterm** (ACL 2026, Industry
Track): a four-agent pipeline (Analysis → Translation → Post-editing → Review) reporting **99.4%
terminology accuracy on the WMT25 Terminology Translation benchmark** and, per its authors,
outperforming **all 20 systems** submitted to that shared task. Its design choices are the
transferable part: **glossary injected at every stage**, not once, and a **reasoning-enabled review
agent** last.

The contrast worth quoting: a practitioner report puts **glossary-specific prompting alone
plateauing in the mid-80% range** for terminology compliance. That is anecdotal, but the gap between
~85% and 99.4% is the gap between a demo and a deliverable — and it is **architectural**, not a
matter of a better model. Product confirmation that the pattern is now table stakes: ServiceNow,
Ada and Zowie all shipped glossary features in which terms carry per-market translations and a
conversation view shows **which terms were applied on each turn**.

### Trend 3 — The region is now a property of the sentence, not of the deployment

The 2026 compliance picture turned language into a per-utterance obligation, and the four regions
have **four different duties** (detail and sourcing caveats in `intel/market.md`):

| Region | Duty | Status |
|---|---|---|
| **North America** | Québec Charter / Bill 96 — **functionally equivalent French** UI where a French version exists | In force since **2025-06-01** |
| **EMEA** | EU AI Act **Art. 50** chatbot disclosure, up to €15M/3% | Applicable **2026-08-02** |
| **APAC** | India DPDP **§5(3)** — notice viewable in **English or any of 22 Eighth Schedule languages** | Rules notified Nov 2025; phase-in **Nov 2026 → May 2027** |
| **LATAM** | Brazil Decree **13,135/2026** — AI **does not remove** the right to real-time human service | Effective **≈2026-11-02** |

**The trend is not "more regulation".** It is that the unit of compliance shrank: from *the system*,
which you certify once, to *the utterance*, which has to be right every time. A model estate
certified in English is not certified. This is the same shift the accessibility pass (fourteenth)
and the erasure pass (thirteenth) recorded in their own layers, which makes it the strongest
cross-boundary pattern in this KB: **2026's obligations attach to individual interactions and
demand per-interaction evidence.**

### Trend 4 — The evaluation metric the whole field quotes can point the wrong way

From `andrewyng/translation-agent`'s own README: translations that **human raters preferred** over
commercial offerings scored **lower on BLEU**. So the standard metric can **invert** on exactly the
agentic pipelines the market is now building. Meanwhile **reference-free quality estimation**
(CometKiwi and relatives) matured enough to be used in production — scoring output with **no human
reference**, which is the only kind of evaluation an agent can run on its own output at runtime.

The practical consequence, and it is a commercial one: **"BLEU ≥ X" is a defective acceptance
criterion** and it is still the default in statements of work. Rank with COMET or reference-free QE,
keep sacreBLEU as a reproducible regression tripwire, and reserve document-level human review for
the terms that carry legal weight. Note what else this exposes: **FLORES**, the benchmark named in
that README, is **archived since 2023-11-20** — the field's reference evaluation set is unmaintained
while the field's output volume grows.

### Trend 5 — In this layer, popularity and licence point in opposite directions

Measured across the two layers where there is a clear leader:

| Category | Most-starred | Licence | Permissive alternative |
|---|---|---|---|
| Translation API/engine | LibreTranslate — **17,840★** | **AGPL-3.0** | `argos-translate` — **MIT**, 6,691★, **and it is the same engine** without the AGPL wrapper |
| TMS | Weblate — **6,180★** | **GPL-3.0** | **Pontoon** — **BSD-3-Clause**, 1,679★ |

Plus the trap that generalises beyond this layer: **Tolgee** (4,162★) presents as Apache-2.0 and
fences its enterprise features into **`ee/` under a non-commercial licence** — the **second
occurrence of the `onyx` pattern** this KB has recorded. The trend to name for 2026: **the
"open-core by directory" model is spreading**, and it is **invisible to a licence badge, to an
SPDX scan of the root, and to every aggregator this pass consulted.** Three aggregators described
Tolgee's self-hosting as fully open source. A supply-chain policy that reads the root `LICENSE` and
stops there will keep getting this wrong, so the check belongs in CI:
**probe `ee/LICENSE` and any directory a root licence names.**

### Trend 6 — The language-identification layer is unmaintained underneath everything above

Every duty in Trend 3 presupposes knowing which language the user used. The three best-known
libraries for it are **dead**: `facebookresearch/fastText` (**26,502★, archived 2024-03-22**),
`google/cld3` (archived 2023-05-24) and the FLORES benchmark (archived 2023-11-20). The live answer
is `pemistahl/lingua-py` (**Apache-2.0**, 1,822★) — with **one-fourteenth** the stars of the archived
default. This is the **eleventh and twelfth archived-but-highly-starred project** this KB has
recorded, and the pattern now has a reliable tell: **the archived ones are the ones the tutorials
recommend.** A compliance control resting on an archived dependency is a finding, not a footnote.
