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
