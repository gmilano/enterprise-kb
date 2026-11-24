---
industry: enterprise
region: Global
updated: 2026-11-24
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
>
> **Third pass, 2026-11-20 (later same day):** this pass found the KB's largest structural
> gap and filled it — there was **no control-plane layer**: no AI gateway, no quota or
> usage-attribution point, no cost governance, no red-teaming, no eval-in-CI and no
> OpenTelemetry instrumentation. Six sections added below. Three canonical repositories were
> also found to have **moved** (Envoy AI Gateway, PyRIT, ragas) — see the rename ledger at
> the end. Same verification channel as before: search API for metadata,
> `raw.githubusercontent.com` for the real `LICENSE` text. Non-GitHub hosts remain
> unreachable from this session, so no market figure here is first-hand.

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

## Agent control plane — the AI gateway, quotas and usage attribution

**This section is new in the third pass of 2026-11-20 and it closes the biggest hole in this
KB.** Everything above governs what an agent *is* and what skills it may load. None of it
governs the thing an agent actually does thousands of times a day: call a model or a tool.
That call is where credentials, routing, quotas, failover, rate limits and **per-team cost
attribution** are enforced — or are not. The 2026 evidence says they are not: IDC's FERS
Wave 4 (July 2026) reports **95% of enterprises running at least one company-funded
agent-enabled workflow in production, but only 45.4% with real-time dashboards tracking
token consumption by workflow** (see `intel/trends.md` trend 12).

