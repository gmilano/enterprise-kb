---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 📈 Repos trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

## 2026-11-20 — fourth pass (latest)

**Method change: searched by what an agent is allowed to *do*, not by what it is built with.**
The third pass swept by architectural layer and found the control plane. This pass asked a
different question — what does an enterprise agent *touch* that has consequences? Money,
personal data, and the systems of record that tell it what is true. Each answer was a layer
this KB did not have. **Sixteen repositories below were absent entirely**, and the most
consequential one has 89 stars while the most-starred one in its own family is five months idle.

All metadata from the GitHub search API on 2026-11-20. **Every licence below was read from the
repository's own `LICENSE` file over `raw.githubusercontent.com` — 16/16 verified, none taken
from a GitHub badge.** Full tables and the commercial reading are in `repos/foundations.md`.

### Agent payments & commerce protocols — zero prior coverage in this KB

`AP2`, `x402`, `agentic-commerce` and the bare word `payment` each returned **no match** across
all eight files before this pass. This is the first layer where an agent's mistake debits a real
account.

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3,281 | **2026-06-17** | Agent Payments Protocol; A2A extension, ~60 payments/tech organisations. The signed-mandate model is the durable idea. **Idle five months.** |
| [agentic-commerce-protocol/agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1,607 | 2026-07-18 | ACP — OpenAI/Stripe lineage, now under its **own neutral organisation**. |
| [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | Apache-2.0 | 571 | **2026-11-11** | HTTP 402 as a machine-payable rail. **The only actively-pushed repo in the family.** |
| [forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol) | MIT | 180 | 2026-07-08 | Agent↔merchant authentication and encryption — the identity question the payment specs leave open. |
| [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-18 | Runnable reference implementation of ACP + UCP. Lowest stars here, highest demo value. |

**The finding, not the list:** three protocols at three layers, all permissive, **and the star
ranking inverts the activity ranking.** AP2 has 5.7× the stars of the x402 extension and has not
been touched since June. This reproduces `intel/trends.md` §11 *inside a single protocol family*.

### PII de-identification — the layer between an agent and customer data

| Repo | Real license | Stars | Pushed | Note |
|------|--------------|-------|--------|------|
| [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) | MIT | 11,989 | 2026-11-19 | PII detection, redaction, masking, anonymisation. **Moved out of `microsoft/` — see the rename ledger.** |
| [data-privacy-stack/presidio-research](https://github.com/data-privacy-stack/presidio-research) | MIT | 321 | 2026-11-19 | Recogniser evaluation harness — makes tuning an evidenced claim. |

### Catalog & lineage — and the "context layer" rebrand

| Repo | Real license | Stars | Pushed | Self-description |
|------|--------------|-------|--------|------------------|
| [open-metadata/OpenMetadata](https://github.com/open-metadata/OpenMetadata) | Apache-2.0 | 15,823 | 2026-11-20 | "The Open **Context Layer** for Data and AI." New to this KB. |
| [unitycatalog/unitycatalog](https://github.com/unitycatalog/unitycatalog) | Apache-2.0 | 3,581 | 2026-11-20 | "Open, Multi-modal Catalog for Data & AI." |
| [OpenLineage/OpenLineage](https://github.com/OpenLineage/OpenLineage) | Apache-2.0 | 2,773 | 2026-11-20 | "An Open Standard for lineage metadata collection." |

**Observation worth selling:** two independent catalog vendors — OpenMetadata and the already-listed
[datahub-project/datahub](https://github.com/datahub-project/datahub) — pushed the same day and
both now lead with the word **"context"**. The category has re-described itself as agent
infrastructure. These are usually *already installed* at the client, which makes them the
cheapest grounding layer in the KB.

### Graph RAG — a 36,699-star MIT repo this KB had never mentioned

| Repo | Real license | Stars | Pushed | Note |
|------|--------------|-------|--------|------|
| [microsoft/graphrag](https://github.com/microsoft/graphrag) | MIT | 36,699 | 2026-11-19 | Category leader, actively pushed. |
| [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | MIT | 4,010 | 2026-01-27 | "Easy-to-hack" — **idle ~10 months.** |
| [circlemind-ai/fast-graphrag](https://github.com/circlemind-ai/fast-graphrag) | MIT | 3,972 | **2025-11-01** | **Idle over a year — verify before proposing.** |
| [DEEP-PolyU/Awesome-GraphRAG](https://github.com/DEEP-PolyU/Awesome-GraphRAG) | MIT | 2,686 | 2026-06-02 | Survey/benchmark index — a reading list, not a dependency. |

### A branch trap that will silently misreport a licence

[datahub-project/datahub](https://github.com/datahub-project/datahub) keeps its `LICENSE` on
**`master`**, not `main`. A verification script that probes only `main` reports this Apache-2.0
repo as **unlicensed**. Three repos in this pass needed the `master` fallback; this KB's own
checker tries both, and that is why. Worth stating because the failure mode is a *false
negative on licence* — the direction that loses Globant a usable repo rather than risking one.

### Searched and not found this pass

- **A LATAM-origin repository in any of the four new layers** — payments/commerce, PII and
  anonymisation, catalog/lineage, and graph RAG were each searched, including Spanish and
  Portuguese vocabulary (`pagos agentes IA`, `agente pagamento IA`, `anonimizacion datos IA`).
  **Result: zero usable.** Everything returned was 0–3 stars with **NOASSERTION (no usable
  licence)** — landing pages, a WhatsApp payment-receipt OCR bot, and student final-year
  projects. This is the **fifth consecutive pass** measuring this gap and the fifth zero.
  Recorded so it reads as measured, not unexamined.
- **A dedicated enterprise DLP repo above 500 stars** — `pii redaction anonymization llm
  stars:>500` returned **no results at all**. Presidio is not merely the leader in this
  category; above 500 stars it is close to the only thing in it.
- **Primary sources for every market figure** — `www.idc.com` and every other non-GitHub host
  fail to resolve in this session (`ENOTFOUND`), as in the third pass. GitHub search API and
  `raw.githubusercontent.com` both work. The evidence split in `intel/trends.md` therefore
  still holds: **repositories are first-hand, market statistics are second-hand.**

## 2026-11-20 — third pass (later still)

Searched by **layer** rather than by star ceiling this time: the earlier passes swept
`stars:>150000` and found the harness/skill band, which meant anything structurally important
but modestly starred stayed invisible. Twelve repositories below were absent from this KB
entirely, and the most strategically important one has 2,423 stars. All metadata from the
GitHub search API on 2026-11-20; every licence read from the repository's own `LICENSE`.

### Control plane — the layer this KB did not have

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 | 2,423 | 2026-11-19 | **Formerly Envoy AI Gateway; now an Agentic AI Foundation project.** One OpenAI-compatible API for every model and MCP server; credentials, routing, quotas, failover and usage attribution in one Envoy-enforced plane. The vendor-neutral answer to the NVIDIA concentration risk recorded in `intel/market.md`. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT core + `litellm/enterprise/` carve-out | 63,615 | 2026-11-20 | The adoption leader — 100+ providers, Rust core with Python SDK. Virtual keys, spend tracking, budgets and fallbacks in the MIT core. |
| [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 | 44,402 | 2026-11-20 | "The API and AI Gateway." Right answer when Kong already fronts the client's API estate; AI features reportedly enterprise-gated — verify per feature. |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | MIT, no carve-out found | 13,421 | 2026-11-20 | 1,600+ LLMs, **50+ guardrails enforced at the gateway** instead of in application code. Cleanest licence in the category. |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 | 9,818 | 2026-11-20 | Go; LLM gateway and MCP gateway in one. Vendor-published comparisons — discount the claims. |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 | 6,291 | 2026-11-17 | Observability-first gateway companion. |

### Cost governance & metering — new category

| Repo | License | Stars | Pushed | Why it is moving |
|------|---------|-------|--------|------------------|
| [opencost/opencost](https://github.com/opencost/opencost) | Apache-2.0 | 6,824 | 2026-11-20 | CNCF Kubernetes/cloud cost monitoring — the GPU and pod spend behind self-hosted vLLM that token counting never sees. |
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | Apache-2.0 | 2,457 | 2026-11-20 | "Metering and Billing for AI, API and DevOps." Turns gateway usage events into per-team entitlements and chargeback. |

### Red teaming, eval gates & OpenTelemetry instrumentation

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT | 27,494 | 2026-11-20 | Eval **and** red teaming, declarative, designed to run as a CI gate. |
| [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 | 19,577 | 2026-11-19 | Unit-test-shaped LLM/agent metrics; drops into existing pytest CI. |
| [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | Apache-2.0 | 16,389 | 2026-11-14 | RAG evaluation metrics. **Ownership moved** from `explodinggradients` — re-pin and re-read the licence. |
| [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 | 10,114 | 2026-11-18 | The LLM vulnerability scanner. Run it against the deployed agent so tool access is in scope. |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | Apache-2.0 | 7,543 | 2026-11-19 | OpenTelemetry-based LLM/agent observability — routes into the client's existing APM. |
| [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | MIT | 4,980 | 2026-11-20 | Microsoft's open red-teaming toolkit. **Canonical location**; `Azure/PyRIT` is the stale old home (128 ★, 2026-03-25). |
| [Agenta-AI/agenta](https://github.com/Agenta-AI/agenta) | MIT Expat core + `ee/` carve-out | 4,922 | 2026-11-20 | Agent/prompt eval and versioning workspace. Copyright **Agentatech UG**, a German entity — a second **EMEA-origin** assurance tool alongside Giskard. |
| [Arize-ai/openinference](https://github.com/Arize-ai/openinference) | Apache-2.0 | 1,331 | 2026-11-20 | OpenTelemetry instrumentation for AI. Note the same vendor's `phoenix` is **Elastic License 2.0** and not open source. |
| [open-telemetry/semantic-conventions](https://github.com/open-telemetry/semantic-conventions) | Apache-2.0 | 690 | 2026-11-20 | Where **GenAI semantic conventions** are standardised. Lowest stars, highest portability leverage in this list. |

### Sandboxing, memory & document AI

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [docling-project/docling](https://github.com/docling-project/docling) | **MIT** | 70,818 | 2026-11-20 | "Get your documents ready for gen AI." **Hosted in the LF AI & Data Foundation**, IBM-originated. MIT + foundation-governed + 70k stars — the default answer to an enterprise document estate, and absent from this KB until now. |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Apache-2.0 | 33,431 | 2026-11-20 | Open-source graph-backed AI memory for agents. Permissive alternative to Mem0. |
| [Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured) | Apache-2.0 | 15,769 | 2026-11-19 | Document-to-structured-data ETL for scheduled ingestion. |
| [e2b-dev/E2B](https://github.com/e2b-dev/E2B) | Apache-2.0 | 14,943 | 2026-11-20 | Secure code-execution sandbox for enterprise agents — a non-NVIDIA option in the isolation slot. |

### Agents that should already have been here

| Repo | License | Stars | Pushed | Note |
|------|---------|-------|--------|------|
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121,597 | 2026-11-20 | AI browser agents — for client systems that have a portal and no API. |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | MIT | 85,545 | 2026-11-20 | "Long-horizon SuperAgent harness." **APAC-origin.** Fourth MIT harness above every Tier-1 framework. |
| [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | **2026-10-18** | Stateful agents, learning memory (MemGPT lineage). Month-plus idle — verify. |

### Renames and ownership moves to fix in existing code — new this pass

| Was | Is now | How it was caught |
|-----|--------|-------------------|
| `envoyproxy/ai-gateway` | [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Old path's `raw` README returns 200 and reads "Formerly Envoy AI Gateway"; search API `repo:` returns 422 for the old name. |
| `Azure/PyRIT` | [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | Old org resolves but is 128 ★ / 2026-03-25; name search ranks `microsoft/PyRIT` first by two orders of magnitude. |
| `explodinggradients/ragas` | [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | `repo:` on the old path returns 422; `ragas in:name stars:>500` returns one repo under a **new organisation**. |

**Three of ~35 repositories checked had moved and two changed organisation.** That is a
supply-chain finding, not a link-rot finding.

### Not permissive / not usable, despite appearances

| Repo | Reality | Stars |
|------|---------|-------|
| [daytonaio/daytona](https://github.com/daytonaio/daytona) | **No `LICENSE` file** (checked 4 filenames × `main`/`master`); last pushed **2026-07-24** | 71,307 |
| [meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) | **Llama 3.2 Community License Agreement** — not OSI open source. GitHub shows `NOASSERTION`, hence the common mistake | 4,486 |
| [getzep/zep](https://github.com/getzep/zep) | Apache-2.0, but the repo is now *"Examples and Integrations"* — Zep itself is a hosted product. Not self-hosted memory | 5,010 |
| [Helicone/ai-gateway](https://github.com/Helicone/ai-gateway) | **GPL-3.0** and last pushed **2025-11-21** — a year cold. Same vendor as the Apache-2.0 `helicone` | 647 |
| [protectai/rebuff](https://github.com/protectai/rebuff) | Apache-2.0 but last pushed **2024-08-07** — over two years cold | 1,533 |

### Searched and not found this pass

- **`envoyproxy/ai-gateway` as a searchable repository** — exists on `raw` (200) but the search
  API refuses the `repo:` qualifier (422). Resolved as the Agent Router move above, so this is a
  *resolved* miss, not an open one.
- **`microsandbox/microsandbox`** — `repo:` returns 422 and no plausible successor surfaced. Do
  not cite it; use `e2b-dev/E2B` or `opensandbox-group/OpenSandbox` for isolation.
- **A LATAM-origin repository in any of the six new layers** — gateway, metering, red teaming,
  eval, sandboxing and document AI were each searched; **zero LATAM-origin repositories
  appeared in any of them.** Consistent with the agent-framework finding in `intel/market.md`
  and recorded here so the gap reads as measured, not unexamined.
- **`microsoft/agent-framework`** — still not located; not re-probed this pass, since the second
  pass checked five channels. Treat as unavailable per `agents/top.md`.


## 2026-11-20 — second pass (later same day)

Measured against the GitHub star ceiling rather than a curated watchlist: a
`stars:>150000` sweep sorted descending, to find what the earlier pass's name-based
searches could not see. All figures from the GitHub search API on 2026-11-20; every license
below read from the repository's own `LICENSE` file.

### The agent/skill band of the GitHub top 40 — most of it new to this KB

| Repo | License | Stars | Pushed | Why it is here |
|------|---------|-------|--------|----------------|
| [morluto/rea](https://github.com/morluto/rea) | MIT | 470,997 | 2026-11-20 | Reverse-engineer anything with agents, from app behaviour down to native binaries. **The most-starred agent repository on GitHub** — above OpenClaw. An application, not a platform. |
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,891 | 2026-11-20 | Still the largest *harness*, and the centre of the skill ecosystem. |
| [mattpocock/skills](https://github.com/mattpocock/skills) | MIT | 328,581 | 2026-11-19 | "Skills for Real Engineers." One engineer's `.agents` directory, more starred than every framework in `agents/top.md` Tier 1 combined. |
| [obra/superpowers](https://github.com/obra/superpowers) | MIT | 322,580 | 2026-11-03 | An agentic skills framework and development methodology. Single author (Jesse Vincent). |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | MIT | 307,599 | 2026-11-20 | Agent-harness performance optimisation: skills, instincts, memory, security. Cross-harness (Claude Code, Codex, Opencode, Cursor). |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | MIT | 284,581 | 2026-11-18 | "Everything is a Plugin." **APAC-origin.** New to this KB. |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT | 264,904 | 2026-11-20 | "The agent that grows with you." New to this KB. |
| [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | **none** | 234,677 | 2026-04-20 | A single `CLAUDE.md`. **No license file** and seven months cold — enormous mindshare, zero reusability. |
| [anomalyco/opencode](https://github.com/anomalyco/opencode) | MIT | 228,170 | 2026-11-20 | "The open source coding agent." |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | AGPL-3.0 | 204,866 | 2026-11-20 | Search, scrape and 550+ data providers through one API. **AGPL — integrate over the API, never vendor it.** |
| [anthropics/skills](https://github.com/anthropics/skills) | **none** | 197,931 | 2026-11-16 | Public repository for Agent Skills. **No license file** — cannot be redistributed in a deliverable. |

### Skill-security and runtime containment — the new governance tooling

| Repo | License | Stars | Pushed | Why it is moving |
|------|---------|-------|--------|------------------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 | 27,027 | 2026-11-19 | Skill security scanner, 71 patterns / 17 categories. The control nobody had a month ago. |
| [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | 2026-11-20 | Runs Hermes / Deep Agents / OpenClaw inside OpenShell with managed inference. |
| [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) | Apache-2.0 | 21,829 | 2026-11-20 | Safe, private agent runtime in Rust. `LICENSE` copyright: **NVIDIA CORPORATION & AFFILIATES**. |
| [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 | 14,026 | 2026-11-20 | Graph/semantic reasoning layer for deterministic query generation. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 | 4,224 | 2026-11-20 | Skill quality gates with reusable CI templates. |
| [NVIDIA/skills](https://github.com/NVIDIA/skills) | Apache-2.0 | 4,095 | 2026-11-20 | NVIDIA product skills (CUDA, robotics, simulation, RAG) for Claude Code / Codex. |
| [NVIDIA/NeMo-Agent-Toolkit](https://github.com/NVIDIA/NeMo-Agent-Toolkit) | Apache-2.0 | 2,710 | 2026-11-18 | Connecting and optimising teams of agents. |
| [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 | 254 | 2026-11-20 | Tool/LLM-call middleware — the policy enforcement point. |

### Also verified new this pass

| Repo | License | Stars | Pushed | Note |
|------|---------|-------|--------|------|
| [a2aproject/A2A](https://github.com/a2aproject/A2A) | Apache-2.0 | 26,604 | 2026-11-20 | Agent2Agent protocol — agent-to-agent interop alongside MCP's agent-to-tool. |
| [kestra-io/kestra](https://github.com/kestra-io/kestra) | Apache-2.0 | 30,293 | 2026-11-20 | Declarative orchestration control plane. |
| [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) | MIT | 31,472 | 2026-11-20 | Batteries-included harness; [deepagentsjs](https://github.com/langchain-ai/deepagentsjs) (MIT, 1,650 ★) for TypeScript. |
| [openclaw/clawhub](https://github.com/openclaw/clawhub) | MIT | 9,557 | 2026-11-20 | Skill + plugin registry. |
| [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | MIT | 53,885 | 2026-11-18 | 5,400+ curated skills. |
| [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 | 13,006 | 2026-11-20 | Catalog/lineage — "context platform for your data and AI stack". |
| [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | 2,630 | 2026-11-19 | Workload identity for the agent process itself. |
| [flowable/flowable-engine](https://github.com/flowable/flowable-engine) | Apache-2.0 | 9,669 | 2026-11-19 | BPM engine — the permissive one. See `verticals/solutions.md`. |
| [camunda/camunda](https://github.com/camunda/camunda) | **Camunda License 1.0** | 4,367 | 2026-11-20 | Now markets itself as "Agentic Orchestration Platform". **Not OSI open source** — details in `verticals/solutions.md`. |

### Renames and moves to fix in existing code — new this pass

| Was | Now | Evidence |
|-----|-----|----------|
| `dbt-labs/dbt-core` | [dbt-labs/dbt](https://github.com/dbt-labs/dbt) | Apache-2.0, 14,192 ★. Old path still serves on `raw.githubusercontent.com` (200) and its README's CI badges point at `/dbt-labs/dbt/actions`; [dbt-fusion](https://github.com/dbt-labs/dbt-fusion) is labelled *"ARCHIVE: code & issue tracking in dbt-core"*. **Pin note: dbt v1 development moved to the `1.latest` branch.** |

### Searched again and still not found

`microsoft/agent-framework` — now 404 on a **third and fourth** channel:
`raw.githubusercontent.com/microsoft/agent-framework/{main,master}/{README.md,LICENSE}`
returns 404 on all four, and `agent-framework in:name user:microsoft` lists 14 repositories,
none canonical. Verified Microsoft-stack substitutes: `microsoft/semantic-kernel` (MIT,
28,790 ★) and [microsoft/agent-framework-go](https://github.com/microsoft/agent-framework-go)
(MIT, 686 ★). **Also checked and rejected:** `solo-io/agentgateway` returns nothing, and
"Aureus ERP", recommended as a permissively licensed ERP by a 2026 vendor roundup, has **no
repository above 0 stars** — the five candidate matches are all personal forks. Fewer real
rows beat padding.

---

## 2026-11-20

Measured by last-push activity and scale on 2026-11-20. All figures from the GitHub
API the same day, not from blog roundups.

| Repo | License | Stars | Why it is moving |
|------|---------|-------|------------------|
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,887 | The breakout agent of 2026 and now the largest agent repo by a wide margin. Pushed same-day. |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | Sustainable Use License | 211,510 | Biggest automation surface in the enterprise, but **fair-code, not OSI** — see `agents/top.md` Tier 2. |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Open WebUI License | 159,142 | Default self-hosted chat UI; license adds a branding restriction, so not a white-label shortcut. |
| [langgenius/dify](https://github.com/langgenius/dify) | Modified Apache-2.0 | 161,564 | Agentic workflows + RAG in one collaborative plane; modified-Apache conditions apply. |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97,264 | The serving layer under most self-hosted enterprise agent stacks. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 | 94,475 | Repositioned as an "agent-native database" — RAG engine converging with the agent runtime. |
| [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | MIT | 93,898 | Moved org from `All-Hands-AI` to `OpenHands`; update any pinned remotes. |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | MIT → Apache-2.0 (in transition) | 92,133 | Reference MCP servers; relicensing is under way, declared at the top of `LICENSE`. |
| [aaif-goose/goose](https://github.com/aaif-goose/goose) | Apache-2.0 | 56,815 | Moved under the Linux Foundation's Agentic AI Foundation org this cycle. |
| [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) | Apache-2.0 | 36,363 | APAC-origin agent framework now at Tier-1 scale, with a JVM sibling. |
| [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 | 17,705 | Sandbox runtime for agents — the isolation layer enterprises need before granting tool access. |
| [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 | 4,867 | MCP/A2A gateway + registry; small but the clearest enterprise MCP control point. |

**Renames and moves to fix in existing code this cycle** — all four verified today:

| Was | Now | Note |
|-----|-----|------|
| `All-Hands-AI/OpenHands` | [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | MIT, 93,898 ★ |
| `block/goose` | [aaif-goose/goose](https://github.com/aaif-goose/goose) | Apache-2.0, 56,815 ★ — AAIF governance |
| `NVIDIA/NeMo-Guardrails` | [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | Apache-2.0 (per `LICENSE`), 7,537 ★ |
| `Giskard-AI/giskard` | [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) | Apache-2.0, 5,962 ★ |

**Searched and not found:** `microsoft/agent-framework` (404), and `dbt-labs/dbt-core`
no longer resolves under that path — only `dbt-labs/dbt-core-bundles` (20 ★) surfaced,
so the dbt reference was dropped rather than guessed at.

---

## Historical — 2026-07-02 (automated pipeline snapshot)

> Kept for trend history, deliberately fenced as plain text so the compiler does **not**
> ingest it as entities. Note this legacy file was byte-identical to `agents/trending.md`
> — the old pipeline wrote the same keyword query into both.
>
> **Dead-link audit, 2026-11-20 (second pass):** all 118 `github.com` repository URLs in this
> KB were checked. **117 resolve.** The single dead one is in the block below —
> `Arid-carrotpudding634/Freequick-Suite` now 404s on the search API and on
> `raw.githubusercontent.com` (`main` and `master`). Left in place because this is fenced
> trend *history*, not data, and a decayed row is itself evidence for why the old
> keyword-matching pipeline was retired.

```text
# 📈 Repos trending

> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [odoo](https://github.com/odoo/odoo) | NOASSERTION | Odoo. Open Source Apps To Grow Your Business. | 52.8k |
| [bgerp](https://github.com/bgerp/bgerp) | GPL-3.0 | Web-базирана система за управление на бизнеса | 60 |
| [CmsToCommerce](https://github.com/roadynet/CmsToCommerce) | MIT | Symfony Commerce Integration Hub for CMS, Amazon, Shopware, ERP/PIM sync and pro | 0 |
| [Simple-Data-Explorer](https://github.com/ysichov/Simple-Data-Explorer) | MIT | Simple Data Explorer - Multi-windows program for viewing SQL tables and links be | 64 |
| [erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | Free and Open Source Enterprise Resource Planning (ERP) | 36.4k |
| [TunNetCom-SilkRoadErp](https://github.com/TunNetCom/TunNetCom-SilkRoadErp) | MIT | Silk Road ERP offers robust modules for managing your sales and purchasing opera | 24 |
| [india-compliance](https://github.com/resilient-tech/india-compliance) | GPL-3.0 | Simple, yet powerful compliance solutions for Indian businesses | 249 |
| [FARM-ERP-EXCEL](https://github.com/NKAdithya/FARM-ERP-EXCEL) | MIT | Farm ERP System built using Microsoft Excel featuring dashboard analytics, finan | 0 |
| [Freequick-Suite](https://github.com/Arid-carrotpudding634/Freequick-Suite) | ? | Build a Flutter and Firebase food delivery suite with customer, merchant, and ri | 0 |
| [SmartPOS-CRM-AI](https://github.com/RaKa8904/SmartPOS-CRM-AI) | MIT | A full-stack Smart POS + CRM platform with ML-powered customer segmentation, pro | 2 |

---
*Pipeline automático — se actualiza cada hora.*
```
