---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 🧩 Patrones de composición — Enterprise

> Concrete recipes. Every repo named below was verified on 2026-11-20 (existence, license,
> stars) and every license is the real one from the repo's `LICENSE` file. Licenses are
> repeated inline on purpose: in enterprise work the license decides the architecture.

## The base pattern, and why it is shaped this way

```
[ Base platform — run STOCK, usually copyleft, client's own deployment ]
                  ↓  exposed as tools, never as a database
[ MCP server per system  →  MCP gateway (registry + policy choke point) ]
                  ↓  identity-bound, policy-checked, sandboxed
[ Agent layer — SEPARATE repo, MIT/Apache = Globant IP ]
                  ↓  durable execution so a 40-step process survives a crash
[ Human-in-the-loop console for writes  +  evaluation evidence capture ]
```

Two rules carry most of the value:
1. **The copyleft/permissive boundary is the MCP interface.** Base platforms (Odoo LGPL,
   ERPNext GPL, Twenty AGPL) run unforked in the client's estate; Globant's agent code sits
   in a separate MIT/Apache repo and talks to them over an API. Fork the base and the
   client's legal team owns the conversation instead of you.
2. **Reasoning text must never reach an actuator directly.** Model output is parsed into a
   typed, validated call; the call is authorised; the call executes in a sandbox.

---

## Receta 1 — Agent-enable an existing ERP without forking it

**For:** a client on Odoo or ERPNext who wants conversational operations and automated
back-office steps. The most common enterprise ask in the pipeline.