| Repo | Real license | Stars | Pushed | Role in the stack |
|------|--------------|-------|--------|-------------------|
| [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 | 2,423 | 2026-11-19 | **Start here.** "The open source control plane for AI and agent traffic, powered by Envoy." One OpenAI-compatible API for every model *and* MCP server; platform teams keep credentials, routing, quotas, failover and **usage attribution** in one place. **Formerly Envoy AI Gateway** — now an **Agentic AI Foundation** project under LF Projects, LLC (`README` states: same code, same maintainers, same cadence, Apache-2.0). Low star count, highest strategic value in this file — see the note below on why. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT core + `litellm/enterprise/` carve-out** (read from `LICENSE`) | 63,615 | 2026-11-20 | The most-adopted gateway by a wide margin, now self-described as "the fastest, litest AI Gateway. Rust core with Python SDK", 100+ providers behind one OpenAI-shaped API. Virtual keys, spend tracking, budgets, fallbacks and logging are in the MIT core. **Check before promising SSO/RBAC/team budgets** — secondary sources place those in the enterprise tier, and `litellm/enterprise/` is separately licensed. |
| [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 | 44,402 | 2026-11-20 | "The API and AI Gateway." The right answer when the client already runs Kong for north-south API traffic and wants one policy plane. **Caveat:** the gateway core is Apache-2.0 but secondary sources place the AI-specific features behind an enterprise licence — verify per feature before scoping. |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | MIT | 13,421 | 2026-11-20 | Fully MIT, no carve-out found. Routes to 1,600+ LLMs with **integrated guardrails (50+)** at the gateway rather than in application code — i.e. a guardrail that an application team cannot forget to call. The cleanest licence in this section. |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 | 9,818 | 2026-11-20 | Go gateway positioning itself as LLM gateway **and** MCP gateway in one. Permissive and real; note that much of the comparative material praising it is published by its own vendor, so treat performance and governance claims as unverified. |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 | 6,291 | 2026-11-17 | Observability-first: one line of code to monitor, evaluate and experiment. Pair with a gateway rather than instead of one. **Do not confuse with** [Helicone/ai-gateway](https://github.com/Helicone/ai-gateway) — **GPL-3.0**, 647 ★, last pushed **2025-11-21** (a year cold). Same vendor, different licence, abandoned. |

**Why the 2,423-star repo leads this table.** `intel/market.md` records a vendor-concentration
risk: the skill-governance toolchain this KB recommends is almost entirely NVIDIA's, and
`ai-openshell/OpenShell`'s vendor-neutral org name hides an NVIDIA copyright. **Agent Router is
the structural mitigation** — it is Apache-2.0, built on Envoy (CNCF graduated), and governed by
the same Agentic AI Foundation that stewards MCP, goose and AGENTS.md. For a CTO asking "what in
this stack is not owned by a single silicon vendor", the control plane is now a true answer.
Rank it on governance, not stars, exactly as `agents/top.md` warns.

## Cost governance & metering — because the gateway only produces the data

A gateway emits usage events. Turning those into per-team budgets, chargeback and a number a
CFO will accept is a separate layer, and it is permissively licensed:

| Repo | License | Stars | Pushed | Role in the stack |
|------|---------|-------|--------|-------------------|
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | Apache-2.0 | 2,457 | 2026-11-20 | "Metering and Billing for AI, API and DevOps" — collects and aggregates usage events at scale. The component that turns gateway token counts into per-team, per-workflow entitlements and invoices. Small repo, exactly the missing piece. |
| [opencost/opencost](https://github.com/opencost/opencost) | Apache-2.0 | 6,824 | 2026-11-20 | CNCF cost monitoring for Kubernetes and cloud spend. Covers the *other* half of agent cost — the GPUs and pods behind self-hosted vLLM, which token counting never sees. |
| [apache/superset](https://github.com/apache/superset) | Apache-2.0 | 75,586 | — | Already listed above; named again because it is the reporting surface where OpenMeter and OpenCost data becomes the cost dashboard IDC says 54.6% of enterprises do not have. |

## Red teaming & adversarial testing — new section, and one licence trap

`agents/trending.md` records that skill scanners are already being bypassed. Scanning is a
static control; the matching dynamic control is adversarial testing, and two serious tools are
permissive:

| Repo | Real license | Stars | Pushed | Role in the stack |
|------|--------------|-------|--------|-------------------|
| [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 | 10,114 | 2026-11-18 | "The LLM vulnerability scanner." The de facto probe suite — run it against the deployed agent, not the bare model, so tool access is in scope. |
| [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | MIT | 4,980 | 2026-11-20 | Python Risk Identification Tool for generative AI — Microsoft's open red-teaming framework. **Note the location:** the canonical repo is now `microsoft/PyRIT`. The widely linked [Azure/PyRIT](https://github.com/Azure/PyRIT) is the old home — **128 ★, last pushed 2026-03-25** — so a bookmark or a blog link from early 2026 points at a stale mirror. |
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT | 27,494 | 2026-11-20 | Listed again in the next section: it does **both** eval and red-teaming/vulnerability scanning, and it is the one tool here that is designed to run as a CI gate. |

**Licence trap — read before anyone proposes Llama Guard.**
[meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) (4,486 ★, pushed 2026-11-13)
is routinely recommended as an open guardrail. Its `LICENSE` is the **LLAMA 3.2 COMMUNITY
LICENSE AGREEMENT** — *not* MIT, *not* Apache-2.0 and **not an OSI open source licence**. It
carries acceptable-use terms and bespoke conditions. GitHub reports it as `NOASSERTION`, which
is why it keeps being mistaken for permissive. Use the Apache-2.0 and MIT options above, or
clear PurpleLlama with legal first.

**Stale, so not recommended:** [protectai/rebuff](https://github.com/protectai/rebuff)
(Apache-2.0, 1,533 ★) is a prompt-injection detector still widely cited, but it was last pushed
**2024-08-07** — over two years cold. Recorded so a future pass does not rediscover it as new.

## Evaluation in CI & OpenTelemetry instrumentation

The KB already lists evaluation *libraries*. What it lacked is the layer that makes evaluation a
**gate** and makes agent behaviour readable in the client's existing observability stack — which
matters because an enterprise will not adopt a second, agent-only monitoring tool.

| Repo | License | Stars | Pushed | Role in the stack |
|------|---------|-------|--------|-------------------|
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT | 27,494 | 2026-11-20 | Test prompts, agents and RAG, plus red teaming and vulnerability scanning, declaratively. **The eval gate to put in the pipeline** — MIT, no carve-out found. |
| [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 | 19,577 | 2026-11-19 | "The LLM evaluation framework" — unit-test-shaped metrics for agent and RAG outputs. Pairs naturally with pytest in an existing Python CI. |
| [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | Apache-2.0 | 16,389 | 2026-11-14 | RAG-specific evaluation metrics. **Ownership moved:** this is the repo formerly at `explodinggradients/ragas`, which no longer resolves. The org change matters for supply-chain review — re-pin the dependency and re-read the licence rather than assuming continuity. |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | Apache-2.0 | 7,543 | 2026-11-19 | OpenTelemetry-based observability for LLM and agent applications. The route into the client's **existing** APM, not a parallel tool. |
| [Arize-ai/openinference](https://github.com/Arize-ai/openinference) | Apache-2.0 | 1,331 | 2026-11-20 | OpenTelemetry instrumentation for AI observability. Note the licence contrast with the same vendor's [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix), which is **Elastic License 2.0** and not open source — instrument with `openinference`, and treat Phoenix as a product decision. |
| [open-telemetry/semantic-conventions](https://github.com/open-telemetry/semantic-conventions) | Apache-2.0 | 690 | 2026-11-20 | Where the **GenAI semantic conventions** are standardised. 690 stars and structurally load-bearing: agree the span and attribute names here and agent telemetry stays portable across vendors. The vendor-neutral answer to observability lock-in — the same argument as Agent Router, one layer up. |
| [Agenta-AI/agenta](https://github.com/Agenta-AI/agenta) | **MIT Expat core + any `ee/` carve-out** (read from `LICENSE`) | 4,922 | 2026-11-20 | Workspace for building, evaluating and versioning agents and prompts. Copyright **Agentatech UG (haftungsbeschränkt)**, a German entity — so this is a second **EMEA-origin** assurance tool alongside Giskard, and it strengthens the EU-origin toolchain argument in `intel/market.md`. |

## Sandboxed execution, memory & document AI — rounding out the substrate

| Repo | Real license | Stars | Pushed | Role in the stack |
|------|--------------|-------|--------|-------------------|
| [e2b-dev/E2B](https://github.com/e2b-dev/E2B) | Apache-2.0 | 14,943 | 2026-11-20 | "Open-source, secure environment with real-world tools for enterprise-grade agents." Code-execution sandboxing; the complement to `OpenSandbox` above and a non-NVIDIA option in that slot. |
| [docling-project/docling](https://github.com/docling-project/docling) | **MIT** | 70,818 | 2026-11-20 | "Get your documents ready for gen AI." Document conversion and layout understanding across PDF, Office and images. **Hosted in the LF AI & Data Foundation**, IBM-originated (ships alongside the GraniteDocling VLM). MIT + foundation-governed + 70k stars makes this the default answer to an enterprise document estate — and it was **entirely absent from this KB**. |
| [Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured) | Apache-2.0 | 15,769 | 2026-11-19 | Document-to-structured-data ETL. The pipeline-shaped alternative to Docling when ingestion is a scheduled job rather than a request. |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Apache-2.0 | 33,431 | 2026-11-20 | Open-source AI memory platform giving agents persistent, queryable memory over a graph. The permissive alternative to Mem0 in the memory slot. |
| [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | **2026-10-18** | Platform for **stateful** agents with advanced memory that learn over time (the MemGPT lineage). Apache-2.0 and substantial, but note it is the only row in this file over a month without a push — check activity before committing to it. |

**Memory caveat — do not scope `getzep/zep` as self-hosted.**
[getzep/zep](https://github.com/getzep/zep) (Apache-2.0, 5,010 ★) still looks like a
self-hostable memory server and is cited that way. Its `README` now reads **"Zep: Examples and
Integrations"**, and describes Zep itself as "the enterprise context layer for reliable
agents" — a hosted product. The permissive repository is the examples, not the engine. Use
`cognee` or `mem0` where the requirement is self-hosted memory.

**Unlicensed giant in the sandbox slot:** [daytonaio/daytona](https://github.com/daytonaio/daytona)
— "secure and elastic infrastructure for running AI-generated code", **71,307 ★** — has **no
`LICENSE` file** (checked `LICENSE`, `LICENSE.md`, `LICENSE.txt` and `COPYING` on `main` and
`master`) and was last pushed **2026-07-24**. Enormous mindshare, four months cold, and
unusable in a deliverable. Same category as the unlicensed skill collections above: reference
by URL, never by copy.

## Agent payments & commerce protocols — the layer that decides whether an agent may spend money

**New section, fourth pass 2026-11-20.** This KB had **zero** coverage of this layer: `AP2`,
`x402`, `agentic-commerce` and even the bare word `payment` each returned no match across all
eight files. That is a load-bearing gap, because this is the first layer where an agent's
mistake debits a real account. The authorisation question stops being *"which tool may it
call"* and becomes *"how much may it spend, on whose mandate, and with what non-repudiable
evidence afterwards"* — which is a procurement and audit question, not a modelling one.

Three protocols now compete at **different layers of the same stack**, and all are
permissively licensed. Metadata from the GitHub search API on 2026-11-20; every licence below
was read from the repository's own `LICENSE` file.

| Repo | License (read from `LICENSE`) | Stars | Pushed | What it is |
|------|-------------------------------|-------|--------|------------|
| [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3,281 | **2026-06-17** | **Agent Payments Protocol.** "Building a Secure and Interoperable Future for AI-Driven Payments." Google-initiated with ~60 payments and technology organisations; built as an extension to A2A. The mandate/verifiable-credential model — a signed record of *what the user authorised* — is the part worth stealing even if the protocol is not adopted. **Caveat: idle five months.** |
| [agentic-commerce-protocol/agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1,607 | 2026-07-18 | **ACP.** "An interaction model and open standard for connecting buyers, AI agents and businesses." OpenAI/Stripe lineage, now under its own neutral GitHub organisation — an ownership signal worth noting against the KB's foundation-governance trend. |
| [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | Apache-2.0 | 571 | **2026-11-11** | The **A2A x402 extension** — HTTP 402 "Payment Required" revived as a machine-payable rail, bringing cryptocurrency settlement to A2A. **The only actively-pushed repo in this table.** |
| [forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol) | MIT | 180 | 2026-07-08 | Authentication and data encryption between agents, merchants and merchant vendors. Addresses the question the payment protocols leave open: *is this agent who it claims to be, acting for whom?* Cleanest licence in the category. |
| [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-18 | Reference implementation of **ACP and the Universal Commerce Protocol (UCP)**. Small and new, but it is runnable architecture rather than a specification — the fastest way to show a client what this looks like end to end. |

**Read the push dates against the star counts.** AP2 is five times more starred than the x402
extension and has not been touched since June; the extension was pushed nine days ago. This is
the same decoupling recorded in `intel/trends.md` §11, now reproduced inside a single
protocol family. **Do not tell a client "AP2 is the standard" on the strength of 3,281 stars.**
The honest statement is: the mandate model is the durable idea, the settlement rail is still
contested between three protocols, and nothing here is yet safe to build a payment path on
without a human approval step.

**Governance caveat, explicitly second-hand.** Multiple secondary sources report that Google
donated AP2 to the **FIDO Alliance** (one comparison table dates the donation to April 2026).
This pass could not reach `blog.google`, `cloud.google.com`, `fidoalliance.org` or
`ap2-protocol.org` — every non-GitHub host fails to resolve in this session. **The donation is
reported, not verified here.** Verify before it appears in a client deck.

## PII de-identification & data minimisation — the layer between an agent and customer data

**New section, fourth pass 2026-11-20.** `presidio`, `DLP` and `redact` each returned **zero**
matches across this KB before this pass. `PII` appeared only as prose. For an enterprise
agent, de-identification is not a nice-to-have: it is what lets a prompt crossing a model
boundary stop being a personal-data export.

| Repo | License (read from `LICENSE`) | Stars | Pushed | Role |
|------|-------------------------------|-------|--------|------|
| [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) | MIT | 11,989 | 2026-11-19 | **The de facto PII engine** — detects, redacts, masks and anonymises sensitive data across text, images and structured data. **Moved out of the `microsoft/` organisation; see the rename ledger below.** Put it at ingest *and* at egress: once before text reaches a model, once before output reaches a log. |
| [data-privacy-stack/presidio-research](https://github.com/data-privacy-stack/presidio-research) | MIT | 321 | 2026-11-19 | Evaluation harness for building and scoring new PII recognisers. The piece that makes "we tuned detection for this client's data" an evidenced claim rather than an assertion. |
| [protectai/llm-guard](https://github.com/protectai/llm-guard) | MIT | 3,221 | 2026-07-08 | Already in this KB — listed here so the boundary is clear. `llm-guard` is prompt/response *security* (injection, toxicity, leakage); Presidio is *identification and removal* of personal data. They are complements, not alternatives, and clients routinely conflate them. |

**The engagement line:** Presidio is MIT, mature, and the single cheapest credible
answer to "can you prove customer data is not leaving our boundary?" — which is the first
question asked in every EMEA and regulated-sector engagement in `intel/market.md`.

## Catalog, lineage & the "context layer" convergence

**New section, fourth pass 2026-11-20.** `openmetadata`, `unitycatalog` and `openlineage` were
each absent from this KB. The strategically interesting part is not the individual tools — it
is that **the data-catalog category has re-described itself as agent context infrastructure**,
in its own words, on its own repositories.

| Repo | License (read from `LICENSE`) | Stars | Pushed | Self-description and why it matters |
|------|-------------------------------|-------|--------|-------------------------------------|
| [open-metadata/OpenMetadata](https://github.com/open-metadata/OpenMetadata) | Apache-2.0 | 15,823 | 2026-11-20 | "**The Open Context Layer for Data and AI.**" **New to this KB** and the most-starred entry in the category. |
| [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 (LICENSE on **`master`**, not `main`) | 13,006 | 2026-11-20 | "**The Context Platform for your Data and AI Stack.**" Already in this KB; the branch detail is recorded because a licence check that only probes `main` will wrongly report this repo as unlicensed. |
| [unitycatalog/unitycatalog](https://github.com/unitycatalog/unitycatalog) | Apache-2.0 | 3,581 | 2026-11-20 | "Open, Multi-modal Catalog for Data & AI." The open-governance answer where a client is otherwise locked into one vendor's catalog. |
| [OpenLineage/OpenLineage](https://github.com/OpenLineage/OpenLineage) | Apache-2.0 | 2,773 | 2026-11-20 | "An Open Standard for lineage metadata collection." The *standard*, not a product — which is what makes it the integration point rather than another thing to migrate. |

**Why this is a finding and not a list:** two independent catalog vendors, pushed the same day,
both now lead with the word **"context"**. An agent that writes to an ERP has to know which
table it is *allowed to believe*, and lineage is how you answer "where did this number come
from?" after the agent has already acted. That makes the catalog a governance control, not a
data-team tool — and it is usually already installed at the client, which makes it the
cheapest grounding layer available. All four are permissive.

## Graph RAG — the retrieval shape for questions that span documents

**New section, fourth pass 2026-11-20.** `graphrag` returned **zero** matches across this KB,
despite the lead repository being MIT with 36,699 stars. Vector search answers "find me the
passage"; graph-based retrieval answers "what connects these entities across the whole corpus"
— which is the shape of most real enterprise questions (an entity's exposure across contracts,
suppliers, incidents or policies).

| Repo | License (read from `LICENSE`) | Stars | Pushed | Note |
|------|-------------------------------|-------|--------|------|
| [microsoft/graphrag](https://github.com/microsoft/graphrag) | MIT | 36,699 | 2026-11-19 | "A modular graph-based Retrieval-Augmented Generation (RAG) system." The reference implementation and comfortably the category leader. Actively pushed. |
| [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | MIT | 4,010 | 2026-01-27 | "Simple, easy-to-hack." The right choice when the client needs to own and modify the pipeline. **Idle ~10 months.** |
| [circlemind-ai/fast-graphrag](https://github.com/circlemind-ai/fast-graphrag) | MIT | 3,972 | **2025-11-01** | Adaptive retrieval. **Idle over a year — verify before proposing.** |
| [DEEP-PolyU/Awesome-GraphRAG](https://github.com/DEEP-PolyU/Awesome-GraphRAG) | MIT | 2,686 | 2026-06-02 | Curated survey/benchmark index. A reading list, not a dependency — listed so nobody scopes against it. |

**Cost warning to carry into scoping:** graph construction is an indexing cost paid per corpus
and re-paid on refresh, and it is the line item clients do not expect. Price it against the
gateway metering in the control-plane section above, which is where that token spend becomes
visible.

## Agent-to-user interaction & generative UI — the layer this KB did not have at all

Four passes built the substrate under the agent and never named the surface above it. Every
licence here was read from the repository's `LICENSE` file on 2026-11-20.

| Repo | Licence | ★ | Forks | Pushed | Why it is foundational |
|------|---------|---|-------|--------|------------------------|
| [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | MIT | 20,766 | 2,129 | 2026-11-20 | The Agent-User Interaction Protocol — the agent↔user leg beside MCP (tools) and A2A (agents). Implementable without CopilotKit. |
| [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) | MIT | 38,842 | 4,839 | 2026-11-20 | Reference implementation across React, Angular, mobile and Slack. Integrates with LangChain, Mastra, Pydantic AI and Agno — all already in this KB. |
| [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | Apache-2.0 | 17,690 | 1,432 | 2026-11-20 | Google-origin. UI expressed as **data, not code**, against a client-held catalog of pre-approved components — a schema that enforces capability boundaries on the agent. |
| [vercel-labs/json-render](https://github.com/vercel-labs/json-render) | Apache-2.0 | 19,791 | 1,059 | 2026-11-19 | Vercel's generative-UI framework; the natural fit where the client's front end is already Next.js. |
| [thesysdev/openui](https://github.com/thesysdev/openui) | MIT | 15,375 | 1,026 | 2026-11-20 | Third contender calling itself an open standard for the same slot. |
| [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) | MIT | 13,351 | 1,353 | 2026-11-20 | Live React/TypeScript chat library; the migration target for the archived LangChain UIs. |
| [tambo-ai/tambo](https://github.com/tambo-ai/tambo) | MIT | 11,221 | 577 | 2026-11-18 | Generative UI SDK for React. |
| [flyerhq/flutter_chat_ui](https://github.com/flyerhq/flutter_chat_ui) | Apache-2.0 | 2,381 | 864 | 2026-11-19 | Flutter/mobile. The only mobile-first entry found; matters for field and floor workforces. |

**The architectural rule this layer imposes.** Four permissive, actively-developed, mutually
incompatible standards with no foundation steward means the renderer is a **reversible
decision only if you design for it**. Have the agent produce structured UI intent — a typed
payload — and put the AG-UI/A2UI/json-render binding behind one adapter module. If the agent's
reasoning emits renderer-specific markup, the client is married to that renderer.

**The security argument, which is the one that sells.** A2UI's design — the agent may only
request components from a catalog the *client application* holds — is the presentation-layer
version of the rule this KB already carries from automotive: **model output is not a command.**
An agent that can emit arbitrary markup into an internal app is a prompt-injection path to the
employee's screen (a rendered link, a forged confirmation button). A schema-constrained
catalog closes it structurally rather than by filtering text.

### Archived — the chat-shell category is being abandoned

| Repo | Licence | ★ | Status | Note |
|------|---------|---|--------|------|
| [Chainlit/chainlit](https://github.com/Chainlit/chainlit) | Apache-2.0 | 12,498 | **Archived** (API `archived: true`); last push 2026-09-18 | Paris-origin (Chainlit SAS), community-maintained since 2025 per secondary sources. The most-recommended Python conversational-AI shell in the market, and the **only EMEA-origin entry in this layer**. |
| [langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) | MIT | 3,253 | **Archived** | LangGraph chat front end. |
| [langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui) | MIT | 1,705 | **Archived** | UI for Deep Agents. |

**Evidence note, because this is a strong claim.** `archived: true` comes from the GitHub
search API, queried twice. The github.com HTML page returns **403 from this environment**, so
it could not be cross-checked there, and **no README carries a deprecation notice**. For
Chainlit, a PyPI fork found in web search independently states the original team no longer
maintains it. Verify once more before telling a client their platform is dead, then tell them.

## Human approval & escalation — a component, not a convention

| Repo | Licence | ★ | Pushed | Note |
|------|---------|---|--------|------|
| [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) | Apache-2.0 (file-read) | 12,919 | 2026-11-16 | The agent *requests* a human decision through a typed call with routing and timeout, instead of a prompt that asks the model to please check first. |
| [humanlayer/12-factor-agents](https://github.com/humanlayer/12-factor-agents) | **Apache-2.0 — read from file; GitHub reports `NOASSERTION`** | 27,343 | 2025-09-21 | The design-principles document clients quote at you. The file is the unmodified 199-line Apache-2.0 text, no added clauses, so internal adoption and adaptation are permitted. Content is 14 months old. |
| [spotify/portal-ai-plugins](https://github.com/spotify/portal-ai-plugins) | Apache-2.0 | 3,302 | 2026-10-23 | Arrives at the same boundary from platform engineering: catalog actions exposed to coding agents with **help, dry-run and confirmation** built in. |

**Why this belongs in foundations and not in a recipe.** Human-in-the-loop is reported as the
dominant enterprise agent architecture in 2026. Implemented as prompt instructions it is not a
control — it is a hope, and it fails silently under context pressure. Implemented as a typed
call it is auditable, it has an owner, and it produces the approval record an ISO 42001 or EU AI
Act file wants. Wire it between the agent and every irreversible tool.

## Agent workforce management — the 115k-star layer

| Repo | Licence | ★ | Forks | Pushed | Note |
|------|---------|---|-------|--------|------|
| [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT (**`LICENSE` lives on `master`**) | 115,408 | 19,156 | 2026-11-20 | "The open-source app everyone uses to manage agents at work." Agents get a role, a manager and a review surface. |
| [NousResearch/hermes-paperclip-adapter](https://github.com/NousResearch/hermes-paperclip-adapter) | MIT | 2,065 | 404 | 2026-04-04 | Runs the Hermes harness "as a managed employee in a Paperclip company" — harness (`agents/top.md` Tier 0) plugged into a management surface. |

Branch trap, repeated for the second pass running: reading only `main/LICENSE` reports a
115,408-star repository as unlicensed. Probe order is manifest → `LICENSE` → `.md`/`.txt` →
`LICENSE-MIT` → `LICENSE-APACHE` → `COPYING`, across `main` **and** `master`.

## AI inventory & AI-BOM — the prerequisite for everything this KB sells as governance

Trends 3, 10 and 14 and Recetas 7, 9 and 10 all presuppose an estate inventory. No tool in this
KB produced one until now.

| Repo | Licence | ★ | Forks | Pushed | Role |
|------|---------|---|-------|--------|------|
| [CycloneDX/specification](https://github.com/CycloneDX/specification) | Apache-2.0 | 585 | 98 | 2026-11-20 | The OWASP BOM standard: SBOM, SaaSBOM, **ML-BOM**, VEX. The artefact format an auditor already accepts — do not invent a format. |
| [CycloneDX/cyclonedx-python](https://github.com/CycloneDX/cyclonedx-python) | Apache-2.0 | 406 | 107 | 2026-11-19 | Generator for Python projects/environments; Maven, Gradle, .NET and Go generators are siblings in the same org. |
| [sbom-tool/sbom-tools](https://github.com/sbom-tool/sbom-tools) | MIT | 268 | 20 | 2026-11-17 | Semantic SBOM/CBOM/**AI-BOM** diff, quality scoring and compliance validation over CycloneDX/SPDX. The diff is what converts a one-off inventory into drift detection. |
| [Trusera/ai-bom](https://github.com/Trusera/ai-bom) | Apache-2.0 | 368 | 102 | **2026-05-24** | Discovery: find every AI agent, model and API in the infrastructure. The only discovery-shaped tool located. **Six months idle — treat as a fork candidate, not a dependency.** |
| [apisec-inc/mcp-audit](https://github.com/apisec-inc/mcp-audit) | MIT | 167 | 45 | 2026-08-18 | Scans MCP configs for exposed secrets, shadow APIs and models. Narrow but pointed at the right surface given >10,000 MCP servers reported in production. Three months idle. |

**Read the numbers honestly: this layer is immature.** The obligations are worth millions in
procurement; the open tooling tops out at 585 stars and two of the five pieces are months idle.
That is a gap, and gaps are where delivery revenue is — assembling, operating and reporting from
this inventory is studio work, not a product purchase. It is also the cheapest credible first
deliverable for a client who says "we need AI governance" and cannot say what they run.

## Internal developer portal — the front door for the engineering organisation

| Repo | Licence | ★ | Forks | Pushed | Note |
|------|---------|---|-------|--------|------|
| [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34,891 | 7,786 | 2026-11-20 | CNCF portal framework. In clients that run it, the software catalog already answers *what exists and who owns it* — the two questions every agent grounding effort starts by re-deriving badly. |
| [spotify/portal-ai-plugins](https://github.com/spotify/portal-ai-plugins) | Apache-2.0 | 3,302 | 260 | 2026-10-23 | Portal CLI inside coding agents: catalog search, service briefings from ownership/health/incident data, guarded action invocation. |

**Use before building.** Before standing up a catalog for an agent (`DataHub`, `OpenMetadata`
elsewhere in this file), check whether the client runs Backstage. If they do, the ownership graph
exists, is already trusted by the engineering org, and can be the agent's grounding source on
day one.

## Determinism & spec-driven delivery

[github/spec-kit](https://github.com/github/spec-kit) — MIT, **150,799 ★**, 13,548 forks, pushed
2026-11-20. Spec-driven development tooling: write the specification, generate against it, verify
against it. It is listed here because *specify → generate → verify* is the only agentic delivery
shape an audit or QA function accepts, and because at 150k stars it is what a client's developers
have probably already installed. Combine with the CI evaluation gate in Receta 10.

## Durable execution without an orchestrator, and one BUSL trap

- [dbos-inc/dbos-transact-py](https://github.com/dbos-inc/dbos-transact-py) — MIT, 1,693 ★,
  pushed 2026-11-20. Database-backed durable Python workflows. The right size when a pilot needs
  crash-safe resumption but not a Temporal cluster.
- [restatedev/restate](https://github.com/restatedev/restate) — 4,725 ★, GitHub reports
  `NOASSERTION`; the `LICENSE` on **both `main` and `master`** is the **Business Source License
  1.1**. BUSL is *not* open source — a use limitation applies until a conversion date. It
  appears in most "durable agents" discussions; **it cannot be presented to a client as open
  source.** Use Temporal or `dbos-transact-py`.

## Secrets & authorisation — two additions beside OPA, Cerbos and Keycloak

- [openbao/openbao](https://github.com/openbao/openbao) — MPL-2.0, 9,112 ★, pushed 2026-11-20.
  The Linux Foundation Vault fork; the foundation-governed answer for the place agent credentials
  live. **MPL-2.0 is weak, file-level copyleft:** run it as a service next to proprietary code
  freely; modifying its own files and shipping them closed is the thing it forbids.
- [cedar-policy/cedar](https://github.com/cedar-policy/cedar) — Apache-2.0, 1,889 ★, pushed
  2026-11-20. AWS-origin authorisation language whose differentiator is formal analysis of
  policies. A third option beside OPA and Cerbos, worth naming on an AWS-heavy estate.

## Rename ledger — four canonical repos moved (three verified third pass, one fourth pass)

The method note at the end of this file says to probe three channels before writing "does not
exist". Applied again, it caught three moves that would each have produced a dead link or a
stale dependency:

| Was | Is now | Evidence |
|-----|--------|----------|
| `envoyproxy/ai-gateway` | [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) (Apache-2.0, 2,423 ★) | Old path's `raw` README returns **200** and renders as "Agent Router … **Formerly Envoy AI Gateway**"; the search API's `repo:` qualifier returns **422** for the old name. Project moved to the **Agentic AI Foundation**. |
| `Azure/PyRIT` | [microsoft/PyRIT](https://github.com/microsoft/PyRIT) (MIT, 4,980 ★, pushed 2026-11-20) | Old org still resolves but is **128 ★ / 2026-03-25**; a `PyRIT in:name stars:>100` search ranks `microsoft/PyRIT` first by two orders of magnitude. |
| `explodinggradients/ragas` | [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) (Apache-2.0, 16,389 ★) | `repo:explodinggradients/ragas` returns **422**; `ragas in:name stars:>500` returns exactly one repository, under a **new organisation**. Treat as an ownership change, not just a rename. |
| `microsoft/presidio` | [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) (MIT, 11,989 ★, pushed 2026-11-19) | **Found fourth pass, 2026-11-20.** `presidio in:name` indexes only the new path; `presidio in:name user:microsoft` returns **no main repo** — only `presidio-genproto` (10 ★, 2021) and a dstoolkit sample. The old path still serves files, so it is a **redirect, not a deletion**: `LICENSE` fetched from both paths is **byte-identical (1,083 bytes, md5 `cef898d1f3cfb58e111560aa3c250f10`)** and `docs/index.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md` and `pyproject.toml` all return 200 on both. Copyright line reads **"Presidio Contributors"**, not Microsoft Corporation — consistent with a move out of the vendor organisation. |

**Why this keeps happening, and what it means commercially:** three of roughly thirty-five
repositories checked in the third pass had moved, and two of the three changed *organisation*,
not just name. The fourth pass checked roughly twenty more and caught a fourth move — Presidio
out of `microsoft/` — so the rate is holding at close to one in ten. A client's `requirements.txt` or Helm chart pinned to the old coordinates keeps
working until it silently does not. **Offer dependency-provenance review as a line item** — it
is cheap, it is evidenced by this ledger, and it is exactly the kind of finding that justifies
the governance work in `compose/patterns.md`.

---

## The data plane under the agent — added sixth pass, 2026-11-20

**Why this section exists.** This KB had the *context* layer (catalog, lineage, ontology) and
the *transformation* layer (dbt), and nothing in between or below: no governed metric
definition, no entity resolution, no change data capture, no query engine. Those are the four
things that decide whether an enterprise data agent answers from numbers the client's finance
team recognises, or invents a plausible join. Every licence below was read from the
repository's own file or manifest.

### Semantic / metrics layer — the contract that makes the agent's answer auditable

This is the layer that turns "the agent wrote some SQL" into "the agent requested a certified
metric." It is the governance deliverable, not a convenience.

| Repo | Licence (how established) | ★ | Origin | Role |
|------|---------------------------|---|--------|------|
| [cube-js/cube](https://github.com/cube-js/cube) | **Apache-2.0 default across the repo, MIT in parts** — read `LICENSE`; note root `package.json` declares `"MIT"`. Permissive either way. | 21.3k | North America | The most complete open semantic layer: metrics, dimensions, joins and access rules as code, served over SQL/REST/GraphQL **and MCP**. The default choice for Receta 14. |
| [dbt-labs/metricflow](https://github.com/dbt-labs/metricflow) | **Apache-2.0** — `pyproject.toml` declares `license = "Apache-2.0"`, `LICENSE` agrees | 1.9k | North America | "Define, build and maintain metrics in code." The right pick when the client already runs dbt and the metric definitions should live beside the models. |
| [malloydata/malloy](https://github.com/malloydata/malloy) | **MIT** — explicit `SPDX-License-Identifier: MIT` in the licence file | 2.6k | North America | A language for describing data relationships. Use where the semantic model itself is the artefact being designed; composable where Cube is served. |

**Licence note worth carrying into a client conversation:** all three are permissive. This is
the rare layer in 2026 where the governance-critical components are *not* source-available —
which is exactly why the layer below it is such a trap.

### Entity resolution — the component that decides whether "customer 360" is real

An agent asked "what is this customer's total exposure?" is wrong by construction if the
client is one row in CRM, two in billing and three in support. This is unglamorous and it is
the difference between a demo and a deliverable.

| Repo | Licence (how established) | ★ | Origin | Role |
|------|---------------------------|---|--------|------|
| [moj-analytical-services/splink](https://github.com/moj-analytical-services/splink) | **MIT** — `LICENSE` reads "MIT License, Copyright (c) 2020 Ministry of Justice" | 2.6k | **EMEA (UK Ministry of Justice)** | "Fast, accurate and scalable probabilistic data linkage with support for multiple SQL backends." Runs the linkage *inside* the client's warehouse (DuckDB, Spark, Athena) rather than extracting data — which is why it survives a data-residency review. **Built and maintained by a government department**, which is an unusually strong provenance story for a regulated client. |
| [J535D165/recordlinkage](https://github.com/J535D165/recordlinkage) | **BSD-3-Clause** — `pyproject.toml` declares `license = {text = "BSD-3-Clause"}` | 1.1k | EMEA (Netherlands) | "A powerful and modular toolkit for record linkage and duplicate detection in Python." Smaller and in-memory; the right tool for a scoped reconciliation, not an estate. |
| [zinggAI/zingg](https://github.com/zinggAI/zingg) | **AGPL-3.0 — read the licence file, it is the full GNU Affero text** | 1.3k | APAC (India) | "AI based entity resolution, identity resolution, master data management and deduplication at scale for humans and agents." Capable and well-documented — and **copyleft**. See the containment rule below. |

**The recommendation is Splink, and it is not a close call for Globant's purposes.** It is MIT,
it is government-maintained, and it pushes computation to the warehouse. Zingg is the more
marketed project and the AGPL makes it the wrong default: usable as a separate, unmodified
service behind a process boundary, unusable linked into something Globant delivers as the
client's own software. Same containment discipline this KB already applies to copyleft ERP.

### Change data capture and ingestion — and the licence minefield this KB had not mapped

**This is the finding of the pass.** The energy pass established that the *metering* layer is
where non-OSI licences concentrate. The same thing is true here, for the same structural
reason, and it generalises — see `intel/trends.md`.

**Clean and permissive — build on these:**

| Repo | Licence (how established) | ★ | Origin | Role |
|------|---------------------------|---|--------|------|
| [debezium/debezium](https://github.com/debezium/debezium) | **Apache-2.0** — `LICENSE.txt`; README notes the Antlr grammars in `debezium-ddl-parser` are MIT | 13.4k | EMEA (Red Hat) | "Change data capture for a variety of databases." Log-based CDC — reads the WAL/binlog rather than polling, so it does not add load to the client's production OLTP box. The reference implementation of the category. |
| [dlt-hub/dlt](https://github.com/dlt-hub/dlt) | **Apache-2.0** — `LICENSE.txt` is the full Apache text | 6.1k | EMEA (Berlin) | "An open source Python library that makes data loading easy." Pipelines are code — testable, reviewable, diffable. The permissive substitute for the source-available ELT tools below. |
| [meltano/meltano](https://github.com/meltano/meltano) | **MIT** — `pyproject.toml` and `LICENSE` agree | 2.7k | North America | Declarative, code-first ELT over the Singer tap/target ecosystem. Use where the client wants a connector catalogue without a vendor runtime. |
| [duckdb/duckdb](https://github.com/duckdb/duckdb) | **MIT** — Stichting DuckDB Foundation | 43.2k | EMEA (Netherlands) | "A high-performance analytical database system." The local/embedded engine that makes Splink and a semantic layer testable on a laptop before anything touches client infrastructure. |
| [apache/iceberg](https://github.com/apache/iceberg) | **Apache-2.0** | 9.4k | Global (ASF) | "A high-performance format for huge analytic tables." The table format that keeps the agent's reads reproducible — snapshot isolation means two agent runs can be compared. |

**Source-available or copyleft — read before quoting, and do not assume from the badge:**

| Repo | What the licence actually is | ★ | What it blocks |
|------|------------------------------|---|----------------|
| [airbytehq/airbyte](https://github.com/airbytehq/airbyte) | **Root `LICENSE` is the Elastic License 2.0 (ELv2).** The README carries **two** badges, MIT *and* ELv2. Airbyte's own marketing page states "Airbyte Core is open source under Apache 2.0" — **the repository does not support that claim.** | 22.4k | ELv2 forbids providing the software to third parties as a managed service. **A Globant-operated Airbyte for a client is exactly the use ELv2 exists to prevent.** The MIT/ELv2 path boundary is **not documented at any path probed this pass** (`airbyte-integrations/LICENSE` → 404, licence FAQ doc → 404), so a specific connector's reuse requires reading that connector's own licence file first. Measured limit, stated as one. |
| [bruin-data/ingestr](https://github.com/bruin-data/ingestr) | **Functional Source License 1.1 (FSL-1.1-ALv2)** — not OSI. README: *"Each version becomes Apache 2.0 two years after release."* | 4.0k | A **non-compete window**, not a permanent restriction — a licence class this KB had not previously recorded. Today's release is restricted; the release from two years ago is Apache-2.0. If a client insists on ingestr, the compliant path is pinning a version older than two years, which is a real engineering decision with a real cost. |
| [metabase/metabase](https://github.com/metabase/metabase) | **AGPL-3.0 outside the top-level `enterprise/` directory; Metabase Commercial Licence inside it.** Note the root `package.json` declares `"license": "private"` — a manifest read alone would have produced a *false negative* here. | 50.4k | Network copyleft. Deployable as a separate service; **not** embeddable or modifiable inside a proprietary client product without AGPL compliance. The most-starred repo in this whole section and the one most likely to be assumed safe. |
| [lightdash/lightdash](https://github.com/lightdash/lightdash) | **MIT, except `packages/backend/src/ee/`, which is under a separate licence.** Established by reading the licence file; the sidebar names no licence. | 6.2k | Classic open core. The MIT path is genuinely usable — just never build against `/ee`, and pin that exclusion in the build so it cannot drift in later. |

**The method rule this produced, which applies to every industry in this rotation:**
*the root `LICENSE` file and the package manifest can disagree, and either one alone can be
wrong in either direction.* Metabase's manifest says `"private"` (false negative — it is AGPL
plus commercial). Cube's manifest says `MIT` while its `LICENSE` says Apache-2.0 by default
(both permissive, no harm). Airbyte's marketing says Apache-2.0 while its `LICENSE` says ELv2
(false positive, and the dangerous direction). **Read both, and when they disagree, say so
rather than picking the convenient one.**

---

## The entitlement boundary — who the agent is acting for, and what that person may see (added seventh pass, 2026-11-20)

**Why this section exists.** Six passes of this file built the substrate around the agent:
policy engines that decide *which tool* an agent may call (OPA, Cerbos, Cedar), workload
identity that attests *which process* is calling (SPIRE), an IAM that gives the agent a
user-shaped login (Keycloak), and a vault for its credentials (OpenBao). Every one of those
answers a question about the **agent**. None of them answers the question a client's security
team actually asks first:

> *"When an employee asks the agent something, does the agent only see what **that employee**
> is allowed to see?"*

That is a different control, in a different place, and this KB had **no component for it at
all** — `OpenFGA`, `Casbin`, `OAuth` and token exchange returned **zero matches across all
eight files** before this pass. The failure mode it prevents is the most common real-world
enterprise AI incident: an agent indexes a corpus once, with the permissions of whoever built
the index, and then answers everyone out of that flat index. Nothing is hacked. The agent
simply tells a contractor what the board papers say.

### Relationship-based authorization engines (the Zanzibar family)

Role-based checks are the wrong shape here: entitlements in a document estate are
*relationships* ("this user is in this group, which inherits this folder"), not roles. The
engines below are all modelled on Google's Zanzibar paper. Licences were read from each
repository's own `LICENSE` file; stars, push dates and archived status come from the GitHub
API on 2026-11-20.

| Engine | Repo | Licence (read from `LICENSE`) | ★ | Pushed | Role in the stack |
|--------|------|-------------------------------|---|--------|-------------------|
| Casbin | [apache/casbin](https://github.com/apache/casbin) | Apache-2.0 | 20,508 | 2026-11-20 | **The most-starred authorization library in open source, and it moved to the Apache Software Foundation** — see the rename ledger entry below. Library-embedded rather than a service: ACL, RBAC, ABAC and ReBAC models in one policy engine, with first-party ports for Java, Python, Node, .NET, Go and Rust. The right choice when authorization must run *inside* the application process with no network hop. |
| SpiceDB | [authzed/spicedb](https://github.com/authzed/spicedb) | Apache-2.0 | 7,233 | 2026-11-20 | The most-starred Zanzibar *database*. Stores and queries the permission graph itself, with consistency guarantees designed for exactly the "check 400 retrieved chunks before they reach the model" problem. Pinecone's own access-control tutorial is built on it. |
| OpenFGA | [openfga/openfga](https://github.com/openfga/openfga) | Apache-2.0 | 6,168 | 2026-11-20 | CNCF-hosted (its README carries the `cncf_#openfga` Slack badge); created at Auth0 and **in production behind Auth0 FGA since December 2021**, with Grafana Labs, Canonical and Docker named as adopters in its own `ADOPTERS.md`. The best-documented option for the agent case specifically — Auth0 publishes worked RAG-filtering integrations, including a LangChain4j/Java one, which matters for the JVM cores in `compose/patterns.md` Receta 6. |
| Ory Keto | [ory/keto](https://github.com/ory/keto) | Apache-2.0 | 5,421 | **2026-09-04** | A permission server from the Ory stack, genuinely Apache-2.0. **Caveat: two and a half months since last push** — the only entry here not pushed the day it was measured. Verify activity before committing a client to it. |

### Delegated authority — carrying the *user's* identity to the tool

A permission engine is useless if the agent reaches the downstream system as itself. The
enterprise pattern is **delegation**: the human stays the subject, the agent is named as the
actor, and the token's authority is narrowed below the user's own grant.

| Piece | Repo | Licence | ★ | Pushed | Role |
|-------|------|---------|---|--------|------|
| MCP auth extensions | [modelcontextprotocol/ext-auth](https://github.com/modelcontextprotocol/ext-auth) | MIT | 179 | 2026-11-10 | **The primary source for the enterprise MCP authorization profile** (see below). Small star count, canonical status — this is a specification repository, so rank it by provenance, not traction. |
| OAuth2 / OIDC provider | [ory/hydra](https://github.com/ory/hydra) | Apache-2.0 | 17,675 | **2026-07-29** | OpenID-certified OAuth 2.1 provider, usable as the authorization server that performs the token exchange. **Nearly four months idle** — recorded with that caveat, not as a recommendation. |
| Auth at the edge | [oauth2-proxy/oauth2-proxy](https://github.com/oauth2-proxy/oauth2-proxy) | MIT | 15,392 | 2026-11-19 | A reverse proxy that terminates OIDC in front of a service. The pragmatic way to put a real enterprise identity in front of an agent endpoint that has none, without modifying the agent. |

### The MCP enterprise authorization profile — read from the primary source

`modelcontextprotocol.io` **does not resolve from this environment** (see the verification-channel
note at the end of this file), so the specification was read directly from the repository over
`raw.githubusercontent.com`, at
`specification/stable/enterprise-managed-authorization/2026-07-28/enterprise-managed-authorization.mdx`
(HTTP 200). **Protocol revision `2026-07-28`.** Quoting the spec's own structure:

- The profile is an application of the **Identity Assertion JWT Authorization Grant**
  (`draft-ietf-oauth-identity-assertion-authz-grant`, "ID-JAG"), which is itself a profile of
  **Identity Chaining Across Trust Domains** (`draft-ietf-oauth-identity-chaining`).
- The flow is three steps: **(1)** SSO to the MCP Client over OpenID Connect or SAML →
  **(2)** Token Exchange, **RFC 8693** → **(3)** JWT Authorization Grant, **RFC 7523**.
- The authorization server that issues tokens for the MCP Server is the one "advertised in the
  MCP Server's Protected Resource Metadata (**RFC 9728**)".
- In this profile the **Client** is the MCP Client, the **Resource Server** is the MCP Server,
  and the **IdP Authorization Server** is the enterprise identity provider used for SSO.

**What it buys the client, in the spec's own terms:** end users stop having to "manually connect
and authorize the MCP Client to each MCP Server", and enterprise admins get "visibility and
control over which MCP Servers are able to be used within the organization." That second one is
a procurement capability, not a developer convenience — it is the answer to "how do we stop
staff wiring arbitrary MCP servers into our data", which is the question `intel/trends.md` §10
says the skill supply chain raised and left open.

**The honest status, which must be said before this is proposed to a client.** The MCP
extension is published as stable at revision `2026-07-28`, but **the IETF draft underneath it
is unfinished**: secondary sources put ID-JAG at `draft-04`, published 21 May 2026 and
expiring 22 November 2026 — *two days from this pass*. An expiring Internet-Draft is normal
IETF mechanics and does not mean the work is dead, but it does mean **the normative base can
still change**. `datatracker.ietf.org` and `www.ietf.org` are both unreachable from this
environment (DNS failure and HTTP 000 respectively), so **this KB has not verified the draft
revision or its status against the IETF directly** — the revision number above is
single-sourced from vendor and blog material and is the weakest datum in this section. Treat
it as "specified and shipping, not yet standardised": vendor material reports Okta as the
first IdP, **Keycloak support as experimental**, and Atlassian shipping the flow in Rovo MCP.

### Licence traps in this layer — and they are the dangerous direction

Authorization tooling markets itself in the same language whether it is permissive or not, and
three of the best-known names in the category are **not** usable the way a reader would assume:

| Repo | What the licence actually is | ★ | What it blocks |
|------|------------------------------|---|----------------|
| [Permify/permify](https://github.com/Permify/permify) | **AGPL-3.0** — confirmed by reading `LICENSE` on `master` ("GNU AFFERO GENERAL PUBLIC LICENSE, Version 3"). | 5,975 | Network copyleft, and it sits on the request path of every authorization check. Deployable as a separate service; **not** embeddable in a proprietary client product. It presents as "authorization as a service inspired by Google Zanzibar" — the same sentence SpiceDB and OpenFGA use, with a materially different licence. |
| [osohq/oso](https://github.com/osohq/oso) | Apache-2.0, but **ARCHIVED on 2026-10-22**. Its own description now reads *"Legacy Oso open source library (archived)"*. | 3,480 | Read-only. No security response. **Four prior passes of this KB found the same shape** (three archived chat UIs, then archived Vanna at 23.8k ★) — this is the fifth archived-but-highly-starred project found in six passes, and the pattern is now a standing check rather than an observation. |
| [zitadel/zitadel](https://github.com/zitadel/zitadel) | **AGPL-3.0.** | 15,622 | Frequently suggested as the modern open alternative to Keycloak for agent identity. Keycloak is **Apache-2.0**; Zitadel is AGPL. If a client wants an identity provider they can modify and embed, that difference decides it. |

**The rule this layer adds to the KB's licence method:** in the authorization layer the
*category name is not a licence signal*. "Zanzibar-inspired", "open source", "authorization as
a service" describe Apache-2.0 SpiceDB, Apache-2.0 OpenFGA and **AGPL-3.0 Permify** equally
well. This is the same structural finding the energy KB recorded in the metering layer — *the
licence filter runs before the popularity filter* — reproduced in a completely different
industry, which is evidence it generalises across this whole rotation.

### Rename ledger addition — `casbin/casbin` → `apache/casbin` (seventh pass)

| Was | Is now | Evidence |
|-----|--------|----------|
| `casbin/casbin` | [apache/casbin](https://github.com/apache/casbin) (Apache-2.0, 20,508 ★, pushed 2026-11-20) | `repo:casbin/casbin` returns **422** from the search API. `casbin in:name stars:>300` returns **12** repositories, **ten of them under `apache/`**: the core plus `casbin-jcasbin` (2,652 ★), `casbin-node-casbin` (2,921 ★), `casbin-pycasbin` (1,778 ★), `casbin-Casbin.NET` (1,344 ★), `casbin-rs` (1,153 ★), `casbin-gorm-adapter`, `casbin-server` and `casbin-gateway`. The old path still serves files on **`master` (200)** but **404s on `main`**, so it is a redirect, not a deletion — the same signature as the Presidio move. The old path's `README.md` now opens with the **ASF licence header** ("Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements"), which is the confirmation: this is a donation to a foundation, not a vanity rename. |

**Why this one matters more than a dead link.** It is the fifth rename this ledger has caught in
roughly fifty repositories checked across four passes — the rate is holding near one in ten —
but it is the first where the destination is a **foundation**. `intel/trends.md` §5 records
protocols moving from vendor control to foundation governance (MCP → Linux Foundation, Envoy AI
Gateway → Agentic AI Foundation). Casbin is the same movement reaching the *authorization*
layer, and it is the direction an enterprise client should want: ASF governance brings a
trademark policy, a security process and a release process that a single-vendor repository does
not have. **Note the whole family lives on `master`, not `main`** — a detail that matters because
this KB's own probe lists default to `main` first, and the energy KB has a documented false
negative from exactly that assumption.

### Method notes from this pass — two new ways to be wrong

**1. A new way to measure a false *positive* — the name-collision cluster.** This KB has nine
documented ways to measure a false *zero*. This pass found the inverse. A web search for the
precise technical phrase `permission-aware RAG ... entitlements` returned, in its top ten, **six
GitHub repositories all named essentially `permission-aware-rag`**, with confident, specific,
professional READMEs — one advertising *"0 restricted chunks leaked in 330 adversarial tests"*,
another *"a benchmark of three filtering strategies on 50K chunks"*. Verified against the API,
their star counts are **1, 0, 0, 19, 0 and 0**, and **three have no licence file at all**. They
are personal demos. **The cause is structural and will recur in every industry in this
rotation: web search ranks on semantic match to the README, and when the search phrase *is* the
repository name, the whole result page fills with near-identical zero-traction projects.** The
discriminator is unchanged and cheap — resolve every candidate through the API before writing
it down — but the *trigger* is new and worth naming: **a page of search results that all share
one repository name is a warning sign, not a confirmation.** Had this pass trusted the result
page, it would have written six fictional components into a recipe.

**2. `curl -sI https://github.com/...` is not an existence check in this environment.** Probed
against **eighteen** repositories known from the API to be alive, it returned **403 for all
eighteen** — the agent proxy refuses github.com HTML browsing uniformly, regardless of whether
the path exists. A pass that used it naively would conclude every repository in this KB is
dead. The two channels that do work, and that every row above was verified on, are
**(a)** the GitHub search API with an exact `repo:` qualifier, which also returns licence,
archived status, stars and push date in one call, and **(b)** `raw.githubusercontent.com` for
file-level existence, which additionally reveals the default branch. All seventeen repositories
named in this section returned **200 on raw** for `README.md` or `LICENSE`.

---

## The write channel — the integration runtime that carries the agent's action into the system of record (added eighth pass, 2026-11-21)

The seventh pass established *what the agent may read*. The question a client security
team asks immediately afterwards is **what it may change, and through what**. This KB
held workflow-automation tools (`n8n`, `activepieces`, `kestra`) and durable-execution
engines (`temporal`, `restate`, `dbos`), but not the **enterprise integration layer** —
the one that already holds the client's live connections to SAP, Salesforce, JDBC, JMS,
AS/400 and the message bus. As of 2026 that layer speaks MCP and A2A natively, which
changes the economics of Receta 1 completely.

All rows verified live 2026-11-21; licences byte-read from each repository's `LICENSE`.

| Repo | Stars | Licencia | Último push | Rol |
|---|---|---|---|---|
| [apache/camel](https://github.com/apache/camel) | 6,419 ★ | Apache-2.0 (11,357 B, `LICENSE.txt`) | 2026-11-21 | The integration runtime. **An existing Camel route becomes an agent tool without new integration code.** |
| [conductor-oss/conductor](https://github.com/conductor-oss/conductor) | 32,494 ★ | Apache-2.0 (11,309 B) | 2026-11-20 | Netflix-origin workflow orchestration, now community-governed. Choose it when the shape is orchestration of services; choose Camel when the shape is mediation between protocols and legacy endpoints. |
| [dapr/dapr](https://github.com/dapr/dapr) | 26,212 ★ | Apache-2.0 (11,411 B, `master`) | 2026-11-19 | CNCF. State, pub/sub and workflow as sidecar APIs. **Workflow versioning since v1.17 (Feb 2026).** |
| [dapr/dapr-agents](https://github.com/dapr/dapr-agents) | 778 ★ | Apache-2.0 (11,356 B) | 2026-11-12 | Agents as durable workflows, each agent an actor, every LLM and tool interaction persisted. |

### What was read from the code rather than the announcement

`components/camel-ai/pom.xml` on `main` lists these modules. This is the authoritative
list; it is **not** what the release blogs say:

```
camel-a2a                     camel-ai-tool                 camel-ai-resource
camel-mcp-server              camel-mcp-server-api          camel-ai-observability
camel-ai-observability-api    camel-ai-prompt               camel-langchain4j-agent
camel-langchain4j-agent-api   camel-langchain4j-chat        camel-langchain4j-ingest
camel-docling                 camel-openai                  camel-semantic
camel-semantic-openai         camel-semantic-wolf-defender  camel-kserve
camel-qdrant  camel-pgvector  camel-milvus  camel-neo4j  camel-pinecone  camel-weaviate
```

Plus `dsl/camel-jbang/camel-jbang-plugin-mcp` for the coding-assistant surface.

**Three things follow, and two of them contradict the secondary sources:**

1. **`camel-ai-tool` is a unified tool component.** One route is simultaneously
   callable by LangChain4j, Spring AI, OpenAI-shaped clients and any MCP client. It
   supersedes `camel-langchain4j-tools` (deprecated) and `camel-spring-ai-tools`
   (removed). *Practical consequence:* a client with 200 existing Camel routes into
   their ERP has 200 candidate agent tools and zero new integration code to write.
2. **The MCP artefact is `camel-mcp-server`, not `camel-mcp`.** Apache's own blog uses
   the short form; the tree does not contain it. Copying the blog gives a dependency
   coordinate that does not resolve.
3. **`camel-a2a` exists and no blog, roundup or release note mentioned it.** It was
   found only by reading the module list. When a layer is this new the `pom.xml` is more
   current than anything written about it — **read the manifest, not the announcement.**

### `camel-semantic-wolf-defender` — a guardrail in a place this KB had no guardrail

Its POM: *"Detect prompt injection in text using local Wolf-Defender inference"*,
configured by `wolfDefender.modelDirectory` and `wolfDefender.download`.

Every guardrail this KB holds — `protectai/llm-guard`, `guardrails-ai/guardrails`,
`nvidia-nemo/guardrails`, `protectai/rebuff` — sits **beside the model**. This one sits
**inside the integration route**: on the path the payload actually travels, as a step
in the mediation, running **locally** with no call out to a scanning service. For an
estate that will not send payloads to a third party — which is most regulated EMEA and
APAC clients — that placement is the difference between a deployable control and a
rejected one. Apache-2.0, inside a project the client's integration team already runs.

---

## Machine-readable control evidence — the OSCAL layer (added eighth pass, 2026-11-21)

**Zero occurrences of OSCAL across all nine files before this pass.** This KB has
argued since its fourth pass that governance became a buying requirement, and in
trend 14 that ISO/IEC 42001 is a procurement gate rather than a standard to cite. It
had no tooling that *produces the evidence* — only tooling that produces the behaviour
the evidence would describe. OSCAL is the format US federal programmes ingest and
auditors increasingly accept.

| Repo | Stars | Licencia (byte-read) | Último push | Rol |
|---|---|---|---|---|
| [usnistgov/OSCAL](https://github.com/usnistgov/OSCAL) | 972 ★ | **worldwide public domain** (badge: `NOASSERTION`) | 2026-11-16 | The schema: catalogs, profiles, component definitions, SSPs, assessment plans, assessment results — XML/JSON/YAML. |
| [usnistgov/oscal-content](https://github.com/usnistgov/oscal-content) | 477 ★ | worldwide public domain | 2026-10-27 | NIST SP 800-53 and companions already expressed as OSCAL catalogs. Import controls; do not transcribe them. |
| [usnistgov/oscal-cli](https://github.com/usnistgov/oscal-cli) | 72 ★ | worldwide public domain | 2026-11-19 | Validate and convert. This is the CI gate. |
| [oscal-compass/compliance-trestle](https://github.com/oscal-compass/compliance-trestle) | 292 ★ | Apache-2.0 (11,357 B) | 2026-11-17 | Authoring platform — compliance-as-code over OSCAL with CI. v5 current, OSCAL 1.2.1; PyPI 5.2.1, v4 in maintenance. |
| [oscal-compass/compliance-trestle-mcp](https://github.com/oscal-compass/compliance-trestle-mcp) | 2 ★ | Apache-2.0 (11,357 B) | 2026-11-11 | **The keystone of Receta 17.** Trestle over MCP, registered `io.github.oscal-compass/compliance-trestle-mcp`. |
| [oscal-compass/compliance-trestle-fedramp](https://github.com/oscal-compass/compliance-trestle-fedramp) | 3 ★ | Apache-2.0 | 2026-08-27 | FedRAMP profile. **North America only** — see the EMEA caveat below. |
| [complytime/complyctl](https://github.com/complytime/complyctl) | 38 ★ | Apache-2.0 (11,342 B) | 2026-11-21 | **The runtime, and the correct slug.** Pulls [Gemara](https://github.com/ossf/gemara) policy layers from an **OCI registry**, scans via providers, emits **EvaluationLog, OSCAL, SARIF, Markdown**. Carries OpenSSF Best Practices and Scorecard badges. |
| [complytime/complytime-providers](https://github.com/complytime/complytime-providers) | 1 ★ | Apache-2.0 | 2026-11-20 | Providers as standalone executables bridging complyctl to **OpenSCAP, Ampel and OPA**, discovered by naming convention `complyctl-provider-*`. Description notes they were *"formerly plugins"*. |
| [complytime/complypack](https://github.com/complytime/complypack) | 1 ★ | Apache-2.0 | 2026-11-20 | Assessment-logic packaging. |
| [complytime/complytime-collector-components](https://github.com/complytime/complytime-collector-components) | 5 ★ | Apache-2.0 | 2026-11-18 | *"A policy-driven observability toolkit for compliance monitoring"* — the continuous half, against complyctl's point-in-time scan. |
| [ossf/gemara](https://github.com/ossf/gemara) | not measured — the repo is not indexed by the GitHub search API, so no star figure is quoted | Apache-2.0 (11,379 B) | live 2026-11-21 | The OpenSSF policy model complyctl consumes. |
| [ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) | — | **BSD-3-Clause** (1,552 B) | — | Hardening content. The only `LICENSE` in this batch whose first line is a machine-readable SPDX identifier. |
| [ComplianceAsCode/oscal-content](https://github.com/ComplianceAsCode/oscal-content) | 7 ★ | Apache-2.0 (11,356 B) | 2026-05-11 | OSCAL test content paired with ComplyTime, synced bidirectionally with the above. |

### The sentence that makes this layer cheap to sell

**`open-policy-agent/opa` is already in this KB**, held since the governance-substrate
section as an authorisation engine — and it is a **complyctl provider**. The same
policy engine Globant already proposes for runtime authorisation decisions can also
generate the auditor's evidence artefacts. One component, two jobs, no new vendor.

### Licence caveat — public domain is not strictly better than Apache-2.0

The four NIST repositories are **worldwide public domain**, which reads as maximally
permissive and in one respect is. But a US-Government public-domain dedication carries
**no express patent grant and no warranty disclaimer**, both of which Apache-2.0 gives
explicitly. For anything Globant *redistributes* inside a client deliverable, a legal
review may well prefer the Apache-2.0 siblings (`oscal-compass/*`, `complytime/*`) over
the NIST originals, even though the NIST licence is nominally freer. **Do not treat
"public domain" as the end of the licence conversation; it is the start of a different
one.**

### Regional caveat — OSCAL is a North American artefact, and the EMEA equivalent does not exist

OSCAL is NIST's, and its profile ecosystem is FedRAMP-shaped. The EU AI Act's Annex IV
technical documentation obligation has **no machine-readable canonical format** and no
equivalent open-source toolchain. OSCAL is the nearest transferable artefact and it is
genuinely useful as an evidence *substrate* in EMEA — but it is **not** an AI Act
conformity format, and it must never be presented to an EMEA client as one. See
`intel/market.md` for the regional placement.

### Two traps in this layer

**1. Archived, while its own documentation presents it as live.**
[complytime/complyscribe](https://github.com/complytime/complyscribe) — 21 ★,
Apache-2.0 — is **archived** (last push 2026-05-11), yet a ComplyTime QuickStart site
and a May-2026 write-up both present it as the route to bring trestle into CI/CD. The
live path is `complyctl` + `complytime-providers`. This is the **seventh**
archived-or-abandoned-but-still-recommended project this KB has caught.

**2. The org-named repo is not the product.**
[complytime/complytime](https://github.com/complytime/complytime) has **1 star** and
holds *"design and proposed enhancements"*. The product is `complyctl` at 38 ★.
Composing `owner/owner` from an org name would have placed a one-star proposals
repository in a foundations table as the flagship runtime. **List the org and read the
descriptions; never compose the slug.**

---

## Embedded vector store — added eighth pass, 2026-11-21

| Repo | Stars | Licencia | Último push | Rol |
|---|---|---|---|---|
| [lancedb/lancedb](https://github.com/lancedb/lancedb) | 11,960 ★ | Apache-2.0 (11,357 B, byte-read) | 2026-11-21 | Embedded multimodal vector store. Fills the in-process slot beside `qdrant/qdrant`, for retrieval that must run inside the client's own process with no service to procure or network hop to approve. |

**Do not pick up the siblings with the parent.**
`lancedb/lancedb-mcp-server` is `NOASSERTION` **and** last pushed 2025-04-25;
`lancedb/lancedb-vercel-chatbot` is `NOASSERTION` and last pushed 2024-03-26. The
healthy core and the stale satellites share an org name and nothing else — the same
pattern the fourth pass recorded for other projects.

## Rename ledger addition (eighth pass)

| Cited path | Canonical today | Evidence |
|---|---|---|
| `princeton-nlp/SWE-agent` | [SWE-agent/SWE-agent](https://github.com/SWE-agent/SWE-agent) | 20,845 ★, MIT (1,146 B byte-read), pushed 2026-11-16. The old path redirects, which is why every 2026 roundup still prints the stale owner. Sibling [SWE-agent/mini-swe-agent](https://github.com/SWE-agent/mini-swe-agent), 9,925 ★, MIT. |
| `complytime/complyscribe` (as "the CI tool") | [complytime/complyctl](https://github.com/complytime/complyctl) + [complytime/complytime-providers](https://github.com/complytime/complytime-providers) | complyscribe archived 2026-05-11; providers were "formerly plugins". |

## The provenance boundary — proving what the agent is made of (added ninth pass, 2026-11-24)

The seventh pass asked *what may the agent read*. The eighth asked *what may it change, and what
proves it was allowed to*. Both answers assume something this KB had never established: **that the
components doing the reading and writing are what they claim to be.**

**The layer was measurably empty.** Before this pass, across all nine files:
`sigstore` 0, `cosign` 0, `in-toto` 0, `SLSA` 0, `attestation` 0, `syft` 0, `grype` 0, `trivy` 0,
`dependency-track` 0, `guac` 0, `model card` 0. `SBOM` scored 24 hits — **entirely as a compliance
noun in the AI-BOM section above, with no tool that produces, signs or consumes one.**

**The distinction that organises this section, and it is the sales argument too:**

- An **inventory** is a list you asserted. (`CycloneDX`, `sbom-tools`, `Trusera/ai-bom` — already above.)
- A **scan** is an opinion, at one moment, by one tool. (`SkillSpector`, `snyk/agent-scan` — already above.)
- **Provenance is a verifiable claim about origin**, signed by an identity, recorded in a log a third
  party can check, and **re-checkable later without trusting the party who made it.**

A client asking "is this MCP server safe?" is asking for a scan. A client asking "can you prove in
two years' time that the model and tools in this decision were the ones we approved?" is asking for
provenance, and **nothing above this line could answer it.**

### Signing, attestation and transparency — the primitives

Every row verified 2026-11-24: existence and HEAD sha via `git ls-remote`, licence **byte-read from
the repository's own `LICENSE`** over `raw.githubusercontent.com`, last-commit date from a shallow
bare clone. **Stars, the `archived` flag and the SPDX badge come from `gh api search/repositories`,
which works in this session** — unlike `gh api repos/<owner>/<repo>` and raw `api.github.com`, both of
which return **403**. One repository, `CycloneDX/cdxgen`, is **absent from that search index** (HTTP
422, the same blind spot the eighth pass hit on `ossf/gemara`): its figures are page-read and its
licence byte-read, and **a repository missing from the index is not a repository that does not exist** —
`git ls-remote` says it is live.

| Repo | Licence (byte-read) | ★ | Last commit | Role in an agent estate |
|---|---|---|---|---|
| [sigstore/cosign](https://github.com/sigstore/cosign) | Apache-2.0 | 6,468 | 2026-11-23 | Keyless signing and verification for containers and blobs. The default way to sign the image an agent runs in without operating a key management ceremony. |
| [sigstore/rekor](https://github.com/sigstore/rekor) | Apache-2.0 | 1,238 | 2026-11-22 | The append-only transparency log. This is the component that makes a signature *re-checkable by a third party later*, which is the whole difference from a scan. |
| [sigstore/model-transparency](https://github.com/sigstore/model-transparency) | Apache-2.0 | 250 | 2026-11-23 | **Signs model weights, not code.** Signs a whole model directory, emitting a Sigstore bundle containing a DSSE envelope wrapping an **in-toto statement** that lists every file as a `(path, digest)` pair; verification recomputes the hashes. Supports keyless OIDC, traditional keys, and **PKCS#11 hardware**. 250 ★ — the *only* permissive tool located that signs a model, and the KB had nothing here. |
| [in-toto/in-toto](https://github.com/in-toto/in-toto) | Apache-2.0 (badge says `NOASSERTION`) | 1,056 | **2026-08-27** | The supply-chain integrity framework the attestation format comes from. **Default branch is `develop`, not `main`** — a shallow clone of HEAD gets `develop`. Three months since last commit; it is a specification reference implementation, so read that as stability, not abandonment. |
| [in-toto/witness](https://github.com/in-toto/witness) | Apache-2.0 | 622 | 2026-11-23 (push); `main` commit 2026-09-21 | **The bridge to two layers this KB already holds.** Records an attestation at each pipeline step, with **keyless signing via Sigstore *and SPIFFE/SPIRE*** (see "Workload identity for agents" above) and an **embedded OPA Rego policy engine** (see "Identity, policy & isolation"). Also RFC3161 timestamping. Two components already in this KB gain a second job here. |
| [in-toto/attestation](https://github.com/in-toto/attestation) | Apache-2.0 (badge says `NOASSERTION`) | 396 | 2026-11-23 | The attestation *spec* and predicate types. Cite it rather than inventing a payload shape. |

### SBOM production → consumption — and the half this KB was missing

The AI-BOM section above produces documents. **Nothing consumed them.** An SBOM that is generated and
filed is a compliance artefact; an SBOM that is continuously matched against a vulnerability feed is a
control. These are the consumption half.

| Repo | Licence (byte-read) | ★ | Last commit | Role |
|---|---|---|---|---|
| [anchore/syft](https://github.com/anchore/syft) | Apache-2.0 | 9,957 | 2026-11-23 | SBOM **generation** from container images and filesystems. The de-facto producer; CycloneDX and SPDX output. |
| [anchore/grype](https://github.com/anchore/grype) | Apache-2.0 | 13,339 | 2026-11-20 | Vulnerability scanner that **takes an SBOM as input**. Syft → Grype is the minimal produce-then-consume pair, and it runs offline against a cached DB. |
| [aquasecurity/trivy](https://github.com/aquasecurity/trivy) | Apache-2.0 | 39,670 | 2026-11-24 | The largest tool in this layer by a wide margin: vulnerabilities, misconfiguration, secrets **and SBOM** across containers, Kubernetes, repos and clouds. If a client already runs one thing here, it is this. |
| [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track) | Apache-2.0 | 4,513 | 2026-11-23 | **The continuous-monitoring platform**, and the piece that converts a one-off inventory into a standing control: ingest SBOMs, re-evaluate against new advisories, alert on drift. OWASP flagship. See `verticals/solutions.md`. |
| [guacsec/guac](https://github.com/guacsec/guac) | Apache-2.0 | 1,581 | 2026-11-24 | Aggregates SBOMs **and attestations** into one queryable graph: CycloneDX, SPDX, **in-toto ITE6, DSSE, SLSA**, and VEX in both CSAF and OpenVEX. The only tool located that answers cross-cutting questions ("which deployed agents contain this component?"). **Caveat from its own page: identifiers are often absent, so it links metadata with heuristics and ingestion errors occur.** |
| [google/osv-scanner](https://github.com/google/osv-scanner) | Apache-2.0 | 11,612 | 2026-11-23 | Scans lockfiles and images against OSV.dev. Note honestly: **its page does not claim SBOM ingestion** — do not assume the SBOM path without testing it. |
| [CycloneDX/cdxgen](https://github.com/CycloneDX/cdxgen) | Apache-2.0 (byte-read) | 1.1k (page-read — **absent from the GitHub search index**, see below) | 2026-11-24 | **The wire between this section and the AI-BOM section above.** Dedicated `aibom` command covering *prompt files, AI services, MCP configs and model metadata*, accepting Hugging Face purls and direct `Modelfile`/`.gguf` inputs — and it **submits directly to a Dependency-Track server.** Gotcha from its own page: `--component-type` does **not** by itself enable model discovery. |

### Format translation and VEX — the unglamorous pieces that decide whether any of it composes

| Repo | Licence (byte-read) | ★ | Last commit | Note |
|---|---|---|---|---|
| [protobom/protobom](https://github.com/protobom/protobom) | Apache-2.0 | 339 | 2026-11-23 | Neutral protobuf representation that converts **SPDX 2.2/2.3/3.0.1 ↔ CycloneDX 1.2–1.7**. The answer when the client's scanner emits one format and their auditor demands the other — which, after CISA 2026 dropped SWID, is the only remaining axis of disagreement. |
| [openvex/vexctl](https://github.com/openvex/vexctl) | Apache-2.0 | 222 | 2026-11-23 | Produces VEX statements: *"this CVE is present but not exploitable here."* The tool that stops a 4,000-finding SBOM report from being politically unusable. |
| [openvex/spec](https://github.com/openvex/spec) | **CC0-1.0** | 203 | 2026-10-30 | The spec, public-domain dedicated. **CC0 is not "better than Apache-2.0"** — same caveat as the OSCAL section: no patent grant, no warranty disclaimer. |
| [bomctl/bomctl](https://github.com/bomctl/bomctl) | Apache-2.0 | 159 | **`main` commit 2025-09-10; last push 2025-11-20** | Format-agnostic SBOM manipulation. **Default branch untouched for fourteen months, no push for twelve.** Listed so nobody rediscovers it as new; `protobom` is the maintained path for the same job. |

### The SLSA tooling has declared itself unmaintained — read the README, not the repo page

This is the pass's second headline, it is primary-source, and **it inverts this KB's own detection
heuristic.**

Five prior passes recorded archived-but-still-starred projects whose READMEs *failed to say so*. The
rule that produced was: trust the repo metadata over the docs. **Here the opposite holds.** Both
reference SLSA tools are **not archived**, carry recent release tags (`v2.7.1`, `v2.1.0`) and look
alive on their repo pages — and both READMEs say, at line 11:

> *"This project is **no longer actively maintained**. We are working on guidance and simpler tooling to replace it."*

| Repo | State as measured 2026-11-24 | What the README instructs instead |
|---|---|---|
| [slsa-framework/slsa-verifier](https://github.com/slsa-framework/slsa-verifier) | Apache-2.0, **352 ★**. `main` last commit **2026-08-06**, and that commit is literally *"docs: Add maintenance status for slsa-verifier (#898)"*. Tags up to `v2.7.1`. **Default branch (`HEAD`) resolves to `refs/heads/Hayden-IO-patch-1`**, a personal patch branch at a *different* sha from `main` — so a plain `git clone` does not get `main`. | Verify GitHub-generated attestations with **`gh attestation verify`**. |
| [slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator) | Apache-2.0, **610 ★**. `main` last commit **2026-08-06**. README: most recent release **v2.1.0, February 2025**; existing provenance **remains valid** and the reusable workflows **continue to work**, but *"should not be assumed to receive updates, including for GitHub Actions runtime deprecations."* | Generate provenance with **GitHub artifact attestations**. |

**The sentence to carry into an engagement**, quoted from the generator's own README because it is the
migration risk in one line: *"GitHub artifact attestations are verified with `gh attestation verify`
rather than with slsa-verifier, so **migrating changes how your consumers verify**."* A provenance
migration is not an internal refactor — it breaks every downstream verifier at once.

**And the strategic reading, which is the part a client should hear from Globant and not from a vendor:**
the open-source, CI-agnostic SLSA verification path has been retired in favour of **a platform feature of
a single vendor.** `gh attestation` is genuinely good — but it is GitHub's. An estate on GitLab,
Bitbucket, Jenkins or self-hosted CI has **no drop-in successor named by the project itself**, and this
pass searched for a GitLab equivalent and **did not find one** (see "Gaps measured" below). For those
clients the remaining permissive path is `cosign` + `in-toto`/`witness` + `rekor` assembled by hand —
which is studio work, not a product purchase.

**One number puts this layer in proportion before anyone quotes a budget.** The reference SLSA
verifier has **352 stars**; the generator has **610**. `trivy`, in the same supply-chain family, has
**39,670**. The provenance *primitives* an auditor will ask about are two orders of magnitude less
adopted than the scanner a client has probably already installed — which is precisely why this is
delivery work rather than a procurement line, and why **"we already run Trivy" is not an answer to
"can you prove this model is the one you approved".**

### Measured in this environment: "offline verification" has an online bootstrap

`gh` 2.89.0 is present here and exposes `gh attestation verify`, `download` and `trusted-root`. The
documented air-gap story is: fetch `trusted_root.jsonl` once, then verify offline with
`--custom-trusted-root`. **Run in this session's restricted network, the fetch fails closed:**

```
$ gh attestation trusted-root
Failed to verify the TUF repository: failed to create TUF client: failed to load metadata:
tuf refresh failed: Get "https://tuf-repo-cdn.sigstore.dev/14.root.json": Forbidden
exit=1, 0 bytes written
```

**So the trusted root cannot be *obtained* offline — only *used* offline once obtained.** For an
air-gapped or egress-filtered estate this is a concrete, costed prerequisite, not a footnote:
`tuf-repo-cdn.sigstore.dev` must be reachable from *some* permitted host at least once, the resulting
root must be pinned and shipped inward as a controlled artefact, and its refresh must be owned by
someone. Verification **fails closed**, which is the correct behaviour and also means a forgotten root
refresh is an outage. This was measured, not cited.

### MCP server provenance — the registry layer, and what it does and does not prove

The "Agent skill supply chain" section above covers *scanning* a server. This covers **establishing who
published it.**

| Repo | Licence | ★ | Last commit | What it establishes |
|---|---|---|---|---|
| [modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry) | **Mixed — see below** (badge says `NOASSERTION`) | 7,496 | 2026-11-24 | The community registry, run by a Registry Working Group. **It validates namespace ownership at publish time: GitHub OAuth, GitHub OIDC, DNS verification and HTTP verification.** DNS verification proving control of a domain and its subdomains is the real provenance primitive here — it is the difference between "a server called `acme-crm`" and "a server published by whoever controls `acme.com`". **Still a preview release, not GA** — its own page says so, with an API freeze at v0.1 pending v1. |
| [stacklok/toolhive](https://github.com/stacklok/toolhive) | Apache-2.0 | 2,355 | 2026-11-23 | Runs and manages MCP servers as an enterprise platform — the enforcement point that can refuse an unverified server. See `verticals/solutions.md`. |
| [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) | Apache-2.0 | 1,057 | 2026-11-24 | Gateway **and** registry with OAuth, and **security scanning at registration** — unsafe servers, agents and skills are held for review. AWS-oriented deployment (EKS/ECS/EC2, Bedrock). This is the shape to copy: admission control at registration, not at runtime. |
| [cisco-ai-defense/mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) | Apache-2.0 | 1,125 | 2026-11-23 (push); `main` commit 2026-11-19 | **The locally-runnable alternative to `snyk/agent-scan`, and that is why it matters.** Per its README the Cisco AI Defense API key is needed **only for the API analyzer**; YARA, readiness, prompt-defense, static-JSON and vulnerable-package scans need **no key at all**, and the LLM analyzer accepts a **local endpoint such as Ollama** with a placeholder key. For the sovereignty-constrained client that cannot use a metered cloud scanner, this is the candidate — test it, do not assume it. |

**The licence on the MCP registry is not a single SPDX identifier, and this is a new licence class for
this KB.** Byte-read from its `LICENSE`:

> *"The MCP project is undergoing a licensing transition from the MIT License to the Apache License,
> Version 2.0… Contributions made by authors who originally licensed their work under the MIT License
> and who have not yet granted explicit permission to relicense **remain licensed under the MIT
> License**. No rights beyond those granted by the applicable original license are conveyed."*

So the repository is a **per-contribution mixture of MIT and Apache-2.0**, mid-migration. Both are
permissive and Globant can build on either, so this is *not* a blocker — but **"modelcontextprotocol/registry
is Apache-2.0" is a false statement**, and so is "it is MIT". The transition is also **partial across the
org**: the same notice is on `modelcontextprotocol/modelcontextprotocol` and `modelcontextprotocol/servers`,
while [`modelcontextprotocol/python-sdk`](https://github.com/modelcontextprotocol/python-sdk) is **still plain
MIT**. Record the licence per repository and per date, never per organisation.

### Traps found this pass

1. **Archived yesterday, recommended today.** [NimbleBrainInc/mpak](https://github.com/NimbleBrainInc/mpak)
   (Apache-2.0, 14 ★) — an MCP package registry with bundle signing, GitHub-OIDC provenance and an
   **L1–L4 trust-score ladder** topping out at "Attested" — was **archived by its owner on 2026-11-23**,
   *the day before this pass*, with `registry.mpak.dev` to be shut down and servers moved to a
   vendor catalogue. A search engine offered it to this pass as a live finding. **This is the eighth
   archived-but-recommended project in nine passes, and the freshest possible demonstration of why
   every row in this KB is verified on the day it is written.** Structurally it was a real project —
   163 commits, monorepo, Helm chart, CI — and 14 stars. Adoption, not quality, is what killed it.
2. **Cross-ecosystem name collision in security tooling.** `uvx mcp-scan` and `npx mcp-scan` are
   different vendors' software. Full evidence in `agents/top.md`.
3. **A default branch that is somebody's patch branch.** `slsa-verifier`'s `HEAD` → `Hayden-IO-patch-1`.
   For a tool whose purpose is verifying provenance, clone-time ambiguity is the wrong failure to have.
   Always `git clone --branch main` for this repo, or install the released binary.
4. **`develop`, not `main`.** `in-toto/in-toto` defaults to `develop`. A licence or source read against
   `main` is reading a branch the project does not treat as current.
5. **Idle-but-shiny.** `bomctl` (14 months), `mcpshield/mcpshield` (MIT, last commit 2026-02-18, 9 months)
   both present well and are not maintained at the cadence this layer needs.

### Method notes — two new ways to be wrong, and one new instrument

- **Check maintenance status in *both* directions.** Passes 3–8 learned "the repo page knows better than
  the docs" from seven archived projects whose READMEs were silent. SLSA is the inverse: **repo page
  says alive, README says unmaintained.** Neither source dominates. Read both, every time.
- **A permissive licence does not imply a runnable tool.** `snyk/agent-scan` is Apache-2.0 and cannot
  scan without a vendor token and a network call; `cisco-ai-defense/mcp-scanner` is Apache-2.0 and most
  of it runs with no key. **Licence describes redistribution rights; it says nothing about whether the
  capability is local.** This is the same shape as the seventh pass's Onyx `ee/` finding and the sixth
  pass's gated-feature findings — now stated as a general rule.
- **New instrument, reusable by the whole fleet.** `api.github.com` is 403 here and `github.com`/Atom
  feeds are proxy-blocked to `curl`, but three channels work and together replace the API:
  (1) `git ls-remote --symref <url> HEAD` → existence, HEAD sha **and the real default branch**;
  (2) `raw.githubusercontent.com/<repo>/<branch>/LICENSE` → licence **bytes**;
  (3) `git clone --bare --depth 1 --filter=blob:none` then `git log -1 --format=%cI` → authoritative
  last-commit date. **Stars, `archived` and the SPDX badge come from `gh api search/repositories`,
  which works even though `gh api repos/<owner>/<repo>` and `api.github.com` are both 403** — that is
  the channel that caught `mpak`. `git ls-remote --tags` gives the release ladder, which is what
  distinguishes "idle" from "stable and released".
- **`pushed_at` and "last commit on the default branch" are different measurements, and the gap is
  information.** `bomctl` last pushed 2025-11-20 but its `main` has not moved since 2025-09-10;
  `in-toto/witness` shows a 2026-11-23 push over a `main` whose last commit is 2026-09-21. Quote which
  one you mean, because "pushed yesterday" over a frozen default branch is how an idle project looks alive.

### Gaps measured this pass — stated, not left silent

- **No GitLab/non-GitHub provenance successor located.** Searched for a GitLab equivalent to GitHub
  artifact attestations and for non-GitHub offline verification paths; results returned `gh`-specific
  material and third-party *offline verifiers of GitHub attestations*
  ([combinatrix-ai/attestation-verify](https://github.com/combinatrix-ai/attestation-verify),
  [torstei/apt-attest](https://github.com/torstei/apt-attest) — **existence confirmed by `git ls-remote`
  on 2026-11-24; licences not byte-read, maintenance and quality not assessed. Leads to evaluate, not
  recommendations**, and note that both verify *GitHub's* attestations rather than replacing them). **Recorded as an open gap, not as an absence of need** — it is
  the single largest unserved requirement in this layer.
- **No dedicated open-source MCP *signing* tool located.** The registry proves *namespace ownership*;
  nothing located signs the server artefact itself. A 2026 systematisation-of-knowledge paper argues
  the need exists. `cosign` on the server's container image is the available substitute and is what
  Receta 18 uses.
- **LATAM-origin repositories in this layer: zero, measured.** See `intel/market.md`.

---

## The containment boundary — what the agent may *reach*, and what *stops* it (added tenth pass, 2026-11-24)

> **This layer was measurably empty before this pass.** `cilium`, `istio`, `linkerd`, `kyverno`,
> `gatekeeper`, `falco`, `tetragon`, `gVisor`, `Firecracker`, `Kata`, `eBPF`, `mTLS`,
> `NetworkPolicy`, `service mesh`, `Agent Sandbox` and `Prempti` all scored **zero hits across all
> nine files**. `egress` scored eight hits, every one of them prose — the word was used as an
> *adjective describing this session's own proxy* ("egress-restricted estate"), never as a control
> anyone builds. The KB could say an estate was egress-restricted; it could not say with what.
>
> **Verified 2026-11-24** by four channels: existence and real default branch via
> `git ls-remote --symref`; licence **byte-read** from each `LICENSE` over
> `raw.githubusercontent.com`; stars, SPDX, `archived` and last-push via
> `gh api -X GET search/repositories -f q=repo:<owner>/<name>`; and README claims read from
> `raw.githubusercontent.com` rather than from the repo page. `api.github.com/repos/<o>/<r>` is
> **403** in this session for every repository not attached to it, and `github.com` HTML is **403**
> to `curl` while readable to the fetch tool — so the four channels are not redundancy, they are
> the only complete path.

### Why this is a separate layer and not a restatement of the sandbox entries already held

This KB already held **agent sandbox products** — `e2b-dev/e2b`, `daytonaio/daytona`,
`opensandbox-group/opensandbox`, `nvidia/openshell`. What it did not hold is the **isolation
primitive underneath them** or the **network control beside them**. That distinction is the whole
finding of this pass, and it is stated most plainly by the people who build the primitives:

| Source | Statement | What it rules out |
|---|---|---|
| [falcosecurity/prempti](https://github.com/falcosecurity/prempti) README | It is *"not a sandbox, OS-level security, or a substitute for least-privilege environments"*, and it covers *"the commands the agent requests, not the side effects those commands produce at runtime"* | Hook-level interception alone |
| Vercel's gVisor-vs-microVM comparison | Neither gVisor nor a microVM *"automatically denies outbound network access or enforces business permissions"* | Kernel isolation alone |
| Cloud Security Alliance review (Oct 2026) of a July 2026 incident | *No sandbox was technically broken*; an agent **wrote a file that a trusted, unsandboxed component later executed** | Both of the above, together |

**Containment is therefore four controls, not one:** intercept the request, isolate the kernel,
restrict the egress, detect at runtime. **No single project below provides all four.** One repo
attempts all four and it has 46 stars (`Azure/kars`, last row of the third table). That asymmetry —
a complete architecture at 46 stars, incomplete ones at 25,000 — is this pass's commercial finding
and is written up as trend 23 in `intel/trends.md`.

### Sandbox orchestration and the isolation primitives underneath it

| Repo | Licence | ★ | Last push | What it is, and the property that matters |
|---|---|---|---|---|
| [kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox) | Apache-2.0 | 4,703 | 2026-11-23 | **Kubernetes SIG Apps subproject — the emerging standard.** Its README states the scope exactly: *"Agent Sandbox is a sandbox orchestrator. It delegates low-level container isolation to secure 'Sandbox Runtimes' (like gVisor or Kata Containers) by managing Pods configured to use these runtimes (via `RuntimeClass`)."* CRDs `Sandbox`/`SandboxTemplate`/`SandboxClaim`/`SandboxWarmPool` on `agents.x-k8s.io/v1beta1`. **Past 1.0** — its README pins `v1.0.2` as the recommended production/GitOps version. Needs the Gateway API v1.5.0 CRD bundle for gateway-based client connections |
| [google/gvisor](https://github.com/google/gvisor) | Apache-2.0 (byte-read; LICENSE is 14,111 B — Apache plus appendices) | ~20.1k (page figure; see caveat) | — | **"Application Kernel for Containers."** A userspace kernel that intercepts syscalls; needs **no hardware virtualisation on the host**, which is what makes it the default choice on nodes you do not control. Trade-off is syscall-compatibility coverage |
| [firecracker-microvm/firecracker](https://github.com/firecracker-microvm/firecracker) | Apache-2.0 | 38,192 | 2026-11-23 | **"Secure and fast microVMs."** Each sandbox gets its **own guest kernel** — the stronger boundary, and the right answer when the agent's toolchain changes under you |
| [kata-containers/kata-containers](https://github.com/kata-containers/kata-containers) | Apache-2.0 | 9,208 | 2026-11-24 | Lightweight VMs that behave like containers; the other `RuntimeClass` target Agent Sandbox names. Pairs with confidential-computing hardware where the client requires it (`Azure/kars` uses Kata with AMD SEV-SNP as an option) |
| [dagger/container-use](https://github.com/dagger/container-use) | Apache-2.0 | 4,105 | 2026-11-14 | An MCP server **and** CLI (`cu`) that gives each coding agent a fresh container **on its own git branch**, logs its commands, and lets a human `git checkout` the agent's work to review it. Carries an **Experimental** badge and says it is *"in early development"* |

> **gvisor caveat, stated rather than hidden:** `gh api search/repositories -f q=repo:google/gvisor`
> returns **HTTP 422** (*"the listed users and repositories cannot be searched"*) in this session,
> so its star count is the **repo-page figure (~20.1k), not an API figure**, and its last-push date
> could not be established on this channel. Licence and existence **are** byte-read and confirmed.
> Treat the star count as approximate; treat the licence as solid.

### Network containment — the control the isolation primitives explicitly do not provide

| Repo | Licence | ★ | Last push | What it is, and the property that matters |
|---|---|---|---|---|
| [cilium/cilium](https://github.com/cilium/cilium) | **Split: Apache-2.0 user space; BPF templates dual GPL-2.0-only / BSD-2-Clause "at your option"** — see the licence note below | 25,896 | 2026-11-24 | **CNCF Graduated.** eBPF networking, security and observability. For this layer the feature that matters is the **egress gateway**: outbound traffic is steered through a designated gateway node, which is what produces a **fixed, allowlistable exit IP** for an agent workload. Identity-based policy, so rules survive pod IP churn |
| [cilium/tetragon](https://github.com/cilium/tetragon) | Apache-2.0 | 5,206 | 2026-11-24 | *"eBPF-based Security Observability and **Runtime Enforcement**"* — the enforcement half is the point: it can act on a security-significant event, not only record it. Same split-licence shape as Cilium (BSD-2-Clause/GPL badges on the BPF code) |
| [istio/istio](https://github.com/istio/istio) | Apache-2.0 | 38,533 | 2026-11-24 | Service mesh; supplies **workload-identity-based mTLS** between agent and tool. **Ambient mode** (`ztunnel`, Rust) gives this **without a sidecar per pod**, which is what makes it affordable on a warm pool of short-lived sandboxes |
| [linkerd/linkerd2](https://github.com/linkerd/linkerd2) | Apache-2.0 | 11,544 | 2026-11-24 | *"Ultralight, security-first service mesh."* The smaller-footprint alternative where Istio's surface is more than the engagement needs |
| [envoyproxy/gateway](https://github.com/envoyproxy/gateway) | Apache-2.0 | 3,162 | 2026-11-24 | Manages Envoy as a Gateway-API application gateway — the generic enforcement point the KB's AI-gateway row already assumed but never named |
| [mitmproxy/mitmproxy](https://github.com/mitmproxy/mitmproxy) | MIT | 47,161 | 2026-11-23 | *"Interactive TLS-capable intercepting HTTP proxy."* Not a production control — the **lab instrument**. It is how you answer "what does this agent actually send, and to where" **before** you write the allowlist that the other five rows enforce |

> **Licence note — a ninth licence class, and the first one that is split by *component* rather than
> by time, version or revenue.** Cilium's GitHub badge says `Apache-2.0` and the badge is correct;
> it is also incomplete. The repository's own `README.rst` says, byte-read on 2026-11-24:
> *"The Cilium user space components are licensed under the Apache License, Version 2.0. The BPF code
> templates are dual-licensed under the General Public License, Version 2.0 (only) and the 2-Clause
> BSD License (you can use the terms of either license, at your option)."* `bpf/COPYING` returns 200;
> top-level `LICENSE.BSD-2-Clause` returns 404, because the files live under `bpf/`.
> **This resolves in Globant's favour** — the *"at your option"* clause means the BSD-2-Clause branch
> may be taken, so nothing GPL need enter a client deliverable. But the resolution has to be
> *performed and documented*, because the artefact you ship is not licensed by the badge on the page
> that describes the repository. Record the elected option in the client's SBOM.

### Runtime detection, admission control, and the one component that sits inside the agent's loop

| Repo | Licence | ★ | Last push | What it is, and the property that matters |
|---|---|---|---|---|
| [falcosecurity/falco](https://github.com/falcosecurity/falco) | Apache-2.0 | 9,609 | 2026-11-23 | **CNCF Graduated.** *"Cloud Native Runtime Security"* — the syscall-level detection engine, and the base the next row extends |
| [falcosecurity/prempti](https://github.com/falcosecurity/prempti) | Apache-2.0 | **234** | **2026-09-21** | **The only verified repo in this pass that runs *inside* the agent's decision loop.** Falco-powered policy and visibility for AI **coding agents**: it registers on the agent's **hook API**, so a hook fires *before* each tool call, passes the event over a Unix socket to an embedded broker in a Falco plugin, and returns **allow / deny / ask**. Default mode is `guardrails` (verdicts enforced); `monitor` mode only logs. Supports **Claude Code** (Linux/macOS/Windows) and **Codex** (experimental, Linux only). **Two caveats to quote, both from its own README: "Experimental Preview", and last push 2026-09-21 — roughly two months idle at the date of this pass.** Treat as a pattern to implement, not a dependency to ship |
| [kyverno/kyverno](https://github.com/kyverno/kyverno) | Apache-2.0 | 8,375 | 2026-11-24 | *"Unified Policy as Code."* The admission gate: it is where "no sandbox pod may run without a `RuntimeClass` and a default-deny egress policy" becomes **mechanically unskippable** rather than a runbook step. **CNCF Incubating** — see the correction below |
| [open-policy-agent/gatekeeper](https://github.com/open-policy-agent/gatekeeper) | Apache-2.0 | 4,302 | 2026-11-21 | The OPA-family admission controller. This KB has held `open-policy-agent/opa` since early passes **as a policy engine** and never once named the component that applies it at admission — so OPA is now, like `complyctl`, one component doing two jobs |
| [aquasecurity/tracee](https://github.com/aquasecurity/tracee) | Apache-2.0 | 4,683 | 2026-11-01 | *"Linux Runtime Security and Forensics using eBPF."* The forensics angle is the one that matters after an incident, when the question is what the agent did, not what policy said it could do |

> **Correction, resolved against the primary source.** A 2026 comparison blog states that Kyverno
> **graduated** within CNCF in March 2026; another lists it as **Incubating**. Kyverno's **own README**
> says *"Cloud Native Computing Foundation (CNCF) Incubating project"*. **The repository wins.**
> Falco's and Cilium's READMEs both carry *graduated* badges, so the distinction is real and not an
> artefact of inconsistent self-description. This matters commercially only because CNCF maturity is
> quoted in procurement documents — quote it from the README, not from a roundup.

### Reference architectures — repos that compose the four controls instead of supplying one

| Repo | Licence | ★ | Last push | What it is, and the property that matters |
|---|---|---|---|---|
| [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) | MIT | 6,600 | 2026-11-23 | *"Policy enforcement, zero-trust identity, execution sandboxing, and reliability engineering for autonomous AI agents."* Ships a policy engine, a trust/identity layer, a **privilege-ring execution runtime**, SRE primitives (kill switches, SLOs), an MCP security gateway, shadow-AI discovery and an "Agent Mesh". Publishes to PyPI, npm, NuGet **and** crates.io. Claims full **OWASP Agentic Top 10** coverage — a claim worth testing rather than repeating |
| [agentgateway/agentgateway](https://github.com/agentgateway/agentgateway) | Apache-2.0 | 6,394 | 2026-11-24 | *"Next Generation Agentic Proxy for AI Agents and MCP servers"* — LLM gateway, MCP gateway, A2A gateway, inference routing, guardrails, auth/RBAC in one proxy. **A Linux Foundation project**, per its own page: this is the fifth independent confirmation of trend 5 (protocol surfaces moving from vendor control to foundation governance) and the first in the *enforcement* plane rather than the spec plane |
| [Azure/kars](https://github.com/Azure/kars) | MIT | **46** | 2026-11-24 | **"Agent Reference Stack for Kubernetes" — the most complete verified architecture for this layer, and the smallest.** It is the only repo found that implements all four controls: **hardened per-agent sandboxes** (agent UID 1000, router UID 1001, NetworkPolicy, seccomp; Kata + AMD SEV-SNP optional on AKS), **governed egress** (L7 allowlist/blocklist in an inference router, plus an `egress-guard` **iptables init container as a safety net**), **tool governance** (a `ToolPolicy` CRD for per-tool gates and an MCP gateway with per-tool allowlists) and **audit** (every router decision written to a **SHA-256 hash-chained** log). Composes components this KB already holds: **OpenClaw** and **Hermes** are 2 of its 8 supported agent runtimes, alongside OpenAI Agents SDK, Microsoft Agent Framework, LangGraph, Claude Agent SDK and Pydantic-AI; signing is **sigstore/cosign**. **Read the two disqualifiers in the same breath: its README says "Not an officially supported Microsoft product", an "open-source reference implementation" with no SLA, and its CRDs are at `v1alpha1`.** It says it *aims to align* with `kubernetes-sigs/agent-sandbox` and `agentgateway` and that **no formal integration exists yet** |

### Where this layer sits relative to what the KB already held

The containment layer does not replace anything in this file; it closes a circuit between four
sections that were previously unconnected.

- The **AI gateway** section (`litellm`, `bifrost`, `portkey`, `kong`, `helicone`) was already the
  place where an agent's model traffic is inspected. It was never stated that a gateway is only an
  enforcement point **if the sandbox cannot route around it**. Cilium's egress gateway, or kars's
  `egress-guard` iptables container, is what makes the AI gateway non-optional.
- The **entitlement boundary** (pass 7: OpenFGA, SpiceDB, Casbin, Keto) decides what a *user* may
  see. Containment decides what the *process* may reach. A correct OpenFGA model and an open egress
  path is still an exfiltration route, because the agent need not read a document it is forbidden
  to read if it can post the one it is allowed to read to an arbitrary host.
- The **write boundary** (pass 8: Camel, Dapr, Conductor) carries the agent's action into the system
  of record. Admission control (Kyverno/Gatekeeper) is what stops a workload reaching that channel
  without the controls attached.
- The **provenance boundary** (pass 9: cosign, in-toto, syft, OSCAL) proves what the agent is made
  of. Containment is the layer that makes provenance load-bearing: a signed image with unrestricted
  egress is a verified component doing unverifiable things.

### Gaps measured this pass — stated, not left silent

- **No agent-specific egress-inspection project located.** Every egress control found is a
  *generic* network control (Cilium, iptables, mesh) or a *generic* intercepting proxy (mitmproxy).
  The agent-aware inspection happens one layer up, in the AI/MCP gateway, which means **destination
  control and payload control are enforced by two different components with two different policy
  languages**. Nothing located unifies them. This is the clearest build-vs-buy gap in the layer.
- **`litsandbox` (Lightning AI) could not be verified.** Named by an InfoQ piece as an Agent Sandbox
  alternative; `git ls-remote` found **no repository** at `Lightning-AI/litsandbox` or
  `lightning-ai/litsandbox`. **Recorded as an unverified lead, deliberately not written as a finding.**
- **Red Hat is reported to publish a downstream build of `kubernetes-sigs/agent-sandbox`**
  (developers.redhat.com, July 2026). **Secondary-sourced** — the article was surfaced by search but
  the host could not be fetched in this session. Worth confirming for any OpenShift engagement,
  because a supported downstream build changes the support conversation entirely.
- **Agent Sandbox's network defaults are secondary-sourced and could not be confirmed.** A SIG Apps
  announcement is reported to say that from v0.4.3 sandboxes **default to strict network isolation,
  blocking internal cluster IPs and node metadata endpoints unless explicitly managed in the
  `SandboxTemplate`**. If true this is the single most important default in the layer — the node
  metadata endpoint is how a sandboxed process reaches cloud credentials. **It is not in the README
  that was byte-read**, and the two hosts that would settle it — `kubernetes.io` and
  `agent-sandbox.sigs.k8s.io` — **do not resolve in this session's network policy**. Verify against
  the `SandboxTemplate` CRD before quoting it to a client.
- **CNCF status of Agent Sandbox: not yet a CNCF project.** Google's announcement describes
  *"building Agent Sandbox as a CNCF project"* — future tense. It is a Kubernetes SIG Apps
  subproject today. Do not call it CNCF in a deliverable.
- **LATAM-origin repositories in this layer: zero, measured** with a Spanish-language instrument.
  See `intel/market.md`.

## The forge boundary — the inventory was measured with one instrument (added eleventh pass, 2026-11-24)

**This section is different from every other one in this file.** The ten passes before it each
added a *layer* of the agent stack. This one adds nothing to the stack: it reports what happened
when the KB was pointed at **itself** and asked how it knows what it knows. The answer changed
what goes in the tables, so it belongs here rather than only in `intel/trends.md`.

### The measurement, in one line, and it is reproducible

```
grep -roh 'github\.com/[A-Za-z0-9_.-]\+/[A-Za-z0-9_.-]\+' --include='*.md' . | sort -u | wc -l
→ 314
for f in gitlab.com sourceforge.net codeberg.org bitbucket.org git.sr.ht gitee.com huggingface.co; do
  grep -roh "$f" --include='*.md' . | wc -l; done
→ 0 0 0 0 0 0 0
```

**314 distinct repository addresses, every one of them on GitHub.** Not 314 of 320 — 314 of 314.
Before this pass the KB had never cited a repository that was not on github.com.

This is worth stating precisely because the obvious reading is wrong. It is **not** evidence that
nothing relevant exists elsewhere, and it is **not** simply a research failure to be fixed by
searching harder. It is both, in measurable proportions, and the proportions are the finding.

### Why the zero has two causes, and only one of them is fixable in a pass

Nine non-GitHub forges were probed directly from this session. **Eight refuse at the network
layer, before any question about content can be asked:**

| Forge | What it hosts that would matter here | Probe result, 2026-11-24 |
|---|---|---|
| `gitlab.com` | GitLab CE itself, Mayan EDMS, Flectra, GitLab's own AI work | **Reachable** — API `200`, unauthenticated |
| `codeberg.org` | Forgejo and the Gitea-fork ecosystem | `curl (56) CONNECT tunnel failed, response 403` |
| `foss.heptapod.net` | **Tryton** — a full ERP, canonical home | `CONNECT tunnel failed, 403` |
| `gitlab.opencode.de` | **openCoDE** — the German public-sector forge | `CONNECT tunnel failed, 403` |
| `git.openldap.org` | OpenLDAP — the directory under much of the estate | `CONNECT tunnel failed, 403` |
| `pagure.io` | Fedora/RHEL-adjacent enterprise tooling | `CONNECT tunnel failed, 403` |
| `gitee.com` | the dominant **APAC** forge | `CONNECT tunnel failed, 403` |
| `atomgit.com` | OpenAtom-hosted Chinese projects | `CONNECT tunnel failed, 403` |
| `invent.kde.org`, `salsa.debian.org` | upstream packaging of estate components | `CONNECT tunnel failed, 403` |

So the honest statement about eight of nine forges is **"not measured"**, not **"empty"** — and
the distinction is the whole point. `403 CONNECT` is the *instrument* failing, not the subject.
A future pass with a wider network policy may find material there; a future pass that greps, sees
zero and concludes "nothing exists" will publish a false finding. **Record the probe result next
to the grep result, always.**

The one forge that is reachable was then searched properly, and it was not empty. Everything
below was absent from all 8,355 lines of this KB before this pass.

### What is actually on the one reachable alternative forge — enterprise platforms

All rows verified 2026-11-24 via `GET https://gitlab.com/api/v4/projects/<url-encoded-path>?license=true`,
which returns licence, **default branch**, stars and last activity in a single call.

| Platform | Repo | Real licence | Stars | Default branch | Last activity | Why it matters here |
|---|---|---|---|---|---|---|
| **Mayan EDMS** | [mayan-edms/mayan-edms](https://gitlab.com/mayan-edms/mayan-edms) | **GPL-2.0-only** — byte-read from `LICENSE`; the API reported `other` | **683** | `master` | **2026-11-24** | *"Advanced enterprise Free Open Source DMS (document management system)."* The most-starred enterprise platform found off GitHub, and **active the day it was found.** Compare the Document/records section of `verticals/solutions.md`, which held Paperless-ngx, Documenso and GLPI and nothing from this forge. |
| **GitLab CE** | [gitlab-org/gitlab](https://gitlab.com/gitlab-org/gitlab) | **MIT** (API `mit`) | **6,209** | `master` | 2026-11-24 | The forge a large share of enterprise clients already self-host, and its community edition is **permissive**. Relevant as a *platform the agent plugs into*, in the same sense as Odoo. |
| **Flectra** | [flectra-hq/flectra](https://gitlab.com/flectra-hq/flectra) | GPL-3.0 | 252 | **`3.0`** | **2026-07-15** — ~4 months idle | *"Open Source ERP and CRM system built using python and postgresql."* An Odoo-lineage suite. Note the idleness **and** the non-standard default branch before quoting it. |
| **Dokos** | [dokos/dokos](https://gitlab.com/dokos/dokos) | GPL-3.0-or-later | 39 | **`develop`** | 2026-11-24 | *"based on ERPNext, powered by the Dodock/Frappe low-code framework."* A **French** ERPNext derivative, actively developed. The EMEA-localised sibling of the APAC-origin ERPNext this KB already holds. |

**The default-branch column is not decoration.** Of the GitLab projects verified this pass the
default branch was `master` four times, `main` seven times, `develop` once and **`3.0`** once. The
blind `main` → `master` → `develop` iteration this KB has used when GitHub's API was out of scope
would have failed outright on Flectra. GitLab returns the branch in the same call as the licence;
use it.

### What is on that forge in the agent layer — six permissive rows, and two refusals

| Repo | Licence | Stars | Last activity | What it is |
|---|---|---|---|---|
| [fforster/gitlab-mcp](https://gitlab.com/fforster/gitlab-mcp) | **MIT** | **85** | 2026-11-24 | *"A Model Context Protocol (MCP) server for GitLab."* The most-starred permissive MCP component found off GitHub. |
| [nagyv/gitlab-opencode](https://gitlab.com/nagyv/gitlab-opencode) | **MIT** | 59 | 2026-09-17 | *"Run any LLM model with a controlled environment in GitLab CI."* Runs a single LLM call with **custom tool permissions** inside CI — containment (pass 10) applied to the pipeline rather than to a pod. |
| [lx-industries/rmcp-openapi](https://gitlab.com/lx-industries/rmcp-openapi) | **MIT** | 13 | 2026-11-24 | Exposes **OpenAPI endpoints as MCP tools** on the official Rust MCP SDK. The Rust counterpart to the `camel-ai-tool` route-as-tool mechanism recorded in the eighth pass. |
| [lx-industries/rmcp-actix-web](https://gitlab.com/lx-industries/rmcp-actix-web) | **MIT** | 6 | 2026-11-23 | An `actix-web` backend for the same official Rust SDK. Pairs with the row above. |
| [lx-industries/openblob](https://gitlab.com/lx-industries/openblob) | **MIT** | 4 | 2026-11-24 | *"Distributed agentic workloads, no one in charge, everything under control."* Early, but it is a genuine agentic-execution project and it is permissive. |
| [gitlab-org/ai-engineering/agent-foundations/agentic-productivity](https://gitlab.com/gitlab-org/ai-engineering/agent-foundations/agentic-productivity) | **MIT** | 6 | 2026-10-01 | GitLab's own engineering org publishing *"agentic configs, skills, agents and workflows"* under MIT. Low stars, institutional origin — read it for the configs, not the code. |

**Two refusals, stated so nobody re-finds them and assumes they were missed:**

- **[gitlab-org/ai/lazy-mcp](https://gitlab.com/gitlab-org/ai/lazy-mcp)** — 20 stars, pushed
  2026-11-08, **no licence file anywhere in the repository root** (verified by listing the tree,
  not by trusting the API's empty licence field). GitLab Inc.'s own MCP project is therefore
  **not proposable**: no licence is not a permissive licence. Same verdict, same reason, as the
  LATAM energy project excluded in that KB's seventh pass.
- **[gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph)** —
  see immediately below. It is the most interesting thing found this pass and it cannot be built on.

### The find of the pass, and it is a warning: GitLab Orbit

| Property | Value, verified 2026-11-24 |
|---|---|
| Repo | [gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph) |
| Self-description | **"Software lifecycle context graph for AI agents"** |
| Licence reported by the API | `other` |
| **Licence actually in the repo** | **The GitLab Enterprise Edition (EE) licence** — byte-read from `LICENSE.md` |
| Stars / activity | 58 / **2026-11-24** — pushed the day it was found |
| Maturity | `version 1.9.1`, its own Helm charts, a published release badge |
| Shape | Rust (`Cargo.toml`) + npm workspaces, and `AGENTS.md`, `CONTEXT.md`, `skills/`, `.claude/`, `.opencode/`, `.agents/` in the root — **agent-native tooling, not a library** |

The EE licence text is unambiguous: the software *"may only be used in production, if you (and any
entity that you represent) have agreed to, and are in compliance with, the GitLab Subscription
Terms of Service … and otherwise have a valid GitLab Enterprise Edition subscription for the
correct number of user seats."*

**Three things follow, and all three are commercial rather than technical.**

1. **It is source-available, not open source.** `package.json` even carries `"private": true`.
   A client who finds it, reads "GitLab" and "knowledge graph for AI agents", and assumes the
   licence follows GitLab CE's **MIT**, is wrong — within the *same* `gitlab-org` namespace one
   project is MIT and this one requires paid seats. **The namespace is not the licence.**
2. **The community fork does not rescue it.** The README links a community fork at
   `gitlab-community/gitlab-org/orbit/knowledge-graph`. A fork of EE-licensed code carries the EE
   licence; the fork changes who can contribute, not what you may deploy.
3. **The permissive answer to the same problem is already in this KB, on the other forge.** Orbit
   is a context graph for agents. `verticals/solutions.md` holds **OpenMetadata, DataHub, Unity
   Catalog and OpenLineage — all Apache-2.0**. So the sentence for an engagement lead is:
   *the proprietary option is the one with the best marketing line, and the four permissive options
   are the ones the client can own.*

### The air-gap reference implementation — MIT, and it deploys a payload that is not

This is the single most directly reusable thing found this pass, and it extends the ninth pass's
air-gap work package from a described pattern into a **runnable, pinned bill of materials**.

| Property | Value, verified 2026-11-24 |
|---|---|
| Repo | [gitlab-com/public-sector/offline-lab](https://gitlab.com/gitlab-com/public-sector/offline-lab) |
| Licence | **MIT** (`LICENSE` present in root) |
| Stars | **4** |
| Last activity | **2026-11-24** |
| Owner | GitLab's **Public Sector** group — institutional origin, not a hobby repo |

Its own hero line: *"deploy and prove GitLab, Duo Agent Platform and Orbit in an offline
environment."* The request path it builds is **GitLab → AI Gateway → LiteLLM → AWS Bedrock**, with
Alloy shipping logs to Loki and Grafana. LiteLLM is already held in this KB; here it appears in a
stated reference topology rather than as a component.

**Four facts from its air-gapped runbook that are worth more than the repository itself:**

1. **It owns "the canonical list of external dependencies you must mirror internally."** That list
   is the deliverable an air-gapped engagement actually needs, and almost nobody writes it down.
2. **Every image is pinned by tag *and digest*** in `ansible/group_vars/all/versions.yml`, with the
   rule stated plainly: *"an air-gapped mirror plus a moving tag cannot be reproduced."* This is the
   ninth pass's provenance boundary expressed as an operational constraint — pinning by digest is
   the same primitive, reached from the deployment side.
3. **The agentic flows ship inside one image.** The AI Gateway image
   `…/code-suggestions/ai-assist/model-gateway:self-hosted-v<minor>-ee` *"includes the Duo Workflow
   service as a sub-process — mirroring this one image covers agentic flows; there is no separate
   workflow image."* That is a non-obvious deployment fact that changes a mirror plan.
4. **The default topology is not air-gapped.** The README says so: *"the default topology calls a
   hosted model provider; the air-gapped runbook is `docs/runbook/tracks/air-gapped.md`."* Third
   independent confirmation of this KB's standing rule that **"offline" is a separate track with its
   own bootstrap**, never a default.

**And the licence split that decides how to use it.** The IaC is MIT. What it deploys —
the **AI Gateway** ([gitlab-org/modelops/applied-ml/code-suggestions/ai-assist](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist),
64★, active 2026-11-24, **GitLab EE licence byte-read from `LICENSE`**) and **Orbit** — is not. So:

> **Take the method, not the payload.** The mirror list, the digest-pinning discipline, the
> internal-CA-on-every-hop posture and the placement of LiteLLM as the model boundary are all MIT
> and all transfer to *any* self-hosted agent platform. Deploying GitLab's own agent stack is a
> licence purchase, and a different conversation. Receta 21 builds the first and avoids the second.

### LATAM — the first non-GitHub LATAM finding in this KB, and a measured zero beside it

Probing the one reachable alternative forge in **Spanish** produced a split result, and the split
is itself the lesson.

| Probe (Spanish) | Result |
|---|---|
| `agente IA`, `empresa gestion`, `nomina` | **Measured zero.** Nothing above 5 stars; top hits are coursework, and `nomina` collides with `nominatim` because the search is accent-insensitive. |
| `facturacion` | **Not a zero** — a live cluster of fiscal-localisation projects |

| Repo | Licence | Stars | Last activity | What it is |
|---|---|---|---|---|
| [dansanti/facturacion_electronica](https://gitlab.com/dansanti/facturacion_electronica) | **GPL-3.0** | 11 | **2026-10-31** | *"Librería para la facturación Electrónica Chilena."* **Chilean** e-invoicing library — the first LATAM-origin, licence-resolved, non-GitHub repository in this KB. |
| [odoocoop/facturacion_electronica](https://gitlab.com/odoocoop/facturacion_electronica) | **Unresolved** — `429` after backoff | 4 | 2026-11-01 | An Odoo-cooperative LATAM localisation. Licence **not claimed**: the lookup rate-limited twice and a rate limit is not a licence verdict. |
| [torresoftware/apidian2020](https://gitlab.com/torresoftware/apidian2020) | **NONE** | 11 | 2026-06-23 | **Colombian DIAN** e-invoicing validation API. No licence file → **not proposable**, recorded so the next pass does not re-find it hopefully. |

**Why this matters more than 11 stars suggests.** `verticals/solutions.md` already argues that
regional fiscal localisation is what makes a suite deployable. The localisation work for Chile and
Colombia is **on a forge this KB had never looked at**, at star counts a GitHub-calibrated filter
would discard, and one of the three is permissively unusable for want of a licence file. The
commercial read: LATAM localisation is a **relicensing and stewardship conversation with named
authors**, not a greenfield build — the same conclusion the energy KB reached about its own LATAM
layer, arrived at independently here.

### The two migration remnants — why ranking a forge by stars misleads

| Repo | Stars | Licence | Last activity | What it actually is |
|---|---|---|---|---|
| [meltano/meltano](https://gitlab.com/meltano/meltano) (GitLab) | **554** | MIT | **2024-09-11** | Its own description: *"[This project was migrated to GitHub]."* Second-most-starred result for `erp`/`rag`-adjacent searches on the whole forge, and **dead for over two years.** This KB already holds Meltano at its live GitHub address. |
| [gitlab-org/duo-workflow/duo-workflow-service](https://gitlab.com/gitlab-org/duo-workflow/duo-workflow-service) | 10 | `other` | 2026-10-23 | Description: *"This project is migrated to …/code-suggestions/ai-assist."* A migration **within** the same forge. |

**The rule:** a star-ranked forge listing surfaces **abandoned mirrors near the top**, because stars
accumulate and never decay. Read `last_activity_at` and the description **before** the star count.
Both remnants above announce their own death in their description field — which is the cheapest
possible check and the one a star-sorted list invites you to skip.

### A category trap specific to this forge, and it explains the zero

Searching `gitlab.com` for **`agent`** returns, in star order: a browser user-agent switcher, a
Kubernetes cluster agent, `fetchmail`, a network-telemetry agent, and a VPN client. On this forge
the word "agent" is still dominated by its **pre-LLM meaning**. The same query on GitHub returns
LLM agents almost exclusively.

This is the forge-side twin of the vocabulary bias this KB has recorded before, and it has a
practical consequence: **a keyword sweep tuned on GitHub under-reports a non-GitHub forge**, which
is part of why the zero persisted for ten passes. What worked here was searching for the
**domain** (`erp`, `crm`, `facturacion`, `mcp`) rather than the **technology** (`agent`, `agentic`,
`langchain`). `mcp` was the one technology term that worked, because it is a new word with no
prior meaning to collide with.

### One repository where the rename happened in the description, not the path

[gitlab-org/cluster-integration/gitlab-agent](https://gitlab.com/gitlab-org/cluster-integration/gitlab-agent)
— **MIT**, 113★, `master`, active 2026-11-24 — is still at the path of the Kubernetes agent, but its
description now reads: *"**GitLab Relay** — host for various GitLab Features such as: Workflow Engine
(AutoFlow / autocore), GitLab CD, Job Router and Runner Controller."*

The ninth pass recorded renames that moved a repository's **owner and path**. This is the variant
that defeats the detector built for those: **the path is stable and the product changed underneath
it.** A link that still resolves, a licence that is still MIT, and a component that is no longer the
thing the KB described. Check the description against your own one-line summary, not just the HTTP
status.

---

## Twelfth pass, 2026-11-24 — the weights layer: licence instruments, model sources and the tools that inspect them

> **Read the column headings before reading the rows.** There is **no star column in this section**
> and that is deliberate: `api.github.com` returned **403 for every repository outside this session's
> scope**, so star counts and last-push dates **could not be measured this pass**. Rather than copy
> numbers from a listicle, each row carries the **licence, the byte-verified evidence for it, and the
> date it was read**. Every row below was fetched from `raw.githubusercontent.com` on **2026-11-24**.
>
> The organising finding is in `intel/trends.md` (trends 27 and 28): **a model's code repository and
> its weights are two different artefacts with two independent licences**, and reading the `LICENSE`
> file — the only thing a scanner reads — gives the wrong answer in both directions.

### A. The licence instruments themselves

| Repo | Licence | Verified evidence (read 2026-11-24) | Why it matters |
|---|---|---|---|
| [OpenMDW/OpenMDW](https://github.com/OpenMDW/OpenMDW) | The OpenMDW-1.1 text itself; repo docs **CC-BY-4.0** | Canonical text at `1.1/LICENSE.OpenMDW-1.1`, **2,619 bytes**. `README.md` 2,846 B. `FAQ.md` is a **171-byte stub** | **The eleventh licence class in this KB and the first written for weights.** One grant covering model + data + docs + code; adds **database and trade-secret** rights Apache-2.0 does not name; **outputs explicitly unrestricted**; no AUP, no user ceiling. Defensive termination reaches **copyright as well as patents**, which is why it is **not OSI-approved and has no SPDX ID** (review still open 2026-08-29). Rights clearance on training data is pushed to the licensee in capitals — permissive, **not an indemnity** |
| [meta-llama/llama-models](https://github.com/meta-llama/llama-models) | Per-model **Llama Community License Agreements** — not OSI open source | Root `LICENSE` is **78 bytes containing only a URL**. `models/llama4/LICENSE` **7,603 B**; llama3_3 **7,909 B**; llama3_2 **7,669 B**; llama3_1 **7,680 B**. `models/llama4/USE_POLICY.md` **5,824 B** | **The source of truth for the licence family most enterprise agents actually run on**, and the reason Llama repos are reported as `NOASSERTION`: a scanner at the root finds a pointer. **The EU multimodal carve-out is in `USE_POLICY.md:71`, not in any `LICENSE`** — `grep -c 'European Union'` returns 0 across all four licence files and 1 in the AUP |
| [spdx/spdx-3-model](https://github.com/spdx/spdx-3-model) | **Community-Spec-1.0** | `model/AI/Classes/AIPackage.md` **1,687 B**, header reads `SPDX-License-Identifier: Community-Spec-1.0` | The **SPDX 3.0 AI profile**, and it is **not** in `spdx/spdx-spec` — a path worth knowing. `AIPackage` subclasses `/Software/Package` with `informationAboutTraining`, `limitation`, `autonomyType`, `energyConsumption`, `hyperparameter`. **Every property is `minCount: 0`** — all optional, so a conformant AI SBOM can be silent about training data. Require the fields contractually |
| [CycloneDX/specification](https://github.com/CycloneDX/specification) | **Apache-2.0** | `LICENSE` **11,341 B**. `schema/bom-1.6.schema.json` **262,666 B**, containing `machine-learning-model`, `modelCard` and `modelParameters` | The **ML-BOM**, confirmed present in the published 1.6 schema by byte-read rather than by blog. The practical counterpart to SPDX's AI profile, and the one most client toolchains can already emit |

### B. Model sources whose licence this pass verified from a reachable primary

| Repo | Licence of the **weights** | Verified evidence (read 2026-11-24) | Posture for an engagement |
|---|---|---|---|
| [langtech-bsc/salamandra](https://github.com/langtech-bsc/salamandra) | **Apache-2.0** | `LICENSE` **11,357 bytes**, plain Apache-2.0 | **EMEA's cleanest sovereign option.** Barcelona Supercomputing Center, multilingual with Iberian-language focus. No AUP layer, no gate, no inheritance problem. The default answer when a European client wants a non-US base model and a licence legal will sign in one reading |
| [allenai/OLMo](https://github.com/allenai/OLMo) · [allenai/OLMo-core](https://github.com/allenai/OLMo-core) | **Apache-2.0** | `LICENSE` **11,359 bytes** in both | **The only family probed this pass where the code licence and the weights licence agree and both are permissive.** AI2 also publishes training data and code, which is what makes it the realistic candidate when a client asks for a model that survives an OSAID-style openness test |
| [QwenLM/Qwen3](https://github.com/QwenLM/Qwen3) | **Apache-2.0** (per the vendor's own README) | **No `LICENSE` at `main` or `master` (404 both).** `README.md:397`: *"All our open-weight models are licensed under Apache 2.0."* | **The most permissive frontier-class family verified this pass, and a false negative waiting to happen** — the repo looks unlicensed. Note `README.md:398` points to Hugging Face for the licence files, a host this session cannot reach: the prose is the reachable primary |
| [aisingapore/sealion](https://github.com/aisingapore/sealion) | **Varies by base model — MIT "as much as possible", Llama 3 or Gemma otherwise** | `README.md:88` states the terms *"may vary depending on the underlying base model's restrictions"*, naming the Llama3 License and Gemma variants | **APAC's regional model, and the honest example of inheritance.** Its own arXiv paper (2504.05747) claims *"fully open MIT"* while the README and the Gemma-variant card say otherwise. **Resolve the specific checkpoint, never the project** |
| [google-deepmind/gemma](https://github.com/google-deepmind/gemma) | **Code Apache-2.0; weights are a separate question and currently UNRESOLVED** | `LICENSE` **11,358 B** Apache-2.0 — this is the **code**. `README.md` contains **zero** licence statements (grep: no hits) | **The canonical false positive.** Secondary sources disagree on whether Gemma 4 moved to Apache-2.0 in April 2026 while Gemma 1–3 stay under the Gemma Terms of Use. The primary page `ai.google.dev/gemma/terms` **does not resolve from this session**. **Do not quote a Gemma weights licence until legal reads that page** |
| [NVIDIA/Cosmos](https://github.com/NVIDIA/Cosmos) | **OpenMDW-1.1** | `LICENSE` is the OpenMDW-1.1 text at **2,619 bytes — byte-size identical to the canonical file** | **Primary confirmation of the first major adoption of the new class, read from NVIDIA's own repo rather than from a press release.** For contrast, `NVIDIA-NeMo/Nemotron` → `LICENSE` is **Apache-2.0 (11,358 B)**: the code repo, not the weights. Trend 27 reproduced inside one vendor |

### C. Tools that inspect weights — and the licence split between them

| Repo | Licence | Verified evidence (read 2026-11-24) | Use |
|---|---|---|---|
| [mmaitre314/picklescan](https://github.com/mmaitre314/picklescan) | **MIT** | `LICENSE` **1,072 bytes** | Scans pickle files for unsafe opcodes. **The permissive one** — reach for this when the scanner has to ship inside a client deliverable |
| [trailofbits/fickling](https://github.com/trailofbits/fickling) | **LGPL** | `LICENSE` **7,652 B** at `master` (not `main`), header *"GNU LESSER GENERAL PUBLIC LICENSE"* | The better-known pickle-security tool, and **copyleft**. Fine as a standalone CI binary; a licence problem if linked into a shipped product. **The two tools in this slot are not in the same licence class** |
| [protectai/modelscan](https://github.com/protectai/modelscan) | **Apache-2.0** | `LICENSE` **10,754 bytes** | Scans serialised models across formats for unsafe code execution on load. The permissive, pipeline-ready option for an admission gate on third-party weights |
| [huggingface/safetensors](https://github.com/huggingface/safetensors) | **Apache-2.0** | `LICENSE` **11,357 bytes** | The serialisation format that removes the arbitrary-code-execution problem rather than scanning for it. **Prefer requiring `safetensors` over scanning pickles**, and keep the scanner for what arrives anyway |
| [ossf/ai-ml-security](https://github.com/ossf/ai-ml-security) | **Apache-2.0** | `LICENSE` **11,356 bytes** | OpenSSF's AI/ML security working-group material. Foundation-governed, permissive, and the reference to cite when a client asks whose guidance the admission gate implements |
| [sigstore/model-transparency](https://github.com/sigstore/model-transparency) | **Apache-2.0** | Already held in this KB from the ninth pass | **Signs the weights themselves** — Sigstore bundle → DSSE → in-toto statement listing every file as `(path, digest)`. The piece that makes "these are the approved weights" verifiable rather than asserted. Pairs directly with the licence gate in Receta 23 |

**Fifteen repositories, every licence byte-verified from a reachable primary on 2026-11-24, with two
licences deliberately recorded as unresolved rather than guessed.** No row carries a star count,
because stars could not be measured this pass.

---

## The erasure boundary — what the agent must *forget*, what proves it forgot, and the obligation that forbids forgetting (added thirteenth pass, 2026-11-24)

**Why this is a new layer and not a restatement of the de-identification section above.** Twelve
passes built four boundaries — read (seventh), write (eighth), provenance (ninth), containment
(tenth) — plus the weights licence (twelfth). Every one of them governs what the agent **may do**.
None of them governs what has to happen when a person exercises a right and the answer is *remove
it*. The gap was measured, in both of this KB's languages, before a single search was run:

```
grep -ril 'erasure|retention|unlearn|DSAR|Article 17'     *.md  → 0 files
grep -ril 'borrado|supresión|retención|conservación'      *.md  → 0 files
grep -c   'GDPR'                        (whole KB, 10,355 lines) → 2   (both in passing)
```

Two mentions of the GDPR across 10,355 lines and 355 repository addresses. The de-identification
section above is the **prevention** half — keep personal data out of the agent's reach. This
section is the **remediation** half — it is already in there, and someone has asked for it back out.

### Why this layer is harder than the other four

A delete is not an operation, it is a **cascade**, and the agent stack has seven places the same
fact comes to rest. This is the shape of the engagement, and each row is a separate deliverable:

| # | Where the fact lands | What a naive delete does | What actually erases it |
|---|---|---|---|
| 1 | System of record (ERP/CRM row) | Sets a deleted flag — **the bytes stay** (see `verticals/solutions.md`, measured on SuiteCRM) | A hard delete, or anonymisation in place |
| 2 | CDC stream (Debezium, already held) | Emits a **tombstone** that many sinks drop | Sink-side tombstone handling, asserted by test |
| 3 | Lakehouse table (Iceberg/Delta/Hudi) | Row-level delete, **old snapshot still readable** | `expire_snapshots` / `VACUUM` — retention-bounded, so erasure has a *latency*, and you must quote it |
| 4 | Embeddings + vector index | Delete by filter — but the **index copy and any cached vector** may persist | Delete by filter *plus* index compaction, then re-query to prove absence |
| 5 | Evaluation sets & prompt fixtures | Nothing — nobody thinks of them | Treat eval fixtures as a data store with an owner |
| 6 | Fine-tuned weights | Nothing. **Unlearning is not production technology** (measured below) | Retrain without the record — or never put it there |
| 7 | Logs & traces | Nothing — and **deleting them may be unlawful** (EU AI Act Art. 19, India DPDP Rule 8) | Design the log so it can be *kept*: see the rule below |

**Rows 6 and 7 are the two that decide the architecture**, and they point in opposite directions.
Row 6 says personal data must never enter the weights, because there is no supported way to get it
out. Row 7 says the logs must *not* be erasable, because two jurisdictions impose a retention
floor. Taken together they produce one design rule, and it has a legal basis rather than a
preference behind it:

> **Put erasable personal data in retrieval, never in training; and keep identifiers out of the
> log body so the log can be retained at full fidelity without being a copy of what was erased.**

### A. Privacy-request orchestration — and the headline finding is that the product is archived

The one open-source project every 2026 roundup names as *the* open-source DSAR engine has been
archived. Measured through `search/repositories`, which is the only GitHub metadata oracle this
session can reach:

| Repo | Licence | Stars | Last push | State | Read before using |
|---|---|---|---|---|---|
| [ethyca/fides](https://github.com/ethyca/fides) | Apache-2.0 | 483 | 2026-08-06 | **ARCHIVED** | "Privacy as code" — data mapping, consent, and DSAR orchestration with an erasure cascade across connected systems. **The reference design for this layer, and no longer maintained.** Read it, copy the model, do not take a dependency |
| [ethyca/fidesops](https://github.com/ethyca/fidesops) | Apache-2.0 | 49 | 2022-11-30 | **ARCHIVED** | The DSAR-orchestration predecessor, folded into `fides` in 2022. Still cited by current listicles as if live |
| [ethyca/fides-helm](https://github.com/ethyca/fides-helm) | Apache-2.0 | 4 | 2026-10-02 | live | **The chart outlived the product it deploys.** A maintained deployment artefact is not evidence of a maintained application — a new way to misread this layer |
| [ethyca/fideslog](https://github.com/ethyca/fideslog) | Apache-2.0 | 6 | 2025-12-11 | live | Analytics client for the Fides tooling. Peripheral |
| [ethyca/janus-sdk-android](https://github.com/ethyca/janus-sdk-android) | **NOASSERTION** | 0 | 2026-11-20 | live | The vendor's **currently active** line, and it is a mobile consent SDK, not a DSAR engine |
| [ethyca/janus-sdk-flutter](https://github.com/ethyca/janus-sdk-flutter) | **NOASSERTION** | 1 | 2026-11-04 | live | Same line. Licence **not declared** |
| [ethyca/janus-sdk-react-native](https://github.com/ethyca/janus-sdk-react-native) | **NOASSERTION** | 0 | 2026-11-04 | live | Same line |

**The pattern, stated plainly, because it is the commercially important part.** Of 22 repositories
in the `ethyca` organisation, the Apache-2.0 privacy-engineering platform is archived while the only
actively-developed repositories are three mobile SDKs that **declare no licence at all**. This is
the first time this KB has recorded an archival and a **licence regression in the same
organisation**: the open-source asset went away and what replaced it is not open source. A client
who adopted Fides in 2025 has no supported upgrade path inside that namespace.

**What to do instead, and it is not a like-for-like swap.** There is no maintained permissive
replacement for Fides. This pass searched for one and did not find it, and that absence is recorded
as a finding rather than filled with a plausible-looking row. The honest engagement shape is:
**Fides' data map and erasure-cascade model, reimplemented over components that are maintained** —
the catalog and lineage rows below supply the map, and the cascade is application code. That is a
build, it is quotable, and pretending a drop-in exists is how a pilot stalls in month three.

### B. De-identification — the prevention half, already held, and re-measured

| Repo | Licence | Stars | Last push | Note |
|---|---|---|---|---|
| [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) | **MIT** | 12,026 | 2026-11-23 | **Already held since the fourth pass**, including the move out of `microsoft/`. Re-measured here: **11,989 → 12,026 ★**, push 2026-11-19 → **2026-11-23**. Still MIT, still the de facto PII engine |
| [data-privacy-stack/presidio-research](https://github.com/data-privacy-stack/presidio-research) | **MIT** | 321 | 2026-11-19 | Already held. Evaluation and dataset tooling for recogniser quality — **the piece that lets you state a recall number** instead of asserting the redaction works. Unchanged since the fourth pass |
| [EdyVision/pii-codex](https://github.com/EdyVision/pii-codex) | **BSD-3-Clause** | 102 | 2026-02-15 | Categorises and **risk-scores** detected PII against published taxonomies. Permissive, small, and idle ~9 months — use as a library, not a dependency to track |
| [danyuchn/pii-guard](https://github.com/danyuchn/pii-guard) | **MIT** | 257 | 2026-11-15 | Reversible Traditional-Chinese (zh-TW) de-identification so documents can be sent to a model safely. **APAC-origin, and the first non-English de-identification row in this KB** — Presidio's recognisers are English-first, which is a real gap on a Taiwan or Japan engagement |

> **A false finding this pass caught on itself, recorded because the near-miss is the lesson.**
> This pass's opening probe found that `repo:microsoft/presidio` is **unsearchable (422)** and that
> `grep -ril presidio` matches **seven files**, and drew the obvious conclusion: the KB cites a dead
> owner in seven places. **It does not.** The fourth pass (2026-11-20) already caught the move and
> already rewrote every citation — the grep was matching the **new** path. The only genuine
> `microsoft/presidio` strings left in this KB are the three *correct* ones: the "Was" column of the
> rename ledger above, and the anti-pattern in `compose/patterns.md` that tells you not to cite it.
>
> **The rule: a grep for a project's NAME cannot tell you which OWNER the KB cites.** Grep the old
> owner path (`microsoft/presidio`), never the bare name. This is the second time in this pass that
> the KB turned out to be more precise than the search that was auditing it — the first was the EU
> AI Act deferral, where live articles still say "August 2026" and this KB already held the naming
> instrument. Both are the energy KB's rule T88 reproduced in a different industry: **a false gap is
> published as news and degrades correct data, which is worse than a missed finding.**

### C. When erasure is impossible — the statistical route

Row 6 of the cascade has no delete. When a fact is already in a model or an aggregate, the
defensible answer is a **mathematical bound on what can be recovered**, not a claim that it is gone.

| Repo | Licence | Stars | Last push | Use |
|---|---|---|---|---|
| [OpenMined/PySyft](https://github.com/OpenMined/PySyft) | Apache-2.0 | 10,064 | 2026-11-24 | Remote execution over data you are never given a copy of. The architecture for "the model trains where the data lives" — **relevant because data that was never copied needs no cascade** |
| [google/differential-privacy](https://github.com/google/differential-privacy) | Apache-2.0 | 3,380 | 2026-11-20 | DP building blocks in C++/Go/Java plus accounting. The reference implementation to cite in a DPIA |
| [opendp/opendp](https://github.com/opendp/opendp) | **MIT** | 450 | 2026-11-24 | Harvard/OpenDP's DP library, **MIT and committed today**. The permissive choice when the privacy accountant has to ship inside a deliverable |

### D. Unlearning and embedding inversion — measured, and the measurement is the finding

This KB's rule is to state a zero rather than imply coverage. **There is no production-grade LLM
unlearning tooling.** What exists is research code with two-digit star counts, and in one case it
has not been touched in 21 months:

| Repo | Licence | Stars | Last push | What it actually is |
|---|---|---|---|---|
| [OPTML-Group/Unlearn-Sparse](https://github.com/OPTML-Group/Unlearn-Sparse) | **MIT** | 90 | 2026-06-28 | Research code for sparsity-aware unlearning. A paper artefact |
| [locuslab/tofu](https://github.com/locuslab/tofu) | **MIT** | 30 | **2025-02-25** | The TOFU *benchmark* for fictitious-author unlearning. **Idle 21 months.** A benchmark is a way to score a method, not a method |
| [jina-ai/embedding-inversion-demo](https://github.com/jina-ai/embedding-inversion-demo) | **Apache-2.0** | 61 | 2026-03-07 | Demonstrates recovering source text **from an embedding**. Small, permissive, and the right artefact to run in a client workshop |
| [vec2text/vec2text](https://github.com/vec2text/vec2text) | **SOM-1.0 — see the warning below** | 1,150 | 2025-12-27 | The best-known embedding-inversion implementation. **Do not run this against client weights.** Note the path: it is no longer `jxmorris12/vec2text` |

> **Licence class nº 12, and it is the most aggressive clause this KB has recorded.**
> `vec2text/vec2text` reports **`NOASSERTION`** to every scanner. The 3,864-byte `LICENSE` read at
> `master` is the **Software for Open Models License (SOM) Version 1.0, dated 30 August 2023** — not
> OSI-approved, no SPDX identifier. Section 3(A), quoted from the file:
>
> > *"If you use the Software to create, modify, process, or otherwise use any Model, **including
> > usage to create inferences with a Model, whether or not you make the Model available to
> > others**, you must make that Model Source Materials publicly available under Open Licensing
> > Terms."*
>
> "Model Source Materials" is defined in the same file as **"the Model and model weights."** Read
> literally, running this tool to make inferences with a client's private model obliges the client
> to **publish its weights**. This is the inverse of the twelfth pass's finding: that pass found the
> operative clause sat outside the licence, in an acceptable-use policy. This one sits **inside** the
> licence of a *tool* and reaches **your weights**. Use the Apache-2.0 Jina demo for the same
> argument, and cite vec2text as a paper rather than shipping it.

**What the measurement means for the architecture.** Approximate unlearning is not erasure;
retraining is the only remedy that satisfies the right, and its cost is the training cost. So the
rule in the box at the top of this section is not conservatism — **it is the only option that can be
delivered.** The corollary is also commercially useful: an embedding is recoverable to source text,
so a vector store is **not** a safe home for data you have promised to delete. It is a store that
must be included in the cascade, which is row 4.

### E. Where the delete has to land — the cascade substrate

Four of these are already held in this KB for other reasons. They are repeated here with the
**erasure property** that nobody records when they are adopted as data infrastructure:

| Repo | Licence | Stars | Last push | The erasure property |
|---|---|---|---|---|
| [apache/iceberg](https://github.com/apache/iceberg) | Apache-2.0 | 9,453 | 2026-11-24 | Row-level deletes, **and time travel means the deleted row is still readable from older snapshots** until `expire_snapshots` runs. Already held — the property is new |
| [delta-io/delta](https://github.com/delta-io/delta) | Apache-2.0 | 9,085 | 2026-11-24 | Same shape: `DELETE` then `VACUUM`, bounded by a retention window. **The window is the erasure SLA** — quote it |
| [apache/hudi](https://github.com/apache/hudi) | Apache-2.0 | 6,395 | 2026-11-24 | The lakehouse format with first-class **record-level deletes** and a native GDPR-deletion idiom. Worth leading with when erasure is the driver |
| [trinodb/trino](https://github.com/trinodb/trino) | Apache-2.0 | 13,542 | 2026-11-24 | The federated query engine that reaches all of the above. **Also the thing that will happily read a snapshot you thought you deleted** |
| [apache/polaris](https://github.com/apache/polaris) | Apache-2.0 | 2,124 | 2026-11-24 | Open Iceberg catalog with credential vending. Where table-level retention policy can be enforced centrally rather than per job |
| [apache/atlas](https://github.com/apache/atlas) | Apache-2.0 | 2,163 | 2026-11-20 | Metadata and governance with classification propagation — the mature way to tag what is personal data and **have the tag follow the data** |
| [MarquezProject/marquez](https://github.com/MarquezProject/marquez) | Apache-2.0 | 2,311 | 2026-11-23 | The OpenLineage reference server. **Lineage is the prerequisite for erasure**: you cannot cascade a delete through a graph you have not recorded |
| [amundsen-io/amundsen](https://github.com/amundsen-io/amundsen) | Apache-2.0 | 4,780 | 2026-09-10 | **ARCHIVED.** The Lyft data catalog, 4.8k stars, no longer maintained. Listed as a **warning**: it is still recommended in catalog comparisons. Use DataHub or OpenMetadata, both already held |
| [chroma-core/chroma](https://github.com/chroma-core/chroma) | Apache-2.0 | 29,739 | 2026-11-20 | Vector store. Added here because it was the one major permissive vector store this KB did not hold |

> **Measured licence facts in this table, resolved from bytes rather than badges.**
> `pgvector/pgvector` (23,795★, already held) reports `NOASSERTION`; its `LICENSE` at `master` is the
> **PostgreSQL License** — permissive. `weaviate/weaviate` (16,958★, already held) also reports
> `NOASSERTION`, and its `LICENSE` opens: *"Source code in this repository is variously licensed
> under the BSD-3-Clause License, or the Weaviate License."* That is a **second instance of the
> ninth licence class** (split by component inside one repository) — the per-directory check is
> mandatory before embedding Weaviate in a deliverable.

### F. Consent — the lawful basis, and one region now requires a registered intermediary

| Repo | Licence | Stars | Last push | Note |
|---|---|---|---|---|
| [orestbida/cookieconsent](https://github.com/orestbida/cookieconsent) | **MIT** | 5,782 | 2026-11-22 | Dependency-free consent UI, actively maintained. The permissive default |
| [kiprotect/klaro](https://github.com/kiprotect/klaro) | **BSD-3-Clause** | 1,526 | 2025-03-27 | Consent manager from a German privacy-engineering outfit. Reports `NOASSERTION`; `LICENSE` at **`master`** reads *"BSD 3-Clause License… KIProtect GmbH"*. **Idle ~20 months** — quote that honestly |

**The regional catch, and it is an architecture constraint rather than a licence one.** Under
India's DPDP Rules the **Consent Manager must be an Indian company registered with the Data
Protection Board**, and that regime commenced **13 November 2026 — eleven days before this pass**.
Neither library above *is* a registered consent manager, and no amount of open source makes one.
On an India engagement the consent-capture UI is buildable and the consent-manager role is
**procurable from a registered Indian entity**. Detail and the conflicting dates in
`intel/market.md` → APAC.

### Instrument note — star counts and push dates are measurable again

The twelfth pass recorded that it could not measure stars or push dates, because
`api.github.com/repos/{owner}/{repo}` returns 403 outside this session's scope. **Every star count
and push date in this section is measured**, via `gh api -X GET search/repositories -f q='repo:a/b
repo:c/d …'`, which is in scope and returns `license.spdx_id`, `stargazers_count`, `pushed_at`,
`archived` **and `default_branch`** for up to several repositories in a single request. The
reusable details, including the one way this instrument fails silently, are in `intel/trends.md`.

## Accessibility conformance — the layer that decides whether the agent UI can be sold (added fourteenth pass, 2026-11-24)

> Why this is a *foundations* layer and not a nice-to-have: in the EU, **AI Act Article 16(l)**
> obliges providers of high-risk AI systems to comply with the accessibility requirements of
> Directives (EU) 2016/2102 and (EU) 2019/882 — accessibility is an **AI** obligation, not only a
> web one (`intel/market.md`, EMEA, this pass). In US public-sector procurement it is a gate before
> a contract, not a finding after one.
>
> **Verification channels used, because the usual one is gone.** `api.github.com` → 403 for this
> session (as since the ninth pass), and `img.shields.io` and `repos.ecosyste.ms` are also refused
> by the proxy. So: **licence = byte-read** of `raw.githubusercontent.com/<repo>/HEAD/LICENSE`
> (licence *text*, stronger than a badge); **dependencies = byte-read** of `/HEAD/package.json`;
> **stars + archived state** = github.com HTML through WebFetch; **versions and publish dates** =
> `registry.npmjs.org`. Measured 2026-11-24.

### The engines (pick by licence, not by popularity)

| Repo | Licence (byte-read) | ★ | Engine | Note |
|---|---|---|---|---|
| https://github.com/dequelabs/axe-core | **MPL-2.0** | 7.9k | **own** | "Accessibility engine for automated Web UI testing". npm 4.14.1, 2026-11-16. The de-facto engine of the whole layer |
| https://github.com/IBMa/equal-access | **Apache-2.0** | 788 | **own** | `accessibility-checker-engine` declares **zero** axe dependencies. Default branch is `main-4.x`, not `main`. **The only fully permissive engine here** |

### The tools built on them

| Repo | Licence (byte-read) | ★ | Bundles `axe-core`? | Use for |
|---|---|---|---|---|
| https://github.com/microsoft/accessibility-insights-web | MIT | 966 | **yes, 4.11.3** (2026-04-13 — seven months behind 4.14.1) | Browser-extension assessment, FastPass, guided manual checks |
| https://github.com/microsoft/accessibility-insights-service | MIT | 79 | — | Scheduled scans of a site at estate scale. **Requires deploying Azure resources**; no throughput figure published |
| https://github.com/GoogleChrome/lighthouse | Apache-2.0 | 31.2k | **yes, 4.14.1** | The a11y category inside an existing CI that already runs Lighthouse |
| https://github.com/pa11y/pa11y | **LGPL-3.0-only** | 4.6k | — | CLI/CI runner. Pa11y 10 current; **Pa11y 9 support ended 2026-02-27**. Licence is *not* permissive |

### The part automation cannot do — driving an actual screen reader

This is the layer that makes a streaming agent UI testable, and it did not exist in this KB:

| Repo | Licence (byte-read) | ★ | npm | What it does |
|---|---|---|---|---|
| https://github.com/guidepup/guidepup | MIT | 604 | `@guidepup/guidepup` 0.40.0, 2026-11-01 | **Drives real VoiceOver and NVDA** from Playwright/Jest. "Screen reader automation library for testing" |
| https://github.com/guidepup/virtual-screen-reader | MIT | 158 | `@guidepup/virtual-screen-reader` 0.33.0, 2026-09-20 | Simulates a screen reader over a DOM in **unit** tests — **no real screen reader needed**. Its own README says it should supplement, not replace, testing with real screen readers and users |
| https://github.com/nvaccess/nvda | **GPL-2.0-or-later**, two exceptions (`copying.txt`; there is no root `LICENSE`) | — | — | The assistive technology itself. You **drive** it, you do not link it, so it stays out of your artifact — but say that out loud in the OSS review |

### Reference corpora that are not software (do not "build on" these)

| Repo | Licence (byte-read) | What it actually is |
|---|---|---|
| https://github.com/w3c/wcag | **W3C Document Licence** | The WCAG specification sources. Not a software licence |
| https://github.com/act-rules/act-rules.github.io | **W3C Community Contributor License Agreement** | The ACT rules corpus — the machine-readable test definitions behind conformance tooling. Not a software licence |
| https://github.com/ryersondmp/sa11y | **GPL-2.0** | In-page QA checker. Its own `LICENSE.md` records that **versions ≤ 2.0 were MIT** — a dated licence-tightening instance |

### The licence-concentration rule, applied to an engine instead of a category

`intel/trends.md` already generalises licence concentration across a layer. This layer adds a
sharper form: **concentration at the engine, hidden under permissive wrappers.** Five of six tools
tested ship MPL-2.0 `axe-core`; the badge the client reads is the wrapper's. MPL-2.0 is file-level
copyleft — deliverable beside proprietary code, but (a) it belongs in the client's OSS review,
(b) modifications to axe's own rule files must be published, and (c) it belongs in the AI-BOM built
in `compose/patterns.md` Receta 24. The only end-to-end permissive path is IBM's engine.

### The gap this layer still has, stated rather than filled

- **No OSCAL catalog for accessibility.** The eighth pass added OSCAL as the machine-readable
  control format; there is no ready WCAG 2.1 AA / EN 301 549 catalog in `usnistgov/oscal-content`
  found by this pass. Expressing an accessibility control set in OSCAL is a **build**, not an
  adoption. Open item.
- **No non-US origin in the *engine and testing* layer.** All eleven verified repositories above
  originate with US vendors (Deque, Microsoft, Google, IBM) or individual maintainers
  (guidepup — Craig Morten; Sa11y — Toronto Metropolitan University, Canada). **Zero** EMEA-, APAC-
  or LATAM-origin test tooling was found, with the English, Spanish and Portuguese instruments.
  **The scope of that zero matters:** one layer up, in *components*, the position reverses —
  `alphagov/govuk-frontend` (MIT, Crown Copyright/GDS, npm 6.6.0 of 2026-10-15) is EMEA-origin and
  is the single best-tested accessible component set in the open
  (`verticals/solutions.md`, this pass). A zero is only as good as the layer it is measured in.

## La capa de medición del consumo — el sexto límite (added fifteenth pass, 2026-11-24)

> **Tema del pase: el límite del consumo.** Catorce pases gobernaron lo que el agente puede
> **leer** (entitlement), **cambiar** (write), **probar** (provenance), **contener** (containment),
> **olvidar** (erasure) y **quién puede usarlo** (accessibility). Ninguno midió lo que el agente
> **gasta** ni lo que hay que **declarar** sobre ese gasto.
>
> **Medido antes de buscar**, sobre los nueve archivos y en los dos idiomas de la KB:
> `carbon` 0 · `kWh` 0 · `emision/emisión` 0 · `CSRD` 0 · `ESRS` 0 · `kepler` 0 · `codecarbon` 0 ·
> `consumo` 0 · `ambiental` 0 · `eficiencia energética` 0. Cero limpio en los nueve archivos, en
> inglés **y** en español (regla T88: la auditoría de huecos se corre en el idioma de la KB).
> `FinOps`, `metering`, `OpenCost` y `SPIFFE` **sí** estaban: esta capa no es FinOps con otro
> nombre — FinOps mide **dinares**, esta mide **julios**, y el obligado a declararlos no es el CFO.

### Motores de medición — qué se mide y dónde se engancha

Licencia, estrellas, último push y `default_branch` leídos de `gh api search/repositories`
el 2026-11-24; las tres `NOASSERTION` resueltas por lectura byte a byte del `LICENSE`.

| Repo | Licencia | ★ | Último push | Qué mide y dónde se engancha |
|---|---|---|---|---|
| [hubblo-org/scaphandre](https://github.com/hubblo-org/scaphandre) | Apache-2.0 | 2018 | 2026-07-19 | Agente host: potencia por proceso vía RAPL. Exporta a Prometheus. La sonda más bajo nivel de la tabla |
| [sustainable-computing-io/kepler](https://github.com/sustainable-computing-io/kepler) | Apache-2.0 | 1606 | 2026-11-24 | eBPF + RAPL por **pod** de Kubernetes, exporta Prometheus. Es el que atribuye consumo a un workload, no a una máquina |
| [sustainable-computing-io/kepler-operator](https://github.com/sustainable-computing-io/kepler-operator) | Apache-2.0 | 40 | 2026-11-23 | Operador OpenShift/K8s para desplegar el anterior. Sin él, Kepler es un DaemonSet a mano |
| [mlco2/codecarbon](https://github.com/mlco2/codecarbon) | MIT | 1951 | 2026-11-22 | Librería Python: envuelve un entrenamiento o una inferencia y emite kWh + gCO₂e estimados por región |
| [ml-energy/zeus](https://github.com/ml-energy/zeus) | Apache-2.0 | 390 | 2026-11-17 | Medición **y optimización** de energía en GPU para cargas de deep learning; `default_branch=master` |
| [saintslab/carbontracker](https://github.com/saintslab/carbontracker) | MIT | 489 | 2026-11-05 | Predice la huella de un entrenamiento desde las primeras épocas. **Ojo: la ruta que citan los roundups (`lfwa/carbontracker`) no existe** |
| [powerapi-ng/powerapi](https://github.com/powerapi-ng/powerapi) | BSD-3-Clause | 255 | 2026-11-24 | Toolkit para construir medidores de potencia por software. Única BSD-3 de la capa |
| [cloud-carbon-footprint/cloud-carbon-footprint](https://github.com/cloud-carbon-footprint/cloud-carbon-footprint) | Apache-2.0 | 1054 | 2026-04-23 | Estima energía y CO₂e desde las **facturas** de AWS/Azure/GCP. `default_branch=trunk`. Push más antiguo de la tabla — verificar actividad antes de proponerlo como base |
| [thegreenwebfoundation/co2.js](https://github.com/thegreenwebfoundation/co2.js) | **Apache-2.0** (byte-read; la API dice `NOASSERTION`) | 499 | 2026-11-17 | Convierte bytes y kWh en gCO₂e. **Trae datos ODbL — ver la trampa de licencia abajo** |
| [thegreenwebfoundation/grid-intensity-go](https://github.com/thegreenwebfoundation/grid-intensity-go) | Apache-2.0 | 84 | 2026-05-11 | Cliente Go de intensidad de red, pensado para decisiones de planificación |
| [Green-Software-Foundation/if](https://github.com/Green-Software-Foundation/if) | MIT | 184 | 2026-10-24 | *Impact Framework*: declara el cálculo como manifiesto YAML en vez de código. Es el que hace el número **auditable** |
| [Green-Software-Foundation/carbon-aware-sdk](https://github.com/Green-Software-Foundation/carbon-aware-sdk) | MIT | 600 | 2026-11-04 | API de "¿cuándo y dónde corro esto?". `default_branch=dev`, no `main` |
| [kube-green/kube-green](https://github.com/kube-green/kube-green) | MIT | 1390 | 2026-09-02 | Apaga workloads no productivos por horario. El ahorro más barato y el menos citado |
| [mlco2/agentic-footprint](https://github.com/mlco2/agentic-footprint) | MIT | 8 | 2026-11-23 | **Rust, específico de agentes.** 8★ — se cita por existir, no por madurez |
| [mlco2/ecologits](https://github.com/mlco2/ecologits) | **MPL-2.0** | 364 | 2026-11-23 | Huella de GenAI **por API** (modelo cerrado, sin acceso al host). MPL-2.0: copyleft por archivo, no es permisiva |

**Lo que la tabla no tiene y hace falta decirlo:** ninguno de estos mide un *agente*. Miden un
proceso, un pod o una llamada. La atribución por **tarea de agente** (plan → N llamadas →
herramientas → reintentos) no tiene producto maduro: lo único específico son `mlco2/agentic-footprint`
(8★) y `VeiledTee/agent-energy-profiler` (MIT, 0★, 2026-10-24), ambos de una cifra de estrellas. Se
declara como hueco de la capa, no se rellena con una fila verosímil.

### La capa de declaración — el número tiene que salir en un formato, no en un PDF

| Repo | Licencia | ★ | Último push | Para qué |
|---|---|---|---|---|
| [Arelle/Arelle](https://github.com/Arelle/Arelle) | **Apache-2.0** (byte-read; la API dice `NOASSERTION`) | 261 | 2026-11-24 | Procesador XBRL open source — valida y genera el *tagging* digital con el que se presenta el informe. `default_branch=master`. Copyright **Workiva, Inc.** |
| [os-climate/physrisk](https://github.com/os-climate/physrisk) | Apache-2.0 | 72 | 2026-11-23 | Riesgo físico climático por activo — el insumo de la parte "riesgos" del informe |
| [os-climate/osc-transformer-presteps](https://github.com/os-climate/osc-transformer-presteps) | Apache-2.0 | 1 | 2026-11-23 | Extracción previa de informes de sostenibilidad para pipelines NLP. **1★: es infraestructura de un consorcio, no un producto** |

**Por qué Arelle es el hallazgo estructural y no una nota de pie.** Es el mismo patrón que el pase
ocho encontró con OSCAL: cuando la obligación pasa de "publique un informe" a "publique estos
campos", **la herramienta que importa es un procesador de esquema de hace una década, no un modelo**.
Arelle es a ESRS/XBRL lo que `oscal-cli` es a FedRAMP. Y la señal de que la obligación va hacia ahí
está datada: EFRAG publicó el **borrador de taxonomía XBRL de los ESRS revisados el 17-sep-2026**,
con consulta pública cerrada el **11-nov-2026** y entrega prevista a ESMA y la Comisión **antes de
fin de 2026** (nivel snippet, ver más abajo).

### Trampa de licencia del pase, y es de una clase nueva — la licencia de los **datos**

`thegreenwebfoundation/co2.js` aparece como `NOASSERTION` en la API de GitHub. La lectura byte a
byte de su `LICENSE` (12 678 bytes) explica por qué: **un solo archivo contiene dos licencias para
dos activos distintos.**

1. **El código** es Apache-2.0 (el texto íntegro está en el archivo).
2. **Los datos de intensidad de red** que la librería trae empaquetados se republican de
   **Electricity Maps bajo la Open Database License (ODbL)**, y el propio archivo enumera las
   obligaciones, en sus palabras: *"Attribute: Credit Electricity Maps as the source"*,
   *"Share-Alike: Keep derivative works under the same license"*, *"Keep open: Provide unrestricted
   versions if using DRM"*.

**Clase de licencia nº 13 de esta KB: ODbL — y es la primera que no recae sobre código.** La
consecuencia comercial es concreta y no la cubre ninguna regla anterior de este repo: el factor de
intensidad de red es **justamente** lo que convierte kWh en gCO₂e, es decir el dato sin el cual la
capa de medición no produce la cifra que el informe exige. Quien lo toma por esta vía hereda
**share-alike sobre la base de datos derivada** — una superficie de riesgo distinta del copyleft de
código, y que **sobrevive a una librería Apache-2.0**. Dicho al revés, y es la regla:

> **Una librería permisiva puede entregarte una base de datos con copyleft.** El SPDX del repo
> describe el código; no dice nada de los datos que el repo empaqueta.

El mismo texto, **con su errata incluida** (`"Licening for the CO2.js library"`), reaparece dentro
del `LICENSE` de `green-coding-solutions/green-metrics-tool` (35 429 bytes): prueba de que ese
proyecto **vendoriza** co2.js. Y ese archivo es peor todavía — tres licencias en uno:

| Sección del archivo | Lo que el índice promete | Lo que el cuerpo contiene |
|---|---|---|
| línea 2 | "1. License for Green Metrics Tool Source Code" | — |
| línea 3 | "2. License for the bundled Electricity Maps Grid Intensity Data" | — |
| línea 7 | encabezado: *"1. Licening for the CO2.js library **Apache License**"* | el texto que sigue (líneas 10–652) es la **GNU AFFERO GPL v3**, no Apache |
| línea 673 | "2. License for Electricity Maps Grid Intensity Data" | **ODbL**, con atribución y share-alike |

Es decir: **el encabezado contradice a su propio cuerpo.** El veredicto real para
`green-metrics-tool` (260★, push 2026-11-24) es **AGPL-3.0 para el código + ODbL para los datos**, y
eso lo descarta como base propietaria igual que `Boavizta/boaviztapi` (AGPL-3.0, 102★) y
`Boavizta/cloud-scanner` (AGPL-3.0, 43★) — tres proyectos de referencia de la capa, los tres AGPL.
`electricitymaps/electricitymaps-contrib` (AGPL-3.0, 4057★) es la fuente original de los datos y
tiene la misma forma: **código AGPL, datos ODbL.**

> **Regla de método 14 (nueva).** Antes de importar cualquier proyecto de huella ambiental,
> responda **dos** preguntas de licencia, no una: *¿qué licencia tiene el código?* y *¿qué licencia
> tienen los factores de emisión que trae?* En esta capa la segunda respuesta es, casi siempre, ODbL.

### Ejecución carbon-aware — y la única prueba de código del pase

`jobrunr/jobrunr` (3112★, push 2026-11-24) aparece `NOASSERTION`. Resuelto por dos oráculos no
equivalentes:

- su archivo de licencia **no se llama `LICENSE`** (404 en `LICENSE`, `LICENSE.md`, `LICENSE.txt`,
  `COPYING`) sino **`License.md`**, y ese archivo dice en su primera línea que el software está
  **`multi-licensed`**: **LGPL-3.0-or-later** *o* una **licencia comercial** por suscripción, a
  elección del receptor;
- el POM de Maven Central (`org/jobrunr/jobrunr/8.0.0`) declara **solo** *"GNU Lesser General Public
  License v3.0 or later"*, y apunta a `License.md#lgpl-v3-license` — **un ancla**, porque el archivo
  tiene varias secciones.

> **Regla de método 15 (nueva), y corrige la 12.** El manifiesto puede estar **correcto y ser
> incompleto**: en una oferta multi-licencia nombra *una* de las opciones. Un manifiesto que dice
> LGPL no prueba que no exista además una vía comercial, ni al revés. La tabla de desempate del
> pase 19 de `energy-kb` sigue valiendo, pero su paso (1) deja de ser terminal.

**Y la pregunta que de verdad importaba, contestada leyendo el código y no el blog:** ¿el
*scheduling* carbon-aware está en el núcleo abierto o en la edición de pago? `gh api search/code`
sobre `repo:jobrunr/jobrunr carbonaware` devuelve **91 coincidencias**, y las clases están en
**`core/src/main/java/org/jobrunr/`**:

```
core/src/main/java/org/jobrunr/scheduling/carbonaware/CarbonAware.java
core/src/main/java/org/jobrunr/scheduling/carbonaware/CarbonAwarePeriod.java
core/src/main/java/org/jobrunr/scheduling/carbonaware/CarbonAwareScheduleMargin.java
core/src/main/java/org/jobrunr/server/carbonaware/CarbonIntensityApiClient.java
core/src/main/java/org/jobrunr/server/carbonaware/CarbonAwareJobProcessingConfiguration.java
```

Está en el **módulo `core`, en `main`**, no en un módulo Pro: **es usable bajo LGPL-3.0-or-later**,
que para enlace dinámico desde una aplicación propietaria es aceptable en la mayoría de los
*engagements*. Esto es un diferencial real: es el único planificador de esta KB que desplaza trabajo
diferible a ventanas de red limpia, y el agente enterprise está **lleno** de trabajo diferible
(reindexado, *batch* de *embeddings*, evaluaciones nocturnas, reentrenos).

**Pero el mismo archivo de configuración trae una dependencia que hay que declararle al cliente,
leída byte a byte de `CarbonAwareJobProcessingConfiguration.java`:**

```java
public static final String DEFAULT_CARBON_INTENSITY_API_URL =
        getCarbonIntensityForecastApiRootUrl("https://api.jobrunr.io");
public static final Duration DEFAULT_API_CLIENT_CONNECT_TIMEOUT = Duration.ofSeconds(3);
public static final Duration DEFAULT_API_CLIENT_READ_TIMEOUT   = Duration.ofSeconds(3);
public static final Integer  DEFAULT_API_CLIENT_RETRIES_ON_EXCEPTION = 3;
public static final Duration DEFAULT_POLL_INTERVAL = Duration.ofMinutes(5);
```

Por defecto **llama a la API del proveedor** (`api.jobrunr.io`) cada 5 minutos, con *timeouts* de 3
segundos y 3 reintentos. El campo `carbonIntensityApiUrl` **es configurable**, junto con `areaCode` y
`dataProvider`, de modo que se puede apuntar a un endpoint propio. Es exactamente la forma que el
pase trece documentó con SOM-1.0 —*la cláusula que decide está fuera de la licencia*— pero un nivel
más abajo: aquí lo que está fuera de la licencia es una **salida de red a un tercero**, activada por
defecto, en una librería cuya licencia es impecable. En un cliente regulado eso se revisa antes del
*go-live*, y la mitigación es una línea de configuración.

---

## The language boundary — what the agent *says*, in which language, and who signed off on the wording (added sixteenth pass, 2026-11-24)

> **Theme of this pass: the language boundary.** Seven previous passes mapped who the agent acts
> for (entitlement), what it may change (write), what proves it (provenance), where it runs
> (containment), what it is made of (weights), what it must forget (erasure), who can perceive it
> (accessibility) and what it costs the grid (footprint). None asked **in which language the agent
> speaks, and who approved that wording.** For a company that sells into four regions, that is not
> a cosmetic question — it is the one layer where the *same* deliverable is legal in one market and
> unlawful in another.
>
> **Measured before searching, across all nine files and both of the KB's languages:**
> `weblate` 0 · `pontoon` 0 · `tolgee` 0 · `traduora` 0 · `libretranslate` 0 · `argos` 0 ·
> `ctranslate2` 0 · `opus-mt` 0 · `marian` 0 · `messageformat` 0 · `message format` 0 ·
> `sacrebleu` 0 · `COMET` 0 · `fasttext` 0 · `cld3` 0 · `IndicTrans` 0 · `masakhane` 0 ·
> `pseudo-local` 0 · `glossary` 0 · `terminolog` 0 · `translation memory` 0 · `XLIFF` 0 ·
> `locale` 0 · `CLDR` 0 · `Bill 96` 0 · `Eighth Schedule` 0 · `13.135` 0.
> **28 of 30 terms at a clean zero.**
>
> The two non-zero hits are the precise shape of the blind spot, and worth stating:
> - `lingua` **1** — and it is `langtech-bsc/salamandra`'s *description* (Barcelona Supercomputing
>   Center, Iberian languages), already held as a **sovereign base model**. The KB knew about
>   multilingual *models*; it held nothing about multilingual *strings*.
> - `DPDP` **10** — India's data law was already in this KB, but **only as a privacy and erasure
>   instrument**. Its §5(3) language duty (below) appears nowhere. The KB had read the same statute
>   and taken only the half that matched the pass it was doing.
>
> The 18 `l10n` hits that exist are `OCA/l10n-argentina`, `l10n-brazil`, `l10n-chile` and
> `l10n-mexico` — Odoo **fiscal** localisation (tax rules, invoice layouts). That is a false friend:
> in the ERP world "l10n" means tax, in this layer it means language. Both are in this KB now; do
> not let a search for one return the other.
>
> **Verification method for this pass.** Licence, stars, archived state and last push come from
> `gh api search/repositories` on **2026-11-24**. Every `NOASSERTION` or `null` badge was resolved
> by **byte-reading the licence file** from `raw.githubusercontent.com` with a ranged GET (`HEAD` is
> blocked by this session's proxy, and `api.github.com` answers only for session-scoped repos, so
> neither shortcut was available). **`huggingface.co` is proxy-dead from this session (HTTP 000)**,
> which is why every model-*weights* licence below is marked either byte-proven from a GitHub repo
> or explicitly **secondary-sourced**.

### Layer 1 — The translation management system: where a human approves the wording

This is the system of record for *approved* text. An agent that generates customer-facing prose
without one is generating unreviewed legal exposure in every market it ships to.

| Repo | Licence (verified) | Stars | Last push | What it is |
|---|---|---|---|---|
| [mozilla/pontoon](https://github.com/mozilla/pontoon) | **BSD-3-Clause** | 1,679★ | 2026-11-24 | Mozilla's own localisation platform. **The only fully permissive TMS found in this pass** — see the licence conclusion below |
| [WeblateOrg/weblate](https://github.com/WeblateOrg/weblate) | **GPL-3.0** (byte-read) | 6,180★ | 2026-11-24 | The category leader: widest file-format support, tight version-control integration |
| [tolgee/tolgee-platform](https://github.com/tolgee/tolgee-platform) | **Apache-2.0 *except* `ee/`, which is non-commercial** (byte-read — see trap) | 4,162★ | 2026-11-24 | Developer-friendly platform with in-context editing of UI strings |
| [ever-co/ever-traduora](https://github.com/ever-co/ever-traduora) | **AGPL-3.0** | 2,140★ | 2026-11-24 | API-first TMS. **Note the owner** — see the rename ledger entry |
| [translate/translate](https://github.com/translate/translate) | **GPL-3.0** | 988★ | 2026-11-24 | Translate Toolkit: format converters (PO/XLIFF/…) **plus `pofilter` QA checks** — the programmatic gate on translated output |
| [translate/pootle](https://github.com/translate/pootle) | GPL-3.0 | 1,501★ | **2024-08-26** | Superseded by Weblate. Recorded so nobody adopts it from a 2019 blog post |

### Layer 2 — The message format: the shape a translatable string is allowed to have

An LLM that writes `"You have " + n + " messages"` has produced a string that **cannot be
translated correctly** into any language with non-trivial plural rules. This layer is the contract
that prevents it, and it changed status this year.

| Repo | Licence (verified) | Stars | Last push | What it is |
|---|---|---|---|---|
| [unicode-org/message-format-wg](https://github.com/unicode-org/message-format-wg) | **Unicode-3.0** (byte-read; badge said `NOASSERTION`) | 424★ | 2026-10-19 | **The MessageFormat 2 standard.** Primary-source status finding below |
| [unicode-org/icu](https://github.com/unicode-org/icu) | **Unicode-3.0** (byte-read) | 3,651★ | 2026-11-24 | ICU itself — plurals, gender, dates, collation, bidi |
| [unicode-org/cldr](https://github.com/unicode-org/cldr) | **Unicode-3.0** (byte-read) | 1,172★ | 2026-11-24 | The locale **data** under ICU. Separate repo, separate release train |
| [messageformat/messageformat](https://github.com/messageformat/messageformat) | **MIT** (byte-read; OpenJS Foundation) | 1,773★ | 2026-11-09 | MF2 + ICU MessageFormat for JavaScript. Foundation-owned, not vendor-owned |
| [formatjs/formatjs](https://github.com/formatjs/formatjs) | **MIT** — *per package*; **no root licence file** (see trap) | 14,756★ | 2026-11-24 | `react-intl` and friends. The most-starred row in this layer |
| [i18next/i18next](https://github.com/i18next/i18next) | **MIT** (byte-read) | 8,664★ | 2026-11-24 | The default runtime in most JS/TS estates |
| [lingui/js-lingui](https://github.com/lingui/js-lingui) | **MIT** | 5,939★ | 2026-11-19 | Compile-time extraction; small runtime |
| [projectfluent/fluent](https://github.com/projectfluent/fluent) | **Apache-2.0** | 1,695★ | 2026-03-21 | Fluent: asymmetric localisation — a translator may add a plural distinction the source language does not have |
| [projectfluent/python-fluent](https://github.com/projectfluent/python-fluent) | **Apache-2.0** (byte-read; badge said `NOASSERTION`) | 246★ | 2026-06-01 | Fluent for Python — the server-side half |
| [tryggvigy/pseudo-localization](https://github.com/tryggvigy/pseudo-localization) | **MIT** | 141★ | 2026-09-24 | Pseudo-localisation in browser/node: **finds hard-coded strings and layout breakage before a translator is paid** |

#### The primary-source status finding, read from the spec repository

`modelcontextprotocol.io` was proxy-dead in the eighth pass and `unicode.org` reports are no more
reachable from this session, so this was read from `unicode-org/message-format-wg`'s own `README.md`:

> *"The [Unicode MessageFormat Standard](./spec/) is a **stable part of CLDR**. It was **approved by
> the CLDR Technical Committee** and is **recommended for implementation and adoption**. The
> normative version of the specification is published as a part of TR35."*
>
> *"**Unicode MessageFormat** is sometimes referred to as *MessageFormat 2.0*, since it **replaces
> earlier message formatting capabilities built into ICU**."*
>
> *"Some **default functions** and items in the **`u:` namespace are still in Draft status**.
> Feedback from users and implementers might result in changes to these capabilities."*

**Why this is the decision-grade sentence of the pass.** MF2 is no longer a tech preview to wait
out — it is approved, stable and *recommended*, and it **replaces** the ICU MessageFormat syntax
that every existing enterprise estate is written in. So a greenfield agent UI should be authored in
MF2, an existing estate has a migration ahead of it, **and** the `u:` namespace and some default
functions are still Draft, so a client must not be told the whole surface is frozen. All three
statements are true at once; quoting only the first is how a 2028 rewrite gets sold today.

### Layer 3 — The engine that actually translates, and the licence that is not on the repo

| Repo | Licence (verified) | Stars | Last push | What it is |
|---|---|---|---|---|
| [OpenNMT/CTranslate2](https://github.com/OpenNMT/CTranslate2) | **MIT** (byte-read) | 4,764★ | 2026-11-22 | The fast inference engine under most self-hosted MT. CPU-viable |
| [argosopentech/argos-translate](https://github.com/argosopentech/argos-translate) | **MIT** (byte-read) | 6,691★ | 2026-11-17 | Offline translation library — **the permissive core of LibreTranslate** |
| [LibreTranslate/LibreTranslate](https://github.com/LibreTranslate/LibreTranslate) | **AGPL-3.0** (byte-read) | 17,840★ | 2026-11-24 | The self-hosted translation **API**. Most-starred row in the layer and the one legal will stop |
| [Helsinki-NLP/Opus-MT](https://github.com/Helsinki-NLP/Opus-MT) | **code MIT · models CC-BY-4.0** (both byte-read) | 880★ | 2026-02-23 | ~1,000+ language-pair models. The cleanest commercially usable weights in this layer |
| [OpenNMT/OpenNMT-py](https://github.com/OpenNMT/OpenNMT-py) | **MIT** | 7,023★ | 2025-10-14 | Training framework, if a client needs a domain-tuned pair |
| [marian-nmt/marian](https://github.com/marian-nmt/marian) | **MIT** (in `LICENSE.md`, not `LICENSE` — badge said `NOASSERTION`) | 1,475★ | **2023-08-25** | The C++ engine behind Opus-MT's published models. **Three years without a push** |
| [facebookresearch/stopes](https://github.com/facebookresearch/stopes) | **MIT** | 315★ | 2026-08-16 | The NLLB **data pipeline**. MIT — the *code*. See the weights row |

#### The rule this layer proves, and it is the sequel to the twelfth pass

The twelfth pass established that **a repository licence does not govern model weights**. This layer
is the cleanest demonstration of it in the whole KB, because the same lab ships both halves under
different terms:

| Asset | What is MIT/permissive | What actually governs the thing that translates |
|---|---|---|
| **Opus-MT** (Helsinki-NLP) | the repo and tooling: **MIT** | the published models: **CC-BY-4.0** — commercial use permitted **with attribution**. Byte-read from the repo's own `README.md` |
| **NLLB-200** (Meta) | `stopes` pipeline and `fairseq`: **MIT** | the released checkpoints: reported **CC-BY-NC-4.0 — non-commercial**. ⚠️ **SECONDARY-SOURCED.** `huggingface.co` is unreachable from this session (HTTP 000), so this was *not* byte-proven here. **Verify on the model card before it reaches a statement of work** |

**The operational consequence, stated plainly:** an engagement that self-hosts "open source
translation" by pulling NLLB weights behind an MIT-licensed pipeline has, if the secondary source is
right, shipped a **non-commercial** model into a commercial deliverable, and every file in the
repository will say MIT while it does so. Opus-MT is the row that does not have this problem, and
`CC-BY-4.0` carries an **attribution** duty that belongs in the client's notices file, not in a
developer's head.

### Layer 4 — Measuring translation quality, and the metric that disagrees with your users

| Repo | Licence (verified) | Stars | Last push | What it is |
|---|---|---|---|---|
| [Unbabel/COMET](https://github.com/Unbabel/COMET) | **Apache-2.0** | 791★ | 2026-04-21 | Neural MT evaluation. Also the **reference-free QE** family (CometKiwi) — scores output with **no human reference**, which is the only kind of metric an agent can run in production |
| [mjpost/sacrebleu](https://github.com/mjpost/sacrebleu) | **Apache-2.0** | 1,266★ | 2026-08-20 | The reproducible BLEU/chrF++ implementation. Emits a version string so a score is comparable |
| [google-research/mt-metrics-eval](https://github.com/google-research/mt-metrics-eval) | **Apache-2.0** | 141★ | 2026-04-23 | Evaluates *the metrics themselves* against WMT human judgments |

#### The finding that should change how this gets quoted

From `andrewyng/translation-agent`'s own `README.md` — the author's own reported result, not a
third-party benchmark:

> *"even on documents where our agentic workflow captures **context and terminology better**,
> resulting in translations that **our human raters prefer** over current commercial offerings,
> evaluation at the sentence level (using the FLORES dataset) resulted in the agentic system
> **scoring lower on BLEU**."*

So on this layer's own evidence: **BLEU can move in the opposite direction from human preference
for exactly the agentic pipelines this KB recommends building.** An acceptance criterion written as
"BLEU ≥ X" can therefore fail a pipeline that is better, and — worse for a consultancy — pass one
that is worse. Use **COMET or a reference-free QE model for ranking**, keep **sacreBLEU only as a
reproducible regression tripwire**, and put **document-level human or MQM review on the terms that
carry legal weight**. That ordering is the deliverable, not the numbers.

Note also what the quote names: **FLORES**, the field's standard benchmark, is
[`facebookresearch/flores`](https://github.com/facebookresearch/flores) — **770★ and ARCHIVED
since 2023-11-20**.

### Layer 5 — Knowing which language you were spoken to in, and three archived staples

Routing, per-locale policy and the Brazilian and Indian duties below all presuppose detecting the
user's language. The three best-known libraries for it are **dead**, and their star counts hide it.

| Repo | Licence (verified) | Stars | State | Verdict |
|---|---|---|---|---|
| [pemistahl/lingua-py](https://github.com/pemistahl/lingua-py) | **Apache-2.0** | 1,822★ | push 2026-07-20 | ✅ **The live answer.** Accurate on short text, which is the hard case |
| [pemistahl/lingua](https://github.com/pemistahl/lingua) | **Apache-2.0** | 831★ | push 2025-03-21 | ✅ JVM sibling, for a Java estate |
| [facebookresearch/fastText](https://github.com/facebookresearch/fastText) | MIT | **26,502★** | **ARCHIVED 2024-03-22** | ❌ The most-starred row in this entire pass, and it is archived |
| [google/cld3](https://github.com/google/cld3) | Apache-2.0 | 886★ | **ARCHIVED 2023-05-24** | ❌ Still the default suggestion in older tutorials |

### Layer 6 — Regional language assets, placed deliberately

Globant sells into four regions; the languages are not interchangeable, and neither is the tooling.

| Repo | Licence (verified) | Stars | Last push | Region | Note |
|---|---|---|---|---|---|
| [AI4Bharat/IndicTrans2](https://github.com/AI4Bharat/IndicTrans2) | **MIT** | 500★ | 2025-10-03 | **APAC** | Translation for **all 22 scheduled languages of India** — i.e. exactly the set India's DPDP §5(3) names. The lowest-starred, highest-leverage row in this pass |
| [masakhane-io/masakhane-mt](https://github.com/masakhane-io/masakhane-mt) | **MIT** | 334★ | **2022-06-14** | **EMEA** | MT for African languages. Permissive and relevant, **four years without a push** — treat as a research corpus, not a dependency |
| [langtech-bsc/salamandra](https://github.com/langtech-bsc/salamandra) | Apache-2.0 | *(held since twelfth pass)* | — | **EMEA** | Already in this file as a sovereign base model; **also** the Iberian-language asset |
| [SakuraLLM/SakuraLLM](https://github.com/SakuraLLM/SakuraLLM) | **GPL-3.0** | 4,865★ | 2026-07-23 | **APAC** | JP→ZH translation LLM. Listed for completeness and **not recommended**: GPL-3.0, and its domain is light novels and games, not enterprise prose |
| **LATAM** | — | — | — | **LATAM** | **Informed gap.** No LATAM-origin translation or localisation project surfaced in this pass. The region's open-language assets already in this KB (`latam-gpt/language_identifier`, `anonymization-filter`, `toxicity-classifier`) are **corpus-cleaning tools, not translation tooling**. For Spanish/Portuguese, Opus-MT's pairs plus a client-owned glossary is the honest recommendation — not a regional project that does not exist |

### Licence traps in this layer — five, and the first is the one that ends an engagement

**1. Tolgee is not Apache-2.0, and its own root licence file says so.** The badge reads
`NOASSERTION`; an aggregator read it as "Apache-2.0" and another as *"self-hosting is fully
open-source"*. Byte-read from `tolgee/tolgee-platform/main/LICENSE`:

> *"Tolgee monorepo uses multiple licenses. Portions of this software are licensed as follows:
> — All content that resides under the **`"ee/"` and `"/webapp/src/ee"`** directory of this
> repository, is licensed under the license defined in `"ee/LICENSE"`. — Content **outside** of the
> above mentioned directories or restrictions **defaults to the "Apache License 2.0"**."*

And `ee/LICENSE` is **"Tolgee EE License version 1"**:

> *"You can use software made available under this license for **non-commercial purposes only**."*
> … *"**Hosted or Managed Services**: You may not provide the software to third parties as a hosted
> or managed service"* … *"**License Key Functionality**: You may not move, change, disable, or
> circumvent the license key functionality."*

This is the **onyx pattern from the seventh pass, exactly repeated**: a permissive headline with the
enterprise-grade features fenced into `ee/` under terms a consultancy cannot use. Two independent
implications: Globant **may not use `ee/` features in client work at all** (non-commercial), and
**may not run even the Apache-2.0 portion for a client as a managed service** if that service
exposes `ee/` functionality. A probe of a repo's root `LICENSE` that stops at the first line
`Apache License` — which is exactly what a `grep -i "apache"` does — gets this **wrong**.

**2. Weblate is GPL-3.0, and the directories say MIT.** Two aggregators returned MIT in this pass's
searches. Byte-read: `GNU GENERAL PUBLIC LICENSE Version 3`. GPL-3.0 is workable for a *hosted
internal TMS* (no distribution, no network clause) but it is **not** a component to link into a
client's product. The distinction is the engagement.

**3. The most-starred option in two of six layers is the copyleft one.** LibreTranslate
(**17,840★, AGPL-3.0**) and Weblate (6,180★, GPL-3.0) both top their categories. The permissive
answers are **quieter**: `argos-translate` (MIT, 6,691★) *is* LibreTranslate's engine without the
AGPL API wrapper, and **Pontoon** (BSD-3-Clause, 1,679★) is the TMS. In this layer, sorting by
stars sorts **away** from what Globant can ship.

**4. `traduora/traduora` does not exist.** The path returned by an aggregator **422s** against the
search API. The real project is **`ever-co/ever-traduora`** (AGPL-3.0, 2,140★). Eighth addition to
the rename ledger below.

**5. `NOASSERTION`/`null` resolved in four different directions in one pass** — confirming the
ninth pass's inverted rule that a missing badge is *the absence of a verdict*, not a bad licence:
`marian` → **MIT in `LICENSE.md`** (wrong filename); `icu`/`cldr`/`message-format-wg` →
**Unicode-3.0** (a real, permissive, OSI-approved licence GitHub simply does not badge);
`python-fluent` → **Apache-2.0**; `formatjs` → **no root licence file at all**, MIT declared
**per package** (`packages/intl/package.json` → `"license": "MIT"`), which is why the badge is
`null` rather than `NOASSERTION`. And `lingodotdev/lingo.dev` keeps its licence in **`LICENSE.md`**
while its root `readme.md` is a **22-byte pointer file** containing the string
`packages/cli/README.md` — a naive README fetch returns nothing at all.

### Rename ledger addition (sixteenth pass)

| Cited as | Actually | Evidence |
|---|---|---|
| `traduora/traduora` | **`ever-co/ever-traduora`** (AGPL-3.0, 2,140★) | search API **422** on the former; the latter resolves, pushed 2026-11-24 |

### Method notes from this pass — three new ways to be wrong

1. **`huggingface.co` is proxy-dead from this session (HTTP 000 on both `/api/models/…` and
   `/raw/…`).** Any claim about model-weight licensing therefore cannot be byte-proven here. This
   pass marks the one such claim (NLLB) as secondary-sourced rather than promoting it to a finding.
   A GitHub-only verification plane **cannot close the weights question** — and the weights are
   what translate.
2. **A licence file can be a *multi-licence declaration*.** Byte-reading the first 400 bytes of
   `LICENSE` is the method the earlier passes established, and on Tolgee it returns `Apache
   License` — the correct answer is the opposite. When a root licence mentions a **directory**,
   the probe is not finished until that directory's own licence is read.
3. **The licence may not be in a file named `LICENSE`.** Two rows this pass: `marian` → `LICENSE.md`,
   `lingo.dev` → `LICENSE.md`. A 404 on `LICENSE` is not evidence of an unlicensed project.

---

## Decimoséptimo pase — 2026-11-24 — el límite del documento de registro fiscal

> **El tema: lo que el agente puede *emitir en nombre del Estado*.** Dieciséis pases construyeron
> ocho límites — lectura, escritura, procedencia, contención, borrado, accesibilidad, pesos, huella
> e idioma. Todos los decide, en última instancia, quien construye el sistema. **Este no.** Un
> documento fiscal electrónico no es válido porque el software lo diga: es válido porque una
> autoridad tributaria lo acepta, con un formato que ella fija y unas reglas que ella publica.
>
> **Medido antes de buscar**, sobre los nueve archivos y en los dos idiomas de la KB:
> `Peppol` **0** · `AS4` **0** · `EN 16931` **0** · `UBL` **0** (con límite de palabra) ·
> `Factur-X` **0** · `ZUGFeRD` **0** · `Schematron` **0** · `CFDI` **0** · `NF-e` **0** ·
> `Verifactu` **0** · `KSeF` **0** · `FatturaPA` **0** · `ViDA` **0** · `SAF-T` **0** ·
> `EDIFACT` **0** · `X12` **0** · `GS1` **0** · `CTC` **0**.
> **No fue un cero limpio, y el resto importa:** `facturacion` **25** y `e-invoic` **5** ya estaban,
> desde el pase once — tres repos de *localización fiscal* LATAM en GitLab
> (`dansanti/facturacion_electronica`, `odoocoop/…`, `torresoftware/apidian2020`) y los módulos
> `OCA/l10n-*`. Es decir: **la KB tenía el módulo de localización y no tenía ni el formato, ni el
> validador, ni el transporte, ni el modelo de autorización.** Tenía el enchufe y le faltaba la red.

**Instrumento de este pase.** `api.github.com` responde **403** desde esta sesión para repos fuera
del alcance de la sesión, pero `gh api -X GET search/repositories -f q='repo:owner/name …'`
devuelve **estrellas + SPDX + `pushed_at` + `default_branch` + `archived` en una sola llamada** y
acepta varios `repo:` por consulta. Toda licencia `NOASSERTION`/`null` se resolvió **leyendo los
bytes** por GET con rango sobre `raw.githubusercontent.com` (`HEAD` sigue bloqueado por el proxy).
Dos repos se **clonaron** (`--depth 1`) para inspeccionar el árbol, porque la pregunta no era qué
licencia declara el repo sino **qué archivos de terceros empaqueta**.

### Las dos sintaxis de la misma norma no validan igual — probado byte a byte

EN 16931 define **un** modelo semántico de factura y **dos** vinculaciones de sintaxis: **UBL**
(OASIS) y **CII** (UN/CEFACT). Los artefactos oficiales de validación —los *Schematron* que deciden
si una factura pasa— se publican en
[`ConnectingEurope/eInvoicing-EN16931`](https://github.com/ConnectingEurope/eInvoicing-EN16931).
Se leyeron los de la versión **1.3.17** (tag `validation-1.3.17`, commit
`6e35e0ab8b09eb183f7d84b282e24ef95f9f5715`) y **las dos vinculaciones implementan la misma regla de
negocio con aritmética distinta**:

| Regla | UBL (`EN16931-UBL-validation.sch`) | CII (`EN16931-CII-validation.sch`) | Consecuencia |
|---|---|---|---|
| **BR-CO-17** | `abs(cbc:TaxAmount) - 1 < round(…)` — **estricto** | `abs(ram:CalculatedAmount) - 1 <= round(…)` — **inclusivo** | Una factura desviada **exactamente 1,00** unidad monetaria **pasa en CII y falla en UBL**. Un carácter de diferencia en el artefacto oficial. |
| **BR-S-08** | `TaxableAmount - 1 < suma … and TaxableAmount + 1 > suma` — **tolerancia ±1** | `xs:decimal(ram:BasisAmount) = (round(…) …)` — **igualdad estricta** contra sumandos redondeados uno a uno | La base imponible del desglose de IVA admite holgura en UBL y **ninguna** en CII. |

**Por qué esto no es trivia de implementación.** La conversión UBL↔CII es exactamente lo que hace
falta en Peppol, en XRechnung, en Factur-X y en cualquier integración ViDA; es también el primer
trabajo que se le pedirá a un agente en esta capa. **Una conversión fiel puede invertir la validez
sin tocar un solo número.** De ahí la regla de redacción de propuestas:

> **«Cumple EN 16931» no significa nada sin tres datos: qué vinculación (UBL o CII), qué versión de
> artefactos (1.3.17 ≠ 1.3.14) y qué conjunto de reglas encima (CEN, Peppol BIS, XRechnung,
> PINT-SG).** Las reglas nacionales son *forks* de las de CEN, no capas sobre ellas.

### Las reglas oficiales son EUPL-1.2 — sexta aparición de la misma regla de licencia

`ConnectingEurope/eInvoicing-EN16931` — **EUPL-1.2**, leído byte a byte: `LICENSE.txt`, **13 871 B**,
encabezado `Licensed under European Union Public Licence (EUPL) version 1.2`. GitHub lo muestra como
`NOASSERTION`. **La EUPL es recíproca**: quien *empaqueta* los artefactos distribuye obra EUPL.

> **El SPDX de un repo describe su código; no dice nada de los datos que empaqueta, los pesos que
> descarga ni el servicio al que llama.** Pesos (pase 12), AUP (pase 12), SOM-1.0 (pase 13), datos de
> intensidad de red (pase 15), `ee/` (pase 16) — y ahora **las reglas de la propia norma**. Es la
> primera vez que lo empaquetado **es el producto**: un validador sin reglas no valida nada.

### El repo de 1★ que documenta la pila de licencias mejor que los de 200★

| Repo | Licencia (verificada) | ★ | Último push | Rama por defecto | Qué es |
|---|---|---|---|---|---|
| [einvoice-validator/einvoice-validator](https://github.com/einvoice-validator/einvoice-validator) | **código MIT** (`LICENSE`, 1 092 B); *crates* publicados: `MIT AND EUPL-1.2 AND LicenseRef-OASIS-Copyright-Notice AND LicenseRef-UN-CEFACT-Copyright-Notice AND W3C-19980720` | 1 | 2026-11-23 | `main` | Validador EN 16931 (UBL+CII), Peppol BIS 3.0 y Factur-X/ZUGFeRD en Rust. CLI, librería y WASM/npm |
| [attestwire/en16931](https://github.com/attestwire/en16931) | **MIT** | 1 | 2026-10-04 | `main` | Validador y generador EN 16931 en TypeScript, **cero dependencias** |

**Dos maneras de entregar validación EN 16931, y el intercambio es exactamente opuesto.**

1. **Empaquetar los artefactos oficiales.** `einvoice-validator` *vendoriza sin modificar* los dos
   conjuntos 1.3.17 (**364 archivos**, con `SHA256SUMS`, `README` de procedencia y `LICENSE.txt`
   propio por directorio), y declara por *crate* la **expresión compuesta de cinco términos** de la
   tabla. Fidelidad perfecta a la regla oficial; a cambio, **tu binario lleva EUPL-1.2 dentro** más
   los avisos de copyright de OASIS, UN/CEFACT y W3C de los esquemas UBL 2.1 y CII D16B. El
   `Cargo.toml` del *workspace* dice `license = "MIT"` **y es cierto del código**: la expresión
   compuesta vive en los *crates* que sí empaquetan (`einvoice-validator`, `einvoice-cli`,
   `einvoice-wasm`). **La insignia del repo y lo que se distribuye no son la misma cosa.**
2. **Reimplementar las reglas.** `attestwire/en16931` no contiene **ni un solo `.sch` ni `.xslt`**
   (contado: **0**). Reescribe las reglas en TypeScript — sus propios tests razonan sobre el medio
   céntimo de `BR-S-09` y sobre que `CEN-EN16931-CII.sch` usa `<=` donde UBL no. Licencia limpia
   (MIT puro, sin herencia EUPL); a cambio **pasas a ser el autor de las reglas** y heredas la
   divergencia cada vez que CEN publica 1.3.18.

**Lo que `einvoice-validator` *no* empaqueta es igual de instructivo**, y es el inventario de
derechos que nadie más de esta capa escribe: los esquemas **XAdES de ETSI** (el entregable no
permite reproducción sin permiso escrito), los **CII D22B de UNECE** (publicados **sin aviso ni
licencia**, luego sin derecho de redistribución) y los archivos **Peppol BIS 3.0** (se descargan en
tiempo de test, no se redistribuyen). Corpus de pruebas: **5 005 archivos**.

### El transporte: una sola pila permisiva, y es de un solo autor

| Repo | Licencia (verificada) | ★ | Push | Rama | Papel |
|---|---|---|---|---|---|
| [phax/phase4](https://github.com/phax/phase4) | **Apache-2.0** (`LICENSE`, 10 173 B) | 246 | 2026-11-23 | `master` | Cliente y servidor **AS4** embebible; perfiles Peppol y CEF eDelivery incorporados |
| [phax/phoss-ap](https://github.com/phax/phoss-ap) | **Apache-2.0** | 59 | **2026-11-24** | `main` | *Access Point* Peppol completo y autónomo sobre phase4 |
| [phax/peppol-commons](https://github.com/phax/peppol-commons) | **Apache-2.0** | 51 | 2026-11-23 | `master` | Identificadores, *codelists*, SBDH, cliente SMP/SML, MLR/MLS |
| [phax/phoss-smp](https://github.com/phax/phoss-smp) | **MPL-2.0 el *backend*, Apache-2.0 el resto** (`LICENSE.md`, **347 B**) | 216 | 2026-11-23 | `master` | Servidor **SMP** Peppol/OASIS BDXR |
| [phax/ph-ubl](https://github.com/phax/ph-ubl) | **Apache-2.0** | 142 | 2026-11-23 | `master` | Lectura/escritura UBL 2.0–2.4 con validación de esquema |
| [phax/ph-schematron](https://github.com/phax/ph-schematron) | **Apache-2.0** | 137 | 2026-11-23 | `master` | Motor Schematron (XSLT y nativo) — **el que compila las reglas de CEN** |
| [OxalisCommunity/oxalis-ng](https://github.com/OxalisCommunity/oxalis-ng) | **EUPL-1.1-or-later** — declarada **solo en la cabecera del `pom.xml`** | 53 | 2026-10-04 | `master` | *Access Point* Peppol de la comunidad noruega (NorStella) |
| [OxalisCommunity/oxalis](https://github.com/OxalisCommunity/oxalis) | **sin archivo de licencia en la raíz** — `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `NOTICE` → **404** | 150 | 2026-04-16 | `master` | Oxalis clásico. **Su propio README dice: usa Oxalis-NG para toda implementación nueva** |
| [holodeck-b2b/Holodeck-B2B](https://github.com/holodeck-b2b/Holodeck-B2B) | **GPL-3.0** | 93 | 2026-09-09 | `master` | Mensajería AS4 ebMS3 |
| [iterasdev/peppol-py](https://github.com/iterasdev/peppol-py) | **0BSD** | 10 | 2026-10-19 | `master` | Cliente Peppol en Python — **clase de licencia nº 14 en esta KB** |
| [dbkosky/as4](https://github.com/dbkosky/as4) | **Apache-2.0** | 3 | 2026-09-26 | `master` | Implementación AS4 mínima |
| [OpenAS2/OpenAs2App](https://github.com/OpenAS2/OpenAs2App) | **GPL-3.0** | 243 | 2026-11-16 | `master` | **AS2** — el transporte real del EDI norteamericano |

**La forma del hallazgo.** La esquina de transporte de este plano es **estructuralmente copyleft**
salvo por un autor: Oxalis-NG es EUPL, Holodeck B2B y OpenAS2 son GPL-3.0, Domibus (de la Comisión
Europea) es EUPL-1.2. **La única pila AS4/Peppol permisiva y mantenida es la de Philip Helger**, y
eso es un riesgo de concentración que hay que decir en voz alta en una propuesta, no un detalle.
**Quinta aparición del patrón «archivado/desaconsejado pero recomendado»**, con una variante nueva:
Oxalis (150★) no está archivado — **su propio README desaconseja usarlo** mientras sigue siendo el
primer resultado de búsqueda, y además **no tiene archivo de licencia**.

**Sexta vía de resolución de licencia, nueva en esta KB.** Oxalis-NG no tiene `LICENSE`: la licencia
está en la **cabecera del `pom.xml`** (`Licensed under the EUPL, Version 1.1 or – as soon they …`).
Orden de desempate actualizado: (1) `SPDX-License-Identifier` en el manifiesto, (2) directorio REUSE
`LICENSES/<SPDX>.txt`, (3) lectura byte a byte + tamaño, (4) clasificadores de PyPI,
(5) **cabecera del manifiesto de construcción (`pom.xml`, `build.gradle`, `*.csproj`)**.

### Validadores nacionales y formato híbrido (EMEA)

| Repo | Licencia | ★ | Push | Qué resuelve |
|---|---|---|---|---|
| [itplr-kosit/validator](https://github.com/itplr-kosit/validator) | **Apache-2.0** | 199 | 2026-11-17 | Motor de validación XSD+Schematron del **KoSIT** alemán — el de referencia para **XRechnung** |
| [itplr-kosit/validator-configuration-xrechnung](https://github.com/itplr-kosit/validator-configuration-xrechnung) | **Apache-2.0** | 120 | 2026-11-17 | La **configuración** XRechnung para ese motor: escenarios, reglas y versiones |
| [ZUGFeRD/mustangproject](https://github.com/ZUGFeRD/mustangproject) | **Apache-2.0** | 498 | 2026-11-23 | Librería, validador y herramienta **Factur-X / ZUGFeRD / Order-X** en Java |
| [akretion/factur-x](https://github.com/akretion/factur-x) | **BSD-3-Clause** (`LICENSE.txt`, 1 508 B; `NOASSERTION` en la insignia) | 317 | 2026-11-19 | Factur-X en Python: incrusta y extrae el XML del PDF/A-3 |

**Motor y reglas se licencian por separado, y conviene.** El motor de KoSIT es Apache-2.0; la
configuración XRechnung, Apache-2.0; **las reglas CEN que hay debajo, EUPL-1.2**. Es exactamente la
separación que permite entregar: se distribuye el motor permisivo y se **referencia** el paquete de
reglas en lugar de incrustarlo (`einvoice-validate rules fetch xrechnung` hace esto mismo contra el
registro de KoSIT).

### LATAM — el modelo de autorización previa, con la pila realmente disponible

| Repo | País | Licencia (verificada) | ★ | Push | Nota |
|---|---|---|---|---|---|
| [thegreenter/greenter](https://github.com/thegreenter/greenter) | 🇵🇪 Perú (SUNAT) | **MIT** | 378 | 2026-11-16 | **La librería fiscal LATAM permisiva más estrellada de este pase** |
| [giansalex/lycet](https://github.com/giansalex/lycet) | 🇵🇪 Perú | **MIT** | 106 | 2026-11-10 | API REST sobre Greenter — **la superficie que un agente puede llamar** |
| [thegreenter/ubl-validator](https://github.com/thegreenter/ubl-validator) | 🇵🇪 Perú | **MIT** | 16 | 2026-09-02 | Validación UBL antes de enviar a SUNAT |
| [nfephp-org/sped-nfe](https://github.com/nfephp-org/sped-nfe) | 🇧🇷 Brasil | **LGPL-3.0** (`LICENSE.md`, 8 851 B; insignia `NOASSERTION`) | 1 637 | 2026-11-23 | La librería NF-e de referencia — **copyleft débil, no permisiva** |
| [akretion/nfelib](https://github.com/akretion/nfelib) | 🇧🇷 Brasil | **MIT** | 224 | 2026-11-05 | Enlaces Python generados desde los XSD oficiales (NF-e, CT-e, …) |
| [erpbrasil/erpbrasil.edoc](https://github.com/erpbrasil/erpbrasil.edoc) | 🇧🇷 Brasil | **MIT** | 32 | 2026-11-18 | Transmisión de documentos electrónicos a SEFAZ |
| [edueevaristo/reforma-tributaria-api](https://github.com/edueevaristo/reforma-tributaria-api) | 🇧🇷 Brasil | **MIT** | 1 | **2026-11-24** | IBS/CBS por ítem según **NT 2025.002**, validado contra el XSD oficial; incluye *mocks* WireMock de SEFAZ |
| [grupomg-tech/calculadora-reforma-tributaria](https://github.com/grupomg-tech/calculadora-reforma-tributaria) | 🇧🇷 Brasil | **MIT** | 3 | 2026-11-02 | Simulador IBS/CBS/IS — **declara no ser la calculadora oficial de la Receita** |
| [OCA/l10n-brazil](https://github.com/OCA/l10n-brazil) | 🇧🇷 Brasil | **AGPL-3.0** | 376 | 2026-11-24 | Localización Odoo. **Rama por defecto `19.0`**, no `main` |
| [phpcfdi/sat-ws-descarga-masiva](https://github.com/phpcfdi/sat-ws-descarga-masiva) | 🇲🇽 México | **MIT** | 198 | 2026-09-20 | Descarga masiva de CFDI desde el SAT |
| [nodecfdi/cfdi-core](https://github.com/nodecfdi/cfdi-core) | 🇲🇽 México | **MIT** | 4 | 2026-11-23 | Núcleo CFDI en TypeScript |
| [LibreDTE/libredte-lib-core](https://github.com/LibreDTE/libredte-lib-core) | 🇨🇱 Chile | **AGPL-3.0** | 228 | 2026-11-19 | Núcleo DTE del SII. **No permisivo** |
| [LibreDTE/libredte-api-client-python](https://github.com/LibreDTE/libredte-api-client-python) | 🇨🇱 Chile | **LGPL-3.0** | 10 | 2026-11-24 | Cliente del servicio alojado |
| [reingart/pyafipws](https://github.com/reingart/pyafipws) | 🇦🇷 Argentina | **LGPL-3.0** | 366 | **2025-07-20** | Facturación AFIP/ARCA. **Sin push desde hace ~16 meses** — el riesgo es el país que más cambia de interfaz |

**El mapa de licencias de LATAM es el inverso del de EMEA y hay que decirlo en la propuesta.** En
EMEA el *transporte* es copyleft y el *validador* tiene opción permisiva; en LATAM **los núcleos
nacionales más usados son copyleft** (sped-nfe LGPL-3.0, LibreDTE AGPL-3.0, OCA AGPL-3.0, pyafipws
LGPL-3.0) y **la única pila nacional permisiva y viva es la peruana** (Greenter + Lycet + ubl-validator,
MIT las tres). Para Brasil, la vía permisiva existe pero es **otra**: `nfelib` (MIT) + `erpbrasil.edoc`
(MIT), no `sped-nfe`.

### APAC — SDK de un régimen de autorización, con el riesgo de obsolescencia medido

| Repo | Licencia | ★ | Push | Nota |
|---|---|---|---|---|
| [klsheng/myinvois-php-sdk](https://github.com/klsheng/myinvois-php-sdk) | **MIT** | 103 | 2026-01-08 | SDK MyInvois (🇲🇾 LHDN) más estrellado y permisivo |
| [zahidaramai/MyInvoice-SDK-Middleware](https://github.com/zahidaramai/MyInvoice-SDK-Middleware) | **MIT** | 13 | 2026-11-03 | Pasarela REST: autenticación, firma y envío |
| [farhan-syah/myinvois-client](https://github.com/farhan-syah/myinvois-client) | **LGPL-3.0** | 51 | 2025-10-28 | Cliente TypeScript |
| [amaseng/myinvois-open-sdk](https://github.com/amaseng/myinvois-open-sdk) | **Apache-2.0** | 31 | **2024-10-10** | **Dos años sin push**, y el SDK oficial publicó la versión **1.0 en septiembre de 2026**: permisivo pero **desfasado respecto del régimen que implementa** |
| [deadboy18/myinvois-docs](https://github.com/deadboy18/myinvois-docs) | **`NOASSERTION` sin resolver** | 10 | 2026-11-23 | Espejo de documentación. Se registra **sin veredicto**, no como permisivo |

**La trampa específica de esta capa**: aquí la licencia no es el primer filtro, **la fecha de push
lo es**. Un SDK fiscal desfasado no «funciona peor»: produce documentos **rechazados**. El
Apache-2.0 de `amaseng` es el más limpio de los cinco y el **menos utilizable hoy**.

### La capa de extracción — donde sí hay repos grandes, y no son agentes

| Repo | Licencia | ★ | Push | Nota |
|---|---|---|---|---|
| [invoice-x/invoice2data](https://github.com/invoice-x/invoice2data) | **MIT** | 2 254 | **2026-11-24** | Extracción de datos de facturas por plantillas (PDF/texto/imagen). El repo más estrellado del pase |
| [invoicerr-app/invoicerr](https://github.com/invoicerr-app/invoicerr) | **AGPL-3.0** | 735 | 2026-11-24 | Facturación autoalojada. Rama por defecto **`dev`** |

**Hallazgo negativo, medido y relevante para la propuesta:** la búsqueda de *agentes* de cuentas por
pagar devolvió **productos comerciales** (Basware InvoiceAI y su Supplier Agent de feb-2026, la
compra de Rossum por Coupa anunciada en may-2026, Tipalti, Stampli, Vic.ai, AppZen, Ramp) y **ningún
agente open source específico de facturación electrónica**. Lo abierto de este plano **no es el
agente: son las primitivas de cumplimiento** —formato, validador, transporte, firma—. Esa es
exactamente la división de trabajo que hace vendible el encargo (ver `compose/patterns.md`,
Receta 32). ⚠️ *Secundario: listado de proveedores a nivel de snippet, no verificado en primario.*

### Ramas por defecto de este pase — el `main` ciego habría fallado 6 veces

De las **46 direcciones** verificadas en este pase (**42 nuevas** para la KB), **la rama por defecto no fue `main` en 6 casos no obvios**:
`apache/ofbiz-framework` → **`trunk`**, `frappe/erpnext` → **`develop`**,
`OCA/l10n-brazil` → **`19.0`** (¡un número de versión!), `invoiceninja/invoiceninja` →
**`v5-stable`**, `invoicerr-app/invoicerr` → **`dev`**, `LibreDTE/libredte-app-community` →
**`legacy`**, además de los muchos `master` de la pila `phax/*`. `gh api search/repositories`
devuelve `default_branch` **en la misma llamada** que la licencia, así que construir un `raw` URL
sobre `main` por defecto es un error evitable, no una fatalidad.

## Decimoctavo pase — 2026-11-24 — la capa del calendario: la base horaria, los festivos y el día hábil

> **34 direcciones verificadas el 2026-11-24, 29 nuevas para la KB.** Canal: `gh api -X GET
> search/repositories` con varios `repo:` por consulta (SPDX, estrellas, `default_branch`,
> `pushed_at`, `archived` en una sola llamada), porque **`api.github.com` y `gh api repos/<x>`
> responden 403** para repos fuera del alcance de esta sesión. Toda insignia `NOASSERTION`/`NONE` se
> resolvió **leyendo los bytes** del `LICENSE` por `raw.githubusercontent.com`.
>
> **Por qué esta capa es nueva y no una reformulación de la durabilidad que la KB ya tenía.** La KB
> tiene desde hace pases los **motores de ejecución durable** —`temporalio/temporal` (MIT, 24 518★),
> `restatedev/restate`, `dbos`— que responden «qué pasa si el agente se muere a mitad de un proceso
> de 40 pasos». **Eso es resiliencia del orquestador, no corrección del calendario.** Temporal
> reintenta un paso con total fiabilidad **en el instante equivocado** si la zona, el festivo o la
> versión de tzdata están mal. Medido: `tzdata` 0, `IANA` 0, `ISO 8601` 0, `día hábil` 0, `cron` 0,
> `RFC 5545` 0, `day count` 0 en los nueve archivos antes de este pase.

### La fuente de verdad (2) — y su licencia depende de qué archivos copies

| Repo | Licencia (leída por bytes) | ★ | Último push | Nota |
|---|---|---|---|---|
| [eggert/tz](https://github.com/eggert/tz) | **Dominio público**, con excepción BSD-3-Clause | 1 938 | 2026-11-23 | `LICENSE` son **252 B**: «*Unless specified below, all files in the tz code and data (including this LICENSE file) are in the public domain. If the files `date.c`, `newstrftime.3`, and `strftime.c` are present, they contain material derived from BSD and use the BSD 3-clause license*». Es el repositorio **aguas arriba** del tzdb; `data.iana.org` está **bloqueado por el proxy (403)** desde esta sesión, y este repo es el mismo artefacto con igual autoridad. |
| [python/tzdata](https://github.com/python/tzdata) | **Apache-2.0** (insignia `NOASSERTION`) | 126 | 2026-11-01 | El tzdb empaquetado para PyPI. `LICENSE` (625 B) con copyright **2020 Paul Ganssle (Google)** y **2026 Stan Ulbrych**: el relevo de mantenimiento es visible en el archivo. Es la dependencia que decide la respuesta cuando el contenedor **no trae** `/usr/share/zoneinfo`. |

> **Dominio público no es estrictamente mejor que Apache-2.0** —sin concesión de patentes, sin
> renuncia de garantía—, regla que esta KB ya registró en el pase ocho con los artefactos de NIST.
> Aquí reaparece con una vuelta de tuerca: **la licencia de `eggert/tz` es condicional a la presencia
> de tres archivos**, así que un vendor-in parcial puede cambiar el régimen sin que nadie lo note.

### El formato y la localización (2, ya en la KB — aquí con la licencia leída y el papel corregido)

| Repo | Licencia | ★ | Push | Lo que hay que saber |
|---|---|---|---|---|
| [unicode-org/cldr](https://github.com/unicode-org/cldr) | **Unicode V3** para los datos; **UTS #35 restringido** | 1 172 | 2026-11-24 | Un repositorio, **dos regímenes**: ver abajo. |
| [unicode-org/icu](https://github.com/unicode-org/icu) | insignia `NOASSERTION` | 3 652 | 2026-11-24 | El consumidor de CLDR que llevan dentro Java, .NET, Node y los navegadores. **Es el eslabón que forzó el apaño de tzdb de 2026.** |

**La licencia de CLDR, por bytes (`LICENSE`, 3 193 B), y es el hallazgo de licencia nº 2 del pase.**
Sobre UTS #35 —el documento de la norma LDML— dice: «*permission must be obtained from Unicode, Inc.
prior to any reproduction, modification, or other use not permitted by the Unicode Terms of Use*» y
«*You may not make copies of or modifications to this publication for public distribution, or
incorporate it in whole or in part into any product or publication without the express written
permission of Unicode*», con una única salvedad para comentar y forkear **dentro del repositorio**.
Y después: «*All other content in this repo is released under UNICODE LICENSE V3*», que sí es una
concesión permisiva estilo MIT sobre «Data Files» y «Software».
**Traducción operativa: los datos de locale se pueden empaquetar y vender; el texto de la norma no se
puede pegar en un entregable de cliente.** Séptima aparición de la regla de esta KB —*el SPDX de un
repo describe su código, no lo que empaqueta*— y la segunda, tras el pase diecisiete, en que **lo
empaquetado es el producto**.

### Los datos de festivos (6) — donde la licencia del dato se separa de la del código

| Repo | Licencia (verificada) | ★ | Rama | Push | Nota |
|---|---|---|---|---|---|
| [vacanza/holidays](https://github.com/vacanza/holidays) | **MIT** | 1 997 | **`dev`** | 2026-11-24 | El sucesor de `dr-prodigy/python-holidays`. Push **el día de hoy**; es el más vivo de la capa. **Su rama por defecto es `dev`**: un clon ciego de `main` falla. |
| [commenthol/date-holidays](https://github.com/commenthol/date-holidays) | **`(ISC AND CC-BY-SA-4.0)`** — declarado en `package.json` | 1 122 | `master` | 2026-11-19 | **Los datos son share-alike.** Ver abajo. |
| [nager/Nager.Date](https://github.com/nager/Nager.Date) | **MIT** | 1 441 | `main` | 2026-11-18 | .NET. La biblioteca es MIT; **el servicio HTTP alojado tiene sus propias condiciones** y no se verificó en este pase — no lo cotice como si fuera lo mismo. |
| [focus-shift/jollyday](https://github.com/focus-shift/jollyday) | **Apache-2.0** | 144 | `main` | 2026-11-19 | El fork **mantenido** para Java. |
| [svendiedrichsen/jollyday](https://github.com/svendiedrichsen/jollyday) | insignia `NOASSERTION` | **197** | `master` | **2024-05-01** | El original. **Más estrellas que el fork vivo y 2,5 años sin push.** |
| [workalendar/workalendar](https://github.com/workalendar/workalendar) | **MIT** | 946 | `master` | **2024-04-12** | Cálculo de días laborables en Python. **No está archivado**, así que la forja lo muestra vivo. |

**El hallazgo de licencia nº 1 del pase, y es el contraejemplo limpio del pase diecisiete.**
`commenthol/date-holidays` **declara él mismo una expresión compuesta**: su `package.json` dice
`"license": "(ISC AND CC-BY-SA-4.0)"`, y su `LICENSE` (13 715 B) explica el porqué en la primera
línea: «*The data contained in `holidays.yaml` is available under CC BY-SA 4.0 … as the data obtained
relies on wikipedia articles. The required attribution can be found inside the file. All other code
is Copyright (c) 2015 commenthol and available under ISC*».
**El código es permisivo y los festivos son copyleft de datos.** El pase diecisiete escribió que
«ninguno de los de 200★+ de la capa publica una expresión compuesta»; **aquí uno de 1 122★ sí la
publica**, y por eso GitHub lo marca `NOASSERTION`. **Tercera dirección de resolución para
`NOASSERTION`: no es desidia ni es permisivo-oculto, es una expresión compuesta honesta.**
Consecuencia para Globant: **empaquetar `holidays.yaml` en un producto de cliente arrastra
CC BY-SA 4.0 sobre los datos.** Las alternativas verificadas sin esa carga son `vacanza/holidays`
(MIT) y `focus-shift/jollyday` (Apache-2.0).

> **Un calendario de festivos sin mantenimiento no es código viejo: es código incorrecto.** Los
> festivos los cambia un parlamento, no un commit. `workalendar` y `svendiedrichsen/jollyday` llevan
> más de dos años sin push y **ninguno está archivado**, así que ninguna señal automática lo avisa.
> Decimotercera y decimocuarta entrada en la lista de «recomendado pero no usable» de esta KB.

### La aritmética de fechas (9) — y la insignia que no dice de menos, dice nada

| Repo | Licencia (verificada) | ★ | Rama | Nota |
|---|---|---|---|---|
| [date-fns/date-fns](https://github.com/date-fns/date-fns) | insignia **`NONE`**; **MIT** en npm | **36 663** | `main` | El más grande de la capa. Ver abajo. |
| [moment/luxon](https://github.com/moment/luxon) | **MIT** | 16 457 | `master` | El sucesor recomendado de Moment. |
| [moment/moment-timezone](https://github.com/moment/moment-timezone) | **MIT** | 3 880 | **`develop`** | Empaqueta su **propia copia** de tzdata: **un eslabón más que versionar**. |
| [python-pendulum/pendulum](https://github.com/python-pendulum/pendulum) | **MIT** | 6 685 | `master` | Renombrado desde `sdispater/pendulum`. |
| [arrow-py/arrow](https://github.com/arrow-py/arrow) | **Apache-2.0** | 9 053 | `master` | Push 2026-06-22. |
| [dateutil/dateutil](https://github.com/dateutil/dateutil) | **Apache-2.0 *y* BSD-3-Clause** | 2 647 | `master` | Ver abajo. |
| [nodatime/nodatime](https://github.com/nodatime/nodatime) | **Apache-2.0** | 3 007 | `main` | .NET; el modelo de tipos más estricto de la capa. |
| [JodaOrg/joda-time](https://github.com/JodaOrg/joda-time) | **Apache-2.0** | 4 977 | `main` | Java pre-`java.time`; sigue con push (2026-10-28). |
| [HowardHinnant/date](https://github.com/HowardHinnant/date) | **MIT, por archivo** | 3 441 | `master` | Ver abajo. |

**`date-fns`: la insignia `NONE` es literalmente correcta sobre la raíz del repositorio.** Cinco
rutas probadas —`LICENSE`, `LICENSE.txt`, `LICENSE.md`, `license.md`, `LICENCE`— devuelven **404**, y
el `package.json` de la raíz es `@date-fns/root`, `"version": "0.0.0"`, `"private": true`, **sin campo
`license`**: es el manifiesto de un monorepo, no del paquete. El artefacto publicado sí declara:
`https://registry.npmjs.org/date-fns/latest` → **`4.4.0`, `license: MIT`**. **Se resuelve en el
registro, no en la forja.** Esta KB ya usaba los clasificadores de PyPI como canal independiente de
la forja; **ahora queda probado en npm y en la dirección contraria: la forja no dice de menos, no
dice nada, y el registro es la autoridad.**

**`dateutil` es un *AND*, no un *OR*, y eso es lo inusual.** `LICENSE` (2 889 B) abre con Apache-2.0
y en la línea 54 remata: «*The above BSD License Applies to all code, even that also covered by
Apache 2.0*». La mayoría de los duales son disyuntivos («elija una»); **este es conjuntivo: ambas
aplican a la vez**. Permisivo por las dos vías, pero una auditoría que anote solo «Apache-2.0»
describe mal el archivo.

**`HowardHinnant/date`: licenciado archivo por archivo, sexta vía de resolución de esta KB.**
`LICENSE.txt` (1 637 B): «*The source code in this project is released using the MIT License. There
is no global license for the project because each file is licensed individually*». **No existe una
licencia del proyecto**; el vendor-in parcial debe leer la cabecera de cada archivo que copie. Es la
biblioteca de la que salió `std::chrono`, así que su semántica está dentro de todo C++20 moderno.

### La norma y la recurrencia (5)

| Repo | Licencia (verificada) | ★ | Rama | Nota |
|---|---|---|---|---|
| [tc39/proposal-temporal](https://github.com/tc39/proposal-temporal) | **BSD de Ecma International**, con **no-concesión** explícita de patentes de terceros | 3 703 | `main` | Ver abajo. |
| [js-temporal/temporal-polyfill](https://github.com/js-temporal/temporal-polyfill) | **ISC** | 798 | `main` | El polyfill con el que se usa hoy. |
| [jkbrzt/rrule](https://github.com/jkbrzt/rrule) | **BSD-3-Clause ×2** | 3 753 | `master` | Recurrencia **RFC 5545** en JS. Insignia `NOASSERTION` por el nombre `LICENCE` (ortografía británica) y por **dos avisos apilados**: el propio y el de `python-dateutil`, que cubre `./rrule.js` y `./test/tests.js`. Permisivo por ambas vías. |
| [ical4j/ical4j](https://github.com/ical4j/ical4j) | **BSD-3-Clause** | 844 | **`develop`** | iCalendar en Java. |
| [sabre-io/vobject](https://github.com/sabre-io/vobject) | **BSD-3-Clause** | 603 | `master` | iCalendar/vCard en PHP; la base de muchos servidores CalDAV. |

**Ojo con `temporal`: en esta KB la palabra nombra dos cosas que no tienen nada que ver.**
`temporalio/temporal` (MIT, 24 518★) es un **motor de ejecución durable**, y ya estaba en la KB.
`tc39/proposal-temporal` es la **API de fecha y hora de JavaScript**. Son capas distintas, problemas
distintos y dueños distintos. **Nunca las cite por el nombre corto en una propuesta.**

**Y la licencia de la norma JS retiene patentes a propósito.** El `LICENSE` de `tc39/proposal-temporal`
(Ecma International) concede «*the "BSD License"*» y acto seguido avisa: «*This Software may be
subject to third party rights (rights from parties other than Ecma International), including patent
rights, and no licenses under such third party rights are granted under this license even if the
third party concerned is a member of Ecma International*». **Es permisiva en copyright y
expresamente silenciosa —o peor— en patentes**, lo que la sitúa por debajo de Apache-2.0 en el mismo
eje que la KB midió en el pase ocho para el dominio público.

### El día hábil como convención financiera (1), y el planificador (2)

| Repo | Licencia | ★ | Rama | Por qué está aquí |
|---|---|---|---|---|
| [lballabio/QuantLib](https://github.com/lballabio/QuantLib) | **BSD-style** (insignia `NOASSERTION`) | 7 799 | `master` | `LICENSE.TXT` son **8 961 B**: ~200 líneas de titulares de copyright —hasta **2026**— antes del grant de redistribución estilo BSD de 3 cláusulas, y avisos de **código de terceros embebido** (el libro de Peter Jäckel, software de la University of Chicago como operador de Argonne, y un conjunto de números de Joe y Kuo «*under a BSD-style license*»). **Es la implementación de referencia de los calendarios de mercado y de las convenciones de día hábil y conteo de días**: ahí vive la diferencia entre *Following* y *Modified Following* y entre ACT/360 y 30/360. Si un agente calcula un vencimiento de pago, **esta es la semántica correcta**, no un `+30 días`. |
| [apache/airflow](https://github.com/apache/airflow) | **Apache-2.0** | 47 650 | `main` | El planificador con el que el cliente ya corre sus procesos por lotes. Push **hoy**. |
| [fullcalendar/fullcalendar](https://github.com/fullcalendar/fullcalendar) | **MIT** | 20 790 | `main` | La capa de presentación; **MIT y 20 790★ es la excepción permisiva en una esquina copyleft** (ver `verticals/solutions.md`). |

### El `NEWS` de tzdb leído byte a byte — por qué «la hora correcta» no es una propiedad de su código

`eggert/tz/NEWS` son **266 065 B** y documentan **seis releases en 2026**. Lo que importa:

| Release | Fecha | Cambio de calendario civil | Fecha **legal** | Fecha **modelada** |
|---|---|---|---|---|
| 2026a | 2026-03-01 | Moldavia usa horarios de transición de la UE desde 2022; los TZif «right» dejan de instalarse por defecto | — | — |
| 2026b | 2026-04-22 | **Columbia Británica** a **-07** permanente | **2026-03-09** | **2026-11-01 02:00** |
| 2026c | 2026-07-08 | **Alberta** a **-06** permanente · **Marruecos** a **+00** permanente el **2026-09-20** | **2026-06-18** | **2026-11-01 02:00** |
| 2026d | 2026-09-11 | **Territorios del Noroeste** a **-06** (solo `America/Inuvik`) | **2026-08-21** | **2026-11-01 02:00** |
| 2026e | 2026-09-29 | **Manitoba** a **-05** permanente | **2026-10-31** | **2026-11-01 02:00** |
| 2026f | 2026-10-27 | **Cuba no retrasa el reloj** y se queda en **-04 hasta el 2027-11-07** · **fin de los segundos intercalares** | 2026-11-01 | 2026-11-01 |
| *Unreleased* | — | Se **retiran** los apaños (fechas legales restituidas) · **Groenlandia** retrasa **dos horas** el **2027-10-31** | — | — |

**Las cuatro fechas modeladas son incorrectas a propósito**, y el `NEWS` dice por qué: «*This
temporary hack works around limitations in Unicode CLDR and ICU, and is planned to be removed after
CLDR and ICU are fixed*», contra **CLDR 48 (2025-10-29), 48.1 (2026-01-08), 48.2.1 (2026-07-08) y
48.2.2 (2026-09-21)** e **ICU 78 (2025-10-30), 78.2 y 78.3 (2026-03-17)**.

**El apaño se rompió a sí mismo, y el remedio es un flag de compilación.** `NOTE FOR 2026 TEMPORARY
HACK FOR CLDR AND CANADA`: el apaño «*causes zic in tzcode **2023d through 2026a**, in the default
**slim** mode, to generate a TZif file that does not conform to Internet RFC 9636 §3.3*», y ese
archivo «*causes some TZif readers, **including tzcode itself**, to ignore America/Vancouver's
2026-11-01 02:00 transition from PDT (tm_isdst=1) to MST (tm_isdst=0)*». Remedio documentado:
**`zic -b fat`**. Los mismos apaños esquivan además un fallo de `libstdc++ std::chrono` en **GCC
14.1-14.4, 15.1-15.2 y 16.1** (**GCC bug 124851**), corregido en **GCC 16.2**.

**El límite del daño, declarado por los mantenedores y por eso citable ante un cliente:** «*It does
not affect UT offsets, and affects abbreviations and tm_isdst flags only during the period starting
at the legal transition and ending on 2026-11-01 at 02:00*». **Aritmética de instantes: a salvo.
Abreviatura de zona o rama sobre `isdst`: no.**

**La salida tiene un suelo de versión de un mes.** El bloque `Unreleased` restituye las fechas legales
—`America/Vancouver` 03-09, `America/Edmonton` 06-18, `America/Inuvik` 08-21, `America/Winnipeg`
10-31— porque **CLDR 49 (2026-10-22)** corrigió la limitación, y añade: «*users need CLDR 49+ anyway
for timestamps starting on 11-01*».

**Fin de los segundos intercalares (2026f), que es un cambio de época y no un detalle.** «*No more
leap seconds, and leap second tables no longer expire*»: `zic` **ignora las líneas `Expires`** y
`localtime.c` «*no longer supports 49 leap seconds, as 27 now suffice*». Todo código que valide la
caducidad de una tabla de segundos intercalares **está validando algo que ya no caduca**.

> **Límite declarado de este pase.** `data.iana.org` está **bloqueado por el proxy (403)** y
> `www.rfc-editor.org` **no resuelve** en esta sesión, así que **RFC 9636 (TZif) y RFC 9557 (el
> formato de fecha con la zona entre corchetes) NO se leyeron en primario**: las referencias a
> §3.2 y §3.3 son **citas textuales del `NEWS` de tzdb**, que es primario para la cita y secundario
> para el contenido de la norma. **Pendiente para el próximo pase:** leer RFC 9557 y dejar escrito
> por qué un *offset* (`-03:00`) no es una zona (`[America/Santiago]`) con la fuente en la mano.

### Ramas por defecto de este pase — el `main` ciego habría fallado 19 de 34 veces

`dev`: `vacanza/holidays`. `develop`: `moment-timezone`, `ical4j`, `frappe/erpnext`. `trunk`:
`apache/ofbiz-framework`. **`20.0`**: `odoo/odoo`. `master`: `workalendar`, `date-holidays`, `luxon`,
`dateutil`, `QuantLib`, `rrule`, `vobject`, `python/tzdata`, `svendiedrichsen/jollyday`,
`HowardHinnant/date`, `pendulum`, `arrow`, `Kozea/Radicale`. Tercera vez que esta KB mide esto, y la
proporción empeora: **6/46** en el pase diecisiete, **19/34** aquí.

## Decimonoveno pase — 2026-11-24 — la capa del sistema de registro heredado: lo que el agente tiene que **leer** antes de poder escribir nada

Todo lo de abajo se verificó el 2026-11-24: existencia con `git ls-remote --exit-code`,
estrellas/licencia SPDX/último push/archivado con
`gh api -X GET search/repositories -f q='repo:owner/name ...'`, y **cada NOASSERTION
resuelto leyendo el archivo de licencia byte a byte** por `raw.githubusercontent.com`.

### 1. El hallazgo de licencia que invalida una fila que esta KB habría escrito sin mirar

**OpenRewrite no es "Apache-2.0" a secas, y la diferencia recae exactamente sobre el
modelo de negocio de Globant.**

| Módulo | Licencia (leída byte a byte) | ★ | Push |
|---|---|---|---|
| https://github.com/openrewrite/rewrite (motor) | **Apache-2.0** (`LICENSE` = Apache License 2.0) | 4011 | 2026-11-24 |
| https://github.com/openrewrite/rewrite-spring | **Moderne Source Available License** (`LICENSE.md` → `LICENSE/moderne-source-available-license.md`) | 407 | 2026-11-24 |
| https://github.com/openrewrite/rewrite-migrate-java | **Moderne Source Available License** (idem) | 168 | 2026-11-24 |

La MSAL concede "use, copy, **distribute internally**, and prepare derivative works", y
su cláusula *Limitations* dice textualmente que **no** se puede "make the functionality
of the Software or a Modified version available to third parties as a service", lo que
incluye "offering a product or service, **the value of which derives to any extent from
the value of the Software**". Nombra como ejemplos prohibidos a Sourcegraph Batch
Changes, Amazon Q Code Transformer y Broadcom Application Advisor. Además el Licensor
"reserves the right to update this Agreement from time to time", y la licencia termina
automáticamente ante una violación (con 30 días de cura la primera vez).

**Consecuencia operativa, y hay que decirla sin adornos:** el *motor* de OpenRewrite es
Apache-2.0 y Globant puede construir sobre él; el *catálogo de recetas que lo hace
valioso* para una modernización Java/Spring está bajo una licencia propietaria
source-available cuyo texto apunta a prohibir precisamente el uso en un servicio
facturado a un tercero. **Esto no es un dictamen legal — es la lectura del texto, y
exige revisión de Legales antes de incluir recetas `rewrite-spring` o
`rewrite-migrate-java` en una propuesta.** Nota de método: fuentes secundarias de 2026
afirman que "el motor y las recetas siempre serán open source"; **el archivo en el repo
dice otra cosa**, y el archivo gana. Cada módulo `rewrite-*` se lee por separado: la
licencia del motor **no** se hereda.

### 2. Motores de transformación determinística (la capa que sí es componible)

| Repo | Licencia | ★ | Push | Para qué, en esta capa |
|---|---|---|---|---|
| https://github.com/openrewrite/rewrite | Apache-2.0 | 4011 | 2026-11-24 | Refactor masivo sobre un árbol con tipos (LST), no sobre texto. Es la referencia de "transformación con prueba" — pero ver el carve-out de arriba antes de usar su catálogo |
| https://github.com/ast-grep/ast-grep | MIT | 16687 | 2026-11-24 | Búsqueda y rewrite estructural por patrones sobre tree-sitter, CLI en Rust. **La pieza MIT más grande de esta capa**, y la que acepta cualquier gramática tree-sitter — incluidas las de COBOL de la tabla 3 |
| https://github.com/biomejs/gritql | MIT | 4631 | 2026-11-20 | Lenguaje de consulta para buscar/modificar código. **Movido a la organización `biomejs`**: `getgrit/gritql` todavía resuelve (redirect), así que una propuesta que cite la URL vieja no falla, pero apunta a un hogar que ya no es el canónico |
| https://github.com/joernio/joern | Apache-2.0 | 3664 | 2026-11-24 | Code Property Graph para C/C++/Java/JS/Python/Kotlin/binario. **Límite medido: no tiene frontend COBOL.** No prometer CPG sobre código de mainframe |

### 3. Parseo y análisis de COBOL — y por qué aquí no hay una opción permisiva completa

| Repo | Licencia | ★ | Push | Nota |
|---|---|---|---|---|
| https://github.com/uwol/proleap-cobol-parser | MIT | 211 | 2026-03-01 | Parser ANTLR4 de COBOL. El parser COBOL permisivo más usado — **y lleva ~9 meses sin push**: usable, no vivo |
| https://github.com/yutaro-sakamoto/tree-sitter-cobol | MIT | 39 | 2026-10-29 | Gramática tree-sitter de COBOL mantenida. Es la que conecta COBOL con `ast-grep` |
| https://github.com/Spantree/tree-sitter-cobol-enterprise | **MIT** (badge NOASSERTION, leído byte a byte: "MIT License, Copyright (c) 2026 Spantree Technology Group") | 8 | 2026-04-24 | **IBM Enterprise COBOL con parseo completo de `EXEC CICS` / `EXEC SQL` y nodos AST tipados.** Es la única gramática encontrada que cubre el COBOL que de verdad corre en un banco (CICS+DB2 embebidos), y tiene 8★ |
| https://github.com/eclipse-che4z/che-che4z-lsp-for-cobol | **EPL-2.0** (badge NOASSERTION, leído en `master/LICENSE.md`) | 119 | 2026-11-19 | El servidor de lenguaje COBOL de grado producción (autocompletado, diagnósticos, copybooks). Vivo. **No permisivo** |
| https://github.com/OCamlPro/superbol-studio-oss | **AGPL-3.0 para `src/lsp`** (badge NOASSERTION; `LICENSE.md` licencia **por directorio**) | 49 | 2026-11-19 | La alternativa viva al LSP de che4z — y la parte que uno embebería es AGPL-3.0. Su repo hermano `OCamlPro/superbol-artefacts` es AGPL-3.0 entero |
| https://github.com/spgennard/vscode_cobol | MIT | 52 | 2026-11-23 | Extensión VS Code para COBOL, **JCL** y directivas MF. Vivo y MIT — pero es tooling de editor, no análisis semántico |
| https://github.com/OCamlPro/gnucobol | LGPL-3.0 | 72 | 2026-11-24 | El compilador GnuCOBOL. Imprescindible para **golden-master testing** del código migrado; copyleft débil, se enlaza, no se absorbe |

**La conclusión medida, que conviene decir antes que el cliente la descubra:** no existe
un servidor de lenguaje COBOL semántico de grado producción con licencia permisiva. Las
dos opciones vivas son **EPL-2.0** (che4z) y **AGPL-3.0** (superbol/src/lsp). MIT
aparece a nivel de gramática (`tree-sitter-cobol*`), de parser sin mantenimiento reciente
(ProLeap) y de extensión de editor (`vscode_cobol`). Una arquitectura permisiva de
análisis COBOL hay que **armarla** con `tree-sitter-cobol-enterprise` + `ast-grep`, no
comprarla hecha.

### 4. La plomería de z/OS — la capa sin la que no se puede ni leer el estate

| Repo | Licencia | ★ | Push | Por qué está acá |
|---|---|---|---|---|
| https://github.com/zopencommunity/meta | Apache-2.0 | 55 | 2026-11-24 | Gestor de paquetes `zopen` + sitio de la comunidad. La organización tiene **399 repos** de ports Apache-2.0 a z/OS: `bashport` (12★), `gitport` (12★, push 2026-11-23), `makeport` (8★), `zoslibport` (6★), `perlport` (6★). **Es la respuesta a "¿puede mi toolchain correr en la caja?"** y es la capa más barata de todo este pase |
| https://github.com/zowe/zowe-cli | EPL-2.0 | 139 | 2026-11-24 | CLI sobre las REST de z/OSMF: el canal por el que un agente toca datasets y jobs. Es la dependencia real de `zowe/zowe-mcp` |
| https://github.com/openmainframeproject/software-discovery-tool | Apache-2.0 | 42 | 2026-11-24 | Descubrimiento de software instalado. Inventario antes de inventar |
| https://github.com/openmainframeproject/tersedecompress | Apache-2.0 | 30 | 2026-11-15 | Descomprime archivos TERSE/AMATERSE de z/OS y z/VM. **Sin esto no se puede abrir el transfer que el cliente manda.** La pieza menos glamorosa y la primera que se necesita |
| https://github.com/galasa-dev/galasa | EPL-2.0 | 16 | 2026-11-23 | Framework de test automatizado híbrido cloud+mainframe. 16★ para la única opción abierta de test de integración de mainframe |

### 5. El estate SAP — la capa heredada con la mejor cobertura abierta del mundo

| Repo | Licencia | ★ | Push | Nota |
|---|---|---|---|---|
| https://github.com/abapGit/abapGit | MIT | 1984 | 2026-11-24 | Git dentro del sistema SAP. Es lo que convierte un estate ABAP en algo que un agente puede ver como texto versionado |
| https://github.com/SAP/abap-cleaner | Apache-2.0 | 697 | 2026-11-24 | Limpieza automática de estilo ABAP, de SAP. **Upstream real** — ver la trampa del fork abajo |
| https://github.com/SAP/code-pal-for-abap | Apache-2.0 | 444 | 2026-09-21 | Los Clean Code Checks ejecutables dentro de SAP (ATC) |
| https://github.com/marcellourbani/vscode_abap_remote_fs | MIT | 411 | 2026-11-24 | Monta el sistema ABAP como filesystem remoto en VS Code, vía ADT. Es el mismo canal que usan los MCP de `agents/top.md` |
| https://github.com/abap2UI5/abap2UI5 | MIT | 392 | 2026-11-24 | UI5 generado desde ABAP puro: la forma de darle interfaz a un agente **sin** sacar nada del sistema SAP |
| https://github.com/abaplint/abaplint | MIT | 323 | 2026-11-24 | Parser + linter de ABAP en TypeScript, **fuera** del sistema SAP. Es el componente clave de este pase: permite validar salida de modelo **antes** de escribirla en el sistema, y es el parser sobre el que se montan varios MCP de ABAP |
| https://github.com/SAP/abap-file-formats | MIT | 114 | 2026-11-24 | Los formatos de archivo oficiales de los objetos ABAP. Lo que hace determinístico el serializado |
| https://github.com/open-abap/open-abap-core | MIT | 67 | 2026-11-24 | Runtime ABAP fuera de SAP: permite correr lógica ABAP en CI sin un sistema SAP licenciado |
| https://github.com/SAP/styleguides | **CC BY 3.0** (badge NOASSERTION, leído en `main/LICENSE`) | 2055 | 2026-10-21 | El Clean ABAP Styleguide. **No es software: es prosa bajo licencia Creative Commons.** Se puede usar como contexto de un prompt; no es una dependencia de código, y 2055★ no lo convierten en una base |

### 6. IBM i / AS-400 — y una partición de licencia que hay que entender antes de desplegar

| Repo | Licencia | ★ | Push | Nota |
|---|---|---|---|---|
| https://github.com/codefori/vscode-ibmi | MIT | 430 | 2026-11-24 | El tooling IBM i de facto. La organización `codefori` es MIT en lo que importa: `vscode-db2i` (80★), `vscode-rpgle` (59★), `vscode-ibmi-fs` (19★), `ibm-i-development-pack` (14★) |
| https://github.com/Mapepire-IBMi/mapepire-server | **GPL-3.0** | 50 | 2026-11-17 | El servidor que da acceso SQL a Db2 for i |
| https://github.com/Mapepire-IBMi/mapepire-js · `-java` · `-python` · `-jdbc` | **Apache-2.0** (los cuatro) | 22 / 11 / 8 / 6 | 2026-11-18…24 | Los clientes |

**La partición:** el **servidor** es GPL-3.0 y los **clientes** son Apache-2.0. Se
despliega el servidor GPL en la máquina del cliente (sin distribución, sin obligación de
liberar nada) y se construye sobre clientes permisivos. Es una de las pocas
configuraciones donde una pieza copyleft no contamina nada — **pero depende de que
nadie empaquete el servidor en un producto que se entregue.**

### 7. Trampas verificadas de este pase

1. **`clean-core/abap-cleaner` es un fork, no un hogar nuevo.** Resuelve con
   `git ls-remote`, tiene un HEAD distinto (`952c680…` vs `d5d9c96…` del upstream) y su
   README es **idéntico byte a byte** al de `SAP/abap-cleaner`, **incluido el badge REUSE
   que apunta a `github.com/SAP/abap-cleaner`**. No apareció en la consulta `repo:` de
   GitHub search porque **ese endpoint excluye forks por defecto**: ese contraste
   (`ls-remote` OK + ausente de `repo:`) es ahora el instrumento de detección de forks de
   esta KB. Componer `SAP/abap-cleaner`.
2. **`openmainframeproject/cobol-check` (107★, Apache-2.0) está ARCHIVADO** desde
   2026-05-28. Es el framework de **unit testing de COBOL** — exactamente lo que se
   necesita para probar que una migración preserva el comportamiento. **Octavo caso de
   proyecto archivado-pero-recomendado** en esta KB, y el patrón sigue siendo el mismo:
   la documentación adyacente al proyecto lo sigue describiendo como vivo. Sustituto real
   para equivalencia: compilar con GnuCOBOL (LGPL-3.0) y comparar salidas (golden master),
   que es lo que hace `fabioalvesalmeida/cobol-modernization-agents`.
3. **El activo COBOL más estrellado del ecosistema no es software.**
   `openmainframeproject/cobol-programming-course` tiene **3673★** y licencia
   **CC-BY-4.0**: es un curso. Un ranking por estrellas en esta vertical pone material
   didáctico arriba de todo el tooling junto. Nunca ordenar esta capa por estrellas sin
   mirar la licencia: CC-BY = documento, no base.
4. **`BroadcomMFD/cobol-control-flow` (16★) no es open source.** Badge NOASSERTION, y su
   `LICENSE.md` es un "LICENSE AND DISCLAIMER — Copyright © 2020 Broadcom. All rights
   reserved." Vive en la misma familia de extensiones de VS Code que el LSP EPL-2.0 de
   che4z, lo que hace muy fácil asumir que comparte licencia. **No la comparte.**
5. **La familia GnuCOBOL es copyleft y una parte está muerta.** `OpenCobolIDE` (252★,
   GPL-3.0) **archivado desde 2017**; `Martinfx/Cobol` (108★, GPL-3.0) sin push desde
   2019; lo vivo es `OCamlPro/gnucobol` (LGPL-3.0, push 2026-11-24).
6. **Licencia por directorio: la causa de NOASSERTION que nadie espera.**
   `superbol-studio-oss` no declara una licencia de repo porque tiene licencias
   **distintas por carpeta**, y la de `src/lsp` es AGPL-3.0. El badge de GitHub no puede
   expresar eso. Confirma invertida la regla del octavo pase: **NOASSERTION es la
   ausencia de un veredicto; a veces esconde algo más permisivo (NIST, dominio público) y
   a veces algo mucho menos permisivo (AGPL, propietario de Broadcom). Resolver siempre
   por lectura, en los dos sentidos.**

### 8. Instrumentos nuevos y reutilizables por toda la flota (medidos hoy en este proxy)

- **`api.github.com/repos/...` devuelve 403** en esta sesión (confirmado otra vez).
  **Pero `gh api -X GET search/repositories -f q='repo:o/n repo:o2/n2 …'` funciona** y
  devuelve en **una sola llamada** `stargazers_count`, `license.spdx_id`, `pushed_at`,
  `archived` y `fork` para decenas de repos. El decimoctavo pase ya lo usó para
  `repos/trending.md`; este pase lo extiende a `agents/top.md` y a
  `repos/foundations.md` y lo combina con la lectura byte a byte de licencias, de modo
  que reemplaza por completo al probing de HTML de github.com (que sigue dando 403).
- **`search/repositories` excluye forks por defecto** → `ls-remote` OK + ausencia en
  `repo:` = **es un fork**.
- **`ungh.cc` e `img.shields.io` devuelven respuesta VACÍA** por este proxy: no sirven
  como fuente de estrellas. No volver a intentarlo.
- **`raw.githubusercontent.com/<repo>/<branch>/<LICENSE|LICENSE.md|LICENSE.txt>` sí
  funciona** y es la única vía de lectura byte a byte de licencias. `HEAD` está bloqueado
  (000/403): usar GET. Probar siempre `main` y `master`: che4z y superbol viven en
  `master`.

## Vigésimo pase — 2026-11-24 — el límite del ciclo de vida: la identidad del agente se crea, hereda, queda huérfana y hay que darla de baja — y el estado que deja atrás tiene su propio RPO

> Tema: **qué pasa con el agente cuando la persona que lo creó se va de la empresa, y qué
> pasa con lo que el agente recordaba.** Los pases 7 y 8 cubrieron *para quién* actúa el
> agente (authz: OpenFGA, Casbin, SpiceDB) y *qué puede cambiar* (el canal de escritura).
> Ninguno de los diecinueve pases anteriores buscó con el vocabulario del **alta y baja**.
> Medido antes de empezar, sobre los 8 archivos de esta KB:
>
> | Término | Apariciones previas en la KB |
> |---|---|
> | `SCIM` | **0** |
> | `IGA` | **0** |
> | `non-human identity` / `NHI` | **0** |
> | `offboarding` / `decommission` / `provisioning` | **0** |
> | `RPO` / `RTO` (como palabra) | **0** |
> | `backup` / `disaster recovery` | **0** |
> | `velero` / `restic` / `kopia` / `pgBackRest` | **0** |
> | `SailPoint` / `Saviynt` / `Active Directory` | **0** |
>
> Trece ceros en una fila. Esta capa no estaba infrarrepresentada: **no estaba.** Y es la
> primera pregunta del equipo de IAM del cliente, no la última.
>
> **Verificación de este pase.** Las estrellas y `pushed_at` vienen de
> `gh api -X GET search/repositories -f q='repo:<owner>/<name>'`. **Cada licencia de abajo
> se leyó byte a byte** por `raw.githubusercontent.com`, y en este pase eso cambió el
> veredicto **cuatro veces** (ver *Reglas de método* al final). `api.github.com/repos/...`
> y el HTML de `github.com` devuelven **403** por el proxy de esta sesión; `git ls-remote`,
> el clon `--bare --depth 1 --filter=blob:none` y `raw.githubusercontent.com` **sí** funcionan.

### A. Enumerar — no se puede dar de baja lo que no está en una lista

El primer paso del ciclo de vida no es la baja: es el **inventario**. El README del
componente de Microsoft lo dice en una línea que conviene citar tal cual en una propuesta:
*"The Agent Governance Toolkit governs agents that register with it — but **you can't
govern what you can't see.**"*

| Repo | Licencia (leída byte a byte) | ★ | pushed | Qué es / por qué está aquí |
|---|---|---|---|---|
| [microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit) | MIT | 6,603 | 2026-11-24 | **La KB ya tenía este repo desde el pase 8 y nunca nombró el componente que importa.** El escáner de *shadow agents* vive en `agent-governance-python/agent-discovery/` (`src/agent_discovery/{inventory,reconciler,models}.py` + CLI). Escáneres: procesos, config y **organización de GitHub**. Salida JSON para CI. Reconcilia lo descubierto contra el registro de gobierno |
| [Defend-AI-Tech-Inc/agent-discover-scanner](https://github.com/Defend-AI-Tech-Inc/agent-discover-scanner) | MIT | 23 | 2026-07-28 | Escáner de identidad/inventario agéntico, 5 capas (análisis estático, red, eBPF/Kubernetes). **Se autodescribe "the industry-standard"** con 23 estrellas y **4 meses sin commits**: el marketing va muy por delante de la adopción. Útil como referencia de técnica (eBPF), no como dependencia |
| [cartography-cncf/cartography](https://github.com/cartography-cncf/cartography) | Apache-2.0 | 4,201 | 2026-11-24 | Vuelca activos de infraestructura **y sus relaciones** a un grafo Neo4j. Es la herramienta que responde "¿qué alcanza esta credencial?" en una consulta, no en una auditoría manual. **Nombre canónico: `cartography-cncf`, no `lyft/cartography`** (ver *Reglas de método*) |
| [prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Apache-2.0 | 15,321 | 2026-11-24 | Evaluación de postura multi-cloud; es el que encuentra credenciales sin uso y claves de acceso viejas — el hallazgo **NHI1** de OWASP, automatizado |
| [cloud-custodian/cloud-custodian](https://github.com/cloud-custodian/cloud-custodian) | Apache-2.0 | 6,118 | 2026-11-24 | Motor de reglas en YAML sobre recursos cloud: expresa "toda identidad de máquina sin uso en 90 días se desactiva" como **política ejecutable**, no como procedimiento escrito. **Canónico: `cloud-custodian/`, no `capitalone/`** |

### B. Aprovisionar y desaprovisionar: SCIM e IGA

| Repo | Licencia (leída byte a byte) | ★ | pushed | Qué es / por qué está aquí |
|---|---|---|---|---|
| [apache/syncope](https://github.com/apache/syncope) | Apache-2.0 | 349 | 2026-11-24 | Gestión de identidades digitales de la ASF: aprovisionamiento, sincronización de directorios, conectores. **349 estrellas y un commit hoy**: en esta capa las estrellas no son la señal — la gobernanza ASF y la licencia sí |
| [Evolveum/midpoint](https://github.com/Evolveum/midpoint) | **EUPL-1.2 o posterior** (badge: `NOASSERTION`) — **docs en CC BY-NC-ND 4.0** | 556 | 2026-11-24 | La plataforma IGA completa (gobierno + certificación + aprovisionamiento), versión 4.12.0 en desarrollo. **No es Apache-2.0**, aunque el catálogo Joinup de la propia Comisión Europea lo liste así. Ver la advertencia de abajo antes de meterla en una propuesta |
| [goauthentik/authentik](https://github.com/goauthentik/authentik) | **MIT excepto `authentik/enterprise/`** (badge: `NOASSERTION`) | 26,448 | 2026-11-24 | IdP completo. El **proveedor SCIM de salida** (`authentik/providers/scim/`, incluido el comando `scim_sync`) y la **fuente SCIM de entrada** (`authentik/sources/scim/`, 41 archivos) están en la parte MIT. El modelo `Agent` y la caducidad por inactividad **no** |
| [python-scim/scim2-models](https://github.com/python-scim/scim2-models) | Apache-2.0 | 30 | 2026-11-23 | Serialización y validación de recursos SCIM con Pydantic |
| [python-scim/scim2-client](https://github.com/python-scim/scim2-client) | Apache-2.0 | 19 | 2026-11-23 | Construye peticiones SCIM y parsea respuestas |
| [python-scim/scim2-cli](https://github.com/python-scim/scim2-cli) | Apache-2.0 | 9 | 2026-11-23 | CLI para desarrollo contra un servidor SCIM |
| [python-scim/scim2-tester](https://github.com/python-scim/scim2-tester) | Apache-2.0 | 10 | 2026-11-23 | **Comprobador de conformidad de un servidor con los RFC de SCIM.** 10 estrellas y es la pieza que evita entregar un endpoint SCIM que el IdP del cliente rechaza en producción. **Organización canónica `python-scim`, no `yaal-coop`** |
| [elimity-com/scim](https://github.com/elimity-com/scim) | MIT | 255 | 2026-11-13 | Implementación en Go de la especificación SCIM v2: sirve para **exponer** un endpoint SCIM desde un servicio propio, el lado que casi nadie construye |

**Excluido, con el motivo medido:**

| Repo | Licencia | ★ | pushed | Por qué NO |
|---|---|---|---|---|
| [Captain-P-Goldfish/scim-for-keycloak](https://github.com/Captain-P-Goldfish/scim-for-keycloak) | BSD-3-Clause | 210 | **2024-03-10** | La respuesta obvia a "¿cómo le pongo SCIM a Keycloak?" está **muerta**: la primera línea de su README es `# End of Life` y redirige a un sitio comercial. **GitHub NO lo marca como archivado** y los metadatos de la API no lo delatan. Octavo proyecto recomendado-pero-muerto de esta KB, y el primero cuyo único indicador es el README |

> ⚠️ **midPoint: la licencia del código no es el problema; la de la documentación sí.**
> Su `LICENSE` (5 líneas, leído hoy) dice: *"MidPoint code and associated work is licensed
> under European Union Public License, Version 1.2 or later"*, y el `NOTICE` lo confirma:
> *"Licensed under the EUPL-1.2 or later."* La EUPL-1.2 es **copyleft con reciprocidad**,
> no permisiva. Y el mismo archivo añade: *"The documentation is licensed under the terms of
> Creative Commons Attribution-**NonCommercial-NoDerivatives** 4.0."* Para una consultora
> cuyo entregable es, muy a menudo, **documentación adaptada**, la licencia de los docs es
> más restrictiva que la del código: **CC BY-NC-ND prohíbe el uso comercial y las obras
> derivadas.** No se puede reempaquetar la documentación de midPoint en un entregable de
> cliente. El código se puede usar leyendo la EUPL con legal; los docs, no.

### C. Credenciales que caducan solas

| Repo | Licencia (leída byte a byte) | ★ | pushed | Qué es / por qué está aquí |
|---|---|---|---|---|
| [external-secrets/external-secrets](https://github.com/external-secrets/external-secrets) | Apache-2.0 | 6,961 | 2026-11-24 | Operador que lee de un almacén externo y materializa Secrets de Kubernetes: la credencial del agente deja de estar en el manifiesto y pasa a tener un emisor con rotación |
| [cert-manager/cert-manager](https://github.com/cert-manager/cert-manager) | Apache-2.0 | 14,173 | 2026-11-24 | Certificados TLS con renovación automática. Es la vía práctica a la identidad **de corta duración** que piden los tenets del NIST, y encaja con SPIFFE/SPIRE que la KB ya tiene |
| [Infisical/infisical](https://github.com/Infisical/infisical) | **MIT ("MIT Expat") excepto los directorios `ee/`** (badge: `NOASSERTION`) | 30,732 | 2026-11-24 | Plataforma de secretos, certificados y acceso — su propia descripción ya dice "and AI Agents". **Hallazgo medido: el ciclo de vida de las identidades de máquina está FUERA de `ee/`**, en la parte MIT (ver abajo) |

> ✅ **Infisical rompe el patrón de open-core de esta KB, y hay que decirlo.** El pase 7
> encontró que en `onyx-dot-app/onyx` el *permission sync* vivía solo en `ee/`. Este pase
> encuentra que en `authentik` el modelo `Agent` vive solo en `enterprise/`. La predicción
> obvia era que Infisical carvearía lo mismo. **No lo hace.** Listado hoy con
> `git ls-tree -r HEAD --name-only`, sus `ee/` contienen `clients`, `data-access`, `models`,
> `routes`, `services`, `testing` y `external-kms-module.ts` — y el ciclo de vida de las
> identidades de máquina **no está ahí**. Las pruebas e2e que lo demuestran, todas en la
> parte MIT:
>
> - `backend/e2e-test/remove-orphaned-identity-group-memberships-migration.spec.ts` → limpieza de pertenencias **huérfanas**
> - `backend/e2e-test/routes/v1/alert-identity-cleanup.spec.ts` → alerta de limpieza de identidades
> - `backend/e2e-test/routes/v1/identity-credential-expiry-alert.spec.ts` → alerta de **caducidad de credencial**
> - `backend/e2e-test/routes/v1/identity-org-membership-deactivation.spec.ts` → **desactivación** de pertenencia
> - `backend/e2e-test/routes/v1/identity-lockout-keystore.spec.ts`, `identity-auth-boundary.spec.ts`, `identity-tls-cert-auth.spec.ts`
>
> **La lección no es "la función siempre está carveada": es que la línea del carve-out
> cambia en cada producto, y se mide en un comando.** Tres productos, tres líneas distintas.
> El activo reutilizable es el procedimiento, no la predicción.

### D. El estado del agente tiene un RPO, y casi nadie lo ha fijado

La memoria del agente suele vivir en Postgres con pgvector — que esta KB ya tiene. Lo que no
tenía es la consecuencia: **su RPO es un problema de Postgres**, y tiene respuestas abiertas.

| Repo | Licencia (leída byte a byte) | ★ | pushed | Qué es / por qué está aquí |
|---|---|---|---|---|
| [cloudnative-pg/cloudnative-pg](https://github.com/cloudnative-pg/cloudnative-pg) | Apache-2.0 | 9,657 | 2026-11-24 | El operador de Postgres en Kubernetes: archivado de WAL y **PITR** para la base donde vive la memoria del agente. Leer las cuatro advertencias de abajo **antes** de prometer un RPO |
| [pgbackrest/pgbackrest](https://github.com/pgbackrest/pgbackrest) | **MIT** (badge: `NOASSERTION`) | 4,510 | 2026-11-23 | Backup y restore de Postgres, con repositorio, verificación y restore paralelo. Permisiva, y el badge no lo decía |
| [velero-io/velero](https://github.com/velero-io/velero) | Apache-2.0 | 10,386 | 2026-11-24 | Backup/restore y migración de aplicaciones Kubernetes **y sus volúmenes**. **Nombre canónico `velero-io/velero`: `vmware-tanzu/velero` es un redirect** — aunque los *plugins* (`vmware-tanzu/velero-plugin-for-csi`, `-for-vsphere`) siguen canónicamente en `vmware-tanzu`. El núcleo se movió y los plugins no |
| [restic/restic](https://github.com/restic/restic) | **BSD-2-Clause** | 37,429 | 2026-11-22 | Backup rápido, cifrado y deduplicado a almacenamiento de objetos. El más estrellado de toda esta capa |
| [kopia/kopia](https://github.com/kopia/kopia) | Apache-2.0 | 14,809 | 2026-11-23 | Backup incremental multiplataforma con cifrado en cliente; alternativa a restic con licencia Apache |

**Excluido, con el motivo:**

| Repo | Licencia | ★ | pushed | Por qué NO |
|---|---|---|---|---|
| [EnterpriseDB/barman](https://github.com/EnterpriseDB/barman) | **GPL-3.0** | 3,282 | 2026-11-18 | Vivo, mantenido y competente — pero **GPL-3.0**: no entra en algo que Globant distribuya. Para la misma función hay dos permisivas arriba (pgBackRest MIT, CloudNativePG Apache-2.0). Se registra para que nadie lo descubra a mitad de una entrega |

#### Las cuatro advertencias de CloudNativePG, leídas de sus propios docs (`docs/src/recovery.md`, hoy)

1. *"A valid WAL archive is required to perform PITR."* **Sin archivado de WAL no hay PITR**, solo
   restauración del backup completo. Un RPO prometido sin comprobar esto es ficción.
2. *"In CloudNativePG, recovery is **not performed in-place**... Instead, it is used to
   **bootstrap a new cluster**."* El RTO no es "restaurar la base": es **restaurar y conmutar**.
   Cualquier plan que asuma restauración en sitio está mal por diseño del operador.
3. *"If you added or removed a tablespace in your cluster since the last base backup, replaying
   the WAL will fail."* Un cambio de tablespace **invalida** el camino de recuperación hasta el
   siguiente base backup.
4. **La que importa para un agente, y es contraintuitiva:** *"PostgreSQL recovery will stop when
   it encounters the first transaction that occurs after the specified time. **If no such
   transaction exists after the target time, the recovery process will fail.**"* Es decir:
   **recuperar a un instante dentro de una ventana en la que el agente estuvo inactivo falla
   precisamente porque estuvo inactivo.** La identidad dormida y el dato dormido fallan por la
   misma razón, y esa frase une las dos mitades de este pase.

   (Y una quinta operativa: los timestamps deben llevar zona explícita — `2023-07-06T08:00:39Z` —
   porque `2023-07-06 08:00:39` es ambiguo; además, al crear réplicas tras recuperar de un
   `VolumeSnapshot`, el operador *"may fall back to using `pg_basebackup`"*, que en bases grandes
   es **mucho** más lento: eso es RTO, no una nota al pie.)

#### Las tres trampas de los hooks de Velero, leídas de `site/content/docs/main/backup-hooks.md`

1. *"Note that hooks are **not** executed within a shell on the containers."* Un hook escrito
   como one-liner de shell (`pg_dump ... > /backup/x`) **no se ejecuta**: hay que invocar
   `/bin/sh -c` explícitamente y pasar los argumentos como array JSON.
2. `pre.hook.backup.velero.io/timeout` **vale 30 s por defecto**, y `on-error` vale **`Fail`**.
   Un *quiesce* o un flush de un almacén vectorial grande pasa de 30 s: el resultado por defecto
   no es un backup inconsistente, es un **backup fallido**. Es el default correcto y aun así
   sorprende a todo el mundo la primera vez.
3. Desde Velero 1.15 los ítems que deben respaldarse juntos se agrupan en **ItemBlocks**: si un
   ItemBlock tiene varios pods (caso típico de un volumen RWX montado por varios workers del
   agente), se ejecutan **todos** los pre-hooks, luego el backup, luego **todos** los post-hooks.
   Un hook escrito asumiendo un pod por invocación se ejecuta N veces.

### Reglas de método nuevas de este pase (14 a 19)

Este pase trabajó con el plano de la API de repos **cerrado**, y eso produjo reglas que sirven
para toda la flota, no solo para enterprise.

**Regla 14 — `api.github.com/repos/<owner>/<name>` y el HTML de `github.com` devuelven 403 por
este proxy; `gh api -X GET search/repositories -f q='repo:<owner>/<name>'` **sí** funciona.**
Esa es la vía para estrellas, forks, `pushed_at`, `archived` y `fork`. Las otras tres vías
abiertas son `git ls-remote`, el clon `--bare --depth 1 --filter=blob:none` (que da la fecha del
último commit con `git log -1 --format=%cI` **y el árbol completo de archivos sin descargar un
solo blob**) y `raw.githubusercontent.com`. `img.shields.io` y `ungh.cc` siguen vacíos.

**Regla 15 — `search/repositories` es el detector de renombres.** El índice de búsqueda solo
conoce el nombre **canónico**: un `repo:viejo/nombre` que devuelve `total_count: 0` mientras
`git ls-remote` y `raw` sobre ese mismo nombre devuelven 200 **es exactamente la firma de un
redirect**. `git` y `raw` siguen los renombres en silencio y por eso no sirven para esto. Con esa
prueba, tres nombres de esta KB y de la prensa quedaron corregidos hoy:
`lyft/cartography` → **`cartography-cncf/cartography`**; `capitalone/cloud-custodian` →
**`cloud-custodian/cloud-custodian`**; `vmware-tanzu/velero` → **`velero-io/velero`** (con el
matiz de que los plugins de Velero **sí** siguen en `vmware-tanzu`, así que la regla "nunca
compongas owner/owner" se cumple aquí al revés: el núcleo migró y los plugins no). Confirmado por
una segunda vía independiente: las URL que el propio README se autorreferencia.

**Regla 16 — `NOASSERTION` se resolvió cuatro veces en este pase y dio cuatro respuestas
distintas.** El pase 8 dejó escrito que `NOASSERTION` es *la ausencia de un veredicto* y hay que
resolverlo leyendo bytes **en los dos sentidos**. Este pase es la demostración más limpia:
>
> | Repo | Badge | Realidad leída byte a byte | Dirección |
> |---|---|---|---|
> | `pgbackrest/pgbackrest` | NOASSERTION | **MIT** | más permisiva de lo que parecía |
> | `goauthentik/authentik` | NOASSERTION | **MIT con carve-out `enterprise/`** | permisiva **con condición** |
> | `OWASP/www-project-non-human-identities-top-10` | NOASSERTION | **CC-BY-SA-4.0** | licencia de **contenido**, no de código |
> | `Evolveum/midpoint` | NOASSERTION | **EUPL-1.2-or-later** + docs **CC BY-NC-ND** | **menos** permisiva: copyleft |
>
> Cuatro `NOASSERTION`, cuatro veredictos: permisiva, permisiva-con-carve-out, de contenido y
> copyleft. La regla no es "NOASSERTION suele ser permisiva" (pase 8) ni lo contrario: es que
> **el badge no contiene información** y el byte sí.

**Regla 17 — sondear nombres de archivo de licencia en minúscula, o mejor, listar el árbol
primero.** `Captain-P-Goldfish/scim-for-keycloak` dio un falso "sin licencia" en el primer
sondeo porque su archivo se llama **`license.txt` en minúscula**. La lista de candidatos
(`LICENSE`, `LICENSE.txt`, `LICENSE.md`, `COPYING`, `LICENCE`…) nunca es completa: con el clon
blobless ya se tiene `git ls-tree -r HEAD --name-only | grep -iE 'licen|copying'`, que es exacto.

**Regla 18 — el flag `archived` no es la señal de fin de vida; la primera línea del README sí.**
`scim-for-keycloak` está **vivo** para GitHub (no archivado, 210 estrellas, BSD-3-Clause) y
**muerto** para su autor: `# End of Life` es el primer encabezado de su README. Es el octavo
proyecto recomendado-pero-muerto de esta KB y el primero que ningún metadato delata. Añadir al
procedimiento: leer las **primeras 5 líneas del README** de todo repo cuyo `pushed_at` esté a más
de 12 meses.

**Regla 19 — la URL de repositorio que declara un índice de paquetes puede estar mal, y hay que
verificar la ruta, no solo el repo.** El paquete `agentmesh-discovery` 5.0.0 de PyPI declara
`Documentation: https://github.com/microsoft/agent-governance-toolkit/tree/main/agent-discovery`.
Ese directorio **no existe** en la raíz del repo. La ruta real es
`agent-governance-python/agent-discovery/`: le falta un segmento. El paquete es legítimo, MIT y
de Microsoft — pero su puntero publicado da 404, y eso es lo que hace que un ingeniero desconfíe
de un paquete real o confíe en uno falso. Es la **segunda** aparición de la regla del pase 8
("`camel-mcp-server`, no `camel-mcp` como dice el blog de Apache"), ahora desde un índice de
paquetes en vez de un blog: **el puntero publicado por el propio proyecto es una fuente
secundaria.** Y el mismo sondeo mostró el riesgo gemelo: buscar `scim2-models in:name` devuelve,
además del canónico, dos espejos automáticos con nombres mutilados
(`Eternity-gaga/python-scim__scim2-models.55bb0a4b`, `autocode07/…`), 0 estrellas y la misma
licencia. **Buscar por nombre devuelve señuelos; `repo:` devuelve el canónico.**

## La capa de voz — el canal que faltaba tras veinte pases (added twenty-first pass, 2026-11-24)

> **39 direcciones verificadas el 2026-11-24, las 39 nuevas para esta KB.** Instrumento:
> `raw.githubusercontent.com` para **leer el fichero `LICENSE` byte a byte** (`api.github.com`,
> `gh api` y `curl` a `github.com` están denegados por el alcance de sesión), `git ls-remote` para
> existencia y rama por defecto, `WebFetch` sobre el HTML de GitHub para estrellas y banner de
> archivado, y `pypi.org/pypi/<pkg>/json` para clasificadores de licencia independientes de la
> forja. **`huggingface.co` está rechazado por el proxy de egreso (403), así que ninguna licencia
> de *pesos* de esta sección es de primera mano** — están marcadas y no se afirman.

### La cadena de un agente de voz, y por qué tiene seis eslabones y no uno

Un agente de texto tiene un eslabón: el modelo. Un agente de voz tiene seis, y **cada uno lleva su
propia licencia**: transporte (WebRTC/SIP) → VAD y detección de turno → STT → el agente →
TTS → grabación y evidencia. La consecuencia comercial es que **la licencia más restrictiva de la
cadena gobierna el entregable**, y en voz casi nunca es la del framework de agentes.

### Transporte y borde telefónico

| Repo | Licencia | ★ | Papel en la pila |
|---|---|---|---|
| [livekit/livekit](https://github.com/livekit/livekit) | Apache-2.0 | 22,400 | SFU WebRTC de extremo a extremo. El transporte permisivo por defecto |
| [livekit/sip](https://github.com/livekit/sip) | Apache-2.0 | n/m | El puente SIP ↔ WebRTC de LiveKit. **Este es el componente que conecta el agente a la red telefónica pública sin tocar Asterisk** |
| [jambonz/jambonz-feature-server](https://github.com/jambonz/jambonz-feature-server) | **MIT** | n/m | CPaaS auto-alojable: el servidor de aplicaciones de voz. La opción **permisiva** del borde telefónico |
| [jambonz/jambonz-api-server](https://github.com/jambonz/jambonz-api-server) | **MIT** | n/m | API de provisión y control de jambonz |
| [drachtio/drachtio-server](https://github.com/drachtio/drachtio-server) | **MIT** | n/m | El servidor SIP sobre el que se construye jambonz. MIT hasta la capa de señalización |
| [signalwire/freeswitch](https://github.com/signalwire/freeswitch) | **MPL-1.1** | n/m | Conmutador de telefonía. MPL-1.1 (no 2.0): copyleft por fichero, 79,568 B de licencia |
| [kamailio/kamailio](https://github.com/kamailio/kamailio) | **GPL-2.0** | n/m | Proxy SIP de alto volumen. Se integra por protocolo, no por enlazado |
| [OpenSIPS/opensips](https://github.com/OpenSIPS/opensips) | **GPL-2.0** | n/m | Alternativa a Kamailio, misma postura de licencia |

### VAD y turno — el problema que decide si el agente suena humano

| Repo | Licencia | ★ | Papel en la pila |
|---|---|---|---|
| [snakers4/silero-vad](https://github.com/snakers4/silero-vad) | **MIT** | n/m | Detección de actividad de voz. El eslabón que decide cuándo el humano dejó de hablar |
| [pipecat-ai/smart-turn](https://github.com/pipecat-ai/smart-turn) | **BSD-2-Clause** | n/m | Detección de **fin de turno semántica**, no por silencio: distingue «mi número es...» (pausa, sigue hablando) de una frase terminada. Es el componente que elimina la interrupción grosera, y casi ningún listado lo menciona |
| [pipecat-ai/pipecat-flows](https://github.com/pipecat-ai/pipecat-flows) | **BSD-2-Clause** | n/m | Flujos conversacionales estructurados sobre Pipecat: la máquina de estados que un contact centre audita |

### STT — reconocimiento

| Repo | Licencia | ★ | Papel en la pila |
|---|---|---|---|
| [openai/whisper](https://github.com/openai/whisper) | **MIT** | n/m | La referencia multilingüe. Código MIT; **licencia de pesos no verificable en esta sesión** |
| [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) | **MIT** | n/m | Reimplementación con CTranslate2. El runtime de producción habitual |
| [ggml-org/whisper.cpp](https://github.com/ggml-org/whisper.cpp) | **MIT** | n/m | Whisper en C/C++: CPU, borde, sin GPU. La vía para el on-prem con restricción de hardware |
| [m-bain/whisperX](https://github.com/m-bain/whisperX) | **BSD-2-Clause** | n/m | Whisper con alineación a nivel de palabra y diarización. **La alineación temporal es lo que permite redactar PII de un audio**, no sólo del texto |
| [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) | **Apache-2.0** | 16,200 | STT + TTS + diarización + VAD **en un solo runtime ONNX**, con servidor websocket y 12 lenguajes de programación. La pieza más subestimada de esta sección para despliegue embarcado |
| [alphacep/vosk-api](https://github.com/alphacep/vosk-api) | **Apache-2.0** | n/m | STT offline, modelos pequeños, muchos idiomas. Apache-2.0 real (10,172 B: cuerpo sin el apéndice) |
| [speechbrain/speechbrain](https://github.com/speechbrain/speechbrain) | Apache-2.0 | n/m | Toolkit de habla todo-en-uno (ASR, verificación de locutor, mejora) |
| [espnet/espnet](https://github.com/espnet/espnet) | Apache-2.0 | n/m | Toolkit de habla de extremo a extremo, orientado a investigación reproducible |
| [NVIDIA-NeMo/NeMo](https://github.com/NVIDIA-NeMo/NeMo) | Apache-2.0 | n/m | Donde viven los modelos Parakeet/Canary. **Ojo al renombrado: la organización es `NVIDIA-NeMo/`, no `NVIDIA/`** — esta KB ya tenía `NVIDIA-NeMo/Guardrails` y `NVIDIA/NeMo-Agent-Toolkit`, que son organizaciones distintas |

### TTS — síntesis, y la capa con más trampas de licencia de toda la KB

| Repo | Licencia (leída) | ★ | Veredicto |
|---|---|---|---|
| [hexgrad/kokoro](https://github.com/hexgrad/kokoro) | **Apache-2.0** | 10,300 | **La opción permisiva por defecto.** El README afirma pesos Apache («With Apache-licensed weights, Kokoro can be deployed anywhere»); **afirmación del README, no verificada en el origen de pesos** (HF rechazado) |
| [remsky/Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI) | Apache-2.0 | n/m | Kokoro servido con API compatible OpenAI. El eslabón de integración |
| [rhasspy/piper](https://github.com/rhasspy/piper) | **MIT** | 11,300 | ⚠️ **ARCHIVADO por su dueño el 2025-10-06, de sólo lectura.** El README dice «Development has moved» y apunta al sucesor |
| [OHF-Voice/piper1-gpl](https://github.com/OHF-Voice/piper1-gpl) | **GPL-3.0** (`COPYING`, 35,146 B) | n/m | El sucesor mantenido de Piper — **y relicenciado**. El nombre del repositorio lo dice y aun así los listados siguen llamando a Piper «open source TTS» sin más |
| [coqui-ai/TTS](https://github.com/coqui-ai/TTS) | MPL-2.0 | 46,300 | **Sin banner de archivado y sin puntero a ningún fork**, con 46,3k estrellas, aunque la empresa que lo mantenía ya no existe |
| [idiap/coqui-ai-TTS](https://github.com/idiap/coqui-ai-TTS) | MPL-2.0 | n/m | El fork mantenido (Idiap). Mismo texto de licencia, 16,724 B frente a 16,725 B del original |
| [resemble-ai/chatterbox](https://github.com/resemble-ai/chatterbox) | MIT | 28,100 | ⚠️ **«As of August 2026, Chatterbox is retired research and is no longer maintained»** — en el README, **sin banner de archivado** |
| [nari-labs/dia](https://github.com/nari-labs/dia) | Apache-2.0 | n/m | TTS de diálogo (dos voces, turnos). Código Apache-2.0 verificado |
| [SWivid/F5-TTS](https://github.com/SWivid/F5-TTS) | **MIT** (código) | n/m | Código MIT verificado; **licencia de pesos no verificable aquí** y es el caso donde más importa, porque F5 clona voces |
| [fishaudio/fish-speech](https://github.com/fishaudio/fish-speech) | ❌ **«FISH AUDIO COMMUNITY LICENSE AGREEMENT» v1.0, 2026-10-13** | n/m | **No es código abierto.** Uso comercial sólo por debajo de un umbral de ingresos; cualquier *Hosted Service* exige acuerdo escrito aparte. 19,684 B de licencia propia. Actualizada hace seis semanas: la trampa es **fresca** |

### Voz a voz (full-duplex) — y la primera vez que esta KB separa licencia de código de licencia de pesos en la misma fila

| Repo | Licencia de **código** (leída) | Licencia de **pesos** | ★ |
|---|---|---|---|
| [kyutai-labs/moshi](https://github.com/kyutai-labs/moshi) | **MIT + Apache-2.0** (`LICENSE-MIT` y `LICENSE-APACHE`, ambos presentes; GitHub rotula «Apache-2.0, MIT licenses found») | **CC-BY-4.0 según el README** — no verificable en esta sesión | 11,600 |
| [fixie-ai/ultravox](https://github.com/fixie-ai/ultravox) | **MIT** | no verificable aquí | n/m |
| [QwenLM/Qwen3-Omni](https://github.com/QwenLM/Qwen3-Omni) | **Apache-2.0** | no verificable aquí | n/m |

**Por qué esta columna doble es nueva y necesaria.** En texto, la licencia del código y la de los
pesos divergen y rara vez cambia la arquitectura. En voz **la voz es el entregable**: unos pesos
CC-BY-4.0 obligan a **atribuir** en el producto del cliente, lo cual es una obligación que el
cliente tiene que aceptar por contrato, no una nota de ingeniería. Y CC-BY no es Apache: **no hay
concesión de patentes** (la misma lección que el sexto pase aprendió con el dominio público del
NIST, ahora en la capa de pesos).

### Locutor, diarización y antisuplantación — «quién está en la llamada»

| Repo | Licencia | Papel |
|---|---|---|
| [pyannote/pyannote-audio](https://github.com/pyannote/pyannote-audio) | **MIT** | Diarización de locutores: separa agente de cliente en la grabación. Prerrequisito de cualquier redacción de PII por hablante |
| [resemble-ai/resemblyzer](https://github.com/resemble-ai/resemblyzer) | Apache-2.0 | Embeddings de voz (verificación de locutor) |
| [clovaai/aasist](https://github.com/clovaai/aasist) | **MIT** | Detección de *spoofing*/voz sintética. El lado defensivo del mismo problema: en 2026 el fraude por voz clonada entra por el mismo canal que el agente |

> **Advertencia de dos filas, no de una.** `pyannote-audio` y `resemblyzer` producen **plantillas
> de voz**. En Illinois eso es exactamente lo que está en litigio bajo BIPA ahora mismo
> (ver `intel/market.md` → North America). Un *embedding* de locutor creado «sólo para separar
> canales» puede ser un identificador biométrico según cómo lo lea el tribunal, y **la ley no
> define «voiceprint»**. La decisión de arquitectura es: diarizar **sin persistir** el embedding.

### Pegamento de servicio y plataforma on-prem

| Repo | Licencia | Papel |
|---|---|---|
| [speaches-ai/speaches](https://github.com/speaches-ai/speaches) | **MIT** | Servidor auto-alojado con API **compatible con OpenAI** para STT y TTS. El adaptador que permite cambiar de proveedor sin tocar el agente |
| [rhasspy/wyoming](https://github.com/rhasspy/wyoming) | **MIT** | Protocolo de servicios de voz por sockets: desacopla STT/TTS/VAD del orquestador |
| [OpenVoiceOS/ovos-core](https://github.com/OpenVoiceOS/ovos-core) | Apache-2.0 | Plataforma de asistente de voz on-prem (sucesor comunitario del linaje Mycroft) |
| [Mozilla-Ocho/llamafile](https://github.com/Mozilla-Ocho/llamafile) | Apache-2.0 | Empaquetado de un modelo como binario único. Relevante para el borde telefónico sin red |

### Evaluación de agentes de voz — la capa que casi no existe

| Repo | Licencia | Qué mide |
|---|---|---|
| [ServiceNow/eva](https://github.com/ServiceNow/eva) | **MIT** | Puntúa conversaciones **habladas multi-turno** en dimensiones de tarea *y* de audio; soporta agentes en cascada y voz-a-voz. Su métrica de audio depende de un modelo propietario (Gemini) — hay un conjunto sólo-texto para evitarlo |
| [sujitnoronha/voicecheck](https://github.com/sujitnoronha/voicecheck) | **MIT** (clasificador PyPI y `LICENSE` leído) | Pruebas E2E del bucle de audio: latencia al primer byte, degradación de audio, **barge-in** y carga. v0.2.1 en PyPI |

### Corpus

| Repo | Licencia | Nota |
|---|---|---|
| [common-voice/common-voice](https://github.com/common-voice/common-voice) | **MPL-2.0** | La plataforma del corpus multilingüe. `mozilla/common-voice` sirve el mismo texto de licencia (16,725 B): es el mismo proyecto re-alojado, no dos |

### Ceros medidos y direcciones que NO se escriben (porque un 404 no es un hallazgo)

- **VICIdial** — la fuente secundaria más citada lo da como el mejor contact centre de código
  abierto (>14.000 instalaciones). `vicidial/vicidial` **existe pero su `HEAD` apunta a
  `gh-pages`**: es el sitio web, no el producto. `VICIDIAL/astguiclient` **no existe**. El código
  vive en SVN fuera de GitHub. **Por eso no hay fila de VICIdial en esta KB con URL de GitHub.**
- **Dograh** — descrito por su propio post como voz-IA auto-alojable BSD-2-Clause. `dograh-ai/dograh`
  y `dograh/dograh` **no resuelven**. Sin slug, sin fila.
- **Issabel** y **GOautodial** — citados como contact centres sobre Asterisk; `issabel/issabelPBX`,
  `IssabelPBX/issabelPBX` y `GOautodial/GOautodial` **no resuelven**. Sin fila.
- **Redacción de PII en audio**: buscado explícitamente. **No existe una librería mantenida que
  encadene diarización + Presidio + silenciado por marca de tiempo.** Lo que hay es un prototipo
  académico (OST, 2026) y ejemplos de proveedor atados a una nube. **Es un hueco de producto real**,
  y la receta 42 de `compose/patterns.md` lo construye con piezas que sí existen y están verificadas.

## Vigesimosegundo pase — 2026-11-24 — el límite de la tenencia: de quién es la respuesta cuando un despliegue sirve a muchos clientes

> Tema: **el agente multi-inquilino.** El pase 7 resolvió *qué puede leer este empleado*
> (autorización por persona). Este pase resuelve la pregunta de la capa de arriba, que no es la
> misma: **¿de quién es el dato que el agente acaba de recuperar?** Es la pregunta que aparece en
> cuanto el cliente de Globant no es el usuario final, sino un ISV, un banco con filiales o un
> grupo retail con operaciones por país.
>
> **Hueco medido antes de empezar (la razón por la que 21 pases lo saltaron):** sobre los 8
> ficheros de esta KB, `tenancy` = **0 apariciones**, `BYOK` = **0**, `multi-tenant` = **1**,
> `tenant_id` = **0**, `row level security` = **0**, `Kafka` = **0**, `nats-io` = **0**,
> `automq` = **0**, `redpanda` = **0**, `pulsar` = **1**. La KB tenía Qdrant, Weaviate, Milvus,
> pgvector, Keycloak y LiteLLM desde hacía pases — **pero ninguno descrito como primitiva de
> aislamiento por inquilino.** No faltaban los componentes: faltaba la propiedad por la que se
> eligen.
>
> **Instrumentos de este pase** (los tres que funcionan en esta sesión): `git ls-remote` para
> existencia y rama por defecto; `raw.githubusercontent.com` para **leer `LICENSE` byte a byte**;
> y **nuevo y reutilizable por toda la flota: `gh api -X GET search/code -f q='…'`**, que prueba a
> nivel de fichero que una *feature* está dentro del repo permisivo y no en un `ee/` de pago.
> `api.github.com/repos` está **denegado** por el alcance de la sesión y el HTML de `github.com`
> devuelve **403** por `curl` — pero `WebFetch` sobre ese mismo HTML **sí** da estrellas y
> licencia. Tres canales, tres tipos de evidencia distintos.

### El backbone de eventos — la capa que no existía, con Debezium ya dentro 22 veces

**El hallazgo de inventario de este pase, y es vergonzoso en el buen sentido:** la KB citaba
**Debezium 22 veces** — que es un **plugin de Kafka Connect** — y la palabra `Kafka` aparecía
**cero veces**. Se había adoptado el conector sin nombrar nunca el bus al que conecta. Es
exactamente la clase de punto ciego del pase 16: *un vocabulario de consultas por problema tiene
un agujero con la forma de un producto*.

| Repo | Licencia (cómo se verificó) | ★ | Primitiva de tenencia, probada a nivel de fichero |
|---|---|---|---|
| [apache/kafka](https://github.com/apache/kafka) | Apache-2.0 — `LICENSE` leído byte a byte en `master` (11.358 B) | 34,3k | **Cuotas por principal** en el core: `server/src/main/java/org/apache/kafka/server/quota/ClientQuotaManager.java` + `QuotaFactory.java` (21 coincidencias). El control del vecino ruidoso **no** es de pago. |
| [apache/pulsar](https://github.com/apache/pulsar) | Apache-2.0 — byte a byte en `master` (13.300 B) | 15,4k | **`tenant` es entidad de primera clase**, no una convención: `pulsar-broker/.../admin/v2/Tenants.java`, `pulsar-client-tools/.../CmdTenants.java`, `pulsar-client-admin-api/.../Tenants.java`. El README lista «Multi-tenant» en *Main features*. |
| [nats-io/nats-server](https://github.com/nats-io/nats-server) | Apache-2.0 — byte a byte en `main` | 21,1k | **La `Account` es la unidad de aislamiento:** `server/accounts.go`, **5.055 líneas**, con `type Account struct` y `exports`/`imports` (15/25 coincidencias) como **única** forma de cruzar el límite. Proyecto de la **CNCF** (leído del README). |
| [AutoMQ/automq](https://github.com/AutoMQ/automq) | **Apache-2.0** — byte a byte; `LICENSE` **y** `NOTICE` con **cero** menciones a «Business Source»/«BSL» | 10,9k | «Diskless Kafka® on S3». API de Kafka **con licencia permisiva**. `NOTICE`: *Copyright 2023-2025, **AutoMQ HK Limited*** → **origen APAC**, y el `NOTICE` incluye el de Apache Kafka. |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 — byte a byte en `master` | 35,7k | `is_tenant` = **25 coincidencias** de código, incluidas `lib/segment/src/types.rs` y `lib/edge/src/builders/{uuid,keyword}_index_params.rs`. El índice consciente del inquilino está **dentro** del repo permisivo. |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Apache-2.0 — byte a byte en `master` | 46,7k | `partition_key` = **81 coincidencias** (`internal/util/exprutil/expr_checker.go`, `pkg/proto/index_cgo_msg.proto`…). La clave de partición es el límite. |
| [pgvector/pgvector](https://github.com/pgvector/pgvector) | **Licencia PostgreSQL** (permisiva, estilo BSD) — byte a byte: *«Portions Copyright (c) 1996-2026, PostgreSQL Global Development Group»*. **GitHub no muestra insignia de licencia** | 23,8k | No aporta tenencia por sí mismo: la aporta **Postgres** debajo (ver la regla de `FORCE` más abajo). Esa es la frase que hay que decirle al cliente. |
| [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 — `LICENSE.txt` byte a byte | 38,0k | **Organizations está en el core**: `server-spi/src/main/java/org/keycloak/models/OrganizationModel.java` existe en el repo Apache-2.0. **No hace falta la extensión de pago** (ver trampa). |
| [openbao/openbao](https://github.com/openbao/openbao) | **MPL-2.0** — byte a byte | 9,2k | Claves por inquilino / *transit*. **MPL no es permisiva**: es copyleft débil por fichero. Usable, pero **no** es la misma conversación legal que Apache-2.0. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) *(ya en la KB desde el pase 3, con una propiedad nueva)* | MIT | — | **Dato nuevo:** existe una **jerarquía de cliente** explícita — `litellm/types/proxy/auth/customer_hierarchy.py`, `litellm/proxy/auth/customer_hierarchy_auth.py`, `litellm/proxy/management_helpers/customer_hierarchy.py` (**95 coincidencias**) — y un **gateway en Rust** (`litellm/rust/crates/gateway/src/host/auth/mod.rs`). El presupuesto por inquilino ya está construido; esta KB lo tenía como «control plane» sin más. |

**Diez filas, diez repos reales, diez licencias leídas byte a byte.** Ninguna fila de ejemplo,
ningún encabezado como dato.

### Las dos trampas de licencia de este pase — y las dos se venden como «open source»

**1. `p2-inc/keycloak-orgs` es Elastic License 2.0, no Apache-2.0.** Es la extensión de
multi-tenencia para Keycloak que recomiendan los blogs del sector y el propio proveedor
(546 ★, *«Single realm, multi-tenancy for SaaS apps»*). Su fichero **`COPYING`, leído byte a
byte, es la Elastic License 2.0** (3.860 B), y su README lo dice con sus palabras: *«We've
changed the license of our core extensions from the AGPL v3 to the Elastic License v2»*. O sea:
**AGPL-3.0 → ELv2**, un camino que **nunca** pasa por permisivo, mientras el README sigue
hablando de *«making its core extensions open source»*. **Y no hace falta**: `OrganizationModel.java`
está en el core Apache-2.0 de Keycloak. La trampa no es sólo la licencia — es pagar un peaje
legal por algo que el upstream ya regala.

**2. `redpanda-data/redpanda` tiene tres nombres de licencia y ninguno es permisivo.** La rama
por defecto es **`dev`** (no `main` ni `master`), **no hay `LICENSE` en la raíz** y por eso
**GitHub no muestra ninguna insignia**. Lo que sí ship-ea el repo: `licenses/bsl.md` =
*«Redpanda Business Source License 1.1»* y `licenses/rcl.md` = *«Redpanda Community License
Agreement»*. Y el README apunta a un **tercer** nombre: *«Redpanda Community Edition is now
licensed under the Redpanda Community Edition License»* — **cuyo texto no está en el
repositorio**, sino en una página legal del sitio del proveedor. 12,7k ★ de motor compatible con
la API de Kafka que **Globant no puede tomar como base**. El contraste operativo es directo:
**AutoMQ da la API de Kafka bajo Apache-2.0 verificado**.

> **Regla de método 14 (nueva, y vale para toda la flota):** `grep -i` de un **acrónimo** fabrica
> cobertura inexistente. Buscando `RLS` sin límites de palabra salieron **13 coincidencias** en
> esta KB; con `grep -oE '\bRLS\b'` salen **0**. Las 13 eran **«URLs»**. Un hueco medido con un
> acrónimo hay que volver a medirlo con `\b…\b` antes de declararlo cubierto *o* vacío.

### Weaviate: una licencia partida dentro de un repo — y la parte de pago **no** es el aislamiento

Weaviate merece su propio apartado porque es el caso que el pase 7 habría leído mal. Su
`LICENSE` (789 B, leído byte a byte) dice literalmente que el código está *«variously licensed
under the BSD-3-Clause License, or the Weaviate License»*, y que **la licencia de cada fichero se
identifica por su ubicación**: todo lo que está **fuera** del directorio `wl/` es BSD-3-Clause;
todo lo que está **dentro** es *«Copyright Weaviate BV 2026-present, all rights reserved»*,
habilitado **por clave de licencia**, y *«The BSD license does not grant the right to use these
features or circumvent any license key»*. `wl/LICENSE-WEAVIATE` lleva fecha **«Date posted:
August 26, 2026»**: el corte es **reciente**. GitHub, entretanto, muestra la insignia
**«BSD-3-Clause»** a secas, y el README vende *«built-in multi-tenancy, replication, RBAC
authorization»* como ventaja de producción.

**Así que había que medirlo, no suponerlo.** Clonado el repo (`--depth 1 --filter=blob:none`) y
listado el árbol:

- **`wl/` tiene 29 ficheros** en cinco subdirectorios: `backupdedupe/` (planificador de
  deduplicación de backups), `dbusers/` (**expiración** de usuarios de BD), `namespaces/`
  (`handlers/`, `qualifier.go`, **`suspendsweep/`**), `rebalance/` (planificador de rebalanceo de
  shards) y `selfrecovery/` (orquestador de auto-recuperación).
- **Fuera de `wl/`: 84 ficheros con `tenant` en la ruta** — entre ellos
  `adapters/handlers/rest/operations/schema/tenants_create.go`, `tenant_exists.go`,
  `adapters/handlers/grpc/v1/tenants.go` y, llamativamente,
  **`adapters/handlers/mcp/read/tenants.go`** — y **147 con `namespace`**, incluidos los guardas
  de autorización `adapters/handlers/rest/authz/handlers_authz_namespaced_*`.

**La conclusión, dicha como decisión de arquitectura:** en Weaviate **el límite entre inquilinos
es BSD-3-Clause** — crear, comprobar y autorizar inquilinos, por REST, gRPC **y MCP**, es
gratis y permisivo. Lo que está detrás de la clave es **operar muchos inquilinos a escala**:
suspender los inactivos, rebalancear shards, deduplicar backups, auto-recuperarse y expirar
credenciales. **Es el inverso exacto del hallazgo de Onyx del pase 7**, donde lo cerrado *era* el
límite. Y para un presupuesto cambia todo: el aislamiento no se compra, **la operación sí** —
o se construye.

### La tenencia en SQL: `ENABLE` no alcanza, `FORCE` sí

El hueco más barato de cerrar de toda esta capa, y el que esta KB tenía literalmente en cero
(`row level security` = 0, `tenant_id` = 0). Con `pgvector` sobre Postgres, el aislamiento no lo
da la extensión: lo da el motor, y **sólo si se configura contra el propio dueño de la tabla**.
Las reglas que salieron repetidas en fuentes independientes (documentación de EDB/Supabase/AWS y
práctica publicada; **páginas no verificables en esta sesión**, ver la nota de canal):

1. **`FORCE ROW LEVEL SECURITY`, no sólo `ENABLE`** — `ENABLE` no aplica al dueño de la tabla, que
   suele ser el mismo usuario con el que se conecta la aplicación.
2. **El inquilino se fija por transacción**, no por conexión: `set_config('app.tenant_id', …, true)`
   y la política comparando contra eso. Si falta, **no hay fila que coincida: falla cerrado.**
3. **El pool de runtime corre con un rol restringido**, nunca con el de migraciones ni el admin, y
   **nunca con `BYPASSRLS`**.
4. **Lo que se salta RLS por diseño**: funciones `SECURITY DEFINER`, `TRUNCATE`, las
   `REFERENCES` de claves ajenas y `pg_dump` (que fuerza `row_security = off`, por lo que el rol
   de backup necesita `BYPASSRLS` — y ahí vuelve el riesgo por la puerta de atrás).
5. **RLS corrige la corrección, no el rendimiento**: en un índice ANN compartido, los *embeddings*
   de los inquilinos pequeños quedan dispersos entre los nodos del inquilino dominante, y la
   latencia y el *recall* varían por inquilino. La respuesta es **particionar por `tenant_id`** con
   índices por partición, o índices parciales.

> **La frase para la semana 1 de una venta, y es de Gravitee, no nuestra:** *«control planes
> frequently leak data through analytics rather than core CRUD paths»*. Las trazas, las métricas y
> los logs del agente **también** son datos del inquilino. Un pase anterior metió OpenTelemetry en
> esta KB como observabilidad; este pase dice que **el pipeline de telemetría es superficie de
> tenencia** y se aísla o se filtra por ahí.
