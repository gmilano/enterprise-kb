---
industry: enterprise
region: Global
updated: 2026-11-24
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
| Portable JVM runtime | [Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere) | Apache-2.0 |
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

**Addition, fifth pass 2026-11-20 — provider portability on the JVM.**
[Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere) (Apache-2.0, 3,835 ★, 765
forks, pushed 2026-11-20) lets one `@Agent` class run over Spring AI, LangChain4j or a vendor
SDK. On a Japanese or Korean core this matters for a specific reason: the model provider is the
part of the stack most likely to be changed for data-localisation or sovereignty reasons, and
this is the layer that keeps that change out of the agent code. It also removes this recipe's
single-project dependency on `agentscope-java`.

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

## Receta 12 — Put the agent inside the client's own application, not in a chat window

**When to use it.** The client has a pilot that works in a chat box and nobody uses it, or they
want an agent to take over a *step in a process* rather than answer questions about it. This is
the highest-adoption shape available in 2026 and the one four prior passes of this KB never
specified.

**Why this recipe exists at all.** The standalone-chat-shell projects in this category are being
archived — `Chainlit/chainlit` (Apache-2.0, 12,498 ★), `langchain-ai/agent-chat-ui` (MIT,
3,253 ★) and `langchain-ai/deep-agents-ui` (MIT, 1,705 ★) are all reported archived by the
GitHub API, with no notice in their READMEs. Everything live renders *into* the host app.

### Wiring

