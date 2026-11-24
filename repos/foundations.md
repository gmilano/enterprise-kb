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
