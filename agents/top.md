---
industry: enterprise
region: Global
updated: 2026-11-20
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
> **Third pass, 2026-11-20 (later still):** three large MIT repositories that belong in this
> file were found missing entirely — **deer-flow** (85,545 ★, APAC-origin harness),
> **browser-use** (121,597 ★) and **letta** (25,503 ★, stateful agents). Added below. The
> structural finding of this pass is in `repos/foundations.md`: the KB had no **control-plane**
> layer at all — no AI gateway, quotas, usage attribution, cost governance, red-teaming or
> OpenTelemetry instrumentation. Six sections were added there, and they change what this file
> means: picking an agent is now the *smallest* decision in an engagement.

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

## Tier 2 — Popular but license-restricted (use with care)

These are heavily used in the market, so the studio must be able to discuss them —
but they are **not** clean MIT/Apache, and that changes what Globant can ship.
Licenses below were read from each repo's `LICENSE` file, not from GitHub's badge.

| Agent | Repo | Real license | Stars | Commercial constraint |
|-------|------|--------------|-------|----------------------|
| n8n | [n8n-io/n8n](https://github.com/n8n-io/n8n) | Sustainable Use License ("fair-code") | 211,510 | Not OSI open source. Restricts hosting-as-a-service; non-`master` branches are explicitly unlicensed. |
| Dify | [langgenius/dify](https://github.com/langgenius/dify) | Modified Apache-2.0 + extra conditions | 161,564 | Multi-tenant-service and branding conditions added on top of Apache-2.0. |
| Onyx | [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | MIT core + `ee/` enterprise carve-out | 33,484 | Core is MIT; everything under `ee/` is separately licensed. |
| Mastra | [mastra-ai/mastra](https://github.com/mastra-ai/mastra) | Apache-2.0 core + `ee/` carve-out | 29,691 | TypeScript framework; `ee/` directories separately licensed. |
| Activepieces | [activepieces/activepieces](https://github.com/activepieces/activepieces) | MIT core + `packages/ee/` carve-out | 25,638 | ~400 MCP servers bundled; enterprise packages carved out. |
| AutoGen | [microsoft/autogen](https://github.com/microsoft/autogen) | CC-BY-4.0 (per GitHub) | 61,955 | **Legacy.** Superseded — active work moved to AG2 and Microsoft Agent Framework. Do not start new work here. |

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