| Layer | Piece | Licence |
|-------|-------|---------|
| UI protocol | [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) **or** [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | MIT / Apache-2.0 |
| Renderer | [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) (React/Angular/Slack) · [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) · [vercel-labs/json-render](https://github.com/vercel-labs/json-render) if the front end is Next.js · [flyerhq/flutter_chat_ui](https://github.com/flyerhq/flutter_chat_ui) if mobile | MIT / MIT / Apache-2.0 / Apache-2.0 |
| Agent | whatever the client already runs — [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) (MIT), [agno-agi/agno](https://github.com/agno-agi/agno) (Apache-2.0) or [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai) (MIT); all three integrate AG-UI | MIT / Apache-2.0 / MIT |
| Human boundary | [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) | Apache-2.0 |
| Grounding | [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) over the catalog, or [backstage/backstage](https://github.com/backstage/backstage) if the subject is services | Apache-2.0 |
| Traffic plane | [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 |

### Build order

1. **Pick the three screens, not the model.** Identify the exact places in the client's existing
   application where the agent will render. If nobody can name three, the engagement is not ready
   — that is a discovery finding, not a blocker to hide.
2. **Define a typed UI intent of your own** and have the agent emit *only* that. One adapter
   module maps intent → AG-UI or A2UI events. **No renderer vocabulary in prompts, tool
   definitions or agent reasoning.** This is the whole reversibility of the recipe: four live
   standards compete at this layer with no foundation steward (`intel/trends.md` §15), so the
   renderer *will* be reconsidered.
3. **Constrain the component catalog on the client side.** Follow A2UI's model even when using
   AG-UI: the host application holds a catalog of approved components and the agent may only
   *request* from it. An agent that can emit arbitrary markup into an internal app is a
   prompt-injection path to an employee's screen — a rendered link, a forged confirmation
   button. The schema closes it structurally; text filtering does not.
4. **Put `humanlayer` between the agent and every irreversible action**, as a typed call with an
   owner, a route and a timeout — not as a prompt instruction. Carry over the rule this KB holds
   from automotive: **model reasoning text never reaches the actuator**, only a validated
   command with validated arguments.
5. **Ground before you render.** Proposals must cite the record they came from — the catalog
   entity, the ticket, the Backstage service. An agent rendering a confident native widget is
   *more* persuasive than one writing a paragraph, so an ungrounded proposal is more dangerous in
   this shape, not less.
6. **Attribute every call** through the control plane (Receta 9) so the pilot can answer "what
   did this cost per resolved task" on the day it is reviewed.

### Sizing and the milestone to fix

**4–6 weeks** for one screen, one agent, one approval path, in a staging copy of the client's
real front end. **10–14 weeks** for three screens with grounding, cost attribution and an
approval audit trail. Expect **60–70% of effort in the host application and its component
catalog, not in the agent.** Budget it as front-end integration work with an agent attached,
because that is what it is.

**First milestone to fix contractually:** one real screen, one real proposal, rendered with the
client's own components and approved by a real user. Before that exists, do not add a second
agent, a second screen or a model upgrade.

### What to tell the client the limits are

- The renderer choice is a **bet**, not a standard. It is behind an adapter for that reason.
- An agent in-app changes the UX contract: users will treat a native widget as a product
  feature, so proposal quality has to be production quality from the first demo.
- If they are on Chainlit today, say plainly that it is archived, and price the migration
  separately from the new capability. Do not fold a forced migration into a feature quote.

## Receta 13 — AI estate inventory first: the four-week engagement that unblocks every other one

**When to use it.** The client says "we need AI governance" and cannot list what they run. Also
the correct first move whenever ISO/IEC 42001 certification or EU AI Act record-keeping is
mentioned, because both presuppose an inventory and neither accepts a spreadsheet maintained by
hand.

**Why it is a separate recipe.** Recetas 7, 9 and 10 govern agents the client knows about. With
>10,000 MCP servers reported in production market-wide and skills installed per developer, the
estate is not in any vendor portal. **Unknown agents are the ones that cause the incident.**

### Wiring

| Step | Piece | Licence |
|------|-------|---------|
| Discover agents/models/APIs in infrastructure | [Trusera/ai-bom](https://github.com/Trusera/ai-bom) | Apache-2.0 (368 ★, **idle since 2026-05-24 — fork it**) |
| Scan MCP configs for secrets, shadow APIs, models | [apisec-inc/mcp-audit](https://github.com/apisec-inc/mcp-audit) | MIT (167 ★, idle since 2026-08-18) |
| Express as a standard BOM | [CycloneDX/specification](https://github.com/CycloneDX/specification) + [CycloneDX/cyclonedx-python](https://github.com/CycloneDX/cyclonedx-python) (Maven/Gradle/.NET/Go siblings in the same org) | Apache-2.0 |
| Diff, score, validate over time | [sbom-tool/sbom-tools](https://github.com/sbom-tool/sbom-tools) | MIT |
| Inventory the *skills* an agent can load | [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 |
| Services and owners, where it already exists | [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 |
| Where the numbers come from afterwards | the control plane, Receta 9 | Apache-2.0 |

### Build order

1. **Week 1 — discover, do not judge.** Run `ai-bom` and `mcp-audit` across the estate and
   produce the raw list. Resist classifying anything yet; the deliverable of week 1 is a list
   long enough to be uncomfortable.
2. **Week 2 — express it in CycloneDX, not in a format you invented.** ML-BOM/SaaSBOM are part of
   the standard. An auditor who already accepts CycloneDX for software will accept it for AI; a
   bespoke spreadsheet restarts that argument from zero.
3. **Week 3 — make it a diff, not a snapshot.** Wire `sbom-tools` into CI or a weekly job. An
   inventory that is not re-run is a dated document; a diff is a **control**, and controls are
   what 42001 auditors ask to see evidence of.
4. **Week 4 — hand over the evidence pack**: current BOM, diff history, owner per entry,
   approval route per entry (Receta 12 step 4), and the explicit list of what the tooling
   **cannot** see. That last list is the most valuable page in the pack and the honest basis for
   phase two.

### Licence and maintenance posture — read before quoting

Two of the five tools are months idle (`ai-bom` 2026-05-24, `mcp-audit` 2026-08-18) and the
whole layer tops out at 585 stars. **Both are permissive (Apache-2.0, MIT), so forking is
allowed and is the right plan** — quote maintenance of a fork, not dependency on an upstream
that may not move. Do not present this layer to a client as mature tooling; present it as a
standard (CycloneDX) plus scripts Globant maintains. That is accurate and it is also the more
defensible commercial position.

### Sizing

**4 weeks** for one business unit or one cloud account. **8–10 weeks** for a multi-account
estate with the diff in CI and the 42001 evidence pack. Note for EMEA: pair the output with the
AI-Act Annex III scoping already recorded in `intel/market.md` — the inventory is the input to
that scoping, and clients routinely attempt the scoping without it and have to redo it.


---

## Receta 14 — "Ask our data in English", built so the answer reconciles with finance

**For:** the client who asked for a text-to-SQL chatbot in meeting one. This is the most
requested enterprise agent of 2026 and the one most likely to be delivered as a demo that dies
in UAT, because the thing that kills it is not the model.

**The number that should shape the proposal:** text-to-SQL does not degrade with schema
size, it **collapses** — a 2025 study (via vendor secondary sources) measures GPT-4o at **86%
execution accuracy on academic benchmarks and 6% on enterprise databases with more than 1,000
columns**. Every enterprise warehouse worth querying is on the wrong side of that threshold.
So the deliverable is the **semantic layer**, and the agent is the interface onto it.

| Layer | Component | Licence |
|-------|-----------|---------|
| Semantic layer (default) | [cube-js/cube](https://github.com/cube-js/cube) | Apache-2.0 (MIT in parts) |
| Semantic layer (client already runs dbt) | [dbt-labs/metricflow](https://github.com/dbt-labs/metricflow) | Apache-2.0 |
| Semantic modelling language | [malloydata/malloy](https://github.com/malloydata/malloy) | MIT |
| Transformation | [dbt-labs/dbt](https://github.com/dbt-labs/dbt) | Apache-2.0 |
| Ontology / graph grounding (optional) | [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 |
| Catalog / lineage | [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 |
| Data agent | [Canner/WrenAI](https://github.com/Canner/WrenAI) (all code paths Apache-2.0) or [mindsdb/mindsdb](https://github.com/mindsdb/mindsdb) (MIT) | Apache-2.0 / MIT |
| NL-to-SQL technique reference | [XGenerationLab/XiYan-SQL](https://github.com/XGenerationLab/XiYan-SQL) | Apache-2.0 |
| Engine for local build & test | [duckdb/duckdb](https://github.com/duckdb/duckdb) | MIT |
| Table format | [apache/iceberg](https://github.com/apache/iceberg) | Apache-2.0 |
| Tool gateway | [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 |
| Authorisation | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) or [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 |
| Eval gate | [confident-ai/deepeval](https://github.com/confident-ai/deepeval) + [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | Apache-2.0 / MIT |
| Report surface | [evidence-dev/evidence](https://github.com/evidence-dev/evidence) | MIT |

### Wiring

1. **Define the metrics before you connect a model.** Twenty to forty metrics in Cube or
   MetricFlow, each with its dimensions, joins and access rules as code in git. This is the
   billable artefact and the one the client's finance lead must sign. If they will not sign a
   metric definition, the project is not ready for an agent and that is the finding to report.
2. **Forbid raw SQL generation. The agent requests a metric, not a table.** Expose Cube over
   **MCP** and give the agent *only* that tool. It names a metric, dimensions and a time grain;
   the semantic layer generates the SQL. This is what moves accuracy and it is also what makes
   the answer auditable — every response traces to a definition a human approved. Gartner
   (Feb 2026, secondhand) projects **60% of agentic analytics projects relying solely on MCP
   will fail by 2028** without this layer; MCP is the transport, not the governance.
3. **Put authorisation at the semantic layer, not in the prompt.** Row- and column-level rules
   belong in Cube's access control, enforced by OPA or Cerbos against the caller's identity.
   An agent that is *told* not to show salaries will show salaries. Never pass the agent's own
   service credentials — it acts as the asking user or it does not act.
4. **Build and test entirely on DuckDB first.** Load a representative sample locally, run the
   whole stack on a laptop, and only then point it at the warehouse. In a client with a
   data-residency review this is also what lets engineering start in week one while access
   approvals are still moving.
5. **Gate on a question set, not on vibes.** Fifty to a hundred real business questions with
   known-correct answers, run in CI through deepeval/promptfoo on every change to a metric
   definition or prompt. **Report accuracy against that set, never against a public
   benchmark** — the 6% number above is exactly what happens when a public benchmark is used
   as the estimate.
6. **Let the agent write reports as pull requests.** Point it at Evidence, where a report is
   SQL plus markdown in git. The agent proposes, a human merges. This is the one place in the
   recipe where agent output can safely become a durable artefact, because the review step
   already exists.

### What to tell the client the limits are

- **Quote accuracy only against their own question set.** The dbt Labs April 2026 benchmark
  (semantic layer lifting Claude Sonnet 4.6 from 90.0% to 98.2%, GPT-5.3-Codex from 84.1% to
  100%) is **11 questions on one modelled project, run by a semantic-layer vendor**. It
  supports the architecture; it does not predict their numbers. Use it to justify the design,
  never as a service level.
- **Unmodelled questions must fail loudly.** A question outside the metric set returns "not
  defined" and a route to request it — not a guess. Clients accept a bounded tool; they do not
  forgive a confident wrong number in a board pack.
- **The metric set is the roadmap.** Coverage grows per sprint, and that is the renewable
  engagement — not model tuning.

**Deliverable:** 20–40 signed metric definitions in git, served over MCP with row-level
authorisation, one agent answering against them, a CI accuracy gate on the client's own
questions, and a report surface where agent output lands as a reviewable pull request.

---

## Receta 15 — Entity resolution first, when "customer 360" is the actual ask

**For:** the client who wants an agent to answer "what is this customer's total exposure / open
tickets / lifetime value" and whose customer exists as several different rows in several
different systems. The agent is not the problem here and no amount of prompt work touches it.

**Why this is its own recipe:** Receta 14 makes the agent answer from governed metrics. But a
governed metric computed over unresolved identities is *precisely wrong* — it sums one customer
as three. This step runs **before** the semantic layer, and it is the most defensible scoping
call available in a data-agent engagement.

| Layer | Component | Licence |
|-------|-----------|---------|
| CDC from source systems | [debezium/debezium](https://github.com/debezium/debezium) | Apache-2.0 |
| Pipeline / loading | [dlt-hub/dlt](https://github.com/dlt-hub/dlt) | Apache-2.0 |
| Connector catalogue (alternative) | [meltano/meltano](https://github.com/meltano/meltano) | MIT |
| **Entity resolution** | [moj-analytical-services/splink](https://github.com/moj-analytical-services/splink) | **MIT** |
| Scoped reconciliation (small jobs) | [J535D165/recordlinkage](https://github.com/J535D165/recordlinkage) | BSD-3-Clause |
| Engine | [duckdb/duckdb](https://github.com/duckdb/duckdb) (local / mid-size) or Spark via Splink backends | MIT |
| Table format | [apache/iceberg](https://github.com/apache/iceberg) | Apache-2.0 |
| Lineage / catalog | [datahub-project/datahub](https://github.com/datahub-project/datahub) or [OpenLineage/OpenLineage](https://github.com/OpenLineage/OpenLineage) | Apache-2.0 |
| De-identification for non-production | [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) | MIT |
| Metrics over resolved entities | [cube-js/cube](https://github.com/cube-js/cube) | Apache-2.0 |
| Human adjudication console | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 |

### Wiring

1. **Capture changes, do not poll.** Debezium reads the WAL/binlog of the source systems, so
   the client's production OLTP database takes no added query load — the objection that
   usually kills this work in the DBA review. Land it with dlt.
2. **Resolve identities inside the warehouse with Splink.** Splink runs probabilistic linkage
   against DuckDB, Spark or Athena **where the data already is**. Nothing is extracted to a
   third-party service, which is what gets it through a data-residency or GDPR review — and in
   EMEA engagements that property is worth more than any accuracy delta.
3. **Use the provenance in the room.** Splink is **MIT and built by the UK Ministry of
   Justice**. A government-maintained linkage library is a far easier sell to a regulated
   client's risk committee than a vendor library, and it costs nothing to say so.
4. **Never auto-merge a borderline match.** Splink returns a match probability. Set two
   thresholds: auto-link above the high one, auto-reject below the low one, and route the band
   between them to a human in an Appsmith console. **The adjudication queue is a deliverable,
   not an admission of failure** — it is also where the client's domain knowledge enters, and
   it is what makes the golden record defensible to an auditor.
5. **Emit the golden record as a versioned table, with lineage.** Iceberg snapshots plus
   DataHub/OpenLineage, so "why did this customer's total change last Tuesday" is answerable.
   An unexplainable change in a customer total destroys trust faster than a wrong answer.
6. **De-identify before anything non-production.** Presidio on any extract used for
   development, demos or model evaluation. Entity resolution work concentrates exactly the
   personal data that must not leave the production boundary.
7. **Only now layer Receta 14 on top.** Point Cube's metrics at the resolved entity table, and
   the agent inherits correct identities for free.

### Licence posture

Every component in the table is MIT, BSD-3-Clause or Apache-2.0 — this recipe has **no
copyleft and no source-available dependency**, which is unusual for the data plane and worth
stating in a proposal. The one trap is the obvious alternative:
[zinggAI/zingg](https://github.com/zinggAI/zingg) is the more marketed entity-resolution
project and it is **AGPL-3.0**. Usable as an unmodified separate service behind a process
boundary; not usable linked into software Globant delivers as the client's own.

### Sizing and the milestone to fix

Four to six weeks to a first resolved domain (customers *or* suppliers, never both at once),
measured by three numbers the client picks before work starts: duplicate rate before and
after, adjudication queue volume per week, and the count of source systems reconciled. Fix the
milestone on **"the golden record exists and is explainable,"** not on agent accuracy — the
agent is the next recipe and bundling the two is how this work gets blamed for a model's
behaviour.

**Deliverable:** one resolved entity domain in a versioned table with lineage, an
auto-link/auto-reject/adjudicate pipeline with a staffed queue, and a measured duplicate-rate
delta — the prerequisite that makes "customer 360 agent" a buildable sentence.

---

## Receta 16 — The entitlement boundary: an agent that answers each employee only from what that employee may read

**Added seventh pass, 2026-11-20.** The engagement this unlocks is the one every knowledge-agent
pilot hits on the day it stops being a pilot: it worked on the handbook, so the client connects
SharePoint, and now the agent is a data-leakage incident waiting for the right question.
Receta 2 (knowledge agent) and Receta 14 ("ask our data in English") both assume the retrieved
corpus is safe for the asker. **This recipe is what you build when it is not.**

### The failure mode, stated plainly so it can be sold

An agent indexes a corpus **once**, using the credentials of whoever built the index — then
answers **everyone** out of that single flat index. No attacker, no prompt injection, no model
failure: the retrieval layer was never told who was asking. The client's existing access
controls still work perfectly in SharePoint; they simply were never carried into the vector
store. **Oversharing is the default behaviour of every RAG pipeline that nobody explicitly
made entitlement-aware**, which is why it must be designed in at the start and cannot be
bolted on after the index exists.

### Wiring

| Layer | Component | Licence | Why this one |
|-------|-----------|---------|--------------|
| Permission graph | [authzed/spicedb](https://github.com/authzed/spicedb) **or** [openfga/openfga](https://github.com/openfga/openfga) | Apache-2.0 / Apache-2.0 | Stores the client's entitlements as a *relationship* graph. SpiceDB if the graph is large and checks are hot; OpenFGA if you want the published agent/RAG integration patterns and the Auth0 documentation trail. |
| In-process checks | [apache/casbin](https://github.com/apache/casbin) | Apache-2.0 | When authorization must run inside the app with no network hop, or when the client's core is JVM/.NET — first-party ports exist for both (`apache/casbin-jcasbin`, `apache/casbin-Casbin.NET`). Now ASF-governed. |
| Agent identity | [keycloak/keycloak](https://github.com/keycloak/keycloak) | Apache-2.0 | The user's identity and group memberships, which are the *input* to the permission graph. **Apache-2.0 — do not substitute Zitadel, which is AGPL-3.0.** |
| Delegation | [modelcontextprotocol/ext-auth](https://github.com/modelcontextprotocol/ext-auth) profile | MIT (spec) | Carries the *human* as subject and the agent as actor: SSO → token exchange (RFC 8693) → JWT grant (RFC 7523), with the resource server advertised via Protected Resource Metadata (RFC 9728). |
| Edge auth | [oauth2-proxy/oauth2-proxy](https://github.com/oauth2-proxy/oauth2-proxy) | MIT | Puts real OIDC in front of an agent endpoint that has none, without modifying the agent. |
| Process identity | [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | Already in this KB. Attests that the thing presenting the token is the build you approved. |
| Tool-level policy | [open-policy-agent/opa](https://github.com/open-policy-agent/opa) / [cerbos/cerbos](https://github.com/cerbos/cerbos) | Apache-2.0 | Already in this KB. **Complementary, not redundant:** these decide *which tool* the agent may call; the permission graph decides *which rows and documents* the asker may see. A client who has OPA does **not** have this. |

### Build order — and the order is the deliverable

1. **Mirror the source-system ACLs before embedding anything.** For each connector, pull the
   document's permission set at ingest and write it into the permission graph keyed to the
   document id. This is the expensive, unglamorous 60–70% of the work, exactly as the energy
   KB found that connectors and normalisation — not AI — were 70% of a metering pilot.
2. **Decide pre-filter or post-filter, and write the decision down.** *Pre-filter* resolves the
   asker's authorized document ids first and constrains the vector query to them: safe by
   construction, but the id set can be enormous. *Post-filter* retrieves by similarity and then
   drops what the asker may not see: simple, but it over-fetches and the top-k you asked for is
   not the top-k you get, so recall silently degrades for exactly the users with least access.
   **Default to pre-filter where the store supports constrained search; use post-filter only
   with an over-fetch factor you have measured.**
3. **Enforce at retrieval, never in the prompt.** The permission decision is made by
   deterministic backend code before any content enters the context window. **Do not instruct
   the model to respect permissions** — that is a request, not a control, and it fails under
   paraphrase. This is the same rule the automotive and energy KBs reached from the other
   direction: *model reasoning text never reaches the actuator*; here, *unauthorized text never
   reaches the context*.
4. **Make revocation cheap.** Entitlements change daily. If revoking access requires
   re-embedding, the system is wrong: store ACLs as data the query joins against, so a
   revocation is a row update and takes effect on the next question.
5. **Chunk-level, not just document-level.** Document is the natural unit of permission;
   chunks inherit it. State the limit explicitly, because a single document containing both
   public and restricted sections breaks the inheritance and needs splitting at ingest.
6. **Gate the pilot on a leak test, not an accuracy test.** Build an adversarial set: for each
   restricted document, questions whose answer is only in it, asked as a user without access.
   **The release criterion is zero leaks**, and it is a hard gate — unlike accuracy, which is a
   negotiation. Wire it into the CI gate from Receta 10 so it runs on every change.

### Sizing and the milestone to fix

**4–6 weeks** for one connector with a real ACL model (SharePoint or Drive) against a corpus
the client already trusts, including the adversarial leak suite. **10–14 weeks** for three or
more connectors with differing permission models, group inheritance, and revocation SLAs.

**The milestone to fix before any model work:** *for a named test user, the set of document ids
the retrieval layer will return equals the set that user can open in the source system —
measured, not asserted.* If that set does not reconcile, the agent is not the problem and no
amount of prompt work will fix it.

### Licence posture

Every component above is **Apache-2.0 or MIT**. There is no copyleft and no carve-out in this
build, which is the point: the equivalent capability in the most popular open-source enterprise
search platform sits inside an enterprise-licensed directory
(`verticals/solutions.md`, "Enterprise search & the permission-sync carve-out"). **Avoid in
this layer:** `Permify/permify` (AGPL-3.0, sits on the request path), `osohq/oso` (archived
2026-10-22), `zitadel/zitadel` (AGPL-3.0).

### What to tell the client the limits are

- **This does not make the agent trustworthy, only correctly scoped.** It enforces *who may see
  what*; it says nothing about whether the answer is right.
- **The permission graph is now a production dependency on the critical path of every query.**
  It needs the availability, monitoring and failure design of a database — and it must **fail
  closed**.
- **The ACL mirror is eventually consistent with the source system.** Name the lag and make it
  a number in the SLA. For most clients minutes are fine; for board papers during an
  acquisition, minutes are not.
- **The delegation standard is not finished.** The MCP enterprise-managed authorization profile
  is published stable at revision `2026-07-28`, but the ID-JAG draft underneath it is an
  unfinished IETF Internet-Draft, and this KB could not reach the IETF to verify its state
  (`repos/foundations.md`). Build the delegation step behind an adapter, and do not write a
  standards-compliance promise into a statement of work.

---

---

## Receta 17 — The write boundary: an agent that may change the system of record, and an auditor who can verify it afterwards

**When to use it.** The client has accepted Receta 16's read boundary and the agent now
answers each employee from only what that employee may read. The next request is always
the same: *"can it just do it?"* — post the invoice, raise the PO, close the ticket,
issue the credit. This recipe is the answer that survives an audit.

**Who buys it.** The CFO's organisation and Internal Audit, jointly — not IT alone.
That is unusual for an agent engagement and it is the reason this one closes: the
budget holder and the blocker are the same conversation.

### The failure mode, stated plainly so it can be sold

An agent wired into every step of a workflow **can initiate an action and then execute
its own approval inside a single run.** It is not malicious and it is not a bug; the
agent has both tools, so it uses both. What breaks is **segregation of duties** — the
control that requires the person who raises a transaction to be different from the
person who approves it. SoD is not a best practice in a regulated client; it is a SOX
control, and collapsing it is a material weakness.

Say it to the client in one sentence: **"the moment your agent can both request and
approve, you have not automated a control — you have removed one."**

### The architectural finding that determines the whole design

Read from the MCP specification's own source
([modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol),
`schema/2025-06-18/schema.ts` and `docs/specification/2025-06-18/server/tools.mdx`):

> *"NOTE: all properties in ToolAnnotations are **hints**. They are not guaranteed to
> provide a faithful description of tool behavior… Clients should never make tool use
> decisions based on ToolAnnotations received from untrusted servers."*

> *"For trust & safety and security, clients **MUST** consider tool annotations to be
> untrusted unless they come from trusted servers."*

And the defaults: `readOnlyHint` **false**, `destructiveHint` **true**,
`idempotentHint` **false**, `openWorldHint` **true**.

**So the only protocol-level marker that a tool changes something is a hint the client
is instructed not to trust.** Write-path safety therefore **cannot live in tool
metadata**. `destructiveHint` is good documentation and a sound default-deny input to a
policy decision; it is never the enforcement point. Enforcement has to sit where the
call is mediated, in something the client controls. That is this recipe's spine.

### Wiring

```
                    ┌──────────── the agent ────────────┐
                    │  adk-python / MAF / LangGraph /   │
                    │  dapr-agents  (proposes only)     │
                    └───────────────┬───────────────────┘
                                    │  every write attempt
                                    ▼
  ┌──────────────────── THE ONLY WRITE CHANNEL ────────────────────┐
  │  apache/camel  —  camel-mcp-server publishes camel-ai-tool     │
  │  routes that ALREADY connect to the ERP/CRM                    │
  │   · camel-semantic-wolf-defender  → local prompt-injection     │
  │     inference, in-route, no call out                           │
  │   · the route classifies the operation itself; the server's    │
  │     destructiveHint is recorded, never believed                │
  └───────────────┬────────────────────────────────────────────────┘
                  ▼
  ┌──── DECISION ────┐   open-policy-agent/opa  or  cerbos/cerbos
  │ may THIS user,   │   + openfga/openfga (relationship check from Receta 16)
  │ via THIS agent,  │   authority limits read from the ERP's own
  │ change THIS?     │   authority matrix — never restated in a prompt
  └────────┬─────────┘
           ▼
  ┌──── SoD GATE (in the tool, not the prompt) ────┐
  │  reject if requester_id == approver_id         │
  │  reject if agent identity == approver identity │
  │  spiffe/spire gives the agent its own workload │
  │  identity so it can never BE the approver      │
  └────────┬───────────────────────────────────────┘
           ▼
  ┌──── HUMAN AUTHORISATION ────┐  humanlayer/humanlayer
  │ above the materiality tier  │  (a component, not a convention)
  └────────┬────────────────────┘
           ▼
  ┌──── DURABLE, IDEMPOTENT EXECUTION ────┐
  │ temporalio/temporal | restatedev/restate | dapr/dapr workflow │
  │ idempotency key per business action    │
  │ compensation = an APPROVED REVERSAL in the ERP, never a DELETE │
  └────────┬───────────────────────────────┘
           ▼
  ┌──── EVIDENCE, OUTSIDE THE AGENT'S WRITE BOUNDARY ────┐
  │ complytime/complyctl  → OSCAL + SARIF + EvaluationLog │
  │   providers: OpenSCAP · Ampel · OPA (already in stack)│
  │ oscal-compass/compliance-trestle → the SSP, in CI     │
  │ usnistgov/oscal-cli  → validation gate                │
  │ langfuse/langfuse + openllmetry → the behavioural log │
  └───────────────────────────────────────────────────────┘
```

### Build order — and the order is the deliverable

1. **Inventory the write surface before building anything.** Enumerate every tool the
   agent can reach and classify each one yourself: read-only, additive, destructive,
   idempotent or not. Record the server's declared `destructiveHint` beside your own
   classification. **Where they disagree, your classification wins and the disagreement
   is a finding** — it is the first concrete artefact of the engagement and it is
   usually the moment the client realises how large the surface already is.
2. **Make the integration layer the only write channel.** If the client runs Apache
   Camel, publish the existing routes with `camel-ai-tool` through
   `camel-mcp-server` and **block every other write path at the network layer**. One
   mediated channel is the precondition for every control below it; two channels means
   none. *Check the Camel version first — the unified tool component and the built-in
   MCP server are 4.2x-line features, and the artefact is `camel-mcp-server`, not
   `camel-mcp`.*
3. **Give the agent its own identity, distinct from the user's.** `spiffe/spire` for the
   workload identity, token exchange (Receta 16) to carry the user's identity for the
   *read*. The agent must be structurally incapable of being the approver, and that is
   an identity property, not a policy rule.
4. **Move the authority limits out of the prompt.** Read thresholds from the ERP's
   authority matrix at decision time via OPA or Cerbos. A limit written in a system
   prompt is a suggestion to a language model; a limit read from the authority matrix
   is the client's existing control, reused. **This is the step that converts an agent
   project into an internal-controls project, and it is where the CFO's organisation
   starts paying attention.**
5. **Enforce SoD inside the tool.** `approve_invoice` refuses any call where
   `requester_id == approver_id`, and refuses any call where the approver identity is
   the agent's own — **regardless of what the prompt says, and regardless of what the
   model intended**. Test it with a prompt that explicitly instructs the agent to
   self-approve; the tool must refuse and the refusal must be logged.
6. **Set materiality tiers with the client's auditor in the room.** Small, reversible,
   policy-bounded actions commit autonomously; everything above the tier goes to
   `humanlayer`. The tier is the auditor's number, not Globant's and not the CFO's.
7. **Make execution durable and idempotent.** One idempotency key per business action,
   so a retry after a timeout cannot double-post. Use Temporal, Restate or Dapr
   Workflow. **If Dapr: require v1.17 or later for workflow versioning** — without it,
   a deploy while a write is in flight replays the workflow against changed code, which
   is how a durability mechanism corrupts the transaction it was protecting.
8. **Compensate by reversal, never by deletion.** A wrong posting is corrected with an
   approved reversal in the ERP. Remove delete capability on financial records from the
   agent's tool surface entirely — an agent that can delete a record is not a control
   problem, it is an unauditable system.
9. **Emit evidence into a store the agent cannot write to.** `complyctl` produces OSCAL
   assessment results, SARIF and EvaluationLog; `compliance-trestle` assembles the SSP
   in CI; `oscal-cli` validates it as a merge gate. **The agent's write boundary must
   not include the evidence store.** This is the one hard rule in the recipe.
10. **Only then let the agent author compliance documentation.**
    `oscal-compass/compliance-trestle-mcp` exposes trestle over MCP, so the agent can
    draft control narratives and component definitions. Keep `TRESTLE_MCP_TOOLS` at its
    **default**, which exposes only the authoring lifecycle rather than `all`. Note what
    this means: the maintainers shipped a narrower-than-maximal default tool surface —
    **the write-boundary principle, implemented inside an MCP server by its own
    authors.** Cite it to the client; it is evidence the practice is not a consultancy
    invention.

### Licence posture

| Component | Licence | Verified |
|---|---|---|
| [apache/camel](https://github.com/apache/camel) | Apache-2.0 | 11,357 B `LICENSE.txt`, byte-read 2026-11-21 |
| [dapr/dapr](https://github.com/dapr/dapr) · [dapr/dapr-agents](https://github.com/dapr/dapr-agents) | Apache-2.0 | 11,411 B (`master`) / 11,356 B, byte-read |
| [complytime/complyctl](https://github.com/complytime/complyctl) | Apache-2.0 | 11,342 B, byte-read |
| [oscal-compass/compliance-trestle](https://github.com/oscal-compass/compliance-trestle) · [-mcp](https://github.com/oscal-compass/compliance-trestle-mcp) | Apache-2.0 | 11,357 B each, byte-read |
| [usnistgov/OSCAL](https://github.com/usnistgov/OSCAL) · [oscal-cli](https://github.com/usnistgov/oscal-cli) · [oscal-content](https://github.com/usnistgov/oscal-content) | **worldwide public domain** (GitHub badge: `NOASSERTION`) | `LICENSE.md` byte-read: 5,254 B / 3,540 B / 2,105 B |
| [open-policy-agent/opa](https://github.com/open-policy-agent/opa) · [cerbos/cerbos](https://github.com/cerbos/cerbos) · [openfga/openfga](https://github.com/openfga/openfga) · [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | held from earlier passes, re-verified live |
| [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) · [temporalio/temporal](https://github.com/temporalio/temporal) · [restatedev/restate](https://github.com/restatedev/restate) | per earlier passes — **check `restate`'s BUSL note in `repos/foundations.md` before quoting** | — |

**Every component is permissive**, with one deliberate flag: Restate's licence caveat is
already recorded in this KB and Temporal or Dapr Workflow substitutes for it cleanly.

**Two licence warnings specific to this recipe.** First, the NIST repositories are
**public domain, which is not strictly better than Apache-2.0**: there is no express
patent grant and no warranty disclaimer, so for anything redistributed inside a client
deliverable the `oscal-compass/*` and `complytime/*` Apache-2.0 siblings may be the
better legal choice than the nominally freer NIST original. Second,
**`complytime/complyscribe` is archived** (last push 2026-05-11) although its own
QuickStart documentation still presents it as the CI route — use `complyctl` plus
`complytime-providers`.

### Sizing and the milestone to fix

**Twelve to sixteen weeks.** The fixed milestone, in the contract, at **week six**:

> *A tool that refuses to let the agent approve its own request, demonstrated live
> against a prompt that explicitly instructs it to, with the refusal visible in the
> audit log — and the same action completing successfully when a second human approves
> it.*

That demo is short, it is adversarial, and it is the only thing that moves Internal
Audit from blocker to sponsor. It also fails honestly: if the authority matrix cannot
be read programmatically, week six is when everyone finds out, rather than week
fourteen.

### What to tell the client the limits are

- **This does not make the agent's judgement correct.** It makes every action
  attributable, bounded, reversible and evidenced. The agent will still occasionally
  propose the wrong invoice; the control is that a human approved it and the record
  shows who.
- **There is no audit standard for agent write access to an ERP.** The SoD patterns,
  approval thresholds and audit-trail contents in this recipe come from practitioner,
  vendor and consultancy sources that **converge but are not authoritative**. The
  client's own auditor sets the standard. Say so in the proposal — claiming otherwise
  is the fastest way to lose Internal Audit.
- **OSCAL is a North American artefact.** It is a sound evidence substrate anywhere, and
  it is **not** an EU AI Act Annex IV conformity format — no machine-readable canonical
  format for Annex IV exists. Do not let the OSCAL deliverable be heard as AI Act
  certification in EMEA.
- **If the client has no integration layer, step 2 becomes a project.** This recipe is
  dramatically cheaper where Camel, Conductor or Dapr is already deployed and owned by a
  team with a change process. Where there is none, Receta 1's hand-written MCP server is
  the correct starting point and this recipe follows it rather than replacing it.
- **Materiality tiers drift.** A tier set with the auditor in week three is a control
  that needs re-approval when the business changes. Build the tier as configuration with
  its own approval workflow, not as a constant in code.

## Receta 18 — The provenance boundary: prove the agent's components are the ones that were approved

**The ask, in client words.** *"If a regulator or our board asks in two years' time, can you prove the
model, the tools and the MCP servers behind this decision were the ones we approved — and that nobody
swapped one afterwards?"*

**Why the previous seventeen recipes cannot answer it.** Receta 13 builds an inventory (what we think we
run). Receta 7 scans skills (one tool's opinion, at one moment). Receta 16 proves *who the agent acted
for*; Receta 17 proves *that the action was authorised*. **None of them proves the component is what it
claims to be**, because an inventory is an assertion and a scan is not re-checkable by a third party
later. Provenance is: **signed by an identity, recorded in a log someone else can verify, re-checkable
without trusting whoever made the claim.**

**Precondition — pick the fork honestly in week one, because it determines the whole build.**

| If the client's CI is… | Use | Effort |
|---|---|---|
| GitHub (cloud or Enterprise) | **GitHub artifact attestations** + `gh attestation verify` | Low. This is the cheapest provenance story available anywhere. Do not build what the platform gives away. |
| GitLab, Jenkins, Bitbucket, self-hosted | **`cosign` + `in-toto`/`witness` + `rekor`, assembled** | Real engineering. There is **no drop-in successor named by the SLSA project** — this pass searched and found none. Scope it as a build, and see the EMEA subsection of `intel/market.md`: this is the gap worth selling. |

**Do not plan around `slsa-verifier` or `slsa-github-generator`.** Both READMEs declare, at line 11,
*"This project is no longer actively maintained."* Existing provenance stays valid and the reusable
workflows keep working, but they will not be updated — including for GitHub Actions runtime
deprecations. And quote the migration risk from the generator's own README, because it is the part that
surprises people: **"GitHub artifact attestations are verified with `gh attestation verify` rather than
with slsa-verifier, so migrating changes how your consumers verify."**

### Steps

1. **Sign the model, not just the image.** [`sigstore/model-transparency`](https://github.com/sigstore/model-transparency)
   (Apache-2.0, 250 ★) signs a whole model directory, emitting a Sigstore bundle → DSSE envelope →
   **in-toto statement listing every file as a `(path, digest)` pair**; verification recomputes the
   hashes, so any post-signing edit fails. Keyless OIDC by default; traditional keys and **PKCS#11
   hardware** supported where an HSM is mandated. **This is the only permissive model-signing tool this
   KB has located** — if the client's "AI governance" programme does not cover weights, this step is
   the gap nobody has filled.
2. **Sign the runtime and the tools.** [`cosign`](https://github.com/sigstore/cosign) (Apache-2.0,
   6,468 ★) over the agent's container image and over each MCP server image. **There is no dedicated
   open-source MCP *signing* tool** — the registry proves *namespace ownership*, not artefact
   integrity — so signing the server's image is the available substitute. Say that plainly rather than
   implying a maturity that is not there.
3. **Attest the pipeline steps, reusing two components this KB already holds.**
   [`in-toto/witness`](https://github.com/in-toto/witness) (Apache-2.0, 622 ★) records an attestation
   per build step, signs it **keylessly via Sigstore *or via SPIFFE/SPIRE*** — the workload-identity
   layer already in `repos/foundations.md` — and evaluates an **embedded OPA Rego policy**, the engine
   already used in Recetas 9 and 16 for authorization. **Two existing stack components, each gaining a
   second job.** Add RFC3161 timestamping where an auditor wants wall-clock proof.
4. **Record in a transparency log.** [`rekor`](https://github.com/sigstore/rekor) (Apache-2.0, 1,238 ★)
   is the append-only log that makes a signature checkable by a party who does not trust the signer.
   **This is the step that distinguishes Receta 18 from Receta 7** — without it you have a signature,
   not provenance.
5. **Generate the AI-BOM from artefacts, not from a questionnaire.**
   [`cdxgen`](https://github.com/CycloneDX/cdxgen)'s **`aibom`** command covers **prompt files, AI
   services, MCP configs and model metadata**, accepts Hugging Face purls and direct `Modelfile`/`.gguf`
   inputs — and **submits straight to a Dependency-Track server**. Gotcha from its own page:
   **`--component-type` alone does not enable model discovery.** Pair with
   [`syft`](https://github.com/anchore/syft) (9,957 ★) for the conventional software SBOM.
6. **Close the loop — this is the step that makes it a control rather than a document.**
   [`Dependency-Track`](https://github.com/DependencyTrack/dependency-track) (Apache-2.0, 4,513 ★)
   ingests the BOMs and **re-evaluates them continuously as new advisories land**, raising a policy
   violation on an unapproved model or MCP server. Add [`grype`](https://github.com/anchore/grype)
   (13,339 ★) in CI for the fast fail, and [`vexctl`](https://github.com/openvex/vexctl) (222 ★) to mark
   present-but-not-exploitable findings — **without VEX a 4,000-finding report is politically unusable
   and gets switched off**, which is how these programmes actually die.
7. **Add the cross-system graph only when a question demands it.**
   [`guac`](https://github.com/guacsec/guac) (Apache-2.0, 1,581 ★) ingests SBOMs **and** attestations
   (CycloneDX, SPDX, in-toto ITE6, DSSE, SLSA, CSAF/OpenVEX) into one queryable graph — the only tool
   located that answers *"which deployed agents contain this component?"* **Scope it as investigative,
   not authoritative:** its own page states identifiers are often absent, so linking is **heuristic**
   and ingestion errors occur.
8. **Translate formats at the boundary, not throughout.**
   [`protobom`](https://github.com/protobom/protobom) (Apache-2.0, 339 ★) converts **SPDX 2.2/2.3/3.0.1
   ↔ CycloneDX 1.2–1.7**. Since CISA's 2026 elements dropped SWID, SPDX↔CycloneDX is **the only
   remaining axis of format disagreement** — one converter at the auditor-facing edge, not a
   format debate in every pipeline. (`bomctl` does the same job and its `main` has not moved since
   2025-09-10 — do not pick it.)

### The air-gap work package, measured rather than assumed

For a sovereign, air-gapped or egress-filtered estate — the EMEA and APAC case — **budget this
explicitly**:

```
$ gh attestation trusted-root
tuf refresh failed: Get "https://tuf-repo-cdn.sigstore.dev/14.root.json": Forbidden
exit=1, 0 bytes written
```

The documented offline path is *fetch `trusted_root.jsonl` once, then verify with
`--custom-trusted-root`*. **The root can be used offline but not obtained offline.** So:
allowlist `tuf-repo-cdn.sigstore.dev` from one permitted host, pin the root, ship it inward as a
controlled artefact, and **give its refresh an owner** — verification fails closed, which is correct
behaviour and means a forgotten refresh is an outage, not a warning. Keyless OIDC signing has the same
shape: it needs an identity provider reachable at signing time, so in a fully disconnected enclave fall
back to `model-transparency`'s **PKCS#11** path with a local HSM.

### Deliverables and the sentence that sells it

A signed model and image per release; a per-step attestation chain; an AI-BOM in the client's existing
component-analysis platform; a standing policy that fails a deploy when an unapproved model or MCP
server appears; and a one-page runbook for *"prove this artefact was approved"* that a non-engineer can
execute.

**The sentence:** *CISA's 2026 minimum elements make the component **hash** a required field. A hash can
only come from the artefact itself — so an inventory assembled from spreadsheets and vendor
questionnaires cannot produce one, no matter how complete it looks.* That single field is what turns an
AI-BOM from a documentation exercise into a pipeline engagement, and it is the honest reason this work
cannot be done cheaply by someone else.

---

## Receta 19 — Admission control for MCP servers: decide what may join the estate, before it holds a credential

**The ask.** *"Our developers are adding MCP servers weekly. How do we stop an unvetted one from
reaching production data — without becoming the team that says no to everything?"*

**The design principle, and it is the whole recipe.** The `agents/top.md` skill-supply-chain layer
scans servers **at runtime or on a developer's machine**. That is too late: **by the time a server runs,
it has already been handed a credential.** Copy the shape of
[`agentic-community/mcp-gateway-registry`](https://github.com/agentic-community/mcp-gateway-registry)
(Apache-2.0, 1,057 ★), which scans **at registration** and holds unsafe servers, agents and skills for
review. **Admission control, not inspection.**

### Steps

1. **Establish publisher identity.** Run a registry with **namespace-ownership verification**.
   [`modelcontextprotocol/registry`](https://github.com/modelcontextprotocol/registry) (7,496 ★)
   validates via **GitHub OAuth, GitHub OIDC, DNS and HTTP verification**. **DNS verification is the
   real primitive**: it is the difference between "a server named `acme-crm`" and "a server published by
   whoever controls `acme.com`". Two caveats to state up front: it is **a preview release, not GA**
   (API frozen at v0.1 pending v1), and its licence is a **per-contribution MIT/Apache-2.0 mixture**
   mid-transition — both permissive, so buildable, but never describe it as simply "Apache-2.0".
2. **Mirror internally; never allow direct pulls.** Same rule this KB already applies to `clawhub`.
   The registry entry a developer installs from must be one the enterprise admitted.
3. **Scan at registration, and choose the scanner on *architecture*, not licence.** This is where the
   recipe earns its money:
   - [`cisco-ai-defense/mcp-scanner`](https://github.com/cisco-ai-defense/mcp-scanner) (Apache-2.0,
     1,125 ★) — **YARA, readiness, prompt-defense, static-JSON and vulnerable-package analyzers need no
     API key**, and the LLM analyzer accepts a **local endpoint such as Ollama**. The Cisco key is
     needed only for the API analyzer. **The option that works for a sovereign client.**
   - [`snyk/agent-scan`](https://github.com/snyk/agent-scan) (Apache-2.0, 3,276 ★) — broader coverage
     (agents, MCP servers **and skills**), but **requires `SNYK_TOKEN` before any scan**, the free tier
     has a **daily usage limit**, and the analysis runs **vendor-side**. Formerly
     `invariantlabs-ai/mcp-scan`; both paths still resolve to the identical HEAD sha.
   - **Pin by registry and version in the pipeline definition**: `uvx snyk-agent-scan@<version>`.
     `uvx mcp-scan` resolves through a redirect shim and **`npx mcp-scan` is a different owner's
     package entirely** — the project's own README says there is no npm package.
4. **Sandbox the scan itself — the step most teams miss.** Reading an MCP server's tool descriptions
   means **executing the commands in its config** and calling remote URLs **with their configured
   headers**, i.e. the client's own credentials. `snyk/agent-scan` blocks link-local and cloud-metadata
   destinations (`169.254.0.0/16`, `fe80::/10`, `fd00:ec2::254`, `100.100.100.200`), refuses redirects,
   validates DNS per request — and **declares a residual DNS-rebinding window**. So: run registration
   scans in a **disposable container with no production credentials and egress limited to what the
   candidate server legitimately needs**, and never pass `--dangerously-run-mcp-servers` outside it.
   *Treat the registration scanner as a workload that handles untrusted input, because it is one.*
5. **Enforce at runtime.** [`stacklok/toolhive`](https://github.com/stacklok/toolhive) (Apache-2.0,
   2,355 ★) runs and manages MCP servers — the point where a server that failed admission is actually
   **refused** rather than merely flagged. Wire the agent's per-call middleware
   (`NeMo-Relay` in `repos/foundations.md`) so an OPA/Cerbos decision is **enforced per tool call**,
   not logged after it.
6. **Record the admission decision as evidence, reusing Receta 17's machinery.** Emit each decision as
   an attestation via `witness` (step 3 of Receta 18) and feed the resulting component into
   Dependency-Track. **This is what makes the registry auditable instead of merely restrictive**, and
   it is why Recetas 18 and 19 are sold together.

### The contractual deliverable worth borrowing from a dead project

[`NimbleBrainInc/mpak`](https://github.com/NimbleBrainInc/mpak) was **archived by its owner on
2026-11-23**, the day before this pass, and must not be built on. But its **L1–L4 trust ladder —
Basic / Standard / Verified / Attested**, each level a fixed set of controls with the score being the
share that pass — is the clearest articulation of this layer's maturity model found anywhere, and it is
**exactly what a client needs when they ask what "trusted MCP server" should mean in a contract.**
Borrow the ladder as a design reference; implement it on the live components above.

**Define the tiers in the client's own words, then attach controls:** L1 identified, L2 scanned,
L3 publisher-verified (DNS/OIDC), L4 signed and attested with a verifiable chain. **Only L4 answers
Receta 18's question**, and most estates can reach L3 in a quarter — which makes it a credible roadmap
rather than a counsel of perfection.

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

**New anti-patterns, fifth pass 2026-11-20 — each observed in this pass's evidence:**

- **Shipping a chat window and calling it an agent deployment.** Three of the layer's
  best-known chat shells are archived while every live project renders into the host
  application. If the user has to navigate somewhere to talk to the agent, adoption is the
  risk, not capability.
- **Letting renderer vocabulary into the agent's prompts or reasoning.** Four competing
  permissive UI standards, no foundation steward. Renderer-specific output means the next
  standards decision becomes an agent rewrite.
- **Letting an agent emit arbitrary markup into an internal application.** That is a
  prompt-injection path to an employee's screen. The client application holds the component
  catalog; the agent requests from it.
- **Reading `main/LICENSE` and stopping.** `paperclipai/paperclip` (115,408 ★) keeps its
  licence on `master`. The full probe order is manifest → `LICENSE` → `.md`/`.txt` →
  `LICENSE-MIT` → `LICENSE-APACHE` → `COPYING`, across `main` **and** `master`.
- **Trusting GitHub's licence badge.** `humanlayer/12-factor-agents` (27,343 ★) reports
  `NOASSERTION` and is unmodified Apache-2.0. Conversely `restatedev/restate` reports
  `NOASSERTION` and is **BUSL-1.1** — not open source. The badge is a hint either way; the
  file is the answer, and the error is expensive in both directions.
- **Selling governance before the inventory exists.** Every governance recipe in this file
  assumes a list of what runs. If the client cannot produce that list, Receta 13 is the first
  engagement, not an add-on to the fourth.
- **Treating a stale README as a live project.** None of the three archived repositories says
  it is archived. Check the API's `archived` flag and the last push date for every dependency
  you put in a proposal.
- **Letting `destructiveHint` be a security control.** The MCP specification says clients
  **MUST** consider tool annotations untrusted unless they come from trusted servers, and
  its schema says all `ToolAnnotations` properties are *hints* that may not faithfully
  describe behaviour. Classify the write surface yourself and enforce at the mediation
  point. A vendor claiming their platform "respects MCP tool annotations" has described
  documentation as a control. (Eighth pass.)
- **Giving the agent write access to its own evidence store.** `compliance-trestle-mcp`
  makes it genuinely useful for an agent to author control documentation — which means the
  evidence store must sit **outside** the agent's write boundary, or the audit trail is
  self-certified. Useful and self-certifying are one configuration apart. (Eighth pass.)
- **Automating an approval instead of automating the work.** An agent that can both request
  and approve has not automated a control, it has removed one. Segregation of duties is a
  SOX control in a regulated client; collapsing it is a material weakness, not an
  efficiency. Enforce `requester_id != approver_id` in the tool, and prove it with a prompt
  that explicitly instructs the agent to self-approve. (Eighth pass.)
- **Deleting to fix a wrong write.** Corrections to a system of record are approved
  reversals. Remove delete capability on financial records from the agent's tool surface
  entirely. (Eighth pass.)
- **Reading `NOASSERTION` as a restriction.** Four repositories this pass carried the badge
  and were permissive: three NIST repos are **worldwide public domain** and
  `Tencent/LoopForge` is **MIT** behind a corporate preamble. `NOASSERTION` is the absence
  of a verdict, not a verdict — resolve it by byte-read **in both directions**. Treating it
  as a hard exclusion hid the entire NIST compliance stack from this KB for seven passes.
  (Eighth pass.)
- **Composing a repository slug from an org name.** `complytime/complytime` has 1 star and
  holds design proposals; the product is `complytime/complyctl` at 38 ★. List the org and
  read the descriptions. (Eighth pass.)
- **Quoting a dependency coordinate from a release blog.** Apache's own blog names the Camel
  MCP component "camel-mcp"; the tree contains `camel-mcp-server`. The same manifest read
  revealed `camel-a2a`, which no blog mentioned at all. Read the build file, not the
  announcement. (Eighth pass.)
- **Specifying an install by bare tool name.** `uvx mcp-scan` and `npx mcp-scan` install
  **different vendors' software**: PyPI `mcp-scan` is a redirect shim to `snyk-agent-scan`, while
  npm `mcp-scan` is an unrelated owner's MIT package, and the official project's README states there
  is no npm package. Name the registry and pin the version — `uvx snyk-agent-scan@<version>`.
  (Ninth pass.)
- **Reading maintenance status from the repository page alone.** `slsa-verifier` and
  `slsa-github-generator` are **not archived**, carry recent tags and look active — and both READMEs
  say at line 11 *"no longer actively maintained."* Seven earlier passes learned the opposite failure
  (archived, README silent). **Read both sources, every time.** (Ninth pass.)
- **Cloning a provenance tool without naming the branch.** `slsa-verifier`'s default `HEAD` resolves
  to `refs/heads/Hayden-IO-patch-1`, a personal patch branch at a different sha from `main`;
  `in-toto/in-toto` defaults to `develop`. Use `git ls-remote --symref` to learn the real default, then
  clone `--branch` explicitly or install the released binary. (Ninth pass.)
- **Reading "Apache-2.0" as "we can run it ourselves."** `snyk/agent-scan` is Apache-2.0 and will not
  scan without a vendor token, a network call and a daily quota. **Licence governs redistribution;
  it says nothing about whether the capability is local.** For a sovereign client, check the
  architecture before the licence. (Ninth pass.)
- **Promising air-gapped verification without costing the trust root.** `gh attestation trusted-root`
  fails closed in an egress-filtered network (`tuf-repo-cdn.sigstore.dev`, Forbidden, exit 1). The
  Sigstore root can be *used* offline but not *obtained* offline — allowlist it once, pin it, and give
  its refresh an owner. (Ninth pass.)
- **Running a registration scan with production credentials.** Reading an MCP server's tool
  descriptions **executes the commands in its config** and calls remote URLs **with their configured
  headers**. Even the best tool in this layer documents a residual DNS-rebinding window. Scan in a
  disposable container with no production secrets. (Ninth pass.)
- **Claiming one SPDX licence for a whole GitHub organisation.** `modelcontextprotocol/registry`,
  `/modelcontextprotocol` and `/servers` carry a MIT→Apache-2.0 **transition** notice under which
  non-consenting contributions **stay MIT**, while `/python-sdk` is still plain MIT. Record licences
  per repository and per date. (Ninth pass.)
- **Shipping an SBOM assembled from questionnaires.** CISA's 2026 minimum elements make the
  **component hash** a required field, and a hash can only come from the artefact. A complete-looking
  inventory built from spreadsheets cannot satisfy it. (Ninth pass.)
- **Turning on a scanner without VEX.** A 4,000-finding SBOM report with no way to mark
  present-but-not-exploitable gets switched off within a month. Budget `vexctl` as part of the
  rollout, not as a later improvement. (Ninth pass.)

---

## Receta 20 — The containment boundary: an agent that cannot reach what it was not allowed to reach, and a log that proves it

**The engagement this closes.** The client has a working agent pilot (Receta 2, 4 or 12) that has
passed functional review and is stuck at the platform/security gate. The question that stopped it is
not *can it answer* or *may this user see this document* — those are Recetas 2 and 16. It is
**"what can this process reach, and what stops it?"** This recipe is the four controls that answer
it, built on components that are CNCF-graduated rather than on the one repository that already
composes them.

### The failure mode, stated plainly so it can be sold

Three sources, each describing the limit of its own control:

- A **hook-level guardrail** governs *"the commands the agent requests, not the side effects those
  commands produce at runtime"* — [falcosecurity/prempti](https://github.com/falcosecurity/prempti)'s
  own README, which also states it is *"not a sandbox, OS-level security, or a substitute for
  least-privilege environments."*
- **Kernel isolation** — gVisor, a microVM — does not *"automatically deny outbound network access
  or enforce business permissions"* (Vercel's comparison).
- The **July 2026 incident class** reviewed by the Cloud Security Alliance in October 2026: **no
  sandbox was technically broken.** An agent **wrote a file that a trusted, unsandboxed component
  later executed.**

**So the design question is not "is it sandboxed?" but "what reads what the agent writes, and is
that reader inside the boundary?"** A sandbox whose output directory is consumed by an unsandboxed
CI runner, indexer or deploy hook has its boundary in the wrong place. Ask for the list of consumers
of the agent's output in the first workshop; it is usually the finding that justifies the project.

### The architecture to copy, and the repository not to depend on

[Azure/kars](https://github.com/Azure/kars) (MIT, 46 ★) is the only verified repo implementing all
four controls: hardened per-agent sandboxes, **governed egress** (L7 allow/blocklist plus an
`egress-guard` **iptables init container** as a safety net), **tool governance** (a `ToolPolicy` CRD
and an MCP gateway with per-tool allowlists) and **audit** (every router decision in a **SHA-256
hash-chained** log). It also names **OpenClaw** and **Hermes** among its eight supported runtimes,
so it already speaks this KB's agent inventory.

**Read it; do not ship it.** Its README says *"Not an officially supported Microsoft product"*, an
*"open-source reference implementation"* with no SLA, and its CRDs are at **`v1alpha1`**. It states
it *aims to align* with `kubernetes-sigs/agent-sandbox` and `agentgateway` and that **no formal
integration exists yet**. The four shapes below are its shapes, rebuilt on graduated components.

### Wiring

```
                      ┌──────────────── Kyverno / Gatekeeper (admission) ────────────────┐
                      │  no agent pod admitted without: RuntimeClass + default-deny      │
                      │  egress policy + required labels + signed image (cosign)         │
                      └──────────────────────────────┬──────────────────────────────────┘
                                                     │ (3) ADMIT
   ┌─────────────────────────────────────────────────▼─────────────────────────────────────┐
   │  kubernetes-sigs/agent-sandbox   Sandbox / SandboxTemplate / SandboxClaim             │
   │                                  SandboxWarmPool   (agents.x-k8s.io/v1beta1, v1.0.2)  │
   │  ┌──────────────────────────────────────────────────────────────────────────────────┐ │
   │  │ RuntimeClass → google/gvisor  (no hardware virt needed)                          │ │
   │  │              or kata-containers / firecracker  (own guest kernel)                │ │
   │  │                                                                                  │ │
   │  │   agent runtime (OpenClaw / LangGraph / Claude Agent SDK / MAF / ADK …)          │ │
   │  │        │                                                                         │ │
   │  │        │ (1) hook fires BEFORE each tool call                                    │ │
   │  │        ▼                                                                         │ │
   │  │   prempti interceptor ──unix socket──► Falco plugin ──► allow / deny / ask       │ │
   │  └────────┬─────────────────────────────────────────────────────────────────────────┘ │
   │           │ all egress                                                                │
   └───────────┼───────────────────────────────────────────────────────────────────────────┘
               │ (2) cilium default-deny + CiliumEgressGatewayPolicy  → fixed exit IP
               │     + egress-guard iptables init container (belt and braces)
               ▼
   ┌──────────────────────────────────────────────────────────────────────────────────────┐
   │  agentgateway / litellm / bifrost  — the ONLY reachable destination                   │
   │  LLM + MCP + A2A gateway: per-tool allowlist, guardrails, auth/RBAC, cost attribution │
   └───────────────────────────┬──────────────────────────────────────────────────────────┘
                               │ model APIs, MCP servers, tools (each explicitly allowlisted)
                               ▼
   ┌──────────────────────────────────────────────────────────────────────────────────────┐
   │  (4) falco + tetragon (syscall/eBPF detection & enforcement) · tracee (forensics)     │
   │      → hash-chained decision log → OSCAL evidence via complyctl  (NA engagements)     │
   └──────────────────────────────────────────────────────────────────────────────────────┘
```

**The load-bearing idea:** the AI gateway has been in this KB since early passes as the place where
agent traffic is inspected. **It is only an enforcement point if the sandbox cannot route around
it.** Control (2) is what converts the gateway from a convention into a boundary. Without it, the
gateway is a well-instrumented suggestion.

### Build order — and the order is the deliverable

1. **Measure before you restrict (days 1–5).** Run the existing pilot agent with
   [mitmproxy/mitmproxy](https://github.com/mitmproxy/mitmproxy) (MIT) in front of it and
   `falco`/`tetragon` in **observe-only** mode. Produce two lists: **every destination it actually
   reached** and **every tool call it actually made**. Enforcing a policy you have not measured
   takes down legitimate work — this is the same two-phase rule the KB already applies to OPA and
   Tetragon, and it is non-negotiable here because an agent's destination set is emergent.
2. **Isolate (days 5–10).** Install a `RuntimeClass`. Use **gVisor** unless the client controls
   nodes and needs a separate guest kernel, then **Kata** or **Firecracker**. Wrap the agent in a
   `Sandbox` from [kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox),
   pinned to **`v1.0.2`** as its README recommends for GitOps. Add a `SandboxWarmPool` **in this
   step, not later** — it is what makes per-task isolation affordable, and retrofitting it changes
   the `SandboxClaim` flow.
3. **Contain the network (days 10–18).** Default-deny egress. Allow exactly the destinations from
   step 1, and route them through a **Cilium egress gateway** so the estate has a **fixed exit IP**
   that upstream systems can allowlist in turn. Add the **`egress-guard` iptables init container**
   pattern from `Azure/kars` as a second layer — belt and braces is appropriate here because a CNI
   policy misapplied is an open path, silently. **Verify the two destinations that matter most are
   blocked: the cloud node metadata endpoint and internal cluster IPs.** Do not assume a default
   does this (see the unverified note in `repos/foundations.md`); prove it with a probe from inside
   the sandbox and keep the probe as a regression test.
4. **Intercept the intent (days 18–24).** Attach a hook-level guardrail on the agent's hook API,
   in `monitor` mode, with rules built from step 1's tool-call list; then switch to `guardrails`.
   Implement the **pattern** from [falcosecurity/prempti](https://github.com/falcosecurity/prempti)
   rather than shipping it — it is an **"Experimental Preview"** at 234 ★ and was last pushed
   **2026-09-21**. The reusable asset is that **Falco rules** work here, so the client's existing
   Kubernetes detection content applies to agent tool calls.
5. **Admit nothing uncontrolled (days 24–30).** Kyverno (or Gatekeeper, if the client already runs
   OPA — and they probably do; it has been in this KB for passes as a policy engine) enforcing:
   no agent pod without a `RuntimeClass`, without a default-deny egress policy, without required
   labels, and — composing pass 9 — without a **cosign**-verified image. This step is what stops the
   whole build decaying the first time someone is in a hurry.
6. **Prove it (days 30–35).** Emit a **hash-chained log of every policy decision**, and for North
   American engagements map each control to SP 800-53 and emit **OSCAL** via `complyctl` from
   pass 8. For EMEA, map the same controls to the Cloud and AI Development Act's four assurance
   levels (`intel/market.md`). For Brazil, the hash-chained log **is** the deliverable — it is
   defensible against regulation still in drafting.

### Licence posture

| Component | Licence | Note for the client's SBOM |
|---|---|---|
| `kubernetes-sigs/agent-sandbox` | Apache-2.0 (byte-read) | Kubernetes SIG Apps subproject. **Not CNCF** — do not write CNCF next to it |
| `google/gvisor` | Apache-2.0 (byte-read) | Star count is a page figure only; the search API returns 422 for this repo |
| `firecracker-microvm/firecracker`, `kata-containers/kata-containers` | Apache-2.0 | — |
| `cilium/cilium`, `cilium/tetragon` | **Apache-2.0 user space; BPF templates dual GPL-2.0-only / BSD-2-Clause "at your option"** | **Elect BSD-2-Clause and record the election.** The badge says Apache-2.0 and is correct but incomplete; the artefact you ship is not licensed by the repository page |
| `kyverno/kyverno` | Apache-2.0 | **CNCF Incubating** per its own README, not graduated — a 2026 blog says otherwise and is wrong |
| `falcosecurity/falco`, `open-policy-agent/gatekeeper`, `aquasecurity/tracee`, `agentgateway/agentgateway`, `envoyproxy/gateway` | Apache-2.0 | Falco and Cilium are CNCF **Graduated**; agentgateway is a **Linux Foundation** project |
| `falcosecurity/prempti` | Apache-2.0 | **Experimental Preview**, 234 ★, idle since 2026-09-21 — pattern, not dependency |
| `mitmproxy/mitmproxy` | MIT | Lab instrument for step 1; **remove it from the estate before go-live** |
| `Azure/kars`, `microsoft/agent-governance-toolkit` | MIT | kars is `v1alpha1` and explicitly **not a supported product** — architecture reference only |

**Nothing in this recipe is copyleft in the shipped artefact, and nothing is source-available.** The
one place that needed resolving (Cilium's BPF templates) resolves permissively *by election*.

### Sizing and the milestone to fix

**Six to seven weeks** for a single agent workload on an existing cluster with a capable CNI; **ten
to twelve** if a node pool has to be added for a `RuntimeClass`, or the CNI cannot express egress
policy and has to be changed — **and a CNI migration is its own project, so quote it separately or
not at all.**

**Fix the milestone at the end of step 3, not at the end of the build.** The deliverable that proves
the engagement is a **two-page before/after**: the destination list the agent reached when
unrestricted (step 1), the destination list it can reach now, and a **failed probe to the node
metadata endpoint**. That artefact passes a security review on its own and is worth more to the
client than the remaining three steps combined — which is exactly why it should be billed before
them.

### What to tell the client the limits are

- **This stops exfiltration to places you did not allow. It does not stop exfiltration to places
  you did.** If the agent may reach the model API, the model API is an egress path, and the control
  for *that* is payload inspection at the gateway (`presidio` from pass 4), not network policy.
  **Destination control and payload control are two components with two policy languages, and
  nothing found unifies them** — that is a stated gap, not an oversight.
- **Hook-level interception sees requests, not effects.** It cannot see what a command does once it
  runs; that is what `falco`/`tetragon` are for, and even they see syscalls rather than intent.
- **The write-then-execute path is the one that actually bit people in July 2026.** Enumerate the
  consumers of the agent's output and bring them inside the boundary, or accept the risk explicitly
  in writing. No control in this recipe addresses a trusted reader outside the boundary.
- **`SandboxWarmPool` reduces cold start; it does not make isolation free.** gVisor's Sentry and
  Kata's guest kernel both add measurable memory and CPU overhead per sandbox. Size the node pool
  with real numbers from step 2, and for APAC engagements quote **cost per sandboxed task** rather
  than controls implemented — only 28% of APAC enterprises report AI is value-positive today.
- **Falco and Tetragon are detection engineering, not installs.** One practitioner estimate puts a
  realistic rollout at **two to three FTE of detection engineering**, and Falco's overhead scales
  with syscall volume. If the client will not staff rule maintenance, deliver step 4 in `monitor`
  mode and say so, rather than handing over an enforcement posture nobody will tune.

### Anti-patterns — each observed in this pass's evidence

- **Quoting `Azure/kars` as the solution.** It is MIT, complete and 46 stars with `v1alpha1` CRDs and
  no support. Copy the architecture; name graduated components in the proposal.
- **Writing "CNCF" next to Agent Sandbox.** Google's own announcement is future tense: *"building
  Agent Sandbox as a CNCF project."* It is a SIG Apps subproject.
- **Writing "graduated" next to Kyverno** because a 2026 roundup said so. Its README says Incubating.
- **Taking a repo from a web search without reading the "forked from" line.**
  `grosser/agent-sandbox` has 0 stars, an Apache-2.0 badge and a README whose first line is
  byte-identical to upstream's — and the search API cannot warn you, because it excludes forks.
- **Enforcing before measuring.** A default-deny egress policy written from an architecture diagram
  rather than from observed traffic will break the pilot and burn the mandate.
- **Treating the AI gateway as a boundary without egress control.** It is a boundary only when the
  sandbox cannot route around it.
- **Assuming a secure default.** The claim that sandboxes block node metadata and internal cluster
  IPs by default is **secondary-sourced and unverified in this session**. Probe it; keep the probe.

## Receta 21 — The air-gapped agent platform: take the method, leave the payload

**The ask, in the client's words.** *"We need agents, and nothing may call out to the internet."*
Defence, public sector, banking cores, pharma manufacturing and any EMEA client reading the EU AI
Act's high-risk obligations as a hosting constraint all arrive at this sentence. Until this pass the
KB's answer was a described pattern. It is now a **runnable, pinned reference** plus a licence line
that decides how to use it.

### The source, and the licence split that defines the engagement

| Component | Repo | Licence | Verified |
|---|---|---|---|
| The IaC and the runbooks | [gitlab-com/public-sector/offline-lab](https://gitlab.com/gitlab-com/public-sector/offline-lab) | **MIT** | 4★, active 2026-11-24 |
| The AI Gateway it deploys | [gitlab-org/modelops/applied-ml/code-suggestions/ai-assist](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist) | **GitLab EE licence** (byte-read) | 64★, active 2026-11-24 |
| The context graph it deploys | [gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph) | **GitLab EE licence** (byte-read) | 58★, active 2026-11-24 |
| The model boundary in its topology | [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT — already held in this KB | — |

> **The rule that makes this recipe safe: take the method, not the payload.** The *method* — the
> mirror list, digest pinning, internal-CA-on-every-hop, and the placement of LiteLLM as the model
> boundary — is MIT and transfers to **any** self-hosted agent platform. The *payload* is two
> EE-licensed services and deploying them is a licence purchase, not an integration. Build the first.
> Quote the second only if the client already owns GitLab Ultimate seats.

### Steps

1. **Write the mirror list before writing any Terraform.** `offline-lab`'s air-gapped track states
   its own purpose: it *"owns the canonical list of external dependencies you must mirror
   internally."* Reproduce that artefact for the client's chosen stack. It is the deliverable the
   client cannot get anywhere else, it is readable by their security team, and it is billable on day
   one.
2. **Pin every image by tag *and* digest**, in one file, the way `ansible/group_vars/all/versions.yml`
   does. The runbook's own sentence is the one to put in the proposal: *"an air-gapped mirror plus a
   moving tag cannot be reproduced."* This is the ninth pass's provenance boundary arriving from the
   deployment side — same primitive, different motive, and it closes the gap where a mirror silently
   drifts from what was approved.
3. **Place the model boundary at LiteLLM, not at the agent.** In the reference topology the path is
   `platform → AI gateway → LiteLLM → Bedrock`. Swap the last hop for the client's on-premise
   inference and **nothing upstream changes**. That single property is why the model boundary belongs
   at a proxy the client controls: the air-gap decision becomes a configuration change rather than an
   architecture change.
4. **Mirror the agentic flow as one image, not two.** Verified from the runbook: the AI Gateway image
   *"includes the Duo Workflow service as a sub-process — mirroring this one image covers agentic
   flows; there is no separate workflow image."* Teams routinely budget for a workflow service that
   does not exist as a separate artefact. *(This fact is specific to GitLab's packaging; re-verify it
   for whatever platform the client runs — the transferable lesson is **enumerate what is inside each
   image**, because the unit of mirroring is the image, not the service.)*
5. **Budget the scanners separately.** The runbook sends security scanners (SAST, Secret Detection,
   IaC, Dependency, Container) to their own document because they need **extra images plus a Package
   Metadata Database**. An air-gapped estate without the metadata DB has scanners that run and find
   nothing — the worst possible failure mode, because it looks like success.
6. **Wrap it in the four boundaries already in this KB.** Entitlement (Receta 16), write (17),
   provenance (18), containment (20). The air gap is a *perimeter*; it does not answer who the agent
   acts for or what it may change. A client who believes the air gap is the security model should be
   corrected early and in writing.
7. **State the bootstrap.** `offline-lab`'s README says *"the default topology calls a hosted model
   provider; the air-gapped runbook is `docs/runbook/tracks/air-gapped.md`."* **The air gap is a
   separate track with its own bootstrap** — third independent confirmation of this KB's standing
   rule. Never let "offline" appear in a proposal as a default.

### Deliverables, and the sentence that sells it

Four artefacts: **the mirror bill of materials**, **the pinned version manifest**, **the internal-CA
TLS topology**, and **the model-boundary swap procedure**. Then:

> *"Your agents can run with no egress, and we can prove which bytes are inside the perimeter and
> which version of each one. The proof is a file your auditor can read, not a diagram."*

### Anti-patterns, each visible in this pass's evidence

- **Deploying the vendor's agent stack because the IaC was MIT.** The IaC is MIT; the AI Gateway and
  Orbit are EE-licensed and require paid seats. Reading one `LICENSE` and assuming the repository's
  whole output is permissive is exactly the error this pass documents twice.
- **Mirroring with moving tags.** Explicitly called out upstream as non-reproducible.
- **Selling "air-gapped" as the default topology.** It is a distinct track, everywhere, always.
- **Treating the perimeter as the security model.** It is one of five controls, and the only one a
  client can see — which is why it gets over-bought.
- **Assuming a separate workflow image exists.** Verified false for this platform; enumerate images
  rather than inferring them from service names.

---

## Receta 22 — The client's OpenAPI catalogue as the agent's tool surface, and CI as the first place to contain it

**The ask.** *"We want an agent that can actually do things in our systems, and we are not writing
forty integrations."* Every enterprise client of any size already owns an **OpenAPI catalogue** —
usually in an API gateway, usually complete, usually unloved. It is the cheapest agent tool surface in
the estate and it is already governed, versioned and authenticated.

### Components, all permissive, all verified 2026-11-24

| Role | Repo | Licence | Notes |
|---|---|---|---|
| OpenAPI → MCP tools | [lx-industries/rmcp-openapi](https://gitlab.com/lx-industries/rmcp-openapi) | **MIT** | 13★, active 2026-11-24. Built on the **official Rust MCP SDK** |
| HTTP transport | [lx-industries/rmcp-actix-web](https://gitlab.com/lx-industries/rmcp-actix-web) | **MIT** | 6★, active 2026-11-23 |
| The same idea in Java, for a JVM estate | [apache/camel](https://github.com/apache/camel) — `camel-ai-tool` | Apache-2.0 | Already held (eighth pass): one route = one tool |
| Containment for the CI path | [nagyv/gitlab-opencode](https://gitlab.com/nagyv/gitlab-opencode) | **MIT** | 59★. Any LLM in GitLab CI *"with a controlled environment"* and explicit tool permissions |
| The forge itself, if self-hosted | [gitlab-org/gitlab](https://gitlab.com/gitlab-org/gitlab) | **MIT** | 6,209★ |

### Wiring

1. **Export the subset, never the catalogue.** Point `rmcp-openapi` at a **hand-picked** set of
   operations. An agent handed 400 endpoints will choose badly; an agent handed nine will be
   demonstrably useful. The selection is a workshop with the client's API owners and it is the first
   billable artefact.
2. **Let the spec carry the safety metadata, and do not trust it.** The MCP annotation rule this KB
   established in the eighth pass still governs: tool annotations are **hints**, clients must treat
   them as **untrusted**, and the defaults make an unannotated tool a *non-idempotent, destructive,
   open-world* operation. So read/write classification is decided **at the gateway**, by which
   operations you exported, not by metadata the agent can read.
3. **Choose the transport by estate, not by preference.** Rust (`rmcp-actix-web`) where there is a
   platform team and latency matters; `camel-ai-tool` where the client already runs Camel, because
   then one route serves LangChain4j, Spring AI, OpenAI and MCP simultaneously and the integration
   team already knows the idiom.
4. **Contain the CI path first, because it already has credentials.** This is the step teams skip.
   CI is the one place in the estate where an agent inherits a token that can reach production.
   `gitlab-opencode` runs a single LLM call in CI with **explicit tool permissions** — scope it
   before anyone asks for an agent, and the first security review has an answer ready.
5. **Log every call as a write-boundary event** (Receta 17) and attach the entitlement check
   (Receta 16). An OpenAPI operation invoked by an agent is a write to a system of record; the fact
   that it arrived over HTTP from a tool call changes nothing about who is accountable.

### Why this is cheaper than anything else in this file

No new platform, no migration, no model work, and the client already paid for the API gateway, the
specs and the auth. The work is **selection, containment and evidence** — which is also the work that
survives a change of model, framework or vendor. Compare Receta 11 (catalogues) for the same shape on
the data side: *point the agent at what the client already runs.*

### Anti-patterns

- **Exporting the whole catalogue.** The fastest way to a convincing demo and an unusable pilot.
- **Trusting `readOnlyHint`.** It is a hint, it is untrusted by specification, and its default is
  the dangerous value.
- **Writing a bespoke MCP server per API.** That is forty integrations again, wearing a new name.
- **Leaving CI uncontained while hardening the chat surface.** The chat surface holds a session;
  CI holds a deploy token.

---

## Receta 23 — The weights boundary: resolve the licence of the model before the pilot, not after the demo

**For:** any engagement where the deliverable runs on open-weights models — which, after the
sovereignty and cost pressure of 2026, is most of them. **Especially** any EMEA engagement
considering multimodal Llama 4, and any LATAM engagement considering Latam-GPT.

**Duration:** 3–5 days as a standalone gate; one day per additional model once the gate exists.

### The failure mode, stated plainly so it can be sold

The client's AI governance programme scans licences. It reads `LICENSE` files, because that is what
licence scanners read. The agent framework comes back MIT, the serving stack Apache-2.0, the whole
report is green — **and not one line of it describes the model**, which is a separate artefact under
a separate licence that the scanner never enumerated.

Three ways that bill arrives late:

1. **The multimodal EU case.** `meta-llama/llama-models` → `models/llama4/USE_POLICY.md:71` withdraws
   the Section 1(a) rights for multimodal Llama 4 from a *"company with a principal place of business
   in the European Union"*. `grep -c 'European Union'` over `models/llama4/LICENSE` returns **0**.
   The pilot demos, then legal reads the AUP.
2. **The inherited-licence case.** The client adopts the national model for sovereignty reasons.
   Latam-GPT is a **Llama 3.1 70B** derivative under the **Llama 3.1 Community License**: the AUP,
   the naming obligation and the 700M-MAU clause came along with it. The sovereignty was in the data.
3. **The false-negative case.** Someone rejects **Qwen3** because its repository has no `LICENSE`
   file. The weights are **Apache-2.0** (`README.md:397`). A permissive frontier-class model was
   dropped for a filing convention.

### Components, all permissive, all byte-verified 2026-11-24

| Role | Component | Licence |
|---|---|---|
| Weights serialisation requirement | [huggingface/safetensors](https://github.com/huggingface/safetensors) | Apache-2.0 (11,357 B) |
| Admission scan of third-party weights | [protectai/modelscan](https://github.com/protectai/modelscan) | Apache-2.0 (10,754 B) |
| Pickle scan, shippable inside a deliverable | [mmaitre314/picklescan](https://github.com/mmaitre314/picklescan) | **MIT** (1,072 B) |
| Signing the approved weights | [sigstore/model-transparency](https://github.com/sigstore/model-transparency) | Apache-2.0 |
| Licence text source of truth for the Llama family | [meta-llama/llama-models](https://github.com/meta-llama/llama-models) | per-model Community Licenses |
| Guidance the gate implements | [ossf/ai-ml-security](https://github.com/ossf/ai-ml-security) | Apache-2.0 (11,356 B) |

**Do not** reach for `trailofbits/fickling` here: it is **LGPL** (`master/LICENSE`, 7,652 B). It is
fine as a standalone CI binary, a licence problem linked into a shipped product. `picklescan` is the
MIT peer.

### Wiring — the gate is a document plus a CI job, in that order

**Step 1 — build the weights register. One row per model, four licence facts, not one.**

```
model_id            | base_model        | weights_licence        | aup_document            | gate_doc_read
--------------------+-------------------+------------------------+-------------------------+--------------
Qwen3-32B           | (none, base)      | Apache-2.0 (README:397)| none                    | n/a
Salamandra-7B       | (none, base)      | Apache-2.0 (LICENSE)   | none                    | n/a
Llama-4-*-multimodal| (none, base)      | Llama 4 Community      | USE_POLICY.md:71  ← EU  | REQUIRED
LatamGPT-SFT-1.0    | Llama-3.1-70B     | Llama 3.1 Community    | Llama 3.1 USE_POLICY    | REQUIRED
Gemma-*             | (none, base)      | UNRESOLVED             | Gemma prohibited-use    | BLOCKED
```

The `base_model` column is the whole point: **restrictions compose downward and a fine-tune can
never be freer than its base.** Resolve in this order — base licence, then AUP, then the fine-tune's
own licence, then any download gate.

**Step 2 — read the acceptable-use policy as part of the licence.** Not as a policy document. For
each candidate, enumerate every document the licence incorporates by reference and read all of them.
The one-line audit that proves the point, runnable against any shortlist:

```bash
# A restriction can live outside the instrument that grants the rights.
for f in LICENSE USE_POLICY.md; do
  printf '%-16s ' "$f"; grep -c 'European Union' "$f" 2>/dev/null || echo 0
done
```

**Step 3 — answer the licensee question in writing.** For every model whose licence has a
domicile, user-count or field-of-use term, record **which legal entity is exercising the rights**.
For multimodal Llama 4 the clause turns on the licensee's principal place of business and expressly
does **not** reach end users of a product incorporating the model, so the answer depends on
contract structure, not architecture. **This is a question for counsel and it belongs in week one.**

**Step 4 — then, and only then, the CI job.** Require `safetensors`; run `modelscan` and
`picklescan` on anything that arrives in another format; sign the approved weights directory with
`sigstore/model-transparency` so "these are the weights legal approved" is a verifiable claim about
`(path, digest)` pairs rather than an assertion in a slide.

**Step 5 — emit the record as data.** See Receta 24.

### Build order — and the order is the deliverable

1. Weights register with the four licence columns, every value traced to a file and a line.
2. AUP read and summarised per model, with the restrictive clauses quoted verbatim.
3. The licensee-entity determination, in writing, from counsel.
4. CI: format requirement → scan → signature.
5. AI-BOM emission (Receta 24).

### Licence posture

Six components, five permissive (four Apache-2.0, one MIT), one deliberately excluded for being
LGPL. Nothing in this gate obliges the client to disclose anything, and nothing in it ships copyleft.

### What to tell the client the limits are

- **This gate resolves the licence, not the copyright position of the training data.** OpenMDW-1.1
  says so in capitals: the licensee is *"solely responsible for clearing rights of other persons."*
  **A permissive weights licence is not an indemnity for the corpus.** If the client needs that, it
  is a commercial term with a vendor, not an open-source licence.
- **Two licences could not be resolved from this session and the gate says so rather than guessing:**
  Gemma (primary source `ai.google.dev` does not resolve) and the downstream reach of the Apertus
  AUP. A gate that returns "unresolved" is working correctly.
- **Scanners will keep being wrong here**, in both directions, because they read the wrong file.
  The register is the artefact; the CI job only enforces what the register already decided.

---

## Receta 24 — The AI-BOM that actually names the weights licence, because the standards make it optional

**For:** the client who already produces SBOMs — so the pipeline, the signing and the review habit
exist — and now has models in production that the SBOM does not mention. Sequel to **Receta 18**
(the provenance boundary) and the natural consumer of **Receta 23**'s register.

**Duration:** 2–3 weeks on top of an existing SBOM pipeline.

### The architectural finding that determines the whole design

Both standards have the fields. **Neither requires them.**

- **CycloneDX 1.6** — `schema/bom-1.6.schema.json`, byte-read at **262,666 bytes**, carries a
  `machine-learning-model` component type plus `modelCard` and `modelParameters`. ML-BOM is real and
  published.
- **SPDX 3.0** — the AI profile lives in [spdx/spdx-3-model](https://github.com/spdx/spdx-3-model) at
  `model/AI/Classes/AIPackage.md` (1,687 B), **not** in `spdx/spdx-spec`. `AIPackage` subclasses
  `/Software/Package` and carries `informationAboutTraining`, `limitation`, `autonomyType`,
  `domain`, `energyConsumption`, `hyperparameter`.
- **And every one of those properties is `minCount: 0`.** A fully conformant SPDX 3.0 AI SBOM can be
  **silent about training data, silent about limitations, silent about autonomy** — and still validate.

This is the same failure this KB documented one layer down in pass 8: MCP's `ToolAnnotations` are all
hints the client must treat as untrusted, so write-path safety cannot live in tool metadata. **Here:
licence and training-data governance cannot live in SBOM metadata either, because the schema makes it
optional.** The rule is identical — **require the fields in the contract, not in the format.**

### Wiring

| Role | Component | Licence |
|---|---|---|
| ML-BOM schema and validation | [CycloneDX/specification](https://github.com/CycloneDX/specification) | Apache-2.0 (11,341 B) |
| AI profile model and field definitions | [spdx/spdx-3-model](https://github.com/spdx/spdx-3-model) | Community-Spec-1.0 |
| Weights signature referenced from the BOM | [sigstore/model-transparency](https://github.com/sigstore/model-transparency) | Apache-2.0 |
| The licence facts the BOM carries | Receta 23's weights register | — |

### Steps

1. **Write the acceptance criteria as a contract clause, not a format choice.** The sentence that
   does the work: *"Each model component shall carry a non-empty `informationAboutTraining` and
   `limitation`, and shall name both the weights licence and every document that licence
   incorporates by reference."* Without that clause the BOM validates while saying nothing.
2. **Emit one `machine-learning-model` component per model**, with `modelCard` and `modelParameters`
   populated from the register, and the **base model recorded as a dependency** — that edge is what
   makes inherited licences visible to a reviewer, and it is the edge that would have shown a
   reader that Latam-GPT is a Llama derivative.
3. **Record the AUP as a referenced document with its file and line**, not as a URL. `USE_POLICY.md:71`
   is a citation a reviewer can check; "see Meta's website" is not.
4. **Handle the identifier gap deliberately.** OpenMDW-1.1 is **not on the SPDX License List**, so an
   NVIDIA Cosmos-class model will serialise as `NOASSERTION` or a custom string. Put the licence name
   in a declared field and **tell the client's security team in advance**, or their own tooling will
   report a foundation-stewarded permissive licence as "unlicensed". This KB's ninth pass found
   `NOASSERTION` has two causes; **this is a third — a real licence the identifier list has not
   caught up with.**
5. **Attach the signature.** Reference the `sigstore/model-transparency` bundle from the BOM so the
   component identity is `(path, digest)` pairs that can be recomputed, closing the loop with
   Receta 18.

### Deliverables, and the sentence that sells it

An ML-BOM per deployed model, a contract clause that makes its fields mandatory, and a licence
register behind it. The sentence: **"Your SBOM pipeline is already compliant and it does not mention
the models. The standards added the fields and made them optional — so we make them contractual."**

### Anti-patterns — each one observed in this pass's evidence

- **Reading `LICENSE` and calling the model cleared.** It is the wrong file. Measured divergence: two
  of four families, in opposite directions.
- **Treating an acceptable-use policy as a policy.** It modifies the grant. `USE_POLICY.md:71`.
- **Buying "sovereign" as a licence claim.** Latam-GPT carries Meta's licence; SEA-LION's licence
  depends on the checkpoint and its own paper overstates it.
- **Rejecting a model because the repo has no `LICENSE`.** Qwen3 is Apache-2.0.
- **Accepting a model because the repo *has* an Apache-2.0 `LICENSE`.** `google-deepmind/gemma` does;
  that file governs the code.
- **Quoting an OpenMDW model as "OSI-approved".** It is not, and the review was still open at
  2026-08-29 over termination reaching copyright claims.
- **Treating a permissive weights licence as an indemnity for training data.** OpenMDW-1.1 disclaims
  exactly that, in capitals.
- **Shipping `fickling` inside a product.** LGPL. Use `picklescan` (MIT).
- **Accepting "we emit an AI-BOM" as governance.** Every field is optional. Require them by contract.

---

## Receta 25 — The erasure boundary: delete a person from an agentic estate, and prove it

**When to use this.** The client has an agent in production over customer data and has just been
asked — by a regulator, a large customer's DPA, or a privacy function that read the AI Act — *show
us what happens when someone asks to be deleted.* In California since 1 August 2026 the request
arrives as a **45-day polling obligation**; in Chile the law lands **1 December 2026**; in Brazil
the ANPD has named data-subject rights and AI as 2026–2027 priorities **and can suspend the tool
preemptively**. This is the recipe for all three.

### The failure mode, stated plainly so it can be sold

> A customer exercises erasure. A support agent deletes the record in the CRM and confirms it. Six
> weeks later the AI assistant answers a question using that customer's data, because the CRM's
> delete was an `UPDATE … set deleted=1`, the CDC tombstone was dropped by the sink, the lakehouse
> snapshot still holds the row, and the embedding was never in scope at all. **Nobody made a
> mistake.** Every component behaved as documented. The commitment was wrong.

### The architectural finding that determines the whole design

Two of the seven resting places have **no delete operation**:

- **Fine-tuned weights.** Unlearning is research code — `OPTML-Group/Unlearn-Sparse` (MIT, 90★),
  `locuslab/tofu` (MIT, 30★, **idle 21 months**). Approximate unlearning is not erasure; retraining
  is the only remedy that satisfies the right, and it costs the training run.
- **Logs.** EU AI Act Art. 19 requires providers to retain automatic logs **≥ 6 months**; India's
  DPDP Rule 8 pairs erasure with **≥ 1 year** of logs. Deleting them may be the violation.

So the design is fixed before the first component is chosen:

> **Personal data lives in retrieval over deletable stores, never in a fine-tune. Logs carry a
> pseudonymous reference, never the identifier. Everything else is a cascade with a proof step.**

### Components — all permissive unless marked, all verified 2026-11-24

| Role | Component | Licence |
|---|---|---|
| Data map / lineage (the prerequisite) | [MarquezProject/marquez](https://github.com/MarquezProject/marquez) + OpenLineage *(held)* | Apache-2.0 |
| Classification that follows the data | [apache/atlas](https://github.com/apache/atlas), or DataHub / OpenMetadata *(held)* | Apache-2.0 |
| PII detection + a **measured** recall number | [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) + [presidio-research](https://github.com/data-privacy-stack/presidio-research) | MIT |
| Risk-scoring the detections | [EdyVision/pii-codex](https://github.com/EdyVision/pii-codex) | BSD-3-Clause |
| Non-English recognisers (APAC) | [danyuchn/pii-guard](https://github.com/danyuchn/pii-guard) | MIT |
| CDC with tombstone handling | Debezium *(held)* | Apache-2.0 |
| Lakehouse delete + snapshot expiry | [apache/hudi](https://github.com/apache/hudi) (record-level deletes), [delta-io/delta](https://github.com/delta-io/delta), Iceberg *(held)* | Apache-2.0 |
| Query engine that must *also* stop seeing it | [trinodb/trino](https://github.com/trinodb/trino) | Apache-2.0 |
| Central table/retention policy | [apache/polaris](https://github.com/apache/polaris) | Apache-2.0 |
| Vector delete + compaction | Qdrant / Milvus / pgvector / Weaviate *(held)*, [chroma-core/chroma](https://github.com/chroma-core/chroma) | Apache-2.0 (see split-licence note for Weaviate) |
| Retention & erasure policy **as code, per jurisdiction** | OPA / Cerbos *(held)* | Apache-2.0 |
| Durable orchestration of a 7-system cascade | Temporal / Conductor / dapr workflows *(held)* | Apache-2.0 |
| Machine-readable evidence | OSCAL assessment results *(held, eighth pass)* | Public domain |
| Egress filter on agent CLI traffic | [crp4222/PrivAiTe](https://github.com/crp4222/PrivAiTe) | BSD-3-Clause |
| **Reference design only — do not depend on** | [ethyca/fides](https://github.com/ethyca/fides) — **ARCHIVED** | Apache-2.0 |

**There is no maintained permissive DSAR engine to install.** This pass searched and did not find
one. Fides is the model to read; the orchestration is application code on durable execution.

### Wiring

```
      Erasure request
   (DROP poll / portal / DPA)
             │
             ▼
   ┌──────────────────────┐   identity resolution  ← the step that actually fails
   │ Request intake       │───────────────────────► entity resolution (held, 6th pass)
   └──────────┬───────────┘
              │ subject → every system holding them, FROM THE LINEAGE GRAPH
              ▼
   ┌─────────────────────────────────────────────────────────────┐
   │ Durable cascade workflow (one activity per resting place)   │
   ├─────────────────────────────────────────────────────────────┤
   │ 1 system of record   → hard delete / anonymise in place     │
   │ 2 CDC stream         → tombstone, sink asserted by test     │
   │ 3 lakehouse          → DELETE  then  expire_snapshots/VACUUM│
   │ 4 vector index       → delete by filter  then  compaction   │
   │ 5 eval fixtures      → owned store, same treatment          │
   │ 6 fine-tuned weights → MUST BE EMPTY BY DESIGN              │
   │ 7 logs/traces        → pseudonym map entry deleted, LOG KEPT│
   └──────────┬──────────────────────────────────────────────────┘
              │ every activity emits (subject, system, action, timestamp, operator)
              ▼
   ┌──────────────────────┐
   │ Re-query proof step  │  ask each store for the subject again — absence is
   │ (the deliverable)    │  the evidence; a successful delete call is not
   └──────────┬───────────┘
              ▼
      OSCAL assessment results + dated erasure certificate
```

### Build order — and the order is the deliverable

1. **Lineage first, and refuse to start without it.** You cannot cascade through a graph you have
   not recorded. If the client has no lineage, that is the first work package and it is billable on
   its own merits.
2. **Classify, then measure the classifier.** Run `presidio-research` and report recall as a
   number. "We detect PII" is not a finding; "we detect 94% of the entity types in your data, these
   are the misses" is.
3. **Prove row 6 is empty.** Audit every fine-tune and every training set for personal data
   *before* promising anything. If it is in there, say so immediately — the remedy is a retrain and
   it must be budgeted, not discovered in month four.
4. **Fix row 1 honestly.** Establish whether the platform's delete is a soft delete. For SuiteCRM
   this is verified in `verticals/solutions.md`; for Odoo, ERPNext, Dolibarr and Axelor **run the
   check**, do not assume either way.
5. **Build the cascade on durable execution**, one activity per resting place, idempotent, retried.
   A cascade that fails halfway with no record is worse than no cascade.
6. **Make the proof step non-optional.** Re-query every store. A 200 from a delete API is a claim;
   an empty result set is evidence.
7. **Quote the latency.** Snapshot expiry and index compaction mean erasure completes on a
   schedule, not instantly. The retention window **is** the erasure SLA — write it into the
   contract rather than discovering it in an audit.

### Sizing and the milestone to fix

Lineage + classification + measured recall: **4–6 weeks.** Cascade over three to five systems with
the proof step: **8–12 weeks.** The milestone that de-risks the engagement is **week 6: a single
subject deleted end-to-end across every system, with the re-query proof and a dated certificate.**
One subject proven beats a design document for twelve systems.

### Licence posture

Every component above is Apache-2.0, MIT or BSD-3-Clause except the AGPL-3.0 suites, which are
reached **over their published APIs** per this file's standing containment rule. The archived Fides
is read, never imported. **`vec2text` is excluded from this recipe by licence** — see the
anti-patterns.

### What to tell the client the limits are

- **Erasure has a latency and we will quote it.** Snapshot and index mechanics, not slowness.
- **Detection has an error rate and we will measure it.** Presidio is good, not perfect.
- **If personal data is already in a fine-tune, there is no supported way to remove it.** The
  remedy is a retrain. Anyone offering "unlearning" is selling research code.
- **We cannot delete the logs, and that is the law working as intended.** See Receta 26.
- **No regulator has published a reconciliation of the retention floor with the erasure duty.** The
  schema below is our engineering reading and is presented as such.

---

## Receta 26 — The log that can be kept: satisfying a retention floor without storing what you erased

**When to use this.** Whenever Receta 25 reaches row 7, and always *before* an agent goes to
production in the EU or India. This is a half-day design decision that costs an estate-wide
migration if it is made late.

### The conflict, in one table

| Instrument | Demands | Floor |
|---|---|---|
| EU AI Act Art. 19 (providers) / Art. 26 (deployers) | Retain automatically generated logs | **≥ 6 months**, from 2 Dec 2027 (Annex III) |
| India DPDP Rules, Rule 8 | Erase on purpose completion **and** retain logs | **≥ 1 year** |
| GDPR Art. 17 / LGPD / Ley 21.719 | Erase on request | On request |

### The degree of freedom

**The AI Act prescribes no log format.** That is the whole solution. The obligation is to retain
*logs*; it is not an obligation to retain *identifiers*.

### Wiring

```
  agent step / tool call
         │
         ▼
  ┌───────────────────┐
  │ OTel instrument.  │  (held — evaluation & observability section)
  │ emits span        │
  └────────┬──────────┘
           │  subject_ref = pseudonym(subject_id)      ← mapping stored SEPARATELY
           │  no names, no emails, no free-text PII in attributes
           ▼
  ┌───────────────────┐        ┌──────────────────────────────┐
  │ Presidio filter   │───────►│ Log store (Loki, held)       │
  │ at log ingest     │ reject │ retention = MAX(floor in     │
  │ (defence in depth)│ on hit │ scope), per jurisdiction      │
  └───────────────────┘        └──────────────────────────────┘
           ▲
           │ tool-call ARGUMENTS are the usual leak — PrivAiTe-shaped
           │ proxy on agent CLI egress catches what instrumentation misses
  ┌────────┴──────────┐
  │ pseudonym mapping │  ← THIS is in the Receta 25 cascade.
  │ store             │     Delete the mapping, the log survives,
  └───────────────────┘     the person is no longer identifiable from it.
```

### Steps

1. **Define `subject_ref` and forbid raw identifiers in log attributes.** A lint rule in CI, not a
   convention in a wiki.
2. **Put the pseudonym mapping in its own store with its own owner**, and register it as resting
   place #8 in the cascade — it is the only place the link survives.
3. **Run Presidio at log ingest as defence in depth.** Instrumentation will leak eventually;
   free-text prompts and error messages are where it happens.
4. **Filter tool-call arguments specifically.** Every guardrail in this KB inspects prompts and
   responses. Tool arguments go to a third party whose logs you can never cascade into — a
   redaction proxy at that boundary is the only control, and `PrivAiTe` is the permissive pattern.
5. **Set retention as policy-as-code per jurisdiction**, to the longest floor in scope. One schema,
   per-jurisdiction retention.
6. **Record the design decision as OSCAL evidence**, so the reconciliation is documented at design
   time rather than defended at audit time.

### Deliverables, and the sentence that sells it

A log schema, a CI rule, a mapping store inside the erasure cascade, a per-jurisdiction retention
policy, and a one-page note explaining how the client meets a retention floor and an erasure duty
simultaneously.

> *"We can keep your AI Act logs for six months and your DPDP logs for a year, delete the person on
> request, and show an auditor both are true — because the log never contained their identity."*

### Anti-patterns — each observed in this pass's evidence

- **Quoting `ethyca/fides` as the open-source DSAR platform.** Apache-2.0, 483★, and **archived**
  since before this pass. 2026 roundups still recommend it. The ninth archived-but-recommended
  project this KB has caught, and the **first where the replacement repositories declare no licence
  at all**.
- **Running `vec2text` against a client's model.** Its `NOASSERTION` badge hides **SOM-1.0**, whose
  §3(A) obliges you to publish the weights of any model you run inference with. Use
  `jina-ai/embedding-inversion-demo` (Apache-2.0) for the same demonstration.
- **Treating a vector store as outside the erasure scope.** Embeddings are invertible to source
  text. The vector index is resting place #4, not an index of something else.
- **Promising "unlearning".** Two-digit-star research code; the leading benchmark idle 21 months.
- **Accepting a platform's delete as erasure.** SuiteCRM's `mark_deleted()` is an `UPDATE`, and
  `mark_undeleted()` ships beside it.
- **Taking a proprietary retention module into an open-source ERP deployment.** At least one
  prominent Odoo GDPR retention/purge module is **OPL-1**. The compliance centrepiece becomes the
  one proprietary dependency.
- **Deleting logs to honour an erasure request.** In the EU and India that may be the violation.
  Delete the mapping, keep the log.
- **Adopting `amundsen-io/amundsen` for the data map.** Apache-2.0, 4,780★, **archived**
  2026-09-10 and still appearing in catalog comparisons. DataHub and OpenMetadata are held and
  maintained.

## Receta 27 — The accessibility gate for an agent UI: make the conformance claim testable, and the licence survivable

**When to sell this.** Any agent with a human interface delivered to (a) a US state or local
government or one of its vendors, (b) anyone placing a product or service on the EU market, (c) an
Argentine financial entity, or (d) a Brazilian consumer-facing brand. In the EU it is not optional
for high-risk systems: **AI Act Article 16(l)** pulls Directives 2016/2102 and 2019/882 into the
provider's obligations, so this attaches to the **conformity file of Receta 3** rather than
competing with it for budget.

**The decision that comes first, before any tool is installed.** Ask the client's open-source review
which licence bucket may appear **in the shipped artifact**:

- **Permissive end-to-end required** → `IBMa/equal-access` (**Apache-2.0**, 788★, default branch
  `main-4.x`). It is the **only** engine in this layer with no `axe-core` dependency. Everything
  else inherits **MPL-2.0**.
- **Weak copyleft acceptable in the artifact, with disclosure** → anything built on
  `dequelabs/axe-core` (**MPL-2.0**, 7.9k★, npm 4.14.1 of 2026-11-16), which means Microsoft's MIT
  tooling, Google's Apache-2.0 Lighthouse, and all three MCP servers. File-level copyleft: ships
  beside proprietary code, but modifications to axe's own rule files must be published.
- **Never assume the badge.** `microsoft/accessibility-insights-web` is MIT and installs
  `axe-core` 4.11.3 anyway. Read `package.json`, not the sidebar.

### Wiring

1. **Static gate in CI (the cheap 80%).** `IBMa/equal-access` `accessibility-checker` as a CLI step,
   or — if the client's pipeline already runs it — `GoogleChrome/lighthouse` (Apache-2.0, 31.2k★)
   with the a11y category. Fail the build on new violations only, never on the backlog; a gate that
   fails on day one gets disabled by week two. This lands **inside the existing CI gate of
   Receta 10**, not beside it.
2. **Give the coding agent the audit tool.** `JustasMonkev/mcp-accessibility-scanner` (**MIT**, 59★,
   npm 5.0.1 published **2026-11-16**, `axe-core` 4.14.0 + `playwright` 1.65.1) as an MCP server, so
   the agent scans, reads findings, edits and re-scans. If MPL-2.0 is acceptable,
   `priyankark/a11y-mcp` (53★) is the only one publishing to npm **with provenance** and running
   weekly Dependabot — better supply-chain posture, worse licence posture. **Do not use the
   most-starred one** (`ronantakizawa/a11ymcp`, 97★): npm last published 2026-03-01 and it pins
   `puppeteer` **13.5.0, dated 2022-03-07**.
3. **Test the thing no scanner can see — the streaming transcript.**
   `guidepup/virtual-screen-reader` (**MIT**, 158★) in **unit** tests over the chat DOM: assert that
   a completed assistant message is announced **once**, that partial tokens are **not** announced,
   and that focus never moves on a status change. Then `guidepup/guidepup` (**MIT**, 604★, npm
   0.40.0 of 2026-11-01) in a **nightly** job driving **real NVDA and VoiceOver**. `nvaccess/nvda`
   is GPL-2.0-or-later — you **drive** it, you never bundle it, and that distinction goes in the OSS
   review in writing.
4. **Build the UI from a component set that already passed.** `alphagov/govuk-frontend` (**MIT**,
   Crown Copyright/GDS, npm 6.6.0 of 2026-10-15) for anything not already on a design system; USWDS
   for US public sector, **after** enumerating its non-public-domain parts. Hand-rolling the chat
   surface is how teams buy themselves the entire component-level backlog.
5. **Produce the artifact the buyer actually wants.** Not a scan report — an **Accessibility
   Conformance Report** (a completed VPAT): the automated JSON from step 1, plus the screen-reader
   results from step 3, plus the manual keyboard pass. Keep it **under two years old and versioned
   to the release** (a real university procurement rule), and state plainly that automated coverage
   is partial.
6. **Register it where the governance already lives.** The MPL-2.0 `axe-core` entry goes in the
   **AI-BOM of Receta 24**. The control statements can be expressed in **OSCAL** (eighth pass) — but
   **no WCAG 2.1 AA / EN 301 549 OSCAL catalog was found**, so budget that as a build, not an
   adoption, and say so before quoting it.

### The streaming rules, stated concretely because no standard states them

Token streaming updates the DOM ~5–20×/second. There is **no normative definition of accessible
streaming** — W3C live-region guidance is advisory — so these are engineering decisions the team
owns:

- Keep streamed text **out** of any `aria-live` region; announce the message **once**, on
  completion.
- **One** dedicated `aria-live="polite"` region for announcements, with `aria-atomic="false"` — not
  `aria-live` on each message bubble.
- Create the region **empty and before** content, or it may be ignored entirely.
- `role="log"` + `aria-live="polite"` for completed messages.
- Do **not** depend on `aria-busy` (inconsistent across browser/screen-reader pairs), and do **not**
  move focus on status updates — announce "thinking" / "response complete" instead.

Evidence that this is real and not theoretical: Atlassian's own agent carries public ticket
**ROVO-978** for exactly this failure.

### Sizing and what to fix as the milestone

Four to six weeks for a single agent surface: week 1 the licence decision and the CI gate, week 2
the component audit, weeks 3–4 the streaming behaviour and the screen-reader suite, weeks 5–6 the
manual pass and the ACR. **The milestone is the signed ACR, not a green pipeline** — a green
pipeline on partial automated coverage is the deliverable clients later discover was worthless.

### What to tell the client the limits are

- **An automated scan is not conformance.** Automated rules cover a fraction of WCAG; keyboard and
  screen-reader flows need a person or a driven screen reader.
- **A VPAT is self-reported.** State guidance in the US already warns buyers of this and recommends
  independent validation — offer the validation, do not resent the scepticism.
- **The US Title II date moved**: 2027-04-26 (≥50,000 population) and 2028-04-26 (<50,000 and
  special districts), per the DOJ interim final rule of 2026-04-20. **Do not pitch urgency against
  the old April 2026 date** — the client's counsel knows.
- **The EU baseline is moving to WCAG 2.2 AA** via EN 301 549 V4.1.1 (reported 2026-09-02,
  secondary-sourced). Build to 2.2, not 2.1, where the EU is in scope.

### Anti-patterns for this receta

- **Promising "MIT only" and then installing Microsoft's MIT scanner** — which brings MPL-2.0
  `axe-core` with it. Five of six tools in this layer do.
- **Taking the most-starred MCP server** into a client pipeline. It is the stalest and ships a
  2022 browser.
- **Putting streamed tokens into an `aria-live` region.** The two outcomes are a firehose or
  silence.
- **Adopting `pa11y/pa11y` (LGPL-3.0-only) or `ryersondmp/sa11y` (GPL-2.0)** into a distributed
  artifact without checking — Sa11y was MIT at v2.0 and is not any more.
- **Quoting `w3c/wcag` or `act-rules/act-rules.github.io` as open source to build on.** W3C
  Document Licence and a W3C Contributor Licence Agreement are **not software licences**. (The APG
  repo, `w3c/aria-practices`, is under the W3C **Software and** Document License — different thing.)
- **Citing `NBR 17060`** for Brazil. This pass searched for it and could not confirm it exists in
  the form it is commonly cited.

## Receta 28 — Atribuir el consumo del agente a una unidad de negocio (added fifteenth pass, 2026-11-24)

**Cuándo.** El cliente tiene que responder una de estas tres preguntas y no puede: *¿cuánta energía
consume nuestra plataforma de agentes?*, *¿cuánto de eso es del equipo X?*, *¿qué ponemos en el
informe?* Típicamente llega por el área de sostenibilidad o por un inquilino que exige el dato por
contrato (en APAC, casi siempre por contrato — ver `intel/market.md`).

**El problema real, dicho antes de la arquitectura.** Ninguna herramienta madura mide *agentes*.
Kepler mide **pods**, Scaphandre mide **procesos**, CodeCarbon envuelve **llamadas**. Un agente es un
plan que estalla en N llamadas al modelo, M invocaciones de herramienta y reintentos. **No hay
producto que cierre ese hueco**: lo que hay es composición, y el puente lo construye el *engagement*.
Decirlo así es parte de la receta — un cliente al que se le promete "medición de agentes de caja"
descubre el hueco en la semana tres.

**Cableado (cuatro etapas, todas con licencia permisiva):**

1. **Medir el *pod*** — `sustainable-computing-io/kepler` (Apache-2.0, 1606★) como DaemonSet, o
   `…/kepler-operator` (Apache-2.0) si el cliente está en OpenShift. eBPF + RAPL, exporta a
   Prometheus. **Esto da julios por pod, que es lo máximo que la infraestructura sabe.**
2. **Contar el trabajo del agente** — el plano de control que esta KB ya tiene en **Receta 9**: el
   *gateway* de IA emite *tokens* y llamadas **por clave virtual**, y la clave virtual ya está
   asociada a equipo, producto o inquilino. **Esto da unidades de trabajo por unidad de negocio.**
3. **Construir el puente, que es el entregable que no existe comprado** — repartir los julios del
   paso 1 entre las claves del paso 2, proporcionalmente a una unidad declarada (*tokens* de salida
   ponderados, o segundos de GPU si el servidor los expone). **Declare la regla de reparto como un
   supuesto explícito y versionado**; es una estimación, no una medición, y un auditor lo va a
   preguntar. Si hay GPU dedicada, `ml-energy/zeus` (Apache-2.0, 390★) mide directamente y el
   reparto se evita.
4. **Hacer el número auditable** — `Green-Software-Foundation/if` (MIT, 184★): el cálculo se declara
   como **manifiesto YAML**, no como código. Es lo que convierte "nuestro script lo calculó" en "la
   metodología es esta, versionada y re-ejecutable". **Esta etapa es la que hace vendible el
   conjunto**, y es la más barata de las cuatro.

**Para la cifra de carbono, y aquí está la trampa que decide la arquitectura.** Convertir kWh en
gCO₂e necesita un **factor de intensidad de red**. La vía habitual (`thegreenwebfoundation/co2.js`,
Apache-2.0) **trae los datos de Electricity Maps bajo ODbL, con *share-alike***, de modo que la base
de datos derivada del cliente hereda obligaciones. **Tres salidas, en orden de preferencia:**

- **factor del operador nacional** cuando existe con licencia usable — en Colombia,
  `EquipoAnaliticaXM/API_XM` (**MIT**, 75★, `default_branch=master`) da SIMEM/XM directo;
- **factor contractual** que el propio proveedor de nube o *colo* entrega al cliente (en APAC es lo
  que el operador ya está obligado a producir por contrato);
- **ODbL aceptada a conciencia**, con atribución a Electricity Maps y share-alike sobre la base
  derivada — que para un informe publicado suele ser tolerable, y para un producto revendido no.

**Qué entregar, y el límite que hay que escribir en la propuesta.** Un *dashboard* de julios y
gCO₂e por equipo, la regla de reparto versionada, el manifiesto IF y —si el cliente reporta— la
salida en XBRL con `Arelle/Arelle` (**Apache-2.0** por lectura directa, 261★). **El límite:** los
pasos 1, 2 y 4 son medición y metodología; **el paso 3 es una estimación**. No se presenta como
medición y no se firma como tal.

---

## Receta 29 — Mover el trabajo diferible del agente a ventanas de red limpia, bajo LGPL (added fifteenth pass, 2026-11-24)

**Cuándo.** El cliente ya mide (Receta 28) y pregunta lo siguiente, que es lo razonable: *¿y ahora
cómo bajamos el número?* Es la receta más barata de esta KB porque **no toca el modelo ni el
agente**: sólo mueve **cuándo** corre el trabajo que no tiene que correr ahora.

**La observación que la hace viable:** una plataforma de agentes enterprise está **llena** de trabajo
diferible — reindexado de documentos, *batch* de *embeddings*, evaluaciones nocturnas, reentrenos,
compactación de memoria, barridos de *red teaming*. Nada de eso tiene a un humano esperando. Es
exactamente la clase de carga que se puede desplazar unas horas sin que nadie lo note.

**Cableado:**

1. **El planificador** — `jobrunr/jobrunr` (3112★). **Verificado leyendo el código, no un blog:**
   `gh api search/code` sobre `repo:jobrunr/jobrunr carbonaware` devuelve **91 coincidencias** y las
   clases viven en **`core/src/main/java/org/jobrunr/scheduling/carbonaware/`** y
   `…/server/carbonaware/` — **módulo `core`, fuente `main`, no un módulo Pro.** Es decir, el
   *scheduling* carbon-aware **está en el núcleo abierto**.
2. **La licencia, y la decisión que implica** — `License.md` (no `LICENSE`: 404 en los cuatro
   nombres habituales) declara el proyecto **`multi-licensed`**: **LGPL-3.0-or-later** *o* comercial
   por suscripción, **a elección del receptor**. Para enlace dinámico desde una aplicación
   propietaria la vía LGPL es aceptable en la mayoría de los *engagements*; **si el cliente
   distribuye un binario modificado, la conversación cambia** y existe la vía comercial. Decidir esto
   en la semana uno, no en la auditoría.
3. **La dependencia que hay que declarar antes del *go-live*** — leído de
   `CarbonAwareJobProcessingConfiguration.java`, por defecto la librería llama a
   **`https://api.jobrunr.io`** cada **5 minutos**, con *timeouts* de **3 s** y **3 reintentos**.
   `carbonIntensityApiUrl`, `areaCode` y `dataProvider` **son configurables**: en un cliente regulado
   se apunta a un endpoint propio y **la mitigación es una línea de configuración**. No es un
   defecto; es una salida de red activada por defecto en una librería de licencia impecable, y se
   revisa como tal.
4. **La alternativa si el *stack* no es JVM** — `Green-Software-Foundation/carbon-aware-sdk` (MIT,
   600★, `default_branch=**dev**`, no `main`) responde "¿cuándo y dónde corro esto?" por API, y
   `thegreenwebfoundation/grid-intensity-go` (Apache-2.0, 84★) hace lo mismo desde Go. Con MIT y
   Apache-2.0 no hay la conversación del punto 2.
5. **El ahorro que nadie cita y es el más grande** — `kube-green/kube-green` (MIT, 1390★) apaga los
   *namespaces* no productivos fuera de horario. En una plataforma de agentes con entornos de
   desarrollo, *staging* y evaluación, **esto suele superar cualquier ganancia por desplazamiento
   temporal**, y se implementa en días.

**Orden de construcción recomendado:** (5) primero, porque es el más barato y el resultado es
inmediato y medible con la Receta 28 ya instalada; después (1)+(3) si el cliente es JVM, o (4) si no
lo es. **(2) se resuelve antes de escribir código.**

**Qué no promete esta receta.** No reduce julios: **reduce gCO₂e** moviendo consumo a horas de red
más limpia — salvo `kube-green`, que sí reduce julios porque apaga. La diferencia importa cuando el
cliente paga la electricidad: **el desplazamiento mejora el informe y casi no mueve la factura.**
Dígalo antes de que lo pregunte el CFO.

---

## Receta 30 — The agent that may speak to a customer in their own language: terminology-controlled generation with a human approval gate (added sixteenth pass, 2026-11-24)

**The problem it solves.** A client wants their agent to answer customers in Spanish, Portuguese,
French and Hindi. The naive build — put the target language in the system prompt — fails four
different ways at once: brand and product terms drift per utterance, plural and gender agreement
breaks, nobody can say who approved any sentence, and in **Québec, the EU, India and Brazil** the
result may be unlawful rather than merely poor. This receta makes the wording **governed**:
generated, measured, approved, and provable after the fact.

### The architectural finding that determines the whole design

**Glossary injection has to happen at every stage, not once.** The measured bar is **AIDAterm**
(ACL 2026, Industry Track): a four-agent pipeline reporting **99.4% terminology accuracy on the
WMT25 Terminology Translation benchmark** — per its authors, better than **all 20 systems** submitted
to that shared task. The contrast that makes it an architecture and not a prompt-tuning exercise: a
practitioner report puts **glossary prompting alone plateauing in the mid-80s**. The gap between
~85% and 99.4% is **structural** — pre-analysis, injection at each hop, and a reasoning review agent
last — not a better model.

And the second finding, which decides the acceptance criteria: from `andrewyng/translation-agent`'s
own README, translations its **human raters preferred** scored **lower on BLEU**. **So BLEU can
reject the better pipeline.** Rank with COMET/QE; use sacreBLEU only as a regression tripwire.

### Components — all verified 2026-11-24, licences byte-read

| Role | Component | Licence | Why this one |
|---|---|---|---|
| String + glossary system of record | [`mozilla/pontoon`](https://github.com/mozilla/pontoon) | **BSD-3-Clause** | **The only fully permissive TMS.** Holds source strings, translations, glossary, translation memory, reviewer sign-off and the audit trail |
| Message format | [`unicode-org/message-format-wg`](https://github.com/unicode-org/message-format-wg) (MF2) + [`messageformat/messageformat`](https://github.com/messageformat/messageformat) | **Unicode-3.0** / **MIT** | MF2 is **stable in CLDR and recommended**; it is what keeps plural/gender correct in generated text |
| Locale data | [`unicode-org/cldr`](https://github.com/unicode-org/cldr) + [`unicode-org/icu`](https://github.com/unicode-org/icu) | **Unicode-3.0** | Plurals, dates, collation, bidi — the things an LLM gets subtly wrong |
| Language detection | [`pemistahl/lingua-py`](https://github.com/pemistahl/lingua-py) | **Apache-2.0** | Accurate on short text. **Not** fastText (archived) or cld3 (archived) |
| Deterministic MT (bulk/fallback) | [`OpenNMT/CTranslate2`](https://github.com/OpenNMT/CTranslate2) + [`Helsinki-NLP/Opus-MT`](https://github.com/Helsinki-NLP/Opus-MT) models | **MIT** / models **CC-BY-4.0** | Self-hosted, CPU-viable, commercially usable **with attribution**. ⚠️ **not NLLB** — see the licence posture |
| Quality estimation | [`Unbabel/COMET`](https://github.com/Unbabel/COMET) (CometKiwi, reference-free) | **Apache-2.0** | **Reference-free** — the only kind of score an agent can compute on its own output at runtime |
| Regression tripwire | [`mjpost/sacrebleu`](https://github.com/mjpost/sacrebleu) | **Apache-2.0** | Reproducible, version-stamped. A tripwire, **not** a gate |
| Glossary/format QA | [`translate/translate`](https://github.com/translate/translate) (`pofilter`) | GPL-3.0 | Run as a **CLI in a pipeline** (separate process, invoked not linked) so copyleft stays contained |
| Pre-release layout check | [`tryggvigy/pseudo-localization`](https://github.com/tryggvigy/pseudo-localization) | **MIT** | Finds hard-coded strings and layout breakage **before** a translator is paid |
| Localisation CI agent | [`lingodotdev/lingo.dev`](https://github.com/lingodotdev/lingo.dev) | **Apache-2.0** (in `LICENSE.md`) | Extract → translate → open PR, with **your own model** (`model: "anthropic/claude-sonnet-4.5"`) |
| India 22-language path | [`AI4Bharat/IndicTrans2`](https://github.com/AI4Bharat/IndicTrans2) | **MIT** | Covers exactly the **Eighth Schedule** set DPDP §5(3) names |
| Human escalation (Brazil) | `humanlayer/humanlayer` *(already in this KB)* | — | Decree 13,135/2026 requires a real-time human path |

### Wiring

```
                        ┌──────────────────────────────────────┐
  customer utterance ──▶│ lingua-py  →  locale + script        │
                        └──────────────┬───────────────────────┘
                                       ▼
                  ┌────────────────────────────────────────────┐
                  │ STAGE 1 · ANALYSIS agent                    │
                  │ pull glossary + TM for THIS locale from     │
                  │ Pontoon; mark which terms are in scope      │
                  └────────────────┬───────────────────────────┘
                                   ▼
                  ┌────────────────────────────────────────────┐
                  │ STAGE 2 · GENERATION agent                  │
                  │ answer in target locale, glossary INJECTED  │
                  │ output as MF2 messages, never concatenation │
                  └────────────────┬───────────────────────────┘
                                   ▼
                  ┌────────────────────────────────────────────┐
                  │ STAGE 3 · POST-EDIT agent                   │
                  │ glossary re-injected (NOT assumed held)     │
                  │ + pofilter + MF2 parse must both pass       │
                  └────────────────┬───────────────────────────┘
                                   ▼
                  ┌────────────────────────────────────────────┐
                  │ STAGE 4 · REVIEW agent (reasoning-enabled)  │
                  │ CometKiwi score + glossary term validation  │
                  └────────────────┬───────────────────────────┘
                                   ▼
                    ┌──────────── GATE ─────────────┐
            QE ≥ θ AND 100% glossary terms valid    │  else
            AND locale ∈ auto-approve set           │   ▼
                    │                        ┌──────────────────────┐
                    ▼                        │ Pontoon suggestion   │
             render to customer              │ queue → HUMAN review │
             + evidence record               └──────────┬───────────┘
                                                        ▼
                                              approved → TM → reused
```

### Build order — and the order is the deliverable

1. **Pseudo-localise the existing UI first.** `pseudo-localization` over the current product, before
   any agent work. It finds hard-coded strings and layout breakage in hours, and it tells you
   whether this is a two-week project or a two-quarter one. Skipping this is how the estimate is
   wrong.
2. **Stand up Pontoon and import the client's existing glossary.** If they have none, the first
   deliverable is the glossary — 50–200 brand, product and legal terms. **Do not** let the agent
   invent it; it is a client sign-off artefact.
3. **Fix the message format before generating anything.** Convert the target surfaces to MF2.
   Generated strings multiply a format problem by volume.
4. **Wire detection + the four stages**, glossary re-injected at each.
5. **Calibrate the gate on a held-out set the client's reviewers score by hand.** θ is **derived,
   not chosen**: pick it so that auto-approved output matches reviewer-accepted output at the rate
   the client's brand owner will sign. Record the number and the date.
6. **Turn auto-approval on for one locale only**, then widen by measurement.
7. **Attach the evidence record** (below) before go-live, not after the first complaint.

### The gate, stated so it can be audited

Auto-approve **only** when all four hold: **(a)** reference-free QE ≥ θ, **(b)** **100%** of in-scope
glossary terms present and correctly formed, **(c)** the MF2 message parses and its plural/gender
categories are complete for the target locale, **(d)** the locale is in the client-approved
auto-approve set. Anything else becomes a **Pontoon suggestion for a human**. Every TMS in this
layer models machine output as a *suggestion* precisely because it has always needed review —
Receta 30 uses that data model as the control rather than working around it.

**The agent must never call the approval endpoint.** An agent that approves its own wording turns the
only control in this layer into a logging step.

### The evidence record — one row per customer-facing utterance

`timestamp · conversation id · detected locale · rendered locale · model + version · glossary
version · MF2 message id · QE model + score · glossary validation result · auto-approved or
reviewer id · AI-disclosure string rendered (EU) · human-escalation offered (BR)`

This single row is what answers all four regional duties, and it is why the receta is worth more
than a translation feature: **Québec** (was functionally equivalent French served?), **EU Art. 50**
(was the disclosure rendered?), **India DPDP §5(3)** (was the notice available in the principal's
language?), **Brazil 13,135/2026** (was a real-time human path offered?). Without the record each
answer is an opinion.

### Licence posture

Permissive throughout the **generation and scoring** path: Pontoon **BSD-3-Clause**, CTranslate2
**MIT**, COMET/sacreBLEU **Apache-2.0**, lingua-py **Apache-2.0**, messageformat **MIT**, ICU/CLDR
**Unicode-3.0**, IndicTrans2 **MIT**, lingo.dev **Apache-2.0**. Two conditions to honour and one to
avoid:
- **Opus-MT models are CC-BY-4.0** → **attribution belongs in the client's notices file.**
- **`pofilter` is GPL-3.0** → invoke as a **subprocess**, do not link.
- ❌ **Do not substitute NLLB weights.** `stopes`/`fairseq` are MIT but the checkpoints are reported
  **CC-BY-NC-4.0 (non-commercial)** — ⚠️ secondary-sourced, `huggingface.co` unreachable from this
  session. Every file in the repo will say MIT while a non-commercial model does the translating.
- ❌ **Do not use Tolgee as the TMS.** Its `ee/` tree is **non-commercial** and forbids managed
  service provision.

### What to tell the client the limits are

1. **99.4% is the published terminology bar, not a guarantee** — and it is terminology accuracy, not
   correctness of meaning.
2. **θ is a business decision**, calibrated on their reviewers' judgments, revisited when the model
   changes. A model upgrade **invalidates the calibration**.
3. **Reference-free QE scores content, not liability.** Legally operative sentences — pricing, safety,
   consent, contractual terms — stay on the human path regardless of score.
4. **MF2's `u:` namespace and some default functions are still Draft.** Most of the standard is
   stable and recommended; that part may still move.
5. **This does not make the agent lawful by itself.** It makes the language defensible and the
   evidence available. The regional duties in `intel/market.md` are **secondary-sourced** and need
   the client's counsel.

### Anti-patterns — each one observed in this pass's evidence

- **"BLEU ≥ X" as the acceptance criterion.** The one metric whose own reference implementation's
  ecosystem shows it inverting against human preference on agentic pipelines.
- **Injecting the glossary once, in the system prompt.** This is the mid-80s plateau. AIDAterm's
  result comes from injecting at **every** stage.
- **String concatenation for generated text.** `"You have " + n + " messages"` cannot be translated
  correctly into languages with non-trivial plural rules. MF2 exists for this.
- **Detecting language with fastText because it has 26,502 stars.** Archived 2024-03-22. cld3 too
  (2023-05-24).
- **Taking "Apache-2.0" from Tolgee's badge.** Its root `LICENSE` is a multi-licence declaration and
  `ee/` is non-commercial.
- **Benchmarking on FLORES without saying it is archived** (2023-11-20).
- **Letting the agent approve its own wording.** The control becomes a log line.

---

## Receta 31 — The French-equivalence audit: proving an agent estate meets a per-utterance language duty (added sixteenth pass, 2026-11-24)

**Why this is a separate receta.** Receta 30 **builds** a governed language pipeline — weeks to
months. This one **measures an estate the client already runs** and produces a defensible record in
**two to three weeks**. It is the door-opener, because the Québec deadline has **already passed**
(final provisions in force **2025-06-01**) and the EU Art. 50 date has too (**2026-08-02**). A
client in breach today buys an audit faster than a platform.

### The question it answers, in the regulator's own terms

Not "is the agent translated?" but **"is a functionally equivalent French version being served to
this user, in this conversation, every time?"** Reported duty: where a French version of software
exists and has been commercially released, non-French versions may be sold in Québec only if a
**functionally equivalent French version** is offered; for employee-facing tools, if the vendor
offers French, the employer must make it available. ⚠️ **Secondary-sourced** (law-firm and vendor
commentary) — verify against the Charter and the OQLF.

**Functional equivalence is where agents fail, and it is testable.** Four failure modes, each a test:

| Failure | Test | Component |
|---|---|---|
| Agent answers English to a French prompt | detect language of **every turn**, compare to rendered language | `lingua-py` (Apache-2.0) |
| Agent starts French, drifts to English mid-conversation | per-**turn** comparison, not per-session | same |
| French path loses a feature or tool | run the **same task script** in both locales, diff tool calls and outcomes | harness |
| French output is grammatically degraded | **reference-free QE** per locale, compare distributions | CometKiwi (Apache-2.0) |

### Wiring

```
  task script (N scenarios × both locales)
        │
        ▼
  agent under test ──▶ turn log ──┬─▶ lingua-py       ─▶ language match per turn
                                  ├─▶ CometKiwi       ─▶ quality per locale
                                  ├─▶ tool-call diff  ─▶ feature parity
                                  └─▶ MF2 parse       ─▶ plural/gender completeness
        │
        ▼
  conformance record ──▶ per-locale gap list, ranked by customer exposure
```

### Steps

1. **Inventory the estate.** Every agent surface with customer or employee contact, and the locales
   each claims. Half the findings are usually here: surfaces nobody listed.
2. **Write 20–40 task scenarios** from the client's real top intents — not synthetic prompts.
3. **Run each in both locales**, logging every turn.
4. **Score the four tests.** Language match is the headline; **feature parity is the one that
   surprises people**, because a French path that silently loses a tool is a non-equivalent version
   even when every sentence is perfect French.
5. **Rank gaps by customer exposure**, not by ease of fix.
6. **Deliver the record plus the remediation plan** — and the plan is Receta 30, scoped to the gaps
   actually found.

### Deliverables, and the sentence that sells it

A **per-locale conformance record** (the same row shape as Receta 30), a **ranked gap list**, and a
**reproducible harness the client keeps and re-runs in CI**. The sentence: *"You can currently
answer, with evidence, the question of whether a Québec user was served a functionally equivalent
French experience in each of the last N conversations — or you cannot, and the deadline was
2025-06-01."*

### Extending it to the other three regions, at marginal cost

The harness is the same; only the assertion changes. **EMEA:** was the Art. 50 AI disclosure rendered,
in which language (**open question** — see the EMEA gap in `intel/market.md`), and is the client the
**provider** for that agent. **APAC:** can the data principal view the notice in **any of the 22
Eighth Schedule languages** (IndicTrans2, MIT, is the remediation path). **LATAM:** was a **real-time
human path** offered, per Brazil Decree 13,135/2026 — effective ≈**2026-11-02**. One harness, four
regional assertions, four conversations with four different buyers.

### Anti-patterns for this receta

- **Auditing per session instead of per turn.** Drift is the common failure and per-session sampling
  hides it.
- **Testing only text quality.** Feature parity is half the legal definition.
- **Reporting a score instead of a record.** The duty is per-utterance; a single percentage is not
  evidence.
- **Promising the EU language question is settled.** This pass searched for it and **found no
  evidence either way.** Say so — it is a cheap question for the client's counsel and an expensive
  thing to guess.
