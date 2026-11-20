---
industry: enterprise
region: Global
updated: 2026-11-20
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

## Trend sources that disagree — recorded, not reconciled

- **North American adoption:** Stanford AI Index 2026 says **90%** organisational AI use;
  NVIDIA says **70%** active usage; US Census BTOS says **5.4–19.8%**. Different questions
  ("any use ever" vs "used in the last two weeks"), not different facts. Quote the one that
  matches the question being asked, and say which.
- **Enterprise AI spend:** Menlo Ventures' **$176.8B / 5.4x YoY (Sept 2026)** is a single
  vendor estimate and the only figure of its kind found. Treat as directional.
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
