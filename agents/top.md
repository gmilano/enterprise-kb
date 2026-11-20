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

## Tier 1 — Permissive license, enterprise-ready (16 verified)

| Agent | Repo | License | Stars | Description |
|-------|------|---------|-------|-------------|
| OpenClaw | [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,887 | The AI that really does things. Any OS. Any Platform. |
| Langflow | [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | MIT | 156,801 | Building and deploying AI-powered agents and workflows (visual builder). |
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
- **No LATAM-origin agent framework of any scale exists.** See `intel/market.md`.
