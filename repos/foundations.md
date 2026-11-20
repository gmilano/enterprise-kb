---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 🏗️ Repos fundacionales — Enterprise

> The layers an enterprise agent platform needs underneath the agents themselves.
> All rows verified against the GitHub API on 2026-11-20. `NOASSERTION` badges were
> resolved by reading each repository's `LICENSE` file — the real license is shown.
>
> Enterprise buyers in 2026 do not buy an agent, they buy a *governed* agent. The
> serving, identity, policy, isolation and evaluation rows below are what turn a
> framework demo into something a client's risk committee will approve.
>
> **Second pass, 2026-11-20 (later same day):** three sections added — agent skill supply
> chain, data/semantics/transformation, and workload identity — plus the `dbt` gap resolved.
> Network policy in this session reaches GitHub only, so every row here is GitHub-verified
> (search API for metadata, `raw.githubusercontent.com` for the actual `LICENSE` text).

## Serving & retrieval

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97,264 | High-throughput, memory-efficient LLM inference and serving engine. The default self-host/sovereign serving layer. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 | 94,475 | Agent-native database / RAG engine with deep document understanding. |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | MIT | 52,967 | Document processing platform for AI — ingestion and parsing of enterprise document estates. |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 | 35,644 | High-performance vector database and search engine. |
| [deepset-ai/haystack](https://github.com/deepset-ai/haystack) | Apache-2.0 | 27,062 | Orchestration framework for context-engineered, production LLM pipelines. **EMEA-origin (Berlin).** |

## Identity, policy & isolation — the governance substrate

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 | 37,980 | Identity and access management. Gives an agent a real enterprise identity instead of a shared API key. |
| [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | Apache-2.0 | 12,501 | General-purpose policy engine (CNCF graduated). Express "which agent may call which tool" as versioned policy. |
| [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 | 17,705 | Secure, fast, extensible sandbox runtime for AI agents — isolation before tool execution. |
| [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 | 4,664 | Open-core authorization management; per-identity, per-resource decisions at request time. |
| [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 | 4,867 | AI gateway, registry and proxy fronting MCP, A2A and REST/gRPC APIs. The single enterprise choke point for tool access. |

## Evaluation, observability & safety

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | Apache-2.0 (per `LICENSE`) | 7,537 | Programmable safety and security controls on LLM conversations. Renamed from `NVIDIA/NeMo-Guardrails`. |
| [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) | Apache-2.0 | 7,628 | Input/output validation and structure enforcement for LLM calls. |
| [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) | Apache-2.0 | 5,962 | Evaluation and testing library for LLM agents. **EMEA-origin (Paris)** — useful when an EU client wants an EU-origin assurance toolchain. |
| [protectai/llm-guard](https://github.com/protectai/llm-guard) | MIT | 3,221 | Security toolkit for LLM interactions — prompt injection, PII, secrets scanning. |

## Durable execution & analytics

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [temporalio/temporal](https://github.com/temporalio/temporal) | MIT | 24,518 | Durable execution. The honest answer to "what happens when an agent dies halfway through a 40-step process". |
| [apache/superset](https://github.com/apache/superset) | Apache-2.0 | 75,586 | Data visualization and exploration platform — the reporting surface over agent outcomes. |
| [agentsmd/agents.md](https://github.com/agentsmd/agents.md) | MIT | 25,620 | Open format for guiding coding agents. The portable way to ship agent context into a client repo. |

## Agent skill supply chain — the layer that did not exist last quarter

A client who adopted a harness (see `agents/top.md` Tier 0) also adopted a dependency tree
of natural-language *skills* that execute with the agent's own OS permissions, pulled from
public registries, usually without review. The controls for that are now open source and
permissive. Every row verified on 2026-11-20; `LICENSE` read directly in each case.

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 | 27,027 | Pre-install security scanner for agent skills and MCP servers: **71 vulnerability patterns across 17 categories** (prompt injection, data exfiltration, privilege escalation, excessive agency, system-prompt leakage, memory poisoning, tool misuse, rogue agent, anti-refusal, trigger abuse, dangerous code via AST, taint tracking, YARA signatures, MCP least privilege, MCP tool poisoning). The gate in front of the registry. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 | 4,224 | Quality gates once a skill is admitted: harness-compatibility checks, semantic overlap detection (two skills that fight each other), synthetic evaluation datasets, and live agent evaluation measuring how a skill changes behaviour. **Ships reusable CI templates** — this is what makes it a control rather than an audit. |
| [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) | Apache-2.0 | 21,829 | "The safe, private runtime for autonomous AI agents", Rust. Runtime containment for skills that scanning missed. **Provenance note:** despite the vendor-neutral org name, its `LICENSE` is copyright **NVIDIA CORPORATION & AFFILIATES**; [NVIDIA/OpenShell-Community](https://github.com/NVIDIA/OpenShell-Community) (Apache-2.0, 193 ★) mirrors it. Read as an NVIDIA project when assessing vendor concentration. |
| [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | Runs Hermes Agent, LangChain Deep Agents and OpenClaw inside OpenShell with managed inference. The migration path from a developer-chosen harness to a governed deployment. |
| [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 | 254 | Multi-language agent runtime for execution-scope management, lifecycle events and **middleware on tool and LLM calls**. Small repo, structurally important: it is where an OPA/Cerbos decision can be enforced per call instead of merely logged. |
| [openclaw/clawhub](https://github.com/openclaw/clawhub) | MIT | 9,557 | The skill + plugin registry itself. Know it because it is what the client's developers are installing from; mirror it internally rather than allowing direct pulls. |
| [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | MIT | 53,885 | 5,400+ skills filtered and categorised from the official registry. Useful as a corpus to scan against when sizing a client's exposure. |

**Two unlicensed giants to keep out of deliverables:**
[anthropics/skills](https://github.com/anthropics/skills) (197,931 ★) and
[multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
(234,677 ★) have **no `LICENSE` file** — checked `LICENSE`, `LICENSE.md`, `LICENSE.txt`,
`LICENSE-MIT` and `COPYING` on both `main` and `master`. Developers may use them; Globant
cannot vendor, redistribute or sublicense them into a client product. Reference them by URL,
never by copy.

## Data, semantics & transformation

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [dbt-labs/dbt](https://github.com/dbt-labs/dbt) | Apache-2.0 (read from `LICENSE`) | 14,192 | The transformation layer. **This resolves the gap recorded earlier today** — see the note below. Pushed 2026-11-20. |
| [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 | 14,026 | Semantic, graph-based reasoning layer over data: deterministic query generation, better context retrieval, explainable agent workflows. The honest answer to "the agent hallucinated a join" — give it an ontology, not more prompt. |
| [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 | 13,006 | "The context platform for your data and AI stack" — catalog, lineage and governance metadata. What tells an agent which table it is allowed to believe. |
| [kestra-io/kestra](https://github.com/kestra-io/kestra) | Apache-2.0 | 30,293 | Declarative orchestration control plane across data, infrastructure and business processes. Complements Temporal: Kestra schedules and declares, Temporal guarantees mid-flight recovery. |

## Workload identity for agents

| Repo | License | Stars | Role in the stack |
|------|---------|-------|-------------------|
| [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | 2,630 | SPIFFE runtime: cryptographic workload identity (CNCF graduated). Keycloak gives an agent a *user-shaped* identity; SPIRE gives the agent **process** a verifiable one, which is what you need to attest that the thing calling a tool is the build you approved. |
| [docker/mcp-gateway](https://github.com/docker/mcp-gateway) | MIT | 1,642 | Docker's MCP gateway CLI plugin. A lighter alternative to `mcp-context-forge` when the client's estate is already Docker-centric. |
| [agntcy/dir](https://github.com/agntcy/dir) | Apache-2.0 | 208 | Distributed announce and discovery for multi-agent systems (AGNTCY). Early, small — listed as the thing to watch for cross-organisation agent discovery, not to build on yet. |
| [a2aproject/A2A](https://github.com/a2aproject/A2A) | Apache-2.0 | 26,604 | The Agent2Agent protocol — open protocol for interoperability between opaque agentic applications. The companion bet to MCP: MCP connects an agent to tools, A2A connects agents to each other. |

**Stale, so not recommended:** [lasso-security/mcp-gateway](https://github.com/lasso-security/mcp-gateway)
(MIT, 403 ★) is a plausible-looking enterprise MCP gateway but was last pushed **2026-01-22**
— ten months cold. Recorded so a future pass does not rediscover it as new.

## Permissive-license caveats on two widely used tools

Both are excellent and both are commonly assumed to be open source. They are not quite:

| Repo | Real license | Stars | Constraint |
|------|--------------|-------|-----------|
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | MIT core + `ee/`, `web/src/ee/` carve-outs | 37,671 | `LICENSE` copyright now reads **ClickHouse, Inc.** (acquired 16 Jan 2026). Core stays MIT. |
| [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) | **Elastic License 2.0** | 12,365 | ELv2 is *not* an open source license — it forbids offering the product as a service. Check before embedding in a client deliverable. |

## Gap resolved this pass — `dbt-core` was a rename, not a disappearance

Earlier today this file recorded the transformation layer as deliberately absent because
`dbt-labs/dbt-core` did not resolve. **It was renamed.** The canonical repository is now
[dbt-labs/dbt](https://github.com/dbt-labs/dbt) — **Apache-2.0** (read from `LICENSE`),
**14,192 ★**, pushed 2026-11-20. Three pieces of evidence, all collected today:

1. `raw.githubusercontent.com/dbt-labs/dbt-core/main/README.md` returns **200** — GitHub is
   serving the old path by redirect, which is what a rename looks like and a deletion does not.
2. That README's CI badges point at `github.com/dbt-labs/dbt/actions`, i.e. the content
   behind the old name is the new repository.
3. [dbt-labs/dbt-fusion](https://github.com/dbt-labs/dbt-fusion) (730 ★) is explicitly
   labelled *"ARCHIVE: code & issue tracking in dbt-core"*, confirming the lineage.

That README also carries a live warning that **dbt v1 development has moved to the
`1.latest` branch** — relevant when pinning. Related and verified: [dbt-labs/dbt-mcp](https://github.com/dbt-labs/dbt-mcp)
(Apache-2.0, 624 ★), an MCP server for dbt, and [dbt-labs/dbt-agent-skills](https://github.com/dbt-labs/dbt-agent-skills)
(Apache-2.0, 766 ★), curated agent skills for dbt — scan them with SkillSpector before use
like any other skill bundle.

**Method note worth keeping:** a 404 on `github.com/<owner>/<repo>` is not evidence of
deletion. Renames keep serving on `raw.githubusercontent.com`, and the search API's `repo:`
qualifier returns nothing for an old name while a `<name> in:name user:<owner>` search finds
the successor. Probe all three before writing "does not exist". Applied to
`microsoft/agent-framework`, all three probes still come back empty — see `agents/top.md`.
