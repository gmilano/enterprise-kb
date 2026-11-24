---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 🎯 Agentes AI — Enterprise

> Agent frameworks and platforms Globant can build enterprise solutions on.
> **Focus: MIT / Apache-2.0 / BSD** — the licenses Globant can build on commercially.
> Every row below was verified against the GitHub API on 2026-11-20 (existence,
> SPDX license, stars, description). Licenses reported as `NOASSERTION` by GitHub
> were resolved by reading the repository's actual `LICENSE` file.
>
> **Second pass, 2026-11-20 (later same day):** Tier 0 added. Every Tier-0 row had its
> `LICENSE` file read directly from `raw.githubusercontent.com`, not taken from the badge.
> Tier 1 is unchanged except that OpenClaw moved up into Tier 0, where it belongs.
>
> **Fourth pass, 2026-11-20 (latest): no agent rows changed, and that is the finding.** This pass
> searched by *consequence* rather than by capability — what does an enterprise agent touch that
> has a blast radius? — and the sixteen repositories it found are **none of them agents**. They are
> the layers around the agent: an **agent payments** stack (three competing permissive protocols,
> the most-starred of which is five months idle), **PII de-identification**
> ([data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio), MIT, 11,989 ★ —
> **moved out of `microsoft/`**), **catalog and lineage** as the grounding layer, and
> **[microsoft/graphrag](https://github.com/microsoft/graphrag)** (MIT, 36,699 ★), which this KB had
> never once mentioned. Tables in `repos/foundations.md`; build in `compose/patterns.md` Receta 11.
> **Taken with the third pass, the message to an engagement lead is now unambiguous: the agent is
> the least consequential choice on the page.** Tier 0 and Tier 1 below are unchanged and still
> correct — they are just no longer where the risk or the billable work lives.
>
> **Third pass, 2026-11-20 (later still):** three large MIT repositories that belong in this
> file were found missing entirely — **deer-flow** (85,545 ★, APAC-origin harness),
> **browser-use** (121,597 ★) and **letta** (25,503 ★, stateful agents). Added below. The
> structural finding of this pass is in `repos/foundations.md`: the KB had no **control-plane**
> layer at all — no AI gateway, quotas, usage attribution, cost governance, red-teaming or
> OpenTelemetry instrumentation. Six sections were added there, and they change what this file
> means: picking an agent is now the *smallest* decision in an engagement.

> **Fifth pass, 2026-11-20 (latest): no agent rows changed again — and this time the news is a
> die-off one layer over.** This pass searched by *counterparty* (who is on the other side of the
> agent) and found the surface where the agent meets a human, which four prior passes never
> touched. Three of that layer's best-known repositories are **archived** —
> [Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★),
> [langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★) and
> [langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui) (MIT, 1,705 ★) —
> and **none of their READMEs says so.** They share one shape: a standalone chat window in front
> of an agent. Everything live in that layer has the other shape: the agent renders *into* the
> client's own application. See the new section below, `repos/foundations.md`, and
> `compose/patterns.md` Recetas 12–13.

> **Sixth pass, 2026-11-20 (latest): a whole agent *category* was missing, not a row.**
> This pass searched by **first client request** — the thing an enterprise asks for in meeting
> one — and found the **data agent** (text-to-SQL / "ask our data in English") absent from five
> passes of this file. Four live implementations added as **Tier 2** below, three of them
> APAC-origin, plus one 23.8k-star project that has been **archived since March 2026**. The
> category's real deliverable is the semantic layer underneath it, not the agent; see
> `repos/foundations.md` and `compose/patterns.md` **Recetas 14–15**.

> **Seventh pass, 2026-11-20 (latest): no agent rows changed — for the third pass running, and
> the reason is now a finding in its own right.** This pass searched by **the question a client's
> security team asks first**: *when an employee asks the agent something, does the agent only see
> what that employee may see?* The layer that answers it — relationship-based authorization and
> delegated identity — was **absent from all eight files**: `OpenFGA`, `Casbin`, `OAuth` and
> token exchange returned **zero matches** before this pass. It contains **no agents at all**,
> which is why six passes of this file missed it. Four verified engines added in
> `repos/foundations.md` ("The entitlement boundary"), the build is `compose/patterns.md`
> **Receta 16**, and the commercially sharpest result is in `verticals/solutions.md`: in Onyx,
> the most popular open-source enterprise search platform, **document permission sync exists
> only inside the enterprise-licensed `ee/` directory** — verified at file level. Also this
> pass: **`casbin/casbin` moved to the Apache Software Foundation** (rename ledger), and
> **three passes in a row have now found their headline one layer below the agent.** Taken
> together the message to an engagement lead is unchanged and stronger: *the agent is the least
> consequential choice on the page.*

> **Ninth pass, 2026-11-24 (latest): no agent rows changed — for the fourth pass running — and the
> headline is that the *best-known tool in this file's own security perimeter changed owner, name and
> business model, and every roundup still cites the old one.*** This pass searched by **provenance**:
> not *what may the agent read* (seventh pass) or *what may it change* (eighth), but **what is the
> agent made of, and who signs for it.** The layer was empty — `sigstore`, `cosign`, `in-toto`,
> `SLSA`, `syft`, `grype`, `trivy`, `attestation`, `dependency-track`, `guac` and `model card` all
> returned **zero matches across all nine files** before this pass, while `SBOM` appeared only as a
> compliance noun with no tool behind it. The KB could *produce* an inventory and *scan* a skill; it
> could not **prove where anything came from**. Full tables in `repos/foundations.md`; builds in
> `compose/patterns.md` **Recetas 18–19**.
>
> **Three findings that change what is already written in this file.** (1) The MCP scanner this KB's
> adjacent layer depends on, `invariantlabs-ai/mcp-scan`, **is now [`snyk/agent-scan`](https://github.com/snyk/agent-scan)**
> (Apache-2.0, 3,300 ★) — vendor-owned, **requires a `SNYK_TOKEN` before any scan**, and the free tier
> has a **daily usage limit**. The code is permissive; the analysis is a metered service. (2) The PyPI
> name `mcp-scan` is now a **redirect shim** (`requires_dist: ['snyk-agent-scan']`) while the **npm name
> `mcp-scan` is a different tool by a different owner** — so `uvx mcp-scan` and `npx mcp-scan` install
> *unrelated software from unrelated vendors*, and `snyk/agent-scan`'s own README states **there is no npm
> package**. (3) The scanner is itself an attack surface: to read tool descriptions it **executes the
> commands in your MCP config** and connects to remote servers **with your configured headers**, and its
> README declares a **residual DNS-rebinding window**. Table below.


## Tier 0 — The harness layer (new category this pass, all MIT)

The unit enterprises now adopt is not a framework but a **harness**: the agent plus the
permissions it runs under, the systems it can reach, and what it is explicitly forbidden
to do. Salesforce's 2026 framing is the cleanest client-facing definition — *"whose
permissions does it operate under? what systems can it reach, and what is it explicitly
prevented from doing? together, these configurations and integrations comprise the agent's
harness."* That is a procurement question, not a modelling one, which is why it matters here.

Three MIT harnesses are now at a scale no framework in Tier 1 approaches. This corrects
this KB's own earlier claim that OpenClaw led "by a wide margin" — it leads the harness
category, but it is not alone in its order of magnitude.

| Harness | Repo | License (read from `LICENSE`) | Stars | Pushed | What it is |
|---------|------|-------------------------------|-------|--------|------------|
| OpenClaw | [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,891 | 2026-11-20 | The AI that really does things. Any OS, any platform. Largest harness; the de facto skill-ecosystem centre of gravity. |
| DeepSeek Harness | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | MIT (c) 2026 DeepSeek | 284,581 | 2026-11-18 | "Everything is a Plugin." Plugin-first harness from DeepSeek. **Absent from this KB until now.** |
| Hermes Agent | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT (c) 2025 Nous Research | 264,904 | 2026-11-20 | "The agent that grows with you." Persistent-memory harness from Nous Research. |
| DeerFlow | [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | MIT | 85,545 | 2026-11-20 | "An open-source long-horizon SuperAgent harness that researches, codes, and creates." **APAC-origin (ByteDance)** and **absent from this KB until this pass** — a fourth MIT harness above every Tier-1 framework. Long-horizon framing matters for enterprise: it is built for tasks that run past one context window. |
| Deep Agents | [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) | MIT (c) LangChain, Inc. | 31,472 | 2026-11-20 | "The batteries-included agent harness." The LangChain/LangGraph-native option — JS sibling: [langchain-ai/deepagentsjs](https://github.com/langchain-ai/deepagentsjs) (MIT, 1,650 ★). |
| NemoClaw | [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | 2026-11-20 | **The enterprise answer to the other four.** Runs Hermes, LangChain Deep Agents and OpenClaw *more securely* inside NVIDIA OpenShell with managed inference. The only governance-first entry in this tier. |

Also in this tier but a different shape: [anomalyco/opencode](https://github.com/anomalyco/opencode)
(MIT, 228,170 ★) — "the open source coding agent" — and
[morluto/rea](https://github.com/morluto/rea) (MIT, 470,997 ★), an agent-based reverse
engineering tool that is the single most-starred agent repository on GitHub. `rea` is an
application, not a platform; it is listed so nobody is surprised to find something above
OpenClaw in the rankings.

**Why Tier 0 matters commercially:** a client who has already picked a harness has already
made the decisions Globant used to make for them — identity, permission surface, tool
reach. The engagement then starts from *constraining* an adopted harness, not choosing a
framework. See `compose/patterns.md` Receta 7.

## Tier 1 — Permissive license, enterprise-ready (15 verified; OpenClaw moved to Tier 0)

| Agent | Repo | License | Stars | Description |
|-------|------|---------|-------|-------------|
| Langflow | [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | MIT | 156,801 | Building and deploying AI-powered agents and workflows (visual builder). |
| browser-use | [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121,597 | Python library for AI browser agents. **New to this KB this pass**, and the second-most-starred entry in Tier 1. The practical answer when a client's "API" is a vendor web portal with no API at all — common in insurance, logistics and public-sector filing. Treat the browser as a tool that needs sandboxing and credential scoping like any other. |
| OpenHands | [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | MIT | 93,898 | AI-driven software development agents. |
| Mem0 | [mem0ai/mem0](https://github.com/mem0ai/mem0) | Apache-2.0 | 69,277 | The memory layer for AI agents — drop-in memory infrastructure. |
| CrewAI | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | MIT | 61,126 | Orchestrating role-playing, autonomous AI agents in collaborative crews. |
| goose | [aaif-goose/goose](https://github.com/aaif-goose/goose) | Apache-2.0 | 56,815 | Extensible AI agent that installs, executes and edits — beyond suggestions. |
| LangGraph | [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | MIT | 45,191 | Build resilient, stateful agent graphs with durable execution. |
| Agno | [agno-agi/agno](https://github.com/agno-agi/agno) | Apache-2.0 | 43,244 | The self-managing agent platform. |
| DSPy | [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy) | MIT | 39,152 | Programming — not prompting — language models; compiles/optimises pipelines. |
| AgentScope | [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) | Apache-2.0 | 36,363 | Build and run agents you can see, understand and trust. **APAC-origin.** |
| OpenAI Agents SDK | [openai/openai-agents-python](https://github.com/openai/openai-agents-python) | MIT | 30,784 | Lightweight framework for multi-agent workflows. |
| Sim | [simstudioai/sim](https://github.com/simstudioai/sim) | Apache-2.0 | 30,164 | Collaborative workspace to build, deploy and monitor agents (`apps/sim/ee` carve-out). |
| Semantic Kernel | [microsoft/semantic-kernel](https://github.com/microsoft/semantic-kernel) | MIT | 28,790 | Integrate LLM technology into apps; strong .NET/Java enterprise story. |
| Letta | [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | Platform for **stateful** agents — advanced memory that learns and self-improves over time (the MemGPT lineage). New to this KB. **Caveat: last pushed 2026-10-18**, the only entry here over a month idle; verify activity before committing. |
| Pydantic AI | [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai) | MIT | 21,312 | Typed Python agents, realtime voice, embeddings; every model/provider. |
| PraisonAI | [MervinPraison/PraisonAI](https://github.com/MervinPraison/PraisonAI) | MIT | 9,365 | **Private AI agents for highly regulated teams**, self-hosted. |
| AG2 | [ag2ai/ag2](https://github.com/ag2ai/ag2) | Apache-2.0 | 5,076 | AG2 (formerly AutoGen): the open-source AgentOS. |

Also permissive and worth knowing for JVM shops:
[agentscope-ai/agentscope-java](https://github.com/agentscope-ai/agentscope-java) — Apache-2.0, 6,435 ★ —
distributed, production-grade, long-running agents on the JVM.
And, new this pass, [Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere) —
Apache-2.0, 3,835 ★, pushed 2026-11-20 — a portable agent runtime where one `@Agent` class runs
over Spring AI, LangChain4j or a vendor SDK, which is how a JVM shop avoids re-writing agents
when it changes model provider.

## Tier 2 — Popular but license-restricted (use with care)

These are heavily used in the market, so the studio must be able to discuss them —
but they are **not** clean MIT/Apache, and that changes what Globant can ship.
Licenses below were read from each repo's `LICENSE` file, not from GitHub's badge.

| Agent | Repo | Real license | Stars | Commercial constraint |
|-------|------|--------------|-------|----------------------|
| n8n | [n8n-io/n8n](https://github.com/n8n-io/n8n) | Sustainable Use License ("fair-code") | 211,510 | Not OSI open source. Restricts hosting-as-a-service; non-`master` branches are explicitly unlicensed. |
| Dify | [langgenius/dify](https://github.com/langgenius/dify) | Modified Apache-2.0 + extra conditions | 161,564 | Multi-tenant-service and branding conditions added on top of Apache-2.0. |
| Onyx | [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | MIT core + `ee/` enterprise carve-out | 33,488 | Core is MIT; everything under `ee/` is separately licensed. **Seventh pass, verified at file level: the carve-out contains document permission sync** — `backend/ee/onyx/external_permissions/` returns 200 and there is **no copy outside `ee/`** (404). The MIT build therefore retrieves over a flat index for every user. See `verticals/solutions.md`. |
| Mastra | [mastra-ai/mastra](https://github.com/mastra-ai/mastra) | Apache-2.0 core + `ee/` carve-out | 29,691 | TypeScript framework; `ee/` directories separately licensed. |
| Activepieces | [activepieces/activepieces](https://github.com/activepieces/activepieces) | MIT core + `packages/ee/` carve-out | 25,638 | ~400 MCP servers bundled; enterprise packages carved out. |
| AutoGen | [microsoft/autogen](https://github.com/microsoft/autogen) | CC-BY-4.0 (per GitHub) | 61,955 | **Legacy.** Superseded — active work moved to AG2 and Microsoft Agent Framework. Do not start new work here. |

## The agent-to-user layer — not agents, but where the agent meets the employee (new this pass)

Everything above decides what the agent *is*. This decides whether anyone uses it. Four prior
passes of this KB went from framework → harness → control plane → blast radius without once
naming the surface the user actually sees, which is also where an engagement is judged.

Licences below were **read from each repository's `LICENSE` file**; stars and push dates are from
the GitHub API on 2026-11-20.

| Piece | Repo | Licence | ★ | Pushed | Role |
|-------|------|---------|---|--------|------|
| AG-UI protocol | [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | MIT | 20,766 | 2026-11-20 | **The third protocol.** MCP = agent↔tool, A2A = agent↔agent, AG-UI = agent↔user. Open and free to implement without CopilotKit's framework. |
| Frontend stack | [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) | MIT | 38,842 | 2026-11-20 | React/Angular/mobile/Slack implementation; authors of AG-UI. $27M Series A May 2026 (Seattle). |
| A2UI | [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | Apache-2.0 | 17,690 | 2026-11-20 | Google-origin, announced 15 Dec 2025, 1.0 shipped. Agent streams **layout data, not code**; client holds a catalog of pre-approved components. The strongest *security* story in the layer. |
| json-render | [vercel-labs/json-render](https://github.com/vercel-labs/json-render) | Apache-2.0 | 19,791 | 2026-11-19 | Vercel's generative-UI framework. |
| openui | [thesysdev/openui](https://github.com/thesysdev/openui) | MIT | 15,375 | 2026-11-20 | A third self-declared "open standard" for the same slot. |
| Chat surface | [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) | MIT | 13,351 | 2026-11-20 | The live React chat library — the replacement for the archived LangChain UIs. |
| React SDK | [tambo-ai/tambo](https://github.com/tambo-ai/tambo) | MIT | 11,221 | 2026-11-18 | Generative UI SDK for React. |
| Mobile | [flyerhq/flutter_chat_ui](https://github.com/flyerhq/flutter_chat_ui) | Apache-2.0 | 2,381 | 2026-11-19 | Flutter; for a phone-first workforce (field service, retail floor, logistics). |
| Human approval | [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) | Apache-2.0 | 12,919 | 2026-11-16 | The agent requests a human decision as a typed call, not a politely-worded prompt. |
| Agent management | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT (`LICENSE` on `master`) | 115,408 | 2026-11-20 | "The open-source app everyone uses to manage agents at work." More starred than all of Tier 1 combined. |

**Four permissive standards, no foundation steward, within one order of magnitude of each other.**
That is the opposite of the tool layer, where MCP won and then moved to the Linux Foundation
(`intel/trends.md` §5). **So what:** at the presentation layer a 2026 engagement is placing a
bet, not following a standard. Have the agent emit **structured UI intent** and keep the renderer
behind an adapter, so the bet is reversible. Google states A2UI was built with partners including
the AG-UI/CopilotKit team, so these are overlapping camps rather than clean rivals — do not sell
them to a client as a two-horse race.

**Archived — check whether the client already standardised on one:** `Chainlit/chainlit`
(Apache-2.0, 12,498 ★, Paris-origin, last push 2026-09-18), `langchain-ai/agent-chat-ui` (MIT,
3,253 ★), `langchain-ai/deep-agents-ui` (MIT, 1,705 ★). Also stale, not archived:
[agno-agi/agent-ui](https://github.com/agno-agi/agent-ui) (MIT, 1,879 ★, last push 2026-05-08).
A client on Chainlit has an archived dependency carrying their whole agent front end, and their
README will not have told them. **That is a migration engagement with a deadline the client has
not noticed yet.**

**Also new in this tier's neighbourhood:** [Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere)
(Apache-2.0, 3,835 ★, pushed 2026-11-20) — "portable AI agent runtime for the JVM: one `@Agent`
class runs on Spring AI, LangChain4j and others." It is the JVM answer this KB had only one entry
for, and it matters for Japan/Korea cores (`compose/patterns.md` Receta 6).

## Gaps found this pass — read before planning an engagement

- **Microsoft Agent Framework (MAF) could not be verified.** Vendor blogs and this
  KB's own earlier passes record "MAF, MIT, ~45k ★, v1.0 on 3 Apr 2026" at
  `github.com/microsoft/agent-framework`. On 2026-11-20 that path returns **404**
  (checked twice, two independent channels: HTTP fetch and GitHub search API),
  and `agent-framework in:name stars:>2000` returns **zero** results. What does
  exist and is verified: [microsoft/agent-framework-go](https://github.com/microsoft/agent-framework-go)
  (MIT, 686 ★), whose README still links to the missing upstream repo, plus
  [microsoft/Agent-Framework-Samples](https://github.com/microsoft/Agent-Framework-Samples) (MIT, 395 ★).
  **Do not promise MAF to a client until the canonical repo is located.** Semantic
  Kernel (MIT, 28,790 ★) is the verified Microsoft-stack fallback.
- **MAF still missing — now confirmed on a third channel.** The earlier pass recorded
  `github.com/microsoft/agent-framework` as 404 via HTTP fetch and the GitHub search API.
  Re-checked this pass through a fourth and fifth probe:
  `raw.githubusercontent.com/microsoft/agent-framework/{main,master}/{README.md,LICENSE}`
  returns **404 on all four**, and `agent-framework in:name user:microsoft` returns 14
  repositories, **none of which is the canonical one** — only
  [microsoft/agent-framework-go](https://github.com/microsoft/agent-framework-go) (MIT, 686 ★),
  [microsoft/agent-framework-durable-extension](https://github.com/microsoft/agent-framework-durable-extension)
  (MIT, 25 ★) and [microsoft/Agent-Framework-Samples](https://github.com/microsoft/Agent-Framework-Samples)
  (MIT, 395 ★), plus workshop and conference repos. A global `agent-framework in:name stars:>500`
  search returns no Microsoft canonical repo either. **Treat MAF as unavailable, not
  unverified.** Verified fallbacks: Semantic Kernel (MIT, 28,790 ★) for the Microsoft stack —
  noting that vendor material describes Semantic Kernel as *folding into* MAF, so the
  Microsoft agent story has no verifiable canonical repository at all right now. For a
  client who needs a Microsoft-shaped answer today, `agent-framework-go` is real and MIT
  but is 686 stars and language-specific.
- **No LATAM-origin agent framework of any scale exists** — re-measured this pass, and the
  number moved slightly. The largest LATAM-origin agent repository found is
  [whitebeardit/agents-team-crafter](https://github.com/whitebeardit/agents-team-crafter)
  (38 ★, **NOASSERTION — no usable license**, last pushed 2026-06-23, Portuguese: *"Cria
  time de agentes de IA por empresas e permite execução e isolamento entre os workspaces"*).
  Last pass measured "one repo, 0 stars"; it is now one repo, 38 stars, still unlicensed and
  five months stale. Also located this pass: the **`latam-gpt` GitHub organisation** (8 public
  repos, Chile/CENIA-led Latam-GPT initiative) — see `intel/market.md` LATAM. Both are
  recorded because an unlicensed repo is a *measured* dead end, not an unexplored one.
- **Star count has decoupled from enterprise suitability — a caveat on this file's own
  rankings.** The GitHub top-40 by stars now contains single-author skill collections:
  [mattpocock/skills](https://github.com/mattpocock/skills) (MIT, 328,581 ★),
  [obra/superpowers](https://github.com/obra/superpowers) (MIT, 322,580 ★) and
  [affaan-m/ECC](https://github.com/affaan-m/ECC) (MIT, 307,599 ★) are each more starred
  than every framework in Tier 1 combined, and each is one person's repository — no CLA,
  no organisational security response, no release governance. Worse for procurement, the
  two largest *unlicensed* repos in the category are enormous:
  [anthropics/skills](https://github.com/anthropics/skills) (**197,931 ★, no `LICENSE`
  file — checked `main` and `master` against five filenames**) and
  [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
  (**234,677 ★, no `LICENSE` file**, last pushed 2026-04-20). **Implication: stars tell you
  what engineers install, not what Globant may ship.** Rank Tier 1 by license and
  governance; use stars only to know what a client's developers have already pulled in.

---

## Tier 2 — Data agents: the one agent category every enterprise asks for first

**Added sixth pass, 2026-11-20.** Five passes of this file catalogued harnesses, frameworks,
UI surfaces and governance, and never once catalogued the agent an enterprise actually asks for
in the first meeting: *"let us ask our data a question in English."* That agent has its own
category, its own failure mode and its own licence trap, and none of the three were in this KB.

Every row's licence below was established by **reading the repository's own licence file or
package manifest** over `raw.githubusercontent.com`, not from a badge — and in two of the six
cases the badge or the vendor's own marketing page was wrong. Star counts read from the
repository page on 2026-11-20.

| Agent | Repo | Licence (how established) | ★ | Origin | What it is |
|-------|------|---------------------------|---|--------|------------|
| **WrenAI** | [Canner/WrenAI](https://github.com/Canner/WrenAI) | **Apache-2.0 for every code path** — read the `LICENSE` path map; `docs/**` is CC-BY-4.0 | 18.4k | APAC (Canner, Taiwan) | Text-to-SQL agent with its own semantic/modelling layer and an MCP interface. The most complete open implementation of the pattern in this table. |
| **MindsDB** | [mindsdb/mindsdb](https://github.com/mindsdb/mindsdb) | **MIT** — sidebar and README agree | 39.9k | North America | "The unified workspace where open-source models get things done for you": federates many data sources behind one query surface an agent can use. Most-starred repo in this category by a wide margin. |
| **DB-GPT** | [eosphoros-ai/DB-GPT](https://github.com/eosphoros-ai/DB-GPT) | **MIT** | 20.3k | APAC (China) | "Open-source agentic AI data assistant" — agent framework specialised to the database/BI task rather than a general harness pointed at a warehouse. |
| **XiYan-SQL** | [XGenerationLab/XiYan-SQL](https://github.com/XGenerationLab/XiYan-SQL) | **Apache-2.0** | 1.0k | APAC (China) | Multi-generator ensemble for NL-to-SQL. Self-reported **75.63% EX on BIRD test** and 89.65% on Spider test. Small star count, serious benchmark work — use it as the *technique* reference, not the platform. |

**And one archived repository, recorded because its MIT code is still being copied:**

| Repo | Licence | ★ | Status |
|------|---------|---|--------|
| [vanna-ai/vanna](https://github.com/vanna-ai/vanna) | MIT | 23.8k | **ARCHIVED by the owner on 29 March 2026 — read-only.** |

**Four live agents and one corpse, and that is the honest count.** Vanna is the second
most-starred project in this category and it has been read-only for nearly eight months. This
is the *same shape* as the fifth pass's finding one layer over (three archived chat-UI
repositories whose READMEs did not say so): **in the agent ecosystem, star count survives
death.** A client who searched "open source text to SQL" and sorted by stars has a one-in-two
chance of landing on an archived project. Checking `archived` status is now a standing item
in this KB's method, not an incidental observation.

### The failure mode this category has, stated before the recipe

Text-to-SQL does not fail gradually at enterprise scale — it falls off a cliff, and the cliff
is **schema width**:

- A 2025 study, cited through vendor secondary sources, measures **GPT-4o at 86% execution
  accuracy on academic benchmarks and 6% on enterprise databases with more than 1,000
  columns.** Not degraded — collapsed.
- A **dbt Labs benchmark (April 2026)** measures the repair: routing the question through a
  semantic layer moved Claude Sonnet 4.6 from **90.0% to 98.2%** and GPT-5.3-Codex from
  **84.1% to 100%**. **Read the sample before quoting it: 11 questions against one modelled
  project, run by a semantic-layer vendor.** Directionally consistent with the schema-width
  finding; not a general-purpose accuracy claim, and this KB will not present it as one.
- **Gartner (February 2026), cited secondhand:** by 2028, **60% of agentic analytics projects
  relying solely on MCP will fail** without a consistent semantic layer.

**The engineering conclusion, which is the whole point of this tier:** the agent in this
category is not the deliverable. The **semantic layer underneath it** is the deliverable, and
the agent is the interface onto it. That inverts the usual sales conversation and it is
defensible with the three numbers above. Components in `repos/foundations.md`; the build is
`compose/patterns.md` **Receta 14**.

> **Relationship to what this KB already had.** `compose/patterns.md` Receta 8 step 3 already
> said *"fix the semantics before the reasoning"* and pointed at
> [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology). That advice was right and is
> unchanged. What was missing was everything needed to *act* on it — and, separately, a
> non-NVIDIA option, since `intel/market.md` flags vendor concentration as a live risk in the
> governance layer. Cube, MetricFlow and Malloy are that option.

---

## Tier 1 addition — Google ADK, the framework this KB had missed for eight passes (added eighth pass, 2026-11-21)

A knowledge base holding 234 distinct repository addresses held **three of the four**
hyperscaler agent frameworks. Microsoft's, OpenAI's and the Anthropic-adjacent harness
layer were all present and tiered; Google's was absent entirely. Not excluded on
licence, not rejected on maturity — never found, because this KB's discovery queries
are shaped like *problems* and a general-purpose framework answers no single problem.

All four rows verified live on 2026-11-21 (`git ls-remote`), licence byte-read from
each repository's own `LICENSE`.

| Agente | Repo | Licencia | Stars | Último push | Qué aporta |
|---|---|---|---|---|---|
| Google ADK (Python) | [google/adk-python](https://github.com/google/adk-python) | Apache-2.0 (11,357 B) | 22,295 ★ | 2026-11-21 | The reference implementation of **A2A**, the protocol this KB already tracked through [a2aproject/a2a](https://github.com/a2aproject/a2a) without holding its primary consumer. Pushed on the day of this pass. |
| Google ADK (Go) | [google/adk-go](https://github.com/google/adk-go) | Apache-2.0 (11,340 B) | 8,992 ★ | 2026-11-20 | Single static binary. The option when the agent must be deployed into an estate that will not host a Python runtime. |
| Google ADK (Java) | [google/adk-java](https://github.com/google/adk-java) | Apache-2.0 (11,357 B) | 1,778 ★ | 2026-11-20 | The JVM-native choice beside `agentscope-java` and `camel-langchain4j-agent`. Directly relevant to **Receta 6** (APAC enterprise core). |
| ADK community extensions | [google/adk-python-community](https://github.com/google/adk-python-community) | Apache-2.0 | 188 ★ | 2026-11-20 | Held separately from the supported core — the same supported/community split Microsoft uses with `agent-framework-samples`. Read the boundary before quoting support. |

**How to position it.** The honest line to a client is that the three permissive
hyperscaler frameworks are now close enough in capability that **the choice is a
runtime and an ecosystem decision, not a capability one**: Python/Go/Java coverage,
which protocol the client has already committed to (A2A vs MCP-only), and whose
support contract they can buy. This KB's trend 9 holds — the unit of adoption is the
harness, not the framework — so none of these four should be sold as the centrepiece
of an engagement.

## Tier 1 addition — the durable agent (added eighth pass, 2026-11-21)

Relevant specifically because this pass's theme is **writes**. An agent that only reads
can be restarted at will. An agent that was halfway through posting a journal entry
cannot.

| Agente | Repo | Licencia | Stars | Último push | Qué aporta |
|---|---|---|---|---|---|
| Dapr Agents | [dapr/dapr-agents](https://github.com/dapr/dapr-agents) | Apache-2.0 (11,356 B) | 778 ★ | 2026-11-12 | `DurableAgent` runs as a Dapr Workflow instance and each agent is an actor; every LLM and tool interaction is persisted to a durable state store, so an interrupted write resumes instead of restarting. Child-workflow composition for fixed multi-agent patterns, runtime discovery for dynamic ones. |

**The detail that matters more than the framework**: Dapr Workflow gained **versioning
in v1.17 (February 2026)** — running instances keep replaying against the code they
started on, while new instances use the updated code. Deploying mid-transaction is a
routine event in an enterprise, and without versioning a replay against changed code
is how a durable workflow corrupts the thing it was protecting.

**Attribution note:** the v1.0-GA date (March 2026) and the claim that Diagrid ships
durable-workflow integrations for LangGraph, Microsoft Agent Framework, OpenAI Agents
SDK and Pydantic AI come from **vendor sources** (Diagrid's own blog). The repository,
its licence and its last push are verified; the GA date is attributed, not verified.

## Rename — every roundup still cites the old owner (added eighth pass, 2026-11-21)

| Cited as | Canonical today | Evidence |
|---|---|---|
| `princeton-nlp/SWE-agent` | [SWE-agent/SWE-agent](https://github.com/SWE-agent/SWE-agent) | 20,845 ★, MIT (1,146 B, byte-read), pushed 2026-11-16. The old path still redirects, which is why the roundups never notice. Sibling: [SWE-agent/mini-swe-agent](https://github.com/SWE-agent/mini-swe-agent), 9,925 ★, MIT — the stripped-down version, genuinely useful as a *readable* answer when a client asks what an agent loop is. |

## Gap re-measured this pass — LATAM-origin enterprise agents, with the short instrument

**Still zero, and now measured properly.** The fleet's standing concern (recorded in
`rotation.json` as open item 15-R2) is that prior LATAM zeros were measured with
long English queries, which do not discriminate. This pass ran the **short Spanish**
instrument — `agentes IA empresa código abierto github 2026`.

What came back: Spanish-language *articles about global repositories* — Peruvian,
Italian and Spanish blogs ranking OpenCode, Codex, Gemini CLI, OpenHands, Dify and
Langflow. **Not one LATAM-origin enterprise agent repository.** The Spanish-language
layer of this ecosystem is commentary and translation, not supply.

So the zero is now a **measured zero rather than an unmeasured silence**, and it is the
second independent measurement. The LATAM-origin repositories this KB *does* hold
remain the localisation and data-quality layers — `oca/l10n-argentina`,
`oca/l10n-brazil`, `oca/l10n-chile`, `oca/l10n-mexico`, `resilient-tech/india-compliance`
(APAC, for contrast) and the `latam-gpt/*` data-preparation tools. **That is the shape
of LATAM supply: regulatory and linguistic fitness, not agent runtimes.** Sell it that
way — it is a real and defensible differentiator, and it is not a framework.

## Rename, re-owner and namespace collision — the agent security scanner (added ninth pass, 2026-11-24)

The eighth pass opened a rename ledger because roundups keep citing dead owners. This pass found a
worse case in the same shape: not just a move, but **a change of owner, licence posture and business
model at once**, on the tool that the "agent skill supply chain" section above tells a client to run.

| Cited as | Canonical today | Evidence (verified 2026-11-24) |
|---|---|---|
| `invariantlabs-ai/mcp-scan` | [snyk/agent-scan](https://github.com/snyk/agent-scan) | Both paths return the **identical HEAD sha `a8561271`** via `git ls-remote`, so GitHub serves the old address as an alias of the moved repo — the old URL is not broken, it is just no longer the name. 3,300 ★, Apache-2.0, last commit 2026-11-23. Description is now "Security scanner for AI agents, MCP servers **and agent skills**". |
| `mcp-scan` on PyPI | [`snyk-agent-scan`](https://pypi.org/project/snyk-agent-scan/) | PyPI `mcp-scan` 0.4.3 summary: *"This package has been renamed to snyk-agent-scan. This is a redirect package…"*, `requires_dist: ['snyk-agent-scan']`. `snyk-agent-scan` is at 0.7.0, Apache-2.0, 46 releases. |
| `mcp-scan` on npm | **A different project entirely** | npm `mcp-scan` 2.3.0 is MIT, maintainer `rodolfboctor`, repo [Abanoub-Rodolf/mcp-scan](https://github.com/Abanoub-Rodolf/mcp-scan) — unrelated to Snyk/Invariant. `snyk/agent-scan`'s README states **"there is no npm package."** |

### Why this belongs in the agents file and not only in the repos file

**The same five-character command name resolves to two unrelated vendors' software depending on which
package manager a developer types it into.** `uvx mcp-scan` lands on Snyk's Apache-2.0 tool through a
redirect; `npx mcp-scan` lands on an individual's MIT tool. Neither is malicious on the evidence here,
and the npm project is a real project — but a KB that recommends "run mcp-scan" without naming the
ecosystem is **specifying an install by a string that two registries disagree about.** Name the
registry and pin the version in every deliverable: `uvx snyk-agent-scan@<version>`.

### Two properties to quote before a client adopts it

1. **It is permissively licensed and still metered.** `SNYK_TOKEN` must be exported *before* either
   install path will scan; v0.5.x drives a dated analysis API (`2025-09-02`) and is **planned for
   deprecation**. Free-tier scans stop at a daily limit. For an air-gapped or egress-restricted
   estate — which is the EMEA sovereignty case in `intel/market.md` — assume this tool **does not run**
   until proven otherwise, because the analysis is not local.
2. **Scanning untrusted MCP config is itself a privileged act.** From the README: to retrieve tool
   descriptions it **starts stdio MCP servers by executing the commands in the config** and connects to
   remote MCP URLs **with their configured headers** (i.e. the client's own credentials). It refuses
   link-local and cloud-metadata destinations (`169.254.0.0/16`, `fe80::/10`, `fd00:ec2::254`,
   `100.100.100.200`), does not follow redirects, validates DNS before each request — and then says
   plainly that **re-resolution at connection time leaves a DNS-rebinding window.** Run it in a
   disposable sandbox, and never pass `--dangerously-run-mcp-servers` outside one.

**The credit belongs to the project**: a security tool that documents its own residual
vulnerability is behaving better than one that does not. Quote the mitigation *and* the gap.

---

## The containment layer — no agents in it, and one component *inside* the agent (added tenth pass, 2026-11-24)

**For the fifth consecutive pass, no agent row above changed, and that remains the finding.** This
pass searched by the question a client's platform team asks after the security team is satisfied —
*what can this thing reach, and what stops it?* — and the sixteen repositories it verified are
**fifteen infrastructure components and one agent-resident guardrail.** Tables are in
`repos/foundations.md`; the build is Receta 20; the trend is 23.

### The one row that belongs in this file

| Agent-resident component | Licence | ★ | Last push | What it does at the agent's decision point |
|---|---|---|---|---|
| [falcosecurity/prempti](https://github.com/falcosecurity/prempti) | Apache-2.0 | 234 | 2026-09-21 | Registers on the agent's **hook API**; a hook fires **before** each tool call, the event crosses a Unix socket to a broker embedded in a **Falco plugin**, and the rule engine returns **allow / deny / ask** to the agent. `guardrails` mode enforces, `monitor` mode logs. **Claude Code** (Linux/macOS/Windows), **Codex** (experimental, Linux only). **"Experimental Preview" per its own README, and ~2 months idle — a pattern to implement, not a dependency to ship** |

Everything else this KB holds enforces policy on a request the agent has **already formed** — at a
gateway, an admission controller, an authz engine or a network boundary. This is the first verified
component that sees the **intent**, and it is the reason the layer earns a row here at all.

### Why the other fifteen are not agents, stated so nobody looks for them here

The containment layer is kernels, proxies, policy engines and CRDs: `kubernetes-sigs/agent-sandbox`
(the SIG Apps **orchestrator**, Apache-2.0, 4,703 ★, past `v1.0.2`), `google/gvisor`,
`firecracker-microvm/firecracker`, `kata-containers/kata-containers`, `dagger/container-use`,
`cilium/cilium`, `cilium/tetragon`, `istio/istio`, `linkerd/linkerd2`, `envoyproxy/gateway`,
`mitmproxy/mitmproxy`, `falcosecurity/falco`, `kyverno/kyverno`,
`open-policy-agent/gatekeeper`, `aquasecurity/tracee` — plus three reference architectures
(`microsoft/agent-governance-toolkit`, `agentgateway/agentgateway`, `Azure/kars`).

### External confirmation of this file's inventory — the first of its kind

[Azure/kars](https://github.com/Azure/kars) (MIT, 46 ★) lists **eight supported agent runtimes**:
**OpenClaw**, **Hermes** (Nous Research), OpenAI Agents SDK, Microsoft Agent Framework, LangGraph,
Claude Agent SDK and Pydantic-AI. **All eight are already in the tiers above.** Nine passes have
added to this inventory; this is the first time an independent architecture has *reproduced* it and
added nothing. Read that as a maturity signal for Tier 0/Tier 1 — and as a reason to spend the next
pass's effort anywhere but here.

### What to tell an engagement lead

The agent choice above is settled enough that an outside team reaches the same shortlist. **The
unsettled, billable, client-specific decision is which four containment controls wrap it** — and
the one repo that implements all four has 46 stars and `v1alpha1` CRDs. Quote the architecture, not
the repository.