| Layer | Component | License |
|-------|-----------|---------|
| Base (stock) | [odoo/odoo](https://github.com/odoo/odoo) or [frappe/erpnext](https://github.com/frappe/erpnext) | LGPL-3.0 / GPL-3.0 |
| Custom modules | [frappe/frappe](https://github.com/frappe/frappe) | MIT |
| Tool exposure | [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 |
| Agent layer | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) + [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | MIT |
| Identity | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 |
| Authz | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | Apache-2.0 |
| Durability | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Approval UI | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 |

**Wiring:**
1. Run the ERP stock. Write any customisation as a Frappe app (MIT) or an Odoo module in
   the client's own repo — not in a Globant fork of the base.
2. Expose a *narrow* tool surface through mcp-context-forge, wrapping the ERP's existing
   XML-RPC/JSON-RPC or REST API. Register each tool with the business operation it performs,
   not the table it touches.
3. **Split tools by blast radius.** `read_*` tools are autonomous. `write_*` tools return a
   proposed mutation, never execute one.
4. LangGraph holds the state machine; CrewAI roles map to the client's actual job functions.
   Each agent authenticates to Keycloak as itself; OPA policy decides which tools that
   identity may call, in versioned Rego the client's auditors can read.
5. Every `write_*` proposal lands in an Appsmith queue for human approval. On approval,
   Temporal executes the write as a durable workflow with compensation steps.
6. Localise last: pull the OCA `l10n-*` module for the target country into the client's
   deployment (see Receta 5).

**Why this holds up:** LGPL/GPL stays contained in the client's unforked deployment;
Globant's IP is MIT/Apache in a separate repo; the approval queue is what makes an ERP write
agent acceptable to a finance function.

---

## Receta 2 — Enterprise knowledge agent (fastest credible day-one deliverable)

**For:** "we can't find anything across our systems." Low risk, high visibility, read-only.

| Layer | Component | License |
|-------|-----------|---------|
| Search + chat base | [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | **MIT core — stay out of `ee/`** |
| Doc processing | [run-llama/llama_index](https://github.com/run-llama/llama_index) | MIT |
| RAG engine | [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 |
| Vector store | [qdrant/qdrant](https://github.com/qdrant/qdrant) | Apache-2.0 |
| Serving | [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 |
| Memory | [mem0ai/mem0](https://github.com/mem0ai/mem0) | Apache-2.0 |
| Guardrails | [protectai/llm-guard](https://github.com/protectai/llm-guard) | MIT |

**Wiring:** Onyx provides connectors and UI. Route ingestion through LlamaIndex/RAGFlow into
Qdrant. Serve with vLLM so the whole thing can run in-country for a sovereignty-constrained
client. Mem0 carries per-user context across sessions. llm-guard scans both directions for
PII, secrets and prompt injection.

**Non-negotiables:** inherit source ACLs into the retrieval filter — a knowledge agent that
leaks across permission boundaries is the fastest way to lose the account. Cite the source
document on every answer. Keep all Globant work outside `ee/`, which is separately licensed.

---

## Receta 3 — Governed agent platform (the EMEA AI-Act-ready build)

**For:** an EU client who must be able to show conformity for Annex III use — recruitment
scoring, credit assessment, biometrics, education. **Deadline: 2 December 2027** per
Regulation (EU) 2026/1744. Also the reusable template for LATAM clients who have adopted the
EU AI Act as a de facto standard.

| Layer | Component | License |
|-------|-----------|---------|
| Orchestration | [deepset-ai/haystack](https://github.com/deepset-ai/haystack) (EMEA-origin) | Apache-2.0 |
| Agents | [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | MIT |
| Eval / testing | [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) (EMEA-origin) | Apache-2.0 |
| Runtime controls | [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | Apache-2.0 |
| I/O validation | [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) | Apache-2.0 |
| Policy | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) | Apache-2.0 |
| Sandbox | [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 |
| Serving | [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 |
| Observability | [langfuse/langfuse](https://github.com/langfuse/langfuse) | MIT core + `ee/` carve-out |

**Wiring:**
1. Treat **the evaluation suite as the deliverable**, not an afterthought. Giskard tests are
   written from the client's risk register, so each identified risk maps to a named test.
2. Run that suite in CI on every prompt, model or tool change. The stored run history *is*
   the technical documentation evidence — produced as a by-product rather than written at
   the end.
3. NeMo Guardrails enforces conversational rails at runtime; guardrails-ai enforces typed
   output; OPA gates tool access. Three separate layers because an auditor will ask which
   control failed, and a single layer cannot answer.
4. Every tool execution runs inside OpenSandbox — the "human oversight" and "robustness"
   arguments both lean on it.
5. US-vendor-free, EU-origin, self-hosted: Haystack + Giskard + Mistral + vLLM is a fully
   EU-origin stack and a real answer to a sovereignty question.

**Sales note:** the Omnibus deferral from Aug 2026 to Dec 2027 did not reduce demand — IBM
measures **41% of EU executives accelerating governance spend**. Budget exists now and the
deadline is far enough away to do it properly. **Reuse target: sell this same build into
LATAM**, where EU-Act alignment is voluntary but increasingly expected.

---

## Receta 4 — Rescue a stalled pilot (highest-probability 2026 engagement)

**For:** the client who already built an agent that works in a demo and cannot ship it.
Per Cognizant's own stated reason for launching its EMEA unit, and 45% of LATAM models never
reaching production, this is the most likely door Globant walks through.

| Layer | Component | License |
|-------|-----------|---------|
| Durable execution | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Eval harness | [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) | Apache-2.0 |
| Observability | [langfuse/langfuse](https://github.com/langfuse/langfuse) | MIT core |
| Gateway | [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 |
| Identity / authz | [keycloak/keycloak](https://github.com/keycloak/keycloak) + [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 |
| Sandbox | [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 |

**Wiring — do these in order, because the order is the diagnosis:**
1. **Instrument before changing anything.** Langfuse traces on the existing pilot for two
   weeks. Most stalled pilots have no measured failure mode, only an anecdotal one.
2. **Write the eval suite against observed failures**, not imagined ones. This converts
   "it's unreliable" into a pass rate someone can be accountable for.
3. **Replace the ad-hoc retry loop with Temporal.** Long multi-step processes fail at step
   31 and silently leave half-applied state; this is the most common true blocker.
4. **Give it an identity.** Pilots run on a shared key with god-mode access, which is
   exactly what security review blocks. Keycloak identity + Cerbos per-resource authz.
5. **Put tool calls behind the gateway and inside the sandbox.** Now there is one auditable
   choke point to show a reviewer.
6. **Re-scope autonomy honestly.** Reads autonomous, writes proposed-then-approved. Most
   pilots stall because they promised full autonomy on day one.

**Deliverable:** a production-readiness report with a measured pass rate, a named failure
taxonomy and the governance substrate installed. This is the pay-per-output-friendly
engagement — the outcome is verifiable, which matters under Glob.AI pricing.

---

## Receta 5 — LATAM ERP localisation + agentic layer

**For:** a Brazilian, Argentine, Mexican or Chilean client who needs a compliant ERP *and*
an agent layer. Globant's defensible niche: few global SIs can speak to *nota fiscal*
compliance and agent architecture in the same meeting.

| Layer | Component | License |
|-------|-----------|---------|
| Base (stock) | [odoo/odoo](https://github.com/odoo/odoo) | LGPL-3.0 |
| Localisation | [OCA/l10n-brazil](https://github.com/OCA/l10n-brazil) · [l10n-argentina](https://github.com/OCA/l10n-argentina) · [l10n-mexico](https://github.com/OCA/l10n-mexico) · [l10n-chile](https://github.com/OCA/l10n-chile) | **AGPL-3.0** |
| OCA tooling | [OCA/server-tools](https://github.com/OCA/server-tools) | AGPL-3.0 |
| Agent layer | [agno-agi/agno](https://github.com/agno-agi/agno) or [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | Apache-2.0 / MIT |
| Durability | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Approval UI | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 |

**Wiring:**
1. Deploy Odoo + the country `l10n-*` module **into the client's own infrastructure**. The
   localisation is **AGPL-3.0** — it is deployment infrastructure for the client, never a
   component inside a Globant product. Do not vendor it into Globant repos.
2. Keep the agent layer in a separate permissive repo, integrating over Odoo's API.
3. Give tax and invoicing documents their own read-only agent: fiscal document
   interpretation is high-value, low-risk and demos extremely well.
4. All fiscal *writes* go through human approval — a mis-issued *nota fiscal* is a
   regulatory event, not a bug.
5. Compliance posture: LGPD (Brazil) and *habeas data* (Argentina, Colombia) are the real
   gates. If the client has adopted the EU AI Act as its standard, layer Receta 3's
   evaluation stack on top — it transfers directly.

---

## Receta 6 — JVM-native agents for an APAC enterprise core

**For:** an APAC client (or any bank/insurer) whose system of record is Java and who will
not accept a Python sidecar in the transaction path.

| Layer | Component | License |
|-------|-----------|---------|
| Agents (JVM) | [agentscope-ai/agentscope-java](https://github.com/agentscope-ai/agentscope-java) | Apache-2.0 |
| Agents (Python peer) | [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) | Apache-2.0 |
| .NET/Java alt | [microsoft/semantic-kernel](https://github.com/microsoft/semantic-kernel) | MIT |
| Base suite | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 |
| Durability | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |
| Serving (in-country) | [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 |

**Wiring:** agentscope-java for distributed, long-running agents in-process with the JVM
core. Where a client's legal team rejects copyleft outright, **apache/ofbiz-framework is the
only fully Apache-2.0 ERP+CRM+SCM suite** in this KB — small community, but it unblocks deals
nothing else can. Self-host serving with vLLM to satisfy data-localisation requirements,
which are a standing APAC constraint rather than an edge case.

**Per-market caveat:** there is no APAC-wide regime. Korea's AI Basic Act (in force Jan 2026)
and Vietnam's (1 Mar 2026) impose real obligations; Japan is light-touch. Express the
obligation set as OPA policy per market over one agent implementation — do not fork the
agent per country. **Do not promise Microsoft Agent Framework on this stack** until its
canonical repo is located (see `agents/top.md`); Semantic Kernel (MIT) is the verified
Microsoft-stack fallback.

## Receta 7 — Govern an adopted harness and its skill supply chain

**For:** the client whose developers already installed a harness (OpenClaw, DeepSeek Harness,
Hermes Agent, Deep Agents) and whose security function has just realised that the agent is
running community skills with its own OS permissions. **This is the highest-conviction new
offer in this KB** — the exposure is universal among 2026 harness adopters, nobody sold them
a control for it, and the controls are Apache-2.0 and exist today.

| Layer | Component | License | Verified |
|-------|-----------|---------|----------|
| Skill inventory | [openclaw/clawhub](https://github.com/openclaw/clawhub) (registry) + [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) (5,400+ skill corpus) | MIT | 9,557 ★ / 53,885 ★ |
| Pre-install scanning | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) — 71 patterns / 17 categories | Apache-2.0 | 27,027 ★ |
| Quality + behaviour gates | [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) — ships reusable CI templates | Apache-2.0 | 4,224 ★ |
| Runtime containment | [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) or [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 | 21,829 ★ / 17,707 ★ |
| Harness → governed runtime bridge | [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 ★ |
| Per-call enforcement point | [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) — middleware on tool and LLM calls | Apache-2.0 | 254 ★ |
| Policy decision | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) or [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 | 12,501 ★ / 4,664 ★ |
| Agent process identity | [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | 2,630 ★ |
| Human identity | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 | 37,980 ★ |
| Durability | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT | 24,518 ★ |

**Wiring — in this order, because each step produces the evidence for the next:**

1. **Inventory first, and expect it to be the whole sale.** Enumerate every skill, plugin
   and MCP server installed across the client's harnesses. Research on public registries
   found **26.1% of 31,132 skills carried at least one vulnerability** and **36% of 3,984
   ClawHub skills contained prompt-injection techniques** — so an inventory with a scan
   attached is a finding, not a formality. (Figures second-hand; see `intel/trends.md` §10.)
2. **Scan with SkillSpector in CI, not on a laptop.** Point it at the client's actual skill
   set. Its 17 categories map almost one-to-one onto what a CISO already asks about: prompt
   injection, data exfiltration, privilege escalation, excessive agency, system-prompt
   leakage, memory poisoning, tool misuse, MCP tool poisoning, MCP least privilege.
3. **Assume the scanner misses things, and say so out loud.** Trail of Bits bypassed the
   ClawHub, Cisco and `skills.sh` detectors, and CSA recorded five malicious skills evading
   updated ClawScan *and* VirusTotal between Feb–May 2026. **A scan-only deliverable is
   mis-sold.** This is why steps 4–6 exist, and saying it first is what makes Globant
   credible rather than another scanner reseller.
4. **Add behavioural gates with SkillEvaluator.** Separate research found **80% of skills
   had a mismatch between declared and actual behaviour** — mostly bad documentation, not
   malice, which is exactly why a *declaration-vs-behaviour* check is the right control: it
   catches the 80% cheaply and surfaces the malicious remainder by exception. Use its CI
   templates so the gate lives in the client's pipeline after Globant leaves.
5. **Pin provenance and mirror the registry.** No direct pulls from a public registry into
   an environment that can write. Mirror internally, pin by digest, re-scan on update. This
   is ordinary supply-chain hygiene; the novelty is only that the artefact is prose.
6. **Contain at runtime.** Skills execute with the agent's own OS permissions, so scanning
   is necessary and not sufficient. Run the harness inside OpenShell (via NemoClaw) or
   OpenSandbox.
7. **Enforce per call, don't log per call.** NeMo-Relay's middleware on tool and LLM calls is
   where an OPA/Cerbos decision is actually applied. Logging a violation after the ERP write
   is an incident report, not a control.
8. **Give the agent *process* an identity, not just a user.** Keycloak answers "who is this
   agent acting for"; SPIRE answers "is this the build we approved". Both are needed to
   attest a tool call.
9. **Wrap the whole thing in durable execution.** Temporal, so a half-applied multi-step
   write is recoverable rather than discovered.

**Licence watch:** `anthropics/skills` (197,931 ★) and `multica-ai/andrej-karpathy-skills`
(234,677 ★) have **no licence file**. Scan and reference them; never vendor them into the
deliverable. See `agents/top.md`.

**Vendor-concentration watch:** five of the components above are NVIDIA's, including
OpenShell despite its vendor-neutral `ai-openshell` org name. Deliberately pair them with
non-NVIDIA controls (OPA/Cerbos, Keycloak, SPIRE, OpenSandbox, Giskard) so the client is not
handed single-vendor dependence as the price of governance.

**Deliverable:** a scanned and gated skill inventory, a CI pipeline that blocks on
regression, a contained runtime, an enforcement point with per-call policy, and a written
statement of residual risk that names the bypass research. Verifiable, repeatable across
clients, and priceable per output under Glob.AI.

---

## Receta 8 — Agentic process orchestration on an existing BPM engine

**For:** the client with a real process estate — BPM engine, SLAs, audit history, human task
lists — who has been pitched "agentic workflow" and correctly suspects it means replacing
something that works. It does not. The agent becomes a **service task**.

| Layer | Component | License |
|-------|-----------|---------|
| Process engine (new build) | [flowable/flowable-engine](https://github.com/flowable/flowable-engine) | Apache-2.0 |
| Process engine (lighter / YAML-first) | [kestra-io/kestra](https://github.com/kestra-io/kestra) | Apache-2.0 |
| Process engine (client already runs it) | [camunda/camunda](https://github.com/camunda/camunda) | **Camunda Licence 1.0 — not open source** |
| Semantic layer | [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 |
| Transformation | [dbt-labs/dbt](https://github.com/dbt-labs/dbt) | Apache-2.0 |
| Catalog / lineage | [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 |
| Agent layer | [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) or [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | MIT |
| Tool gateway | [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 |
| Human approval console | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 |
| Durability | [temporalio/temporal](https://github.com/temporalio/temporal) | MIT |

**Wiring:**

1. **Model the process in BPMN and leave it there.** The engine keeps the audit trail,
   SLA timers and task assignment. A process owner can read a BPMN diagram; they cannot read
   an agent's trace. That legibility *is* the governance deliverable.
2. **Make the agent one service task with a typed contract.** In, out, timeout,
   compensation. If the agent fails, the engine's existing error-boundary handling takes
   over — behaviour the client already trusts and has already signed off.
3. **Fix the semantics before the reasoning.** Give the agent an ontology
   (`auto-ontology`) over curated dbt models with DataHub lineage, so queries are generated
   deterministically against tables the agent is allowed to believe. The common failure here
   is prompt-engineering a join that a semantic layer should have made impossible.
4. **Human tasks stay human tasks.** Writes route to the engine's existing task list, or to
   an Appsmith console. Do not invent a parallel approval path beside the one audit already
   covers.
5. **Durability belongs underneath, not inside.** Temporal for agent-side multi-step work;
   the BPM engine stays the system of record for the business process. Two different
   guarantees — do not collapse them.
6. **If it is Camunda, read the licence before writing a line.** Zeebe, Operate and Tasklist
   are Camunda Licence 1.0. Build only against the Apache-2.0 parts — Java Client,
   Spring Boot Starter, Exporter API, Protocol, Gateway Protocol Implementation, BPMN Model
   API — and generated gRPC stubs, which Camunda explicitly states are not derivative works.
   Same containment discipline as a copyleft ERP. Details in `verticals/solutions.md`.

**Deliverable:** one existing business process with an agent in a named service task, its
approval path unchanged, its audit trail intact, and a measured cycle-time delta. The least
glamorous and most repeatable agentic engagement available in 2026.

---

---

## Receta 9 — The agent control plane: one place for credentials, quotas and cost

**For:** the client who says "we have already done AI". Per IDC, 95% of enterprises run at
least one agent-enabled workflow in production and **only 45.4% can see token consumption per
workflow** — while 61.8% rate their own cost governance as "defined" or better. So the client
is almost certainly right that they have agents, and almost certainly unable to tell you what
they cost, who authorised them, or how many there are. **This is the cheapest credible entry
point in this KB: it touches no business logic and no model, and it produces the number that
unlocks the budget for Recetas 3, 4 and 7.**

| Layer | Component | License |
|-------|-----------|---------|
| Control plane (model + MCP traffic) | [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 (Agentic AI Foundation) |
| Control plane (alternative, widest adoption) | [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT core + `litellm/enterprise/` carve-out** |
| Control plane (alternative, guardrails built in) | [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | MIT |
| Control plane (client already runs Kong) | [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 (AI features may be enterprise-gated) |
| MCP registry & proxy | [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 |
| Agent identity (user-shaped) | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 |
| Agent identity (process-shaped) | [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 |
| Tool authorisation | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) or [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 |
| Enforcement point per call | [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 |
| Telemetry naming | [open-telemetry/semantic-conventions](https://github.com/open-telemetry/semantic-conventions) | Apache-2.0 |
| Instrumentation | [traceloop/openllmetry](https://github.com/traceloop/openllmetry) or [Arize-ai/openinference](https://github.com/Arize-ai/openinference) | Apache-2.0 |
| Metering & entitlements | [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | Apache-2.0 |
| Infrastructure cost | [opencost/opencost](https://github.com/opencost/opencost) | Apache-2.0 |
| Reporting surface | [apache/superset](https://github.com/apache/superset) | Apache-2.0 |

**Wiring:**

1. **Inventory before you build — the discovery is half the value.** Point the gateway at
   nothing yet; instead find every existing caller. Grep the estate for provider base URLs and
   SDK imports, and pull provider-side usage by API key. The deliverable of week one is a list
   of agents and callers the client did not know they had. "Agent sprawl" and "shadow AI" are
   named cost drivers; name them with the client's own data.
2. **Put the control plane in front, in pass-through mode, and change nothing else.** Agent
   Router and LiteLLM both expose an OpenAI-compatible API, so migration is a base-URL change
   per caller. Do not add policy yet. The goal of this step is only that **100% of model traffic
   flows through one place**. Nothing below is possible until that is true.
3. **Issue one virtual key per team, workflow and environment — never per developer.** This is
   the step that makes attribution possible, and it is an organisational decision disguised as a
   technical one: the key hierarchy you choose becomes the cost-reporting hierarchy forever.
   Agree it with whoever owns the budget before issuing anything.
4. **Give the agent a real identity.** Keycloak for the user-shaped identity an audit asks about;
   SPIRE for the process-shaped one that attests the *build* calling the tool is the build you
   approved. A shared API key in an environment variable is the thing this recipe exists to
   delete.
5. **Name the spans before you emit them.** Adopt the OpenTelemetry **GenAI semantic
   conventions** and instrument with OpenLLMetry or OpenInference. Agent telemetry then lands in
   the client's existing APM instead of a second, agent-only monitoring tool nobody renews.
   Agreeing the attribute names up front is what keeps this portable when the vendor changes.
6. **Only now add policy, at the gateway and at the call.** Express "which identity may call
   which model or tool, with what budget" as versioned OPA or Cerbos policy. Enforce it at the
   gateway for model traffic and through `NeMo-Relay` middleware for per-call tool decisions —
   a logged decision is not a control.
7. **Turn usage events into money.** OpenMeter aggregates gateway events into per-team
   entitlements and chargeback; OpenCost covers the GPU and pod spend behind self-hosted vLLM
   that token counting never sees. Report both in Superset. **Build the per-workflow token
   dashboard IDC says 54.6% of enterprises lack** — that single chart is usually the thing that
   gets the next phase funded.
8. **Set budgets that fail closed, then test that they do.** A budget that logs an overage is a
   report. Cap per virtual key, and rehearse the breach in staging so the client sees the agent
   degrade predictably rather than invoice unpredictably.

**Why this shape:** the control plane is the only layer that sees every model and tool call, so
it is the only honest place to enforce cost, quota and tool authorisation at once. **Lead with
Agent Router where vendor neutrality is a live objection** — it is Apache-2.0 under the Agentic
AI Foundation, the same foundation that stewards MCP, goose and AGENTS.md, and it is the
structural mitigation for the NVIDIA concentration risk recorded in `intel/market.md`. Lead with
**LiteLLM** where the client's developers have already adopted it (63,615 ★ makes that likely) —
but **verify the carve-out before promising SSO, RBAC or team budgets**, since `litellm/enterprise/`
is separately licensed. Globant's IP in this recipe is the key hierarchy, the policy bundle, the
semantic-convention mapping and the dashboards — all of which sit in a permissive repository and
all of which transfer to the next client.

**Commercial note, and it points inward first.** McKinsey's position is that the unit of
governance should be the completed business outcome, not the token — which is exactly how
**Glob.AI** bills. Pay-per-output puts the token bill on Globant's side of the contract, so
this recipe is **margin protection before it is a client deliverable**. Build it on Globant's own
Glob.AI workloads first; the reference case then writes itself and is honest.

## Receta 10 — The red-team and evaluation gate in CI

**For:** any engagement from Recetas 1–9 that is about to touch production. Receta 7 gates the
*skills* an agent may load, statically. This gates the *agent's behaviour*, dynamically, on
every change — and it is the artefact that makes an EMEA Annex III technical file or a NIST AI
RMF claim evidenced rather than asserted.

| Purpose | Component | License |
|---------|-----------|---------|
| Eval + red team, CI-shaped | [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT |
| Metric-based eval in pytest | [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 |
| RAG-specific metrics | [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | Apache-2.0 (**moved from `explodinggradients`**) |
| Vulnerability probes | [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 |
| Adversarial framework | [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | MIT (**canonical; not `Azure/PyRIT`**) |
| Skill quality gates + CI templates | [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 |
| Skill security scan | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 |
| Evidence capture / EU-origin | [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss), [Agenta-AI/agenta](https://github.com/Agenta-AI/agenta) | Apache-2.0 / MIT Expat core |
| Runtime validation | [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails), [protectai/llm-guard](https://github.com/protectai/llm-guard) | Apache-2.0 / MIT |
| Isolation for destructive probes | [e2b-dev/E2B](https://github.com/e2b-dev/E2B) or [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 |

**Wiring:**

1. **Write the eval set from the client's refusals and incidents, not from a benchmark.** The
   cases that matter are the ones their risk function already worries about. Twenty real cases
   beat a public benchmark for both signal and credibility.
2. **Run promptfoo as a required status check.** Declarative config in the repo, assertions per
   case, and the build fails on regression. This is the step that converts "we evaluated it" into
   a control with a timestamp and a commit hash.
3. **Red-team the deployed agent, not the bare model.** Point `garak` and `PyRIT` at the agent
   **with its tools and gateway attached**, because the interesting vulnerabilities are tool
   misuse, excessive agency and data exfiltration — none of which exist on a bare model. Run
   destructive probes inside E2B or OpenSandbox.
4. **Gate the skills in the same pipeline.** `SkillSpector` for the 71 patterns across 17
   categories, `SkillEvaluator` for harness compatibility, semantic overlap and behavioural
   change. It **ships reusable CI templates** — use them rather than writing stages by hand.
5. **Keep a runtime net, because CI is a point-in-time claim.** `guardrails` or `llm-guard` for
   input/output validation in production, with Portkey's gateway-level guardrails (Receta 9) as
   the layer an application team cannot forget to call.
6. **Capture the evidence as a build artefact.** Every run writes results to durable storage
   keyed by commit. Giskard and Agenta are both **EMEA-origin**, which matters when an EU client
   asks for an EU-origin assurance toolchain — and the archive *is* the Annex III technical
   documentation, produced as a by-product of the pipeline rather than written later.

**Two licence traps to flag before anyone wires them in:**
[meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) is commonly proposed as an
open guardrail and is under the **Llama 3.2 Community License Agreement — not OSI open source**
(GitHub reports `NOASSERTION`, which is why the error is so common). And
[protectai/rebuff](https://github.com/protectai/rebuff) is still widely cited but was last
pushed **2024-08-07** — over two years cold. Use the Apache-2.0 and MIT options in the table.

**Why this shape:** `intel/trends.md` trend 10 records that skill scanners are already being
bypassed, which makes static scanning necessary and insufficient. A CI gate plus adversarial
probes plus a runtime validator is defence in depth where each layer fails differently. And the
evidence archive is what a regulated client's risk committee actually signs — the thing
`intel/market.md` identifies as the hard part of shipping an agent, as opposed to demoing one.

## Receta 11 — A commerce agent that may spend money, with de-identification and catalog grounding

**New this pass (fourth, 2026-11-20).** Covers the three layers the KB was missing: *may it
spend?*, *may it see this personal data?*, *may it believe this table?* Use when a retail,
travel, marketplace or B2B-distribution client wants an agent that completes a transaction
rather than drafting one.

**The honest framing to open with.** The payment protocols are **not settled**: AP2
(Apache-2.0, 3,281 ★) has been idle since **2026-06-17**, the x402 extension (Apache-2.0, 571 ★)
was pushed **2026-11-11**, and ACP (Apache-2.0, 1,607 ★) sits between them. So this recipe does
**not** pick a rail. It builds the two things that survive whichever rail wins — a **signed
mandate** and a **human approval step** — and keeps the rail behind an adapter.

### Wiring

1. **System of record stays stock.** Odoo ([odoo/odoo](https://github.com/odoo/odoo), LGPL-3.0)
   or the client's existing commerce suite, integrated over its API exactly as Receta 1. Never
   forked — the copyleft containment rule in this file applies unchanged.

2. **Grounding: the catalog answers what is true.** Point the agent at the client's existing
   [OpenMetadata](https://github.com/open-metadata/OpenMetadata) (Apache-2.0, 15,823 ★) or
   [DataHub](https://github.com/datahub-project/datahub) (Apache-2.0, 13,006 ★) as **read-only
   MCP tools** — which products, prices and inventory tables are authoritative. Emit every agent
   action as [OpenLineage](https://github.com/OpenLineage/OpenLineage) (Apache-2.0, 2,773 ★)
   events, so "what did the agent change, and from which source?" is queryable *afterwards*.
   This is the audit trail, and it costs a connector because the client already runs the catalog.

3. **De-identification at both boundaries.**
   [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) (MIT, 11,989 ★)
   runs **twice**: once on the way in, before any customer text reaches a model, and once on the
   way out, before any model output reaches a log or a trace. Note the path — it is **no longer
   `microsoft/presidio`**. Tune recognisers for the client's data with
   [presidio-research](https://github.com/data-privacy-stack/presidio-research) (MIT, 321 ★) so
   detection quality is an evidenced number, not a claim. Keep
   [protectai/llm-guard](https://github.com/protectai/llm-guard) (MIT, 3,221 ★) for
   injection/leakage — it is a complement, not a substitute.

4. **Retrieval that spans documents.** Where the question is relational rather than lexical
   ("what is this supplier's exposure across our contracts?"), use
   [microsoft/graphrag](https://github.com/microsoft/graphrag) (MIT, 36,699 ★). **Price the graph
   construction explicitly** — per corpus, re-paid on refresh. If the client needs to own and
   modify the pipeline, [nano-graphrag](https://github.com/gusye1234/nano-graphrag) (MIT, 4,010 ★)
   is the hackable option, **but it has been idle ~10 months** — check before proposing.

5. **The spend cap lives at the gateway, not in the agent.** Enforce budget in
   [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) (Apache-2.0,
   2,423 ★) or [BerriAI/litellm](https://github.com/BerriAI/litellm) (MIT core, 63,615 ★) as in
   Receta 9. An agent that polices its own budget in a prompt has no budget control at all: the
   limit must sit where it is *enforced*, outside the reasoning loop.

6. **Agent identity before agent payment.** SPIFFE workload identity (see
   `repos/foundations.md`) establishes *which* agent is acting;
   [forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol)
   (MIT, 180 ★) covers agent↔merchant authentication. The payment specs answer *how much* and
   *on whose mandate* — neither answers *who is this*. Do not skip this step because the
   protocols do.

7. **The mandate and the approval step — the part that survives.** Record a signed, replayable
   artefact of exactly what the user authorised (scope, amount ceiling, expiry, counterparty),
   modelled on AP2's mandate/verifiable-credential shape even if AP2 is never adopted. Then
   require a **human approval** before any irreversible debit. Put the rail behind an adapter
   interface with one implementation today; the blueprint in
   [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce)
   (Apache-2.0, 89 ★) shows the ACP/UCP shape end to end — treat it as a **demo asset, not a
   production base**.

8. **Gate it in CI.** Receta 10's red-team and eval gate applies with one addition: a test
   class that asserts **no payment path is reachable without a valid mandate and an approval
   record**, and that Presidio's egress filter is on. That assertion is the deliverable an
   auditor wants, and it is also the ISO/IEC 42001 evidence artefact (`intel/trends.md` §14).

### Licence posture

Everything Globant writes — connectors, mandate service, adapters, approval UI — sits in a
separate **MIT or Apache-2.0** repository. Every component above is MIT or Apache-2.0 except the
client's own ERP, which is reached over its API and never forked. **There is no copyleft
obligation on Globant's code in this recipe**, which is the point.

### What to tell the client the limits are

- **No agent gets an unsupervised payment rail in 2026.** The protocols are contested and the
  most-starred one is five months idle. Anyone promising otherwise is reading star counts.
- **Graph construction is a real, recurring cost line**, not a one-off index.
- **Presidio reduces personal-data exposure; it does not eliminate it.** Detection has a
  measurable error rate — measure it with `presidio-research` and report the number.
- **The FIDO Alliance donation of AP2 is reported, not verified** by this KB (no primary source
  was reachable). Verify before it reaches a deck.

## Anti-patterns — each one observed in this pass's evidence

- **Forking the base platform.** Converts a client integration into a copyleft obligation
  on Globant code. Integrate over the API.
- **Letting the agent hold its own spend limit.** A budget enforced inside the reasoning loop is
  not enforced. It belongs at the gateway (Receta 9, Receta 11 step 5).
- **Citing `microsoft/presidio`.** Moved to [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio);
  the old path still redirects, so the error is invisible until a client's security review asks
  who maintains it. Same class of mistake as the three renames in the ledger.
- **Picking a payment protocol on star count.** AP2 has 5.7x the stars of the actively-maintained
  x402 extension and has not been pushed since June 2026. Build the mandate, adapter the rail.
- **Treating ISO/IEC 42001 as EU AI Act compliance.** Reported to reduce Act risk, **not** to
  satisfy it. Clients conflate them; correcting it early is free credibility.
- **Taking a license from a badge, a directory or a blog.** This pass corrected four:
  Phoenix is **Elastic-2.0** (not open source), NocoBase is a **proprietary EULA**, Huly is
  **EPL-2.0** (not Apache-2.0), and NeMo Guardrails **is** Apache-2.0 despite GitHub showing
  `NOASSERTION`. Read the `LICENSE` file.
- **Building on an unverified framework.** `microsoft/agent-framework` is cited everywhere
  as MIT with ~45k stars and **currently 404s**. Verify the repo exists before it reaches a
  statement of work.
- **Shipping a client-branded Open WebUI.** Its license carries a branding restriction.
- **Letting model output reach an actuator.** Parse into a typed call, authorise it, sandbox
  it.
- **Promising full autonomy on day one.** The measured market failure mode. Reads
  autonomous, writes approved.
- **Pinning stale remotes.** Four moves verified this pass: `All-Hands-AI/OpenHands` →
  `OpenHands/OpenHands`, `block/goose` → `aaif-goose/goose`, `NVIDIA/NeMo-Guardrails` →
  `NVIDIA-NeMo/Guardrails`, `Giskard-AI/giskard` → `Giskard-AI/giskard-oss`.
- **Starting new work on AutoGen.** Superseded; use AG2 or a verified alternative.
- **Installing community skills straight into an environment that can write.** They run with
  the agent's own OS permissions, **26.1% of a 31,132-skill sample carried a vulnerability**,
  and the registry scanners have documented bypasses. Mirror, pin, scan, gate, sandbox.
- **Selling a skill scan as the control.** Trail of Bits bypassed three production detectors
  and five malicious skills evaded ClawScan and VirusTotal in Feb–May 2026. Scanning is the
  first of six layers in Receta 7, not the deliverable.
- **Vendoring an unlicensed skill repository.** `anthropics/skills` (197,931 ★) and
  `multica-ai/andrej-karpathy-skills` (234,677 ★) have **no licence file**. Huge star counts,
  zero redistribution rights.
- **Ranking a shortlist by stars.** Single-author skill collections now out-star every
  framework in Tier 1 combined. Rank by licence, governance and maintenance; use stars only
  to learn what is already installed in the client's estate.
- **Assuming Camunda is open source because it says "open" and "agentic".** It is
  **Camunda Licence 1.0** with named Apache-2.0 parts and no root `LICENSE` file.
- **Writing "the repo does not exist" after one 404.** `dbt-labs/dbt-core` 404s on
  `github.com` and is simply **renamed to `dbt-labs/dbt`** — the old path still serves on
  `raw.githubusercontent.com`. Probe three channels (HTML, search API with `repo:`, and
  `<name> in:name user:<owner>`) before recording a gap. Applied correctly, the same three
  probes still find nothing for `microsoft/agent-framework`.
- **Replacing a working BPM engine to be "agentic".** The agent goes in a service task. The
  audit trail, SLA timers and task lists are the reason the client can approve it at all.
