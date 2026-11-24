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

## The agent layer on the forge this KB had never searched (added eleventh pass, 2026-11-24)

**Why these rows are here and were not here yesterday.** Every one of the 314 repository addresses
this KB held before this pass was on `github.com`. That was never a decision — it was an unmeasured
habit, and this pass measured it. The rows below are the **agent-layer** projects found on the one
alternative forge reachable from this session. They are smaller than the GitHub rows above and they
are listed separately for that reason: this is a **completeness** correction, not a change to the
shortlist. Nothing here displaces OpenClaw, LangGraph, CrewAI or the Microsoft/Google/OpenAI
frameworks.

All verified 2026-11-24 via the GitLab projects API with `?license=true`, which returns licence,
default branch, stars and last activity in one call.

| Agent / component | Repo | Licence | Stars | Last activity | What it does |
|---|---|---|---|---|---|
| gitlab-mcp | [fforster/gitlab-mcp](https://gitlab.com/fforster/gitlab-mcp) | **MIT** | **85** | 2026-11-24 | An MCP server for GitLab. The most-starred permissive agent component found off GitHub, and pushed the day it was found. |
| gitlab-opencode | [nagyv/gitlab-opencode](https://gitlab.com/nagyv/gitlab-opencode) | **MIT** | 59 | 2026-09-17 | Runs any LLM in GitLab CI *"with a controlled environment"* — a single call with explicit **tool permissions**. Containment applied to the pipeline instead of the pod. |
| rmcp-openapi | [lx-industries/rmcp-openapi](https://gitlab.com/lx-industries/rmcp-openapi) | **MIT** | 13 | 2026-11-24 | Turns **OpenAPI endpoints into MCP tools** on the official Rust MCP SDK. The client's existing API surface becomes the agent's tool surface with no new service to write. |
| rmcp-actix-web | [lx-industries/rmcp-actix-web](https://gitlab.com/lx-industries/rmcp-actix-web) | **MIT** | 6 | 2026-11-23 | An `actix-web` transport backend for the same official Rust SDK. Pairs with the row above. |
| openblob | [lx-industries/openblob](https://gitlab.com/lx-industries/openblob) | **MIT** | 4 | 2026-11-24 | *"Distributed agentic workloads, no one in charge, everything under control."* Early-stage; recorded because it is genuinely agentic **and** permissive. |
| agentic-productivity | [gitlab-org/ai-engineering/agent-foundations/agentic-productivity](https://gitlab.com/gitlab-org/ai-engineering/agent-foundations/agentic-productivity) | **MIT** | 6 | 2026-10-01 | GitLab's own AI engineering org publishing *"agentic configs, skills, agents and workflows"*. Value is the **configuration**, not the code. |

**Six real rows. Six is what was found, and it is the whole of what was found** — there is no
seventh row because a seventh permissive agent project was not there to list.

### The two that look like rows and are not

- **[gitlab-org/ai/lazy-mcp](https://gitlab.com/gitlab-org/ai/lazy-mcp)** — 20★, pushed
  2026-11-08, **no licence file in the repository root**, confirmed by listing the tree rather than
  trusting an empty API field. GitLab Inc.'s own MCP project cannot be proposed to a client.
  **No licence is not permissive**, and this is the second time in the fleet that a well-starred,
  institution-owned project failed on this exact point.
- **[gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph)** —
  *"Software lifecycle context graph for AI agents"*, 58★, active 2026-11-24, **GitLab Enterprise
  Edition licence**, byte-read from `LICENSE.md`. Production use requires paid seats. It is the most
  capable agent-context product found this pass and it is the one that cannot be built on. Full
  detail in `repos/foundations.md`.

### What to tell an engagement lead

**The shortlist did not move; the map did.** For the sixth consecutive pass no agent row in the
tables above changed, and that stability is now a finding in its own right rather than an absence of
news. What changed is that the KB can now say *why* it believes its own shortlist is complete, and
can name the boundary of that belief: **one forge measured, one forge reachable, seven forges
refused at the network layer and therefore unmeasured.**

The two rows worth a client conversation this week are **`rmcp-openapi`** — because every enterprise
client already owns an OpenAPI catalogue and this converts it into agent tools without writing a
service — and **`gitlab-opencode`**, because CI is the one place in the estate where an agent already
has credentials, and almost nobody has scoped its tool permissions.

---

## Twelfth pass, 2026-11-24 — the licence posture of every row above is incomplete, and here is the missing half

**No agent row changed this pass, for the seventh consecutive pass.** What changed is a column that
was never there. Every licence in the tables above describes **the agent's code**. None of them
describes **the weights the agent loads at runtime** — and those are a separate artefact under a
separate licence, which this KB had never measured.

> **The one-sentence version for a client conversation:** *"CrewAI is MIT. That tells you nothing
> about whether you may use the model it calls."*

### The rule, measured this pass on four model families

`repo_license` and `weights_license` are **independent facts**, and they diverged in **two of the
four** families probed — in **opposite** directions:

| Family | The code repo's `LICENSE` | The weights | Error if you trust the badge |
|---|---|---|---|
| Gemma | **Apache-2.0** (11,358 B) | Gemma Terms of Use (**and currently unresolved** — see below) | **False positive** |
| Qwen3 | **absent** — 404 at `main` and `master` | **Apache-2.0** per `README.md:397` | **False negative** |
| Llama | root `LICENSE` = **78 bytes, a bare URL** | Llama Community License, per model | Scanner reports `NOASSERTION` |
| OLMo | **Apache-2.0** (11,359 B) | **Apache-2.0** | none |

### The clause that decides an EMEA engagement is not in the licence

`meta-llama/llama-models` → `models/llama4/USE_POLICY.md:71`, read 2026-11-24, withdraws the
**Section 1(a)** rights for **multimodal Llama 4** from *"an individual domiciled in, or a company
with a principal place of business in, the European Union"* — while expressly **not** reaching the
**end users** of a product incorporating such a model. `grep -c 'European Union'` over the licence
files of Llama 4, 3.3, 3.2 and 3.1 returns **zero** every time.

**So the question that gates a multimodal Llama 4 pilot for a European client is not technical and
not even really a licence question — it is "which entity is the licensee?"** Ask it in week one.

### The weights to pair with the agents above, licence verified

| Model | Weights licence | Pair it when |
|---|---|---|
| **Qwen3** (`QwenLM/Qwen3`) | **Apache-2.0** (vendor README) | You want frontier-class capability under a permissive licence and can accept a Chinese-origin base model |
| **OLMo** (`allenai/OLMo`) | **Apache-2.0** | The client needs openness that survives scrutiny of the *training data*, not just the weights |
| **Salamandra** (`langtech-bsc/salamandra`) | **Apache-2.0** | EMEA, sovereignty-constrained, and legal wants a licence they can read once and sign |
| **NVIDIA Cosmos** (`NVIDIA/Cosmos`) | **OpenMDW-1.1** | Fine — but warn the client their SPDX tooling will emit `NOASSERTION`, because the licence has no SPDX ID yet |
| **Llama 4 multimodal** | Llama 4 Community License **+ AUP** | Only after the EU-domicile question above has a written answer |
| **Gemma** | **Unresolved this pass** | Not this week. `ai.google.dev` does not resolve from this session; have legal read the terms page |

### What to tell an engagement lead

The agent shortlist is stable and the stability is real. **The new work is one gate, not one tool:**
before any pilot, resolve the weights licence as its own artefact — base model, then fine-tune, then
the acceptable-use policy — and record it next to the agent's licence. That gate is **Receta 23** in
`compose/patterns.md`, it is four permissive components, and it closes the gap that an MIT badge on
the orchestrator has been hiding for eleven passes.

---

## The erasure boundary — the fifth layer, and the one with almost nothing agent-shaped in it (added thirteenth pass, 2026-11-24)

**Why this section exists in the agents file.** Four of the five boundaries this KB now tracks
produced at least one agent. This one produced, measured rather than asserted, **almost nothing** —
and an engagement lead needs to know that *before* promising a client "an agent that handles
deletion requests."

### The measurement, reproducible in four lines

```
gh api search/repositories  q='DSAR agent stars:>50'                      → total_count 0
gh api search/repositories  q='GDPR erasure agent stars:>50'              → total_count 0
gh api search/repositories  q='data subject request automation stars:>50' → total_count 0
gh api search/repositories  q='privacy request agent LLM stars:>50'       → total_count 1
```

Three hard zeros and one hit. For comparison, the same instrument returns hundreds of rows for the
agent-framework queries at the top of this file. **The erasure boundary is a layer of components,
policy and application code — not a layer you can buy an agent for.**

### The one row, and it is a proxy rather than an agent

| Repo | Licence (byte-read 2026-11-24) | Stars | Last push | Why it belongs here |
|---|---|---|---|---|
| [crp4222/PrivAiTe](https://github.com/crp4222/PrivAiTe) | **BSD-3-Clause** (`LICENSE` at `main`, *"Copyright (c) 2025, CRP4222"*) | 70 | 2026-11-22 | Self-hosted **PII redaction proxy for LLM APIs and agent CLIs**. Scrubs names, emails and secrets from OpenAI-compatible traffic **including tool-call arguments**, then restores them in the reply. Local detection, no telemetry |

**Why this small repository is worth a row when this KB's rule is to prefer fewer real rows.** It
sits exactly where Tier 0 of this file has no control. The harness layer — the agent CLIs this KB
records as the unit of enterprise adoption — sends **tool-call arguments** to a model provider, and
every guardrail this KB holds inspects prompts and responses rather than tool arguments. A
redaction proxy at that boundary is the cheapest thing that keeps personal data out of a third
party's logs, which is the one copy you can never cascade a delete into.

**Quote it honestly:** created 2026-05-07, 70 stars, single-maintainer. This is a **pattern to
adopt or reimplement**, not a vendor to depend on. The permissive licence is what makes
reimplementation cheap.

### What is *not* an agent in this layer, stated so nobody looks for one here

- **Privacy-request orchestration** (`ethyca/fides`) is a workflow engine — **and it is archived**.
- **De-identification** (`data-privacy-stack/presidio`, already held since the fourth pass) is a
  library of recognisers.
- **Differential privacy** (`opendp/opendp`, `google/differential-privacy`) is a set of
  mathematical primitives.
- **Unlearning** (`OPTML-Group/Unlearn-Sparse`, `locuslab/tofu`) is research code, two-digit stars,
  and the TOFU benchmark has been **idle 21 months**.

Full tables, licences and the deletion-cascade model in `repos/foundations.md` → *The erasure
boundary*. The build is Receta 25; the log-retention conflict that constrains it is Receta 26.

### What to tell an engagement lead

> There is no agent to install for this, and the best-known open-source platform for it was
> archived in August 2026. What we sell here is **the cascade and the evidence**: a measured map of
> the seven places a fact comes to rest, the code that removes it from each, and a report that
> proves it is gone. The three regions that just acquired dated obligations — California's 45-day
> deletion poll, India's registered consent managers, Chile's law in force on 1 December 2026 —
> make this a compliance deadline rather than a hygiene project.

## The accessibility boundary — three real agent rows, and a licence that is not the one on the badge (added fourteenth pass, 2026-11-24)

> Theme: **can the people the client is legally required to serve actually use the agent, and can
> an agent test that.** Measured before searching, across all nine files of this KB:
> `wcag` = 0, `accessib` = 0, `a11y` = 0, `EN 301 549` = 0, `VPAT` = 0, `axe-core` = 0.
> A clean zero in every file — the fourth layer this rotation has found with no coverage at all.
>
> This pass could **not** use the GitHub API (`api.github.com` → 403, as in every pass since the
> ninth). Licences below are **byte-reads** of each repository's `LICENSE` file over
> `raw.githubusercontent.com`, which is stronger evidence than a badge; star counts are from
> github.com HTML read through WebFetch (curl gets 403 there, WebFetch does not); versions and
> publish dates are from `registry.npmjs.org`. All three channels were new or re-proved this pass.

### The rows that are agents (3 verified — not 5, and the reason is stated)

An accessibility *scanner* is not an agent. What belongs in this file is the MCP server that hands
an agent the ability to audit, read the findings, edit the code and re-audit. There are exactly
three credible community ones, and the ranking by stars is the **inverse** of the ranking by
maintenance:

| Agent / MCP server | Repo | Licence (byte-read) | ★ | npm latest | Engine pinned | Verdict |
|---|---|---|---|---|---|---|
| mcp-accessibility-scanner | https://github.com/JustasMonkev/mcp-accessibility-scanner | MIT | 59 | `mcp-accessibility-scanner` 5.0.1, **2026-11-16** | `axe-core` 4.14.0 (2026-10-05), `playwright` 1.65.1 | **Use this one.** WCAG 2.0/2.1/2.2 at A/AA/AAA, Playwright crawl, keyboard-nav checks, JSON reports |
| a11y-mcp (priyankark) | https://github.com/priyankark/a11y-mcp | **MPL-2.0** | 53 | `a11y-mcp` 1.1.1, 2026-10-26 | `axe-core` ^4.14.0, `puppeteer` ^25.16.0 | Audit → fix → re-audit loop. **Only one of the three that publishes to npm with provenance** and runs weekly Dependabot |
| a11y-mcp-server (a11ymcp) | https://github.com/ronantakizawa/a11ymcp | MIT | 97 | `a11y-mcp-server` 1.1.0, **2026-03-01** | `axe-core` ^4.6.0, **`puppeteer` 13.5.0 — published 2022-03-07** | **Do not put in client CI.** Most-starred, stalest, and pins a browser four and a half years old (current puppeteer is 25.18.1, 2026-11-17) |

None of the three is archived. All three state, or are, unofficial: `a11ymcp`'s own README says it
"is not an official Deque Labs server".

### The licence finding, and it is the headline of this pass

**The permissive badge on this layer belongs to the wrapper, not to the engine.** Proved by reading
`package.json` in each repository, not by reading marketing:

| Tool | Its own licence | `axe-core` in its dependencies? |
|---|---|---|
| `microsoft/accessibility-insights-web` | MIT | **yes** — `axe-core` 4.11.3 |
| `GoogleChrome/lighthouse` | Apache-2.0 | **yes** — `axe-core` 4.14.1 |
| `JustasMonkev/mcp-accessibility-scanner` | MIT | **yes** — `axe-core` 4.14.0 |
| `ronantakizawa/a11ymcp` | MIT | **yes** — `axe-core` ^4.6.0 |
| `priyankark/a11y-mcp` | MPL-2.0 | **yes** — `axe-core` ^4.14.0 |
| `IBMa/equal-access` | **Apache-2.0** | **no — zero axe dependencies, own engine** |

`dequelabs/axe-core` is **MPL-2.0** (byte-read of `LICENSE`, and `MPL-2.0` as the SPDX field of
4.14.1 on npm, published 2026-11-16). MPL-2.0 is **file-level** copyleft: it ships beside
proprietary code without infecting it, so this is not a blocker — but it is **not** in the
MIT/Apache/BSD bucket this file is built on, modifications to axe's own files must be published,
and it must appear in the client's open-source review. **"MIT" on the tool does not mean MIT in the
artifact.** The only way to stay inside the permissive bucket end-to-end is IBM's engine.

### What to tell an engagement lead

- Ask which bucket the client's OSS review allows **before** choosing the scanner. If weak copyleft
  in the shipped artifact is barred, the answer is `IBMa/equal-access` (Apache-2.0, 788★, own
  engine) and nothing else in this layer.
- An automated scan is **not** a conformance claim. Automated rules cover part of WCAG; keyboard
  and screen-reader flows have to be tested by a person or by a driven screen reader
  (`repos/foundations.md`, this pass).
- Do not sell the US deadline that was in every 2026 roundup: **it moved** (see `intel/market.md`,
  North America, this pass).

## La capa del consumo — tres filas reales y un cero medido (added fifteenth pass, 2026-11-24)

> **Tema del pase: el límite del consumo** — lo que el agente **gasta** y lo que hay que
> **declarar** sobre ese gasto. Medido antes de buscar, en los nueve archivos y en los dos idiomas:
> `carbon` 0, `kWh` 0, `emisión` 0, `CSRD` 0, `codecarbon` 0, `consumo` 0. Cero limpio.

**Este es el cuarto pase consecutivo que encuentra una capa sin agentes dentro.** Lo que existe son
**sondas y librerías** (Kepler, Scaphandre, CodeCarbon, Zeus — todas en `repos/foundations.md`), no
agentes. Lo específicamente *agéntico* es minúsculo y hay que presentarlo como lo que es: tres repos
de **una cifra de estrellas**, verificados hoy, que se citan porque **existen y están activos**, no
porque estén maduros.

| Repo | Licencia | ★ | Último push | Qué hace de verdad |
|---|---|---|---|---|
| [mlco2/agentic-footprint](https://github.com/mlco2/agentic-footprint) | MIT | 8 | 2026-11-23 | Rust. De la organización que mantiene CodeCarbon (1951★): huella específica de flujos agénticos. El único con una organización seria detrás |
| [VeiledTee/agent-energy-profiler](https://github.com/VeiledTee/agent-energy-profiler) | MIT | 0 | 2026-10-24 | Python. Perfila energía **por operación** en un flujo multi-paso y —lo valioso— **separa lo medido de lo estimado** |
| [Enterprise-DNA-OS/carbon-accounting-for-claude-code](https://github.com/Enterprise-DNA-OS/carbon-accounting-for-claude-code) | MIT | 0 | 2026-10-18 | Contabilidad de carbono de sesiones de agente de código sobre Postgres. Interesante como *forma*, no como dependencia |

### Por qué estas filas llevan 0★ y se publican igual

Porque la alternativa honesta era dejar la sección vacía, y el hueco **es** el hallazgo: la
atribución de consumo **por tarea de agente** no tiene producto. Un agente no es un proceso: un
*prompt* se expande en N llamadas al modelo, M invocaciones de herramienta y los reintentos, y
ninguna de las sondas maduras sabe sumar eso a una unidad de negocio. Lo que sí hay, y es lo que se
le propone a un cliente hoy, es **composición**: Kepler atribuye por *pod*, el *gateway* del plano de
control (ya en esta KB, `Receta 9`) atribuye *tokens* por clave virtual, y el puente entre ambos se
construye. Está en `compose/patterns.md`, **Receta 28**.

### El dato que convierte esto en un problema de agentes y no de infraestructura

Una fuente de analistas (nivel snippet, sin acceso al primario desde esta sesión) sostiene que la IA
agéntica consume **entre 5 y 30 veces más *tokens* por tarea** que un intercambio único de chatbot.
No se adopta la cifra; se registra con su atribución. Pero fija la dirección: **el agente es el
multiplicador del consumo**, y por eso este límite aparece *ahora* y no cuando la unidad era el
chatbot.

### El proyecto de referencia de la capa está **archivado** — décimo primer caso de esta KB

`Breakend/experiment-impact-tracker` — **MIT, 293★, último push 2024-01-30, `archived=true`**. Sigue
apareciendo en listados de herramientas de huella de ML. Es el **undécimo** proyecto
archivado-pero-recomendado que registra esta KB, y confirma otra vez el patrón del pase ocho: **los
once llegaron por documentación adyacente al proyecto, no por el repo**. Comprobar `archived` antes
de citar sigue siendo barato y sigue pagando.

### Y uno sin licencia, que es distinto de archivado

`ml-energy/leaderboard` — **sin archivo de licencia** (la API devuelve `NONE`), 14★, push
2026-09-23. Es el *leaderboard* de energía de la gente de `ml-energy/zeus` (Apache-2.0, 390★): el
**motor es permisivo y el *leaderboard* no declara nada**. Misma lección que el pase catorce dejó con
el *wrapper* y el motor, en el sentido contrario: **la licencia no se hereda dentro de una
organización, ni hacia arriba ni hacia abajo.** Use Zeus; no reempaquete el *leaderboard*.

---

## The language boundary — three real agent rows, and the metric that would reject the best of them (added sixteenth pass, 2026-11-24)

> **Theme: what the agent *says*, in which language, and who approved that wording.** Measured
> before searching across all nine files: 28 of 30 terms for this layer at a clean zero
> (`weblate` 0 · `tolgee` 0 · `messageformat` 0 · `glossary` 0 · `terminolog` 0 · `XLIFF` 0 ·
> `sacrebleu` 0 · `COMET` 0 …). The full measurement and the whole component substrate are in
> `repos/foundations.md` → *The language boundary*. This file carries only what is **agent-shaped**.

### The rows that are agents (3 verified — not 5, and the reason is stated)

| Agent | Licence (verified) | Stars | Last push | What it does | Verdict |
|---|---|---|---|---|---|
| [lingodotdev/lingo.dev](https://github.com/lingodotdev/lingo.dev) | **Apache-2.0** — byte-read from **`LICENSE.md`** | 5,397★ | **2026-11-20** | Localisation-engineering agent: extracts strings, translates, opens a PR with the result. Config takes **your own model** (`model: "anthropic/claude-sonnet-4.5"`), so the translating step is BYO-key and self-hostable | ✅ **The one adoptable row.** Permissive, active, and the only agent here that fits a CI pipeline |
| [andrewyng/translation-agent](https://github.com/andrewyng/translation-agent) | **MIT** | 5,817★ | **2024-08-04** | The reflection workflow in three steps: translate → have the model critique its own translation → apply the critique | ⚠️ **A pattern, not a dependency.** Two years without a push. Copy the three-step loop; do not `pip install` it |
| [SakuraLLM/SakuraLLM](https://github.com/SakuraLLM/SakuraLLM) | **GPL-3.0** | 4,865★ | 2026-07-23 | JP→ZH translation LLM, APAC-origin | ❌ **Recorded, not recommended.** GPL-3.0, and its domain is light novels and Galgame, not enterprise prose. Listed so an APAC star-count search does not surface it as a finding |

### Why this is three rows and not five, stated so nobody looks for the other two

The language boundary is **overwhelmingly a component layer, not an agent layer** — the fourth time
in this KB a boundary has turned out that way (containment, erasure and consumption were the
others). The things that do the work here are a **TMS** where a human approves wording
(`mozilla/pontoon`, BSD-3-Clause), a **message format** (`unicode-org/message-format-wg`), an
**engine** (`CTranslate2`, MIT), an **evaluator** (`Unbabel/COMET`, Apache-2.0) and a
**language detector** (`pemistahl/lingua-py`, Apache-2.0). None of those is an agent, and padding
this table with them would have produced five rows that no engagement lead could act on. They are
all in `repos/foundations.md` under their own layer headings.

### The strongest agentic result in this layer is a paper, not a repo — recorded as such

**AIDAterm** (ACL 2026, Industry Track) is a **four-agent pipeline** — Analysis → Translation →
Post-editing → Review — for terminology-constrained translation. Its reported result is
**99.4% average terminology accuracy on the WMT25 Terminology Translation benchmark**, which its
authors state **outperformed all 20 systems submitted** to that shared task. The design choices
that matter for anyone rebuilding it: terminology-aware **pre-analysis**, **explicit glossary
injection at every stage** rather than once at the start, and a **reasoning-enabled Review agent**
as the last hop.

⚠️ **No repository was found for it in this pass**, so it is recorded as a **reproducible design**,
not an inventory row. It is the architecture behind Receta 30 in `compose/patterns.md`.

### The finding that should change the acceptance criteria, from the row's own README

`andrewyng/translation-agent` reports, about itself:

> *"even on documents where our agentic workflow captures **context and terminology better**,
> resulting in translations that **our human raters prefer** over current commercial offerings,
> evaluation at the sentence level (using the FLORES dataset) resulted in the agentic system
> **scoring lower on BLEU**."*

**BLEU can move opposite to human preference on exactly the agentic pipelines this KB recommends.**
A statement of work with "BLEU ≥ X" as its acceptance test can therefore **reject the better
pipeline and accept the worse one**. Rank with **COMET** or a reference-free QE model, keep
**sacreBLEU** only as a reproducible regression tripwire, and put **document-level human review on
the terms that carry legal weight**. Note also that **FLORES**, the benchmark in that sentence,
is `facebookresearch/flores` — **770★ and archived since 2023-11-20**.

### The licence trap an engagement lead must know before quoting this layer

**Tolgee** — the developer-friendly TMS an aggregator in this pass described as *"self-hosting is
fully open-source"* — fences its enterprise features into `ee/` under the **Tolgee EE License
version 1**: *"non-commercial purposes only"*, plus no hosted/managed service and no circumventing
the licence key. Its root `LICENSE` is a multi-licence declaration that says so in its third line.
This is the **onyx pattern from the seventh pass repeated exactly**. Byte-level evidence and four
further traps are in `repos/foundations.md`.

### What to tell an engagement lead

1. **There is one adoptable agent here: `lingo.dev`** (Apache-2.0, BYO model). Everything else in
   this layer is a component or a pattern.
2. **The architecture to propose is AIDAterm's**, not a single translation call: glossary injected
   at every stage, with a review agent last. 99.4% terminology accuracy is the published bar.
3. **Do not accept a BLEU threshold as the acceptance criterion.** It is the one metric this
   layer's own evidence says can invert.
4. **The language duty is regional and legally binding, not a nice-to-have** — Quebec's French UI
   rule, the EU AI Act's Art. 50 disclosure, India's 22-language notice duty and Brazil's new
   human-service decree are in `intel/market.md` under their own regions.
5. **This layer is where "the agent works" and "the agent is lawful here" diverge.** A pipeline that
   passes every test in English can be unshippable in Quebec and non-compliant in India.

---

## Decimoséptimo pase — 2026-11-24 — el límite del documento fiscal: 4 filas, y un cero que vale más que las cuatro

> **Tema: lo que el agente puede *emitir en nombre del Estado*.** El pase buscó agentes en la capa
> de factura electrónica / documento fiscal y el resultado tiene dos mitades, las dos útiles.

**El cero, medido y explícito.** No existe —al menos no apareció en la búsqueda de este pase— **un
agente open source específico de cuentas por pagar o de facturación electrónica**. Lo que existe en
esa casilla es **comercial**: Basware InvoiceAI y su *Supplier Agent* (feb-2026), la compra de
Rossum por Coupa (may-2026), Tipalti, Stampli, Vic.ai, AppZen, Ramp.
⚠️ *Secundario: listados de proveedores a nivel de snippet de búsqueda.*
**La lectura correcta no es «falta producto», es «la frontera está en otro sitio»:** en este plano lo
abierto son **las primitivas de cumplimiento** (formato, validador, transporte, firma) y el agente
es la parte que se construye. Para Globant eso es mejor noticia que lo contrario.

**La regla de diseño que impone este plano, y es dura:** *el agente no puede ser el emisor.* La
*guideline* v4.8 de MyInvois (ago-2026) exige la **firma digital del emisor o de su proveedor de
servicios**; en India la ventana de reporte al IRP es de **30 días** desde la fecha del documento
para AATO ≥ ₹10 crore, de modo que **un agente que encola y reintenta puede invalidar el documento
de forma permanente**; y en los regímenes de autorización previa de LATAM un reintento no es
idempotente: **puede crear un segundo documento fiscal.** El agente propone, valida y arma el
expediente; **la emisión la firma un humano o un servicio acreditado.**
⚠️ *Las tres obligaciones son de fuente secundaria (snippet), señaladas también en `intel/market.md`.*

### Filas nuevas (4, verificadas 2026-11-24)

| Agente / herramienta | Repo | Licencia (verificada) | ★ | Push | Por qué está en la capa de agentes |
|---|---|---|---|---|---|
| **mcp-myinvois** | [techtemplemy/mcp-myinvois](https://github.com/techtemplemy/mcp-myinvois) | **WTFPL** — ⚠️ **clase nº 15 en esta KB, y es un problema de política corporativa** | 3 | 2026-09-05 | **Servidor MCP + ficheros `SKILL.md`** para el régimen e-Invoice de Malasia: alta de credenciales, alta de empresa/cliente, envío y entrega. *Sandbox por defecto*; se declara **no oficial** y deja la responsabilidad fiscal en el usuario |
| **Lycet** | [giansalex/lycet](https://github.com/giansalex/lycet) | **MIT** | 106 | 2026-11-10 | Convierte Greenter (PHP, SUNAT 🇵🇪) en **API REST**: es la forma de dar a un agente una herramienta fiscal **determinista y acotada** en lugar de acceso a la librería |
| **einvoice-validate** | [einvoice-validator/einvoice-validator](https://github.com/einvoice-validator/einvoice-validator) | **código MIT**; binario distribuido `MIT AND EUPL-1.2 AND LicenseRef-OASIS… AND LicenseRef-UN-CEFACT… AND W3C-19980720` | 1 | 2026-11-23 | **La puerta de validación que el agente llama, no juzga.** CLI de salida determinista (`einvoice-validate factura.xml`), 5 005 casos de corpus, `rules fetch` para reglas nacionales. **No tiene superficie MCP** (comprobado: 0 coincidencias) — se invoca como proceso |
| **invoice2data** | [invoice-x/invoice2data](https://github.com/invoice-x/invoice2data) | **MIT** | 2 254 | **2026-11-24** | La capa de **extracción** previa al documento estructurado: plantillas sobre PDF/texto/imagen. Es la parte que el modelo mejora, no la que decide validez |

**Nota de licencia sobre la fila 1.** WTFPL es permisiva en intención pero **no trae renuncia de
garantía ni concesión de patentes**, no está certificada por OSI y **varias políticas corporativas
de ingesta la rechazan de plano**. Con 3★ y un régimen fiscal detrás, la recomendación honesta es:
**leerlo como documentación ejecutable del flujo MyInvois** (sus `SKILL.md` describen el camino
completo del portal `hasil.gov.my`) y **no** importarlo como dependencia.

### Qué no cambió, y por qué es la respuesta correcta

Ninguna fila de los *tiers* anteriores se movió. El patrón que el cuarto pase registró —buscar por
**consecuencia** devuelve capas, no agentes— se repite aquí por sexta vez: de las **46 direcciones**
verificadas en este pase (**42 nuevas** para la KB), **4** entran en este archivo y las demás en `repos/foundations.md` y
`verticals/solutions.md`. En un plano donde la validez la decide un tercero, **lo escaso no es la
inteligencia: es la prueba.**

## El límite del calendario — una fila real, un cero medido y la cadena de cinco eslabones (added eighteenth pass, 2026-11-24)

> Tema: **cuándo vence algo, en la hora de quién y en los días laborables de quién.** El pase
> diecisiete encontró **plazos** —India, **30 días** al IRP; las fechas de KSeF; los catálogos CFDI
> 2026— y este pase preguntó si la KB podía **contarlos**. Medido antes de buscar, sobre los nueve
> archivos: `tzdata` **0** · `IANA` **0** · `ISO 8601` **0** · `calendario` **0** · `día hábil` **0** ·
> `business day` **0** · `business hours` **0** · `festivo` **0** · `cron` **0** · `RFC 5545` **0** ·
> `rrule` **0** · `CalDAV` **0** · `day count` **0** · `30/360` **0** · `holiday` **1** · `DST` **1**.
> **La KB tenía los vencimientos y no tenía el calendario.**

### La única fila con forma de agente en toda la capa

| Nombre | Repo | Licencia | Versión | Qué hace |
|---|---|---|---|---|
| mcp-server-time | [modelcontextprotocol/servers → `src/time`](https://github.com/modelcontextprotocol/servers/tree/main/src/time) | **MIT** — `pyproject.toml`: `license = { text = "MIT" }`, leído por bytes | **`2026.11.18`** (seis días), `mcp>=2.3,<3` | Servidor **MCP** de referencia: `get_current_time`, `convert_time` y `get_time_ago`, con nombres de zona **IANA** y detección de la zona del sistema. |

**Una sola fila, y se publica así a propósito.** Es la séptima vez que esta KB registra el mismo
patrón —buscar por **consecuencia** devuelve **capas**, no agentes—: de las **34 direcciones**
verificadas este pase (**29 nuevas**), **1** entra en este archivo y las otras **33** en
`repos/foundations.md` y `verticals/solutions.md`.

### Las dos frases de su README que deciden una integración, citadas

1. «*The offset is elapsed time, counted back from the current instant, so across a daylight-saving
   change "a day ago" is exactly 24 hours ago and its wall-clock reading can differ from now by an
   hour.*» → **«hace un día» son 24 horas, no «ayer a esta hora».** El servidor de referencia
   **documenta la elección** porque son dos respuestas distintas, y un agente que resume «lo que pasó
   en las últimas 24 horas» cruzando un cambio de horario devuelve una ventana desplazada una hora.
2. «*A timezone name … must be an exact IANA key, case included: `Europe/Warsaw` is accepted and
   `europe/warsaw` is rejected on every platform, including macOS, whose case-insensitive filesystem
   would otherwise resolve it.*» → **un LLM que normaliza a minúsculas recibe un error**, y el
   rechazo es deliberadamente **igual en los tres sistemas operativos** para que no haya un bug que
   solo aparece en producción. `get_time_ago` además **rechaza** fracciones, cadenas numéricas y
   booleanos, que es exactamente lo que un modelo emite cuando le piden «dos horas y media».

### Lo que NO es un agente en esta capa, dicho para que nadie lo busque aquí

Las **33 direcciones** restantes son **datos y bibliotecas**: la base horaria (`eggert/tz`,
`python/tzdata`), los datos de locale (`unicode-org/cldr`, `unicode-org/icu`), los datos de festivos
(`vacanza/holidays`, `commenthol/date-holidays`, `nager/Nager.Date`, los dos `jollyday`,
`workalendar`), la aritmética (`date-fns`, `luxon`, `moment-timezone`, `pendulum`, `arrow`,
`dateutil`, `nodatime`, `joda-time`, `HowardHinnant/date`), la norma y la recurrencia
(`tc39/proposal-temporal`, `temporal-polyfill`, `jkbrzt/rrule`, `ical4j`, `sabre-io/vobject`), la
convención de día hábil (`QuantLib`) y las aplicaciones de calendario (`rallly`, `Radicale`,
`easyappointments`, `nextcloud/calendar`). **No hay ningún agente de agenda open source con licencia
permisiva en esta capa**, y conviene decirlo antes de que un *engagement* lo presuponga.

### El dato que convierte esto en un problema de agentes y no de infraestructura

**Un agente no calcula el tiempo: lo hereda de una cadena de cinco eslabones**, y cada uno tiene su
propia versión y su propio calendario de releases:

```
ley o decreto  →  tzdb (eggert/tz)  →  CLDR / ICU  →  runtime del lenguaje  →  el agente
```

En 2026 el segundo eslabón **envió a propósito datos que contradicen el primero** para acomodar al
tercero. Está escrito en el `NEWS` de `eggert/tz`: cuatro jurisdicciones canadienses —Columbia
Británica (legal **2026-03-09**), Alberta (**2026-06-18**), Territorios del Noroeste
(**2026-08-21**) y Manitoba (**2026-10-31**)— se modelaron **todas el 2026-11-01 a las 02:00**,
porque «*This temporary hack works around limitations in Unicode CLDR and ICU*». El detalle completo,
con releases y números de versión, está en `repos/foundations.md` y en `intel/trends.md` (tendencia
37). **Lo que importa para este archivo: ninguno de los agentes de los *tiers* anteriores sabe en qué
versión de tzdata, CLDR o ICU se está ejecutando, y ninguno lo declara.**

### Qué decirle a un lead de engagement

1. **La capa de agenda no se compra, se compone.** Hay **una** fila agéntica (MIT, de referencia) y
   treinta y tres bibliotecas. Quien prometa «un agente que gestiona el calendario» está prometiendo
   integración, no adopción.
2. **Pregunte por versiones, no por features.** `tzdata`, CLDR e ICU de la imagen de contenedor, y el
   `zic` con que se compiló. Si la respuesta es «la del sistema», no hay respuesta.
3. **Un agente que solo compara instantes está a salvo.** Los mantenedores de tzdb lo delimitan:
   «*It does not affect UT offsets, and affects abbreviations and tm_isdst flags only*». Los que
   muestran la abreviatura de zona o ramifican sobre `isdst` **no** lo están.
4. **El festivo no es un dato técnico, es un acto legislativo.** `workalendar` (**MIT**, 946★) lleva
   **inactivo desde 2024-04-12** sin estar archivado: una biblioteca de festivos sin mantenimiento no
   es código viejo, es **código incorrecto**.

## El límite del sistema heredado — seven real agent rows, and the asymmetry that decides which estate an agent can reach at all (added nineteenth pass, 2026-11-24)

**Why this layer was invisible for eighteen passes.** This KB holds 524 distinct
repositories. Before this pass, these probes over all eight files returned **zero
files**: `cobol`, `jcl`, `abap`, `as400`, `iseries`, `odata`, `idoc`, `openrewrite`,
`zowe`, `galasa`, `joern`, `ast-grep`, `tree-sitter`, `abaplint`, `abapgit`,
`mainframe` (1 incidental mention). Every previous pass searched with a vocabulary of
*new* things — frameworks, gateways, guardrails, authz, OSCAL, observability. None
searched with the vocabulary of the thing the client actually runs. An enterprise
engagement does not start at an agent framework; it starts at a system of record that
predates every repository in this file.

**The finding that organises the rest of this section.** Agent reachability of a legacy
estate is decided by **whether that estate already exposes a remote API** — not by its
age, not by its language, not by how much money it moves. Measured on 2026-11-24 with
`gh api -X GET search/repositories`:

| Legacy estate | Pre-existing remote API | Agent-access repos found | Top star count |
|---|---|---|---|
| SAP ABAP (ECC / S/4HANA) | ADT (ABAP Development Tools) over HTTP | 4 independent MCP servers, all MIT/Apache-2.0 | 215★ |
| IBM i / Db2 for i | Mapepire (socket server) | 1 MCP server, MIT | 30★ |
| IBM Z / z/OS | Zowe REST (z/OSMF) | 1 MCP server, EPL-2.0 | 25★ |

SAP's estate is the *oldest* and the *most closed* commercially, and it has the richest
open agent layer, because ADT gave it an HTTP surface years before anyone wanted an
agent. z/OS has the deepest estate and the thinnest agent layer. **Do not price a
mainframe engagement and a SAP engagement off the same assumption about open tooling.**

### The rows — all verified 2026-11-24

Existence by `git ls-remote`, stars/licence/activity by `gh api search/repositories`,
every NOASSERTION resolved by byte-reading the licence file.

| Agente | Repo | Licencia | ★ | Último push | Qué hace, y el detalle que decide si sirve |
|---|---|---|---|---|---|
| Project Starforge (ex Legacy-Modernization-Agents) | https://github.com/Azure-Samples/Legacy-Modernization-Agents | MIT | 234 | 2026-11-22 | COBOL + copybooks + BMS + JCL → Java Quarkus/Spring **o** C# .NET, sobre Microsoft Agent Framework. **El detalle arquitectónico que importa más que el agente:** construye el grafo del estate (programas, transacciones CICS, tablas DB2) **determinísticamente desde el fuente, sin llamadas al modelo**, en Neo4j; el modelo solo interviene en la conversión. Su AST Explorer expone los *parse gaps*, y su propio README los califica de **riesgo de verificación**, no de prueba de que el modelo no vio la línea |
| mcp-abap-abap-adt-api | https://github.com/mario-andreschak/mcp-abap-abap-adt-api | MIT | 215 | 2026-09-16 | Servidor MCP que envuelve `abap-adt-api`: da al agente el estate ABAP del cliente por el mismo canal que usa Eclipse ADT. El repo más estrellado de toda esta capa — y lleva ~2 meses sin push |
| mcp-abap-adt | https://github.com/fr0ster/mcp-abap-adt | Apache-2.0 | 111 | 2026-11-24 | ABAP Cloud (BTP) **y** on-premise ECC/S/4HANA, **CRUD completo**, auth JWT/XSUAA y service-key. Activo hoy. **CRUD completo significa que esta fila cruza el límite de escritura del octavo pase: no la despliegues sin la puerta que allí se describe** |
| abap-mcp-server | https://github.com/marianfoo/abap-mcp-server | Apache-2.0 | 99 | 2026-11-20 | Servidor MCP para ABAP, mantenido activamente; sin descripción en el repo, leer el README antes de comprometerlo |
| ABAP MCP Server SDK | https://github.com/abap-ai/mcp | MIT | 88 | 2026-07-19 | No es un servidor: es el **SDK para escribir el servidor MCP dentro de ABAP**. Es la única fila de esta tabla que no requiere un proceso fuera del sistema SAP — relevante donde el cliente no autoriza un sidecar |
| mcp-server-db2i | https://github.com/Strom-Capital/mcp-server-db2i | MIT | 30 | 2026-11-23 | Db2 for i (IBM i, AS/400) **solo lectura**, cada persona entra **con su propio usuario IBM i**, con allowlist de bibliotecas y enmascarado de columnas. Es la realización más limpia que esta KB ha encontrado del límite de titularidad del séptimo pase: la autorización la resuelve el sistema heredado, no el agente |
| Zowe MCP Server | https://github.com/zowe/zowe-mcp | EPL-2.0 | 25 | 2026-11-24 | El **único** servidor MCP del lado z/OS encontrado en esta búsqueda. Activo hoy, y **EPL-2.0, no MIT ni Apache** — reciprocidad a nivel de archivo, ver la nota de licencias abajo |

Seven rows, all real, all with a verified licence and a measured activity date. Nothing
was padded to reach a round number.

### Lo que se midió y salió cero o casi cero

An informed gap is information; silence looks like coverage.

- **Agentes de migración COBOL:** la consulta `cobol modernization AI agent` ordenada por
  estrellas devuelve **un** proyecto con tracción (Starforge, 234★) y luego una cola de
  POCs de 8★ para abajo (`ltoscano/legacybridge-oss-cobol` 8★ y sin licencia declarada,
  último push 2025-08-08; y una decena de repos de hackathon de 0–1★). **No existe una
  segunda base agéntica de migración COBOL que se pueda componer.** La capa
  determinística (parsers, OpenRewrite, Zowe) está madura; la capa agéntica sobre ella
  está vacía salvo un sample de Microsoft.
- **JCL:** `jcl parser mainframe` → `natan-sysview/tree-sitter-jcl` (1★, MIT) y
  `msradam/fromjcl` (1★, Apache-2.0). Fuera del soporte de editor (che4z, vscode_cobol)
  **no hay cadena de herramientas JCL utilizable**. El JCL es donde vive el orden de
  ejecución del batch; es el agujero más caro de esta lista.
- **RPGLE:** `rpgle language server` → **0 resultados**. La respuesta en IBM i no es un
  LSP independiente sino `codefori/vscode-rpgle` (59★, MIT).
- **Natural / Adabas (Software AG):** `natural adabas software ag parser` → **0
  resultados**. Un estate Natural/Adabas no tiene capa abierta: es trabajo a medida.
- **`smojol`** (herramienta de análisis COBOL citada en documentación de IBM): **0
  resultados** en GitHub search con ese nombre. No se afirma que no exista; se afirma que
  **no se encontró con este instrumento**, y por tanto no entra en la tabla.
- **Repos de origen iberoamericano en esta capa:** `cobol modernizacion legado` → 0;
  `cobol analisis banco espanol` → 0; `mainframe modernizacao cobol` → 3 repos, **todos
  de 0★ y sin licencia declarada**. Es el mismo cero medido que el sexto pase registró en
  la capa de agentes, confirmado con un instrumento distinto y en el dominio donde LATAM
  tiene más estate heredado en producción (banca).

### Trampas de esta capa (todas verificadas, no inferidas)

1. **El cluster de forks que vence al upstream en el buscador.** Buscar en la web
   "COBOL to Java AI agent" devuelve **seis** repos con el mismo README por encima del
   original: `gkaleta/`, `shinya-ambient/`, `aplusdepseudo/`, `vjrithwik/`,
   `josh202310/`, `renehonig/Legacy-Modernization-Agents`. El upstream es
   `Azure-Samples/`. **Regla:** antes de componer cualquier repo encontrado por búsqueda
   web, correrlo por `gh api search/repositories -f q='repo:owner/name'` — ese endpoint
   **excluye forks por defecto**, así que un repo que resuelve con `git ls-remote` pero
   no aparece en la consulta `repo:` **es un fork**. Así se detectó el caso
   `clean-core/abap-cleaner` (ver `repos/foundations.md`).
2. **EPL-2.0 es la licencia de la capa abierta del mainframe, y no es permisiva.**
   `zowe/zowe-mcp`, `zowe/zowe-cli`, `galasa-dev/galasa` y el LSP COBOL de che4z son
   todos EPL-2.0: reciprocidad a nivel de **archivo** y cláusula de licencia secundaria
   compatible con GPL-2.0. Se puede construir alrededor; no se puede tratar como MIT en
   una propuesta. **El criterio "MIT / Apache / BSD" de esta KB no se puede cumplir en
   z/OS: hay que declarar EPL-2.0 explícitamente al cliente.**
3. **Un servidor MCP con CRUD completo es un agente de escritura disfrazado de
   integración.** `fr0ster/mcp-abap-adt` expone CRUD sobre objetos ABAP. El octavo pase
   ya estableció por qué los `ToolAnnotations` de MCP no sirven como control (son hints,
   y los defaults son destructive/non-idempotent). Aplica aquí sin descuento.

## El límite del ciclo de vida — cero filas de agente nuevas, y la primera clase `Agent` que esta KB encuentra dentro de un IdP (added twentieth pass, 2026-11-24)

> **Ninguna fila de Tier 0 ni Tier 1 cambió en este pase, y por quinta vez eso *es* el
> hallazgo.** Este pase buscó con el vocabulario del **alta y la baja** — SCIM, IGA,
> aprovisionamiento, identidades no humanas, huérfanas, RPO — y de los 24 repos verificados
> hoy **ninguno es un agente**. Son la capa que decide si el agente puede ser dado de baja.
> Tablas completas en `repos/foundations.md`; el build en `compose/patterns.md` Receta 38.
>
> Pero este pase sí trae algo que pertenece a *este* archivo y no a `foundations.md`: **la
> primera definición de "agente" que esta KB encuentra escrita dentro de un proveedor de
> identidad**, en código, con semántica de herencia de permisos. No es un framework de
> agentes. Es el modelo de datos con el que un IdP decide qué *es* un agente — y eso cambia
> lo que se puede prometer en un SOW.

### La clase `Agent` de authentik: qué dice el código (leído hoy de `main`)

`authentik/enterprise/agents/models.py`, licencia **EE** (no MIT):

```python
class Agent(Actor):
    @classmethod
    def create_for_user(cls, user, name="", expiring=False, expires=None,
                        policy_behavior=ActorPolicyInheritance.MIRROR) -> Agent:
        # An agent is a machine identity, not a login user: mark it as a service account
        # and disable password auth. It authenticates through its issued API token. By default
        # it MIRRORs its parent, so it can never exceed the access of the user it acts for.
```

Cuatro decisiones de diseño que conviene copiar, con licencia o sin ella:

1. **El agente es una cuenta de servicio, no un usuario que inicia sesión** —
   `type=UserTypes.SERVICE_ACCOUNT`, autenticación por token de API, contraseña deshabilitada.
2. **Todo agente tiene un humano padre** (`parent`), es decir un responsable nombrado. Es
   exactamente lo que piden tanto OWASP NHI1 como los tenets del NIST.
3. **Tiene caducidad de origen**: `expiring` / `expires` heredados de `ExpiringModel`.
4. **Hay un permiso de autoservicio** (`add_agent_self_service`): la organización puede dejar
   que cada persona cree sus propios agentes — que es precisamente cómo aparecen los agentes
   en la sombra, y por eso el inventario del punto A de `foundations.md` no es opcional.

### El triángulo de la herencia: MIRROR, COPY y NONE — y ninguno es gratis

`ActorPolicyInheritance` vive en `authentik/core/models.py`, que **sí es MIT**, con tres valores:

| Valor | Qué hace | Qué falla |
|---|---|---|
| `MIRROR` | Defiere al padre **en vivo**: el agente nunca excede el acceso del humano | Acopla los ciclos de vida. Si se revoca al humano, el agente se queda sin nada en el mismo instante — correcto para contención, **contrario** al tenet del NIST que pide ciclos de vida *separados* |
| `COPY` | **Instantánea** de las asignaciones directas del padre en el momento de la creación | Es el mecanismo de la huérfana. Y falla en **dos direcciones opuestas** (ver abajo) |
| `NONE` | No hereda nada | Hay que construir la autorización a mano; nada es implícito |

El docstring de `copy_parent_policy_bindings()` — también en la parte MIT — dice literalmente
por qué `COPY` falla dos veces:

> *"Unlike MIRROR (which defers to the parent live), COPY takes an independent snapshot at
> creation: the actor holds its own PolicyBindings, so later changes to the parent don't affect
> it. Only bindings that reference the parent as a \*user\* are copied — access the parent derives
> from group membership is not."*

- **Día 1, infra-aprovisionamiento silencioso:** el acceso que el humano tiene *por pertenencia a
  grupos* **no se copia**. El agente arranca sin permisos que su dueño sí tiene y nadie sabe por qué.
- **Día 100, sobre-aprovisionamiento silencioso:** las asignaciones directas quedan **congeladas**.
  Al humano se le revoca un acceso y **el agente lo conserva**.

**Y la línea que lo cierra, en `authentik/core/models.py` (MIT):**

```python
parent = models.ForeignKey(User, on_delete=models.SET_DEFAULT, default=None, null=True, ...)
```

`on_delete=SET_DEFAULT, default=None`: **al borrar al humano, el vínculo se pone a NULL y la fila
del agente sobrevive.** La identidad huérfana no es un descuido operativo — está en el esquema.
Borrar al que se va del IdP **no** borra sus agentes. Eso es OWASP **NHI1** demostrado en una
línea de un archivo con licencia MIT.

### Las dos herramientas de este pase que sí son "de agentes" (y no son agentes)

| Herramienta | Repo | Licencia | ★ | pushed | Qué hace |
|---|---|---|---|---|---|
| **Agent Discovery** | [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) → `agent-governance-python/agent-discovery/` | MIT | 6,603 | 2026-11-24 | Descubre agentes en la sombra por procesos, config y organización de GitHub; los inventaría con deduplicación y los **reconcilia contra el registro de gobierno**. CLI `agent-discovery scan -o json` |
| **Agent Discover Scanner** | [Defend-AI-Tech-Inc/agent-discover-scanner](https://github.com/Defend-AI-Tech-Inc/agent-discover-scanner) | MIT | 23 | 2026-07-28 | Detección en 5 capas (estático, red, eBPF/Kubernetes). **Dormido 4 meses y se autodescribe "industry-standard" con 23 estrellas**: tomar la técnica, no la dependencia |

> **Lo que esto le dice a un lead de engagement:** el agente sigue siendo la decisión más
> pequeña de la página (pases 3, 4, 5, 8). Lo nuevo es que ahora hay **una decisión de
> arquitectura con nombre** que hay que tomar en la semana 1 y escribir en un ADR:
> `MIRROR`, `COPY` o `NONE`. No es un detalle de configuración: decide si la baja del
> empleado da de baja al agente. Y la función que lo gestiona en authentik está detrás de una
> licencia cuyos términos **asignan al proveedor las modificaciones que escribas**.

## El límite de la voz — la primera capa de esta KB en la que el agente *habla*, y la licencia que ningún listado menciona (added twenty-first pass, 2026-11-24)

> Tema: **cuando el agente atiende el teléfono.** Veintiocho términos se midieron en cero antes
> de empezar — `livekit`, `pipecat`, `asterisk`, `freeswitch`, `jambonz`, `vocode`, `whisper`,
> `piper`, `coqui`, `kokoro`, `silero`, `speech`, `telephony`, `call centre`, `contact centre`,
> `TTS`, `SIP`, `WebRTC`, `diarization`, `barge-in`, `robocall`, `TCPA` — **ninguno aparecía en
> los ocho ficheros tras veinte pases.** Los únicos aciertos de `voice` eran subcadenas de
> **`invoice`**, heredadas del pase decimoséptimo. Veinte pases de frontera (lectura, escritura,
> procedencia, contención, forja, pesos, borrado, accesibilidad, huella, idioma, documento fiscal,
> calendario, heredado, ciclo de vida) y el canal por el que la mayoría de los clientes
> empresariales atiende a sus propios clientes **no estaba**.
>
> **Instrumento de este pase (y su límite, que es la mitad del hallazgo).** `api.github.com`,
> `gh api` y `curl` contra `github.com` están **denegados por el alcance de sesión** (HTTP 403 del
> proxy). Lo que **sí** funciona: `raw.githubusercontent.com` (200) para **leer el fichero
> `LICENSE` byte a byte**, `git ls-remote` para probar existencia y rama por defecto, y `WebFetch`
> sobre la página HTML de GitHub para estrellas / banner de archivado. `huggingface.co` está
> **rechazado por el proxy de egreso** (`connect_rejected`, 403), y eso importa más aquí que en
> cualquier pase anterior: **en voz, el entregable es el peso, no el código.** La licencia del
> código de las 47 filas de este pase es de primera mano; **la licencia de los pesos no lo es, y
> está marcada como tal en cada fila donde aplica.** Un peso que no se pudo leer no se afirma.

### Las filas reales de agente de voz (5 verificadas, licencia leída byte a byte el 2026-11-24)

| Framework | Repo | Licencia (leída de `LICENSE`) | ★ | Qué es |
|---|---|---|---|---|
| **Pipecat** | [pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat) | **BSD-2-Clause** | 17,400 | "Open Source framework for voice agents, multimodal apps, and realtime AI. Maintained by Daily and the community." El pipeline por composición: no asume transporte, se elige. v1.0 en abril de 2026 según fuente secundaria. La licencia **BSD-2-Clause es la primera de esta clase en la KB** — permisiva, sin cláusula de patentes (a diferencia de Apache-2.0) |
| **LiveKit Agents** | [livekit/agents](https://github.com/livekit/agents) | **Apache-2.0** | 15,300 | "A framework for building realtime voice AI agents." La opción con batería incluida: sabe sobre qué corre, porque el transporte es de la misma casa ([livekit/livekit](https://github.com/livekit/livekit), Apache-2.0, 22,400 ★, "End-to-end realtime stack for connecting humans and AI") |
| **Unmute** | [kyutai-labs/unmute](https://github.com/kyutai-labs/unmute) | **MIT** | n/m | El front-end full-duplex de Kyutai sobre Moshi: pone voz a un LLM de texto sin pasar por una API de voz propietaria |
| **Vocode** | [vocodedev/vocode-core](https://github.com/vocodedev/vocode-core) | **MIT** | 3,800 | "🤖 Build voice-based LLM agents. Modular + open source." **Sin banner de archivado el 2026-11-24.** Una fuente secundaria afirma que no tiene mantenedor activo; **esta KB no lo afirma, porque no se midió** — la regla del pase decimonoveno sobre espejos obsoletos aplica igual aquí |
| **OpenAI Realtime Agents** | [openai/openai-realtime-agents](https://github.com/openai/openai-realtime-agents) | **MIT** | n/m | Patrones de referencia de agentes de voz en tiempo real (handoff, supervisor). Útil como *forma*, no como dependencia: el runtime al que llama es de pago |

`n/m` = no medido. Las estrellas sólo se obtienen de la página HTML de una en una en esta sesión
(la API está denegada), así que se midieron donde deciden algo y se declaran sin medir donde no.

### Tier 2 — la trampa de licencia de este pase, y es la peor que esta KB ha encontrado para un estudio

| Framework | Repo | Lo que dicen los listados | Lo que dice el fichero `LICENSE` |
|---|---|---|---|
| **TEN Framework** | [TEN-framework/ten-framework](https://github.com/TEN-framework/ten-framework) (11,200 ★) | "Apache-2.0", "open-source framework for conversational voice AI agents" — en al menos tres comparativas de 2026, sin salvedad | **Apache-2.0 "with the following additional conditions"** (© 2025 Agora) |

Las condiciones, citadas textualmente del fichero:

> «You may not (i) host the TEN Framework or the Derivative Works on any **End User devices**,
> including but not limited to any **mobile terminal devices** or (ii) Deploy the TEN Framework in
> a way that competes with Agora's offerings and/or that allows others to compete with Agora's
> offerings, **including without limitation enabling any third party to develop or deploy
> Applications**.»
>
> «You may Deploy the TEN Framework **solely** to create and enable deployment of **your**
> Application(s) **solely for your benefit** and the benefit of your **direct** End Users.»

**Por qué esto es categóricamente distinto de las trampas anteriores de esta KB.** Dify, Camunda y
Mattermost restringen *revender el producto*. Esta cláusula restringe **el modelo de negocio de un
integrador**: un estudio que construye un agente de voz *para un cliente* está, en la letra de la
cláusula 1(ii), «enabling a third party to develop or deploy Applications», y la cláusula 2 limita
el despliegue a *tu propio* beneficio y a tus End Users **directos**. Y la cláusula 1(i) **prohíbe
el despliegue en dispositivos de usuario final, móviles incluidos** — es decir, prohíbe el caso de
uso de voz en el móvil, que es la mitad del mercado. **No es un marco sobre el que Globant pueda
construir trabajo de cliente.** Debe quedar en Tier 2 y debe decirse en la semana 0, no en la
revisión legal.

### El instrumento reutilizable que sale de aquí (vale para toda la flota, no sólo para voz)

**Cuando la barra lateral de GitHub muestra el enlace «License» *sin* nombre SPDX, eso es el
delator de una licencia modificada.** Medido en el mismo pase, con el mismo instrumento:

- `livekit/agents` → «Apache-2.0 license» (nombrada) → Apache-2.0 real, 11,356 B
- `pipecat-ai/pipecat` → «BSD-2-Clause» (nombrada) → BSD-2-Clause real, 1,300 B
- `TEN-framework/ten-framework` → **«License»**, sin tipo → Apache + restricciones, **2,234 B**

El tamaño en bytes es el segundo delator y es más rápido que leer: **Apache-2.0 íntegra pesa
~11,3 kB.** Un fichero que dice «Apache License» y pesa 2,2 kB no es Apache-2.0; es un preámbulo
propio seguido del aviso corto. Esta regla es **la inversa complementaria** de la regla de
`NOASSERTION` del sexto pase (allí la ausencia de veredicto escondía cuatro licencias
*permisivas*; aquí la ausencia de veredicto esconde una *restrictiva*). Juntas: **la ausencia de un
nombre SPDX no es información sobre la permisividad en ninguna dirección — obliga a leer, y hay que
leer en ambos sentidos.**

> **Vigesimosegundo pase, 2026-11-24 — ninguna fila de agente cambia, y esta vez el motivo es
> estructural, no una casualidad.** Este pase buscó por **de quién es el dato** (el agente
> multi-inquilino: el cliente de Globant no es el usuario final, sino un ISV, un banco con
> filiales o un grupo con operaciones por país) y encontró **una capa entera sin un solo agente
> dentro**: Kafka, Pulsar, NATS, AutoMQ, las claves de partición de Qdrant/Milvus, las
> Organizations de Keycloak y la RLS de Postgres. Diez repos verificados, cero agentes.
> **El aislamiento por inquilino no es una propiedad del agente: es una propiedad de todo lo que
> hay debajo de él** — y por eso ningún listado de «mejores agentes 2026» lo menciona.
> Un dato nuevo sí toca este fichero de lado: **LiteLLM** (MIT, ya en Tier 1) tiene una
> **jerarquía de cliente** explícita (`litellm/proxy/auth/customer_hierarchy_auth.py` y dos
> módulos más, 95 coincidencias de código) y un **gateway en Rust**, es decir, el presupuesto y la
> autenticación **por inquilino** ya están construidos en una pieza que esta KB tenía catalogada
> sólo como *control plane*.
> Tablas en `repos/foundations.md`; construcción en `compose/patterns.md` **Receta 44**.
> **Dos trampas de licencia de este pase que afectan a quien elija por marketing:**
> `p2-inc/keycloak-orgs` (la extensión de multi-tenencia de Keycloak más recomendada) es
> **Elastic License 2.0** — vino de AGPL-3.0, nunca pasó por permisiva — cuando el core
> Apache-2.0 de Keycloak **ya trae `OrganizationModel.java`**; y `redpanda-data/redpanda`
> (12,7k ★, API de Kafka) ship-ea **BSL 1.1 + Redpanda Community License** y su README nombra una
> **tercera** licencia cuyo texto no está en el repo. El sustituto permisivo verificado es
> **AutoMQ** (Apache-2.0 leído byte a byte, API de Kafka).

## El límite del remitente — en nombre de quién manda el agente, y qué lo prueba (added twenty-third pass, 2026-11-24)

> **Tema: el canal hermano del pase veintiuno.** El pase veintiuno dio a esta KB el agente que
> **habla**. Este pase pregunta por el agente que **escribe**, que es el canal por el que una
> empresa alcanza de verdad a un cliente o a un proveedor. **Medido en los nueve ficheros antes de
> buscar, sobre 19.436 líneas y 22 pases previos:** `DMARC` **0** · `DKIM` **0** · `SPF` **0** ·
> `ARC` **0** · `BIMI` **0** · `MTA-STS` **0** · `SMTP` **0** · `IMAP` **0** · `phishing` **0** ·
> `suplantación` **0** · `rebote`/`bounce` **0** · `unsubscribe` **0** · `buzón` **0** ·
> `correo electrónico` **0** · `remitente` **1** (y es de **voz**: la pre-declaración de CLI de
> TRAI) · `Gmail` **1** (un nombre de conector en una lista). **La KB sabía quién puede leer, quién
> puede escribir, quién puede hablar — y no sabía con qué dominio firma.**

### Las filas reales (4 verificadas el 2026-11-24, y el porqué de que no haya una quinta)

| Agente | Licencia **resuelta** · ★ · último push | Qué hace, y la advertencia |
|---|---|---|
| [Mail-0/Zero](https://github.com/Mail-0/Zero) | **MIT** (API) · 10.900 ★ · 2026-11-15 · `main` | Cliente de correo con IA, orientado a privacidad. **La única pieza agéntica permisiva de esta capa.** Es un cliente de buzón, no un emisor empresarial: sirve de base de producto, no de MTA. |
| [elie222/inbox-zero](https://github.com/elie222/inbox-zero) | `NOASSERTION` → **AGPL-3.0** (`LICENSE` **36.236 B**, texto íntegro de la AGPLv3 leído byte a byte) · 13.112 ★ · 2026-11-24 · `main` | El asistente de correo con IA más estrellado del ecosistema. **No es base proponible para un estudio**: la AGPL alcanza al servicio en red, que es exactamente la forma en que se entregaría. Catalogado para saber qué es y para poder decir *por qué no*. |
| [GongRzhe/Gmail-MCP-Server](https://github.com/GongRzhe/Gmail-MCP-Server) | **MIT** · 1.173 ★ · **último push 2025-08-06** · `main` | **ARCHIVADO** (`archived: true` en la API). Es el servidor MCP de Gmail **más recomendado de los listados de MCP**, y es la forma habitual de dar manos de buzón a un agente. **Decimosexto proyecto archivado-pero-recomendado de esta KB**, y el delator es el de siempre: lo recomienda la documentación adyacente al propio ecosistema. |
| [MarkusPfundstein/mcp-gsuite](https://github.com/MarkusPfundstein/mcp-gsuite) | **MIT** · 492 ★ · **último push 2025-04-14** · `main` | MCP sobre productos de Google Workspace. **No está archivado**, así que la forja lo muestra vivo: **19 meses sin un commit**. La alternativa al archivado anterior está, ella misma, parada. |

**No hay quinta fila y esto es el hallazgo, no una carencia del pase.** Se buscó agente de correo
empresarial permisivo —emisor, no cliente de buzón— y **no existe**: lo que hay es (a) dos
aplicaciones de buzón con IA, una MIT y una AGPL, (b) dos servidores MCP que son las *manos* del
agente, **uno archivado y el otro parado 19 meses**, y (c) una capa de **infraestructura de correo
sin un solo LLM dentro**, con 28 direcciones verificadas en `repos/foundations.md`.
**Es la misma forma que el pase veintidós encontró en la tenencia: una capa entera sin agentes.**
La consecuencia comercial es directa: **el remitente no se compra, se construye**, y se construye
sobre piezas permisivas que sí existen (Receta 46).

> **La trampa de licencia de este pase, y es la más usada del mundo.**
> [nodemailer/nodemailer](https://github.com/nodemailer/nodemailer) (**17.717 ★**), la biblioteca con
> la que envía correo medio ecosistema Node —y por tanto medio agente empresarial—, trae un `LICENSE`
> de **935 B** que es un **MIT truncado**: dice *«subject to the following conditions:»* y **no
> enumera ninguna condición**, salta directo al descargo de garantía. Por eso la API de GitHub
> responde `NOASSERTION`: el texto **no coincide ni con MIT ni con MIT-0**. La autoridad es el
> registro: `registry.npmjs.org/nodemailer/latest` → **v10.6.1, `license: "MIT-0"`**.
> **La diferencia práctica entre lo que dice el fichero y lo que declara el registro es si hay que
> atribuir o no**, y el fichero no puede contestarlo. **Clase de licencia nº 19 para esta KB
> (`MIT-0`, 0 apariciones en 22 pases).** Cuarta confirmación de la regla del pase dieciocho
> —el registro gana a la insignia— y **la extiende**: en `date-fns` el fichero *faltaba*; aquí el
> fichero **está y está roto**, que es el caso peor, porque invita a leerlo y confiar.

---

## El límite de la firma — qué hace que lo que el agente produjo se sostenga, y por qué un agente no puede firmar (added twenty-fourth pass, 2026-11-24)

> **Medido antes de buscar**, sobre **20.141 líneas** y los nueve ficheros de 23 pases previos:
> `eIDAS` **0** · `PAdES` **0** · `CAdES` **0** · `e-signature` **0** · `firma electrónica` **0** ·
> `qualified signature` **0** · `RFC 3161` **0** · `sello de tiempo` **0** · `no repudio` **0** ·
> `non-repudiation` **0** · `trust list`/`trusted list` **0** · `TSP` **0** ·
> `certificate authority` **0** · `C2PA` **0** · `RFC 9421` **0** · `Web Bot Auth` **0** ·
> `verifiable credential` **0** · `SD-JWT` **0** · `EUDI` **0** · `mDL` **0** · `pyHanko` **0** ·
> `EJBCA` **0** — y `XAdES` **2**, `DocuSign` **4**, `PKCS#11` **4**.
>
> El **pase noveno** dio a esta KB la firma de un **artefacto de build** (sigstore, SLSA, in-toto:
> 46, 54 y 44 apariciones). **Firmar un build no es sellar un documento**, y nada en 23 pases
> preguntó qué prueba que el contrato, la factura o el informe que el agente acaba de redactar
> **vale ante un juez o ante una administración**. El pase 17 le dio a esta KB el documento fiscal;
> el 23, el canal para enviarlo. **Lo que lo firma no se había hecho nunca.**
>
> ### EL HALLAZGO DEL PASE: UN AGENTE NO PUEDE **FIRMAR**; SÓLO PUEDE **SELLAR**
>
> El Reglamento (UE) 910/2014 separa dos actos que el castellano comercial mezcla y que ningún
> listado de herramientas distingue:
>
> | | **Firma** electrónica cualificada (QES) | **Sello** electrónico cualificado |
> |---|---|---|
> | Titular | **Persona física** | **Persona jurídica** |
> | Qué acredita | Origen, integridad **y voluntad** | Origen e integridad — **no voluntad** |
> | ¿Automatizable? | **No**: exige control exclusivo del firmante | **Sí**: es su caso de uso |
> | Base | Art. 25 y ss. | Arts. 35–40 |
>
> **Consecuencia de arquitectura, y es la que se factura:** el agente puede preparar, rellenar,
> enviar y **sellar**; la **firma** la pone una persona. Meter el certificado de firma de un humano
> dentro de una tubería automática **no es un atajo técnico: es una atribución falsa de voluntad**,
> y es exactamente el defecto que un abogado contrario busca primero. *(Nivel resumen: la
> distinción está en el Reglamento, pero las fuentes que la explican son blogs de proveedores con
> interés comercial; el articulado no se leyó en primario — ver el límite declarado abajo.)*

### Las filas reales de esta capa (4 agentes verificados el 2026-11-24; licencia leída byte a byte)

> Esta capa **sí tiene agentes**, al contrario que la tenencia (pase 22) y el remitente (pase 23),
> donde la medición dio cero o casi. Son cuatro, y **se reparten dos MIT y dos AGPL-3.0**.

| Agente | Licencia · último commit · rama | Por qué está aquí |
|---|---|---|
| [varops/signed-md](https://github.com/varops/signed-md) | **AGPL-3.0** (`LICENSE` **34.020 B**, byte a byte) · **2026-11-24** · `develop` | **El único de la capa cuyo diseño coincide con el reparto firma/sello del Reglamento**, y lo dice en su propio README (12.754 B, leído en primario): *«Your agents handle the paperwork. **People approve and sign**»*; *«Only a person approves a template, and an agent can only send the exact revision a person saw»*; y la frase que importa: *«**Guardrails the agent can't talk its way around. These live in the server, not in a prompt**»*. Plantillas en Markdown, **16 herramientas MCP** sobre Streamable HTTP, y *«there is no AI inside Signed.md itself»*. **AGPL-3.0 ⇒ no proponible como base de producto cerrado**, pero es el **plano de referencia** de cómo se pone la puerta humana. |
| [imagine-ai-inc/sign](https://github.com/imagine-ai-inc/sign) | **MIT** (`LICENSE` **1.072 B**) · 2026-11-16 · `main` | **La única pieza agéntica permisiva de la capa.** Firma estilo DocuSign con servidor MCP para que un agente cree, envíe y siga sobres. **Es la base proponible**, y es también la que **no trae puerta humana documentada**: hay que construirla (Receta 49). |
| [hanzoai/sign](https://github.com/hanzoai/sign) | **AGPL-3.0** (`LICENSE` **34.523 B**) · 2026-11-21 · `main` | Alternativa autoalojada a DocuSign. Catalogada para saber qué es y **por qué no**: misma AGPL, y sin capa agéntica visible en los resultados. |
| [signbee/skill](https://github.com/signbee/skill) | **MIT** (`LICENSE` **1.064 B**) · 2026-10-31 · `main` | **No es un servidor: es una *skill* de agente** para flujos de NDA y contrato. Importa como forma de entrega —el agente trae la habilidad, el servicio es de un tercero— y por eso **traslada el límite al proveedor**, no lo resuelve. |

### La pieza que firma lo que el agente **pide**, que es otro acto distinto

| Repo | Licencia · último commit | Qué es, y qué no es |
|---|---|---|
| [cloudflare/web-bot-auth](https://github.com/cloudflare/web-bot-auth) | **Apache-2.0** (`LICENSE` **11.346 B**) · **2026-11-24** · `main` | Implementación de referencia de **Web Bot Auth**: el agente firma **cada petición HTTP** con **RFC 9421** (Ed25519 por agente, cabecera `Signature-Agent`, directorio público en `/.well-known/http-message-signatures-directory`). **RFC 9421 sí es un RFC; Web Bot Auth NO lo es**: es un borrador IETF —grupo constituido a principios de 2026 y **sin documentos adoptados a agosto de 2026**—, así que un RFC es un acontecimiento de 2027 como muy pronto *(nivel resumen; el *datatracker* del IETF no es alcanzable desde esta sesión)*. **Establece identidad, no permiso** — el permiso es el pase 7. Visa **TAP** y Mastercard **Agent Pay** lo usan como capa de autenticación de agente *(secundario, atribuido a Cloudflare)*. |

### Las tres firmas que esta KB ahora sabe distinguir, y nombrarlas aparte es la aportación

1. **Firmar un *build*** → `sigstore`/`cosign`/`in-toto` (pase 9). Lo firma una **máquina de CI**, prueba **procedencia de software**.
2. **Firmar una *petición*** → **RFC 9421** / `web-bot-auth` (este pase). Lo firma el **agente**, prueba **quién llama**.
3. **Sellar un *documento*** → **eIDAS**, PAdES/CAdES/XAdES (este pase). Lo sella la **persona jurídica**, prueba **origen e integridad de un entregable**; la **voluntad** la aporta una persona física y no es delegable.

**Las tres usan criptografía de clave pública y las tres se llaman «firma» en una reunión.** Un
cliente que pide «que el agente firme» casi siempre quiere la 3 y le están vendiendo la 1 o la 2.

### Las trampas de este pase

- **[`Sphereon-Opensource/eidas-signature-client`](https://github.com/Sphereon-Opensource/eidas-signature-client) es la primera recomendación de la búsqueda y lleva 19 meses sin un commit** (último: **2024-04-09**), con **LGPL-3.0** (`LICENSE.md` 7.676 B). No está archivada, así que la forja la muestra viva. **Decimoséptimo proyecto parado-pero-recomendado de esta KB**, y el delator vuelve a ser el mismo: lo recomienda la documentación adyacente al propio ecosistema.
- **La organización `OpenICP-BR` entera está muerta desde 2018** y es el primer resultado para «assinatura digital ICP-Brasil open source»: `libICP` (AGPL-3.0, **2018-09-24**), `wxApp` (AGPL-3.0, **2018-07-11**) y `ktLib` (**sin fichero de licencia**, **2018-11-05**). **Decimoctavo caso**, y el más antiguo que esta KB ha medido.
- **Una dirección que inventé no existe:** `eu-digital-identity-wallet/eudi-srv-web-issuing-qeaa-py` devolvió fallo de autenticación en `ls-remote`, que es cómo se ve un 404 en esta sesión. **Se registra el 404 en lugar de borrarlo**, porque es la prueba de que el nombre se dedujo y no se verificó: de 45 direcciones probadas, **44 existen y 1 fue una conjetura mía**.

---

## Vigesimoquinto pase — 2026-11-24 — el límite de la contraparte: 7 filas reales, y la regla que invalida la fila más estrellada de la capa

> Tema: **a quién le paga, le vende o le compra el agente, y si le está permitido.** Veintiséis
> términos medidos **con límite de palabra** sobre las 20.810 líneas y 24 pases previos, y los
> veintiséis dieron **cero**: `sanctions screening`, `OFAC`, `SDN list`, `denied party`,
> `export control`, `dual-use`, `OpenSanctions`, `FollowTheMoney`, `yente`, `nomenklatura`,
> `watchman`, `beneficial ownership`, `BODS`, `GLEIF`, `KYB`, `restricted party`,
> `politically exposed`, `Entity List`, `MOFCOM`, `alephdata`, `openaleph`, `Archivematica`,
> `REUSE.toml`, `GNU Free Documentation`, `open-supply-hub`, `openownership`.
>
> **El pase séptimo dio el límite de la titularidad (para quién actúa el agente). El octavo, el
> límite de la escritura (qué puede cambiar). Este da el límite de la contraparte: *con quién*
> puede operar.** Es el primero de la serie que no está gobernado por la política interna del
> cliente sino por **listas de terceros que cambian varias veces por semana**.
>
> **Colisión de nombre, declarada para que nadie la confunda.** `counterparty` aparece 4 veces en
> esta KB desde el quinto pase, pero **en otro sentido**: ahí significaba la persona al otro lado
> de la pantalla (la capa de interacción). Aquí significa **la entidad comercial del otro lado de
> la transacción**. Son dos capas distintas y ninguna de las dos contiene a la otra.

### La razón por la que esta capa no se resuelve con una lista de nombres

**La regla del 50 % de OFAC:** una entidad participada en **50 % o más en agregado** por partes
sancionadas **está bloqueada aunque no figure en ninguna lista**. Es decir: el conjunto de
contrapartes prohibidas **es estrictamente mayor que la unión de todas las listas publicadas**, y
la diferencia sólo se puede calcular **sobre el grafo de titularidad**. Un `LEFT JOIN` contra la
SDN responde la pregunta equivocada.

Esto es lo que convierte la capa en un problema de datos y no de *lookup*, y lo que explica por
qué las filas de abajo son un modelo de datos (`followthemoney`), un resolutor de entidades
(`nomenklatura`) y un estándar de titularidad (`BODS`) — y no un cliente de API.

### Las filas que son agentes o servicios de decisión (7 verificadas, 2026-11-24)

| Repo | Licencia (leída del fichero) | ★ | Qué hace, y el detalle que decide la integración |
|---|---|---|---|
| [opensanctions/yente](https://github.com/opensanctions/yente) | MIT | 189 | API de *match-making* de entidades (buscar / recuperar / casar). Su propio README dice que **se puede correr on-premise como *KYC appliance***: el dato no sale del cliente. **Pero ver la trampa de licencia de abajo: el código MIT no te da los datos.** |
| [moov-io/watchman](https://github.com/moov-io/watchman) | Apache-2.0 | 527 | Servicio Go que **descarga y parsea** US CSL (incluye BIS Entity List), OFAC, EU CSL, UK CSL y FinCEN 311. Es la única fila de la capa que trae **las listas oficiales** sin licencia de datos de por medio. Fija una *tagged release*: el motor de búsqueda se rehízo en v0.50+ y las listas EU/UK se estaban reincorporando. |
| [opensanctions/nomenklatura](https://github.com/opensanctions/nomenklatura) | MIT | 274 | Resolución de entidades sobre FtM. **El detalle que importa:** su `Resolver` es un grafo cuyas aristas registran *igual / distinto / **sin decidir***, calcula componentes conexos y **infiere coincidencias transitivas**. El tercer estado es el que permite una cola de revisión humana en vez de un falso positivo. |
| [openaleph/openaleph](https://github.com/openaleph/openaleph) | MIT | 167 | Búsqueda sobre documentos no estructurados **y** datos estructurados, enlazando personas y empresas entre conjuntos, sobre el esquema FtM. Mantenido por **DARC**; es el sucesor declarado de Aleph. |
| [opensanctions/graph](https://github.com/opensanctions/graph) | MIT | — | Conjuntos de datos adyacentes convertidos a FtM, con catálogo JSON publicado. Es **el destino del puntero** de un repo archivado (ver trampa 5). |
| [opensanctions/qarin](https://github.com/opensanctions/qarin) | MIT | 18 | Proyecto de investigación **financiado por la UE (NGI Search)** sobre *calidad del casado de nombres* en herramientas de screening: marco de evaluación, datasets abiertos y, a futuro, algoritmos. **No es un producto** — es el único sitio de la capa donde el criterio de aceptación está siendo construido en abierto. |
| [opensanctions/yente-client](https://github.com/opensanctions/yente-client) | MIT | — | Librería cliente, SDK y CLI de yente. La fila aburrida que evita que cada engagement escriba el suyo. |

### La trampa de licencia de este pase, y es de tres capas, no de dos

`opensanctions/opensanctions` (884 ★) lleva **badge MIT**, y el badge es **cierto e insuficiente**.
Su `COPYRIGHT.md`, leído byte a byte, divide el repositorio en **tres**:

1. **Código — MIT.** Crawlers y configuración incluidos.
2. **Datos producidos por OpenSanctions — CC BY-NC 4.0.** Explícitamente **no** cubiertos por MIT.
   OpenSanctions **reclama derechos de base de datos** sobre la colección y **el uso comercial
   requiere licencia aparte** (de pantalla plana, de reventa, o la API por consulta).
3. **Material de terceros bajo `datasets/` — *ninguna licencia concedida*.** Son copias sin
   modificar de publicaciones ajenas, y el proyecto dice literalmente que **no mantiene un índice
   por fichero de cuáles son**.

**Por qué esto importa para un engagement y no es una nota al pie:** el punto 3 significa que
**no existe una comprobación programática** que separe lo redistribuible de lo que no lo es. Y el
punto 2 significa que **la arquitectura on-premise que el README de yente ofrece es legal sólo con
una licencia de datos de pantalla plana**. El código es gratis; **la capacidad de operar no**.

**La forma correcta de venderlo:** `moov-io/watchman` (Apache-2.0) para las listas oficiales de
gobierno, que no tienen dueño comercial; `yente` + datos licenciados cuando el cliente quiere
cobertura PEP/agregada. Son dos decisiones de compra, no una.

### La fila más estrellada de la capa está muerta, y **no tiene badge de archivado**

[alephdata/aleph](https://github.com/alephdata/aleph) — **2.500 ★, MIT, marcado «Public», sin
aviso de archivo** — declara en su propio README **`PROJECT STATUS: SUNSETTING`**, y que el
mantenimiento **terminó después de diciembre de 2025**: sin actualizaciones, sin arreglos de bugs
y sin soporte a partir del 31-12-2025. El equipo lo reescribió como **Aleph Pro**, de modelo
**comercial** (OCCRP mantiene uso gratuito para periodismo sin ánimo de lucro).

**Esto invierte la regla de detección que esta KB ha usado durante ocho pases.** Hasta ahora el
*tell* de un proyecto muerto era **la bandera `archived`**; aquí el proyecto con **2.500 ★ — nueve
veces las estrellas de su propio sucesor** — está vivo en la página y muerto en el README. La
regla nueva: **la bandera `archived` es suficiente pero no necesaria. Hay que leer la línea de
estado del README en los dos sentidos.** Cualquier *roundup* de 2026 que ordene esta capa por
estrellas va a recomendar Aleph.

**Qué usar en su lugar:** `openaleph/openaleph` (MIT, 167 ★, DARC), *soft fork* declarado y
compatible con el esquema FtM.

### Qué decirle a un lead de engagement

- **No se vende «screening».** Se vende **la diferencia entre la lista y el grafo** — la regla del
  50 % es la frase que abre la conversación con el comité de riesgo, y no requiere hablar de IA.
- **El agente propone, no decide.** El tercer estado de `nomenklatura` (*sin decidir*) es el
  entregable: una cola de revisión con trazabilidad, no un bloqueo automático. Un falso positivo
  en esta capa **congela un pago a un cliente legítimo**; un falso negativo es una sanción.
- **Dos presupuestos, no uno:** software (permisivo, Globant construye) y **datos** (licencia
  comercial de un tercero, el cliente firma). Confundirlos es la forma más rápida de que el
  proyecto muera en *procurement*.
