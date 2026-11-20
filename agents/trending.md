---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 📈 Agentes trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

## 2026-11-20 — sixth pass (latest)

**Headline: the agent an enterprise asks for first was missing from this file entirely, and its
second most-starred implementation has been archived since March.**

Five passes catalogued the agent as a *general* thing — harnesses, frameworks, UI surfaces,
governance. This pass searched by **first client request** instead: what does an enterprise ask
for in meeting one? The answer is always some version of *"let us ask our data a question in
English."* That is a distinct agent category with its own benchmark literature and its own
licence traps, and this KB had none of it.

**New this pass — four live data agents (full table in `agents/top.md`, Tier 2):**

| Agent | Licence | ★ | Origin |
|-------|---------|---|--------|
| [mindsdb/mindsdb](https://github.com/mindsdb/mindsdb) | MIT | 39.9k | North America |
| [eosphoros-ai/DB-GPT](https://github.com/eosphoros-ai/DB-GPT) | MIT | 20.3k | APAC (China) |
| [Canner/WrenAI](https://github.com/Canner/WrenAI) | Apache-2.0 (all code paths) | 18.4k | APAC (Taiwan) |
| [XGenerationLab/XiYan-SQL](https://github.com/XGenerationLab/XiYan-SQL) | Apache-2.0 | 1.0k | APAC (China) |

**Three of the four are APAC-origin.** That is the second time this KB has measured APAC as the
origin region for a whole agent category (the third pass found `deer-flow` the same way), and it
is now a pattern worth stating in a capability deck rather than a coincidence.

**The die-off, continuing last pass's finding:** [vanna-ai/vanna](https://github.com/vanna-ai/vanna)
(MIT, 23.8k ★) was **archived by its owner on 29 March 2026 and is read-only** — nearly eight
months. It is the second most-starred project in the category. Last pass found three archived
chat-UI repositories whose READMEs did not disclose it; this pass found a fourth archived
project in a different layer. **Standing method change: `archived` status is now checked for
every repository this KB recommends, every pass.** Stars do not decay when a project dies, so
star-sorted search actively leads a client to dead code.

**Licence finding — WrenAI, and a correction to the public record.** Secondary sources describe
WrenAI as "Apache 2.0 core with AGPL modules" and some mirrors report it as AGPL-3.0 outright.
**Neither is accurate today.** Its `LICENSE` is an explicit path→licence map: `core/**`,
`sdk/**`, `skills/**`, `examples/**` and the root files are **all Apache-2.0**; `docs/**` is
CC-BY-4.0; the AGPL-3.0 text is shipped **pre-emptively and currently applies to zero paths**.
So: Globant can build on all of it today, *and* the path map is the thing to re-read each pass,
because the project has told us in writing that it intends to add AGPL modules later. That is
the honest statement, and it is neither of the two wrong ones. WrenAI's licence file also states
that **the package manifest is authoritative where it disagrees with the licence file** —
independent corroboration of the manifest-first rule this KB's energy pass derived.

**What did not change:** Tier 0 and Tier 1 are untouched again — the fourth consecutive pass
where the framework choice did not move. The agent is still the least consequential decision
on the page.

---

## 2026-11-20 — fifth pass

**Headline: three of this layer's best-known repositories are archived, and their READMEs do not
say so.** This pass searched the one surface the previous four never touched — **where the agent
meets the human** — and the first thing it measured was a die-off. The GitHub search API reports
`archived: true` for [Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0,
12,498 ★ — the most-recommended Python conversational-AI shell in the market),
[langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★) and
[langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui) (MIT, 1,705 ★).
LangChain has archived **both** of its agent UI repositories.

**Evidence quality, stated because the conclusion is strong:** the `archived` flag comes from the
GitHub search API, re-queried twice. The github.com HTML page returns **403 from this
environment**, so that channel could not cross-check it, and **none of the three READMEs carries
a deprecation notice** — an engineer reading the README would not know. Corroborating signal for
Chainlit only: a PyPI fork surfaced in this pass's web search states the original Chainlit team
is no longer maintaining the project. Treat "archived" as well-founded; treat "and therefore
dead" as a judgement.

**What the pattern means, and it is not a coincidence.** Sort this layer by shape rather than by
stars and the archived repos are all the *same* shape — a **standalone chat window placed in
front of an agent**. Every live, actively-pushed repository in the layer is the *other* shape:
the agent **renders into the client's existing application** using that application's own
components. The chat shell as a product category is being abandoned in favour of in-app
generative UI. For an engagement this is the difference between a deliverable the client's users
must navigate to and one that appears inside the screen they already work in.

### The agent-to-user interaction layer — zero prior coverage in this KB

Verified today against the GitHub API; every licence below was additionally **read from the
repository's `LICENSE` file**, not taken from the badge.

| Repo | Licence (file-read) | ★ | Forks | Pushed | What it is |
|------|---------------------|---|-------|--------|------------|
| [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) | MIT | 38,842 | 4,839 | 2026-11-20 | The frontend stack for agents and generative UI (React, Angular, mobile, Slack). Authors of the AG-UI protocol. |
| [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | MIT | 20,766 | 2,129 | 2026-11-20 | **AG-UI: the Agent-User Interaction Protocol.** The third leg of the protocol triad — MCP for tools, A2A for agent-to-agent, AG-UI for agent-to-user. |
| [vercel-labs/json-render](https://github.com/vercel-labs/json-render) | Apache-2.0 | 19,791 | 1,059 | 2026-11-19 | "The Generative UI framework" (Vercel). |
| [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | Apache-2.0 | 17,690 | 1,432 | 2026-11-20 | **A2UI — Google-origin**, announced 15 Dec 2025, 1.0 released. Agent streams **layout data, not code**; the client holds a catalog of pre-approved components and the agent may only request from it. |
| [thesysdev/openui](https://github.com/thesysdev/openui) | MIT | 15,375 | 1,026 | 2026-11-20 | "The Open Standard for Generative UI" — a third contender for the same slot. |
| [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) | MIT | 13,351 | 1,353 | 2026-11-20 | TypeScript/React library for AI chat; the live option where the archived LangChain UIs used to be. |
| [tambo-ai/tambo](https://github.com/tambo-ai/tambo) | MIT | 11,221 | 577 | 2026-11-18 | Generative UI SDK for React. |
| [CopilotKit/openfuse](https://github.com/CopilotKit/openfuse) | MIT | 6,544 | 964 | 2026-11-20 | Reference personal agent (browser, terminal, files) built on CopilotKit — a worked example, not a platform. |
| [flyerhq/flutter_chat_ui](https://github.com/flyerhq/flutter_chat_ui) | Apache-2.0 | 2,381 | 864 | 2026-11-19 | The mobile answer: Flutter chat/agent SDK. Relevant wherever the client's workforce is phone-first. |

**Archived — do not start here, and check whether a client already did:**
[Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★,
**archived**, last push 2026-09-18, Paris-origin),
[langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★,
**archived**), [langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui)
(MIT, 1,705 ★, **archived**). Also stale but not archived:
[agno-agi/agent-ui](https://github.com/agno-agi/agent-ui) (MIT, 1,879 ★, last push
**2026-05-08** — six months).

### Human approval as a component, not a code review habit

| Repo | Licence | ★ | Pushed | Note |
|------|---------|---|--------|------|
| [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) | Apache-2.0 (file-read) | 12,919 | 2026-11-16 | Approval/escalation layer: the agent requests a human decision as a typed call rather than a prompt asking nicely. |
| [humanlayer/12-factor-agents](https://github.com/humanlayer/12-factor-agents) | **Apache-2.0 — read from the file; GitHub reports `NOASSERTION`** | 27,343 | 2025-09-21 | The design-principles document the market quotes. The licence file is the **unmodified** 199-line Apache-2.0 text with no added clauses, so an enterprise *may* adopt it internally — a question clients do ask. **Content is 14 months stale.** |
| [humanlayer/fold](https://github.com/humanlayer/fold) | MIT | 187 | 2026-10-23 | Provider-agnostic agent core; small, listed for completeness. |

This is the T46 probe paying off again: a 27,343-star repository reported `NOASSERTION` turned
out to be plain, unaltered Apache-2.0. Three passes of this KB have now found the same class of
error. **GitHub's licence badge is a hint; the file is the answer.**

### Agents managed as a workforce — a 115,408-star MIT repo this KB never mentioned

| Repo | Licence | ★ | Forks | Pushed | Note |
|------|---------|---|-------|--------|------|
| [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT (**`LICENSE` is on `master`, not `main`**) | 115,408 | 19,156 | 2026-11-20 | "The open-source app everyone uses to manage agents at work." More starred than every framework in `agents/top.md` Tier 1 combined. |
| [NousResearch/hermes-paperclip-adapter](https://github.com/NousResearch/hermes-paperclip-adapter) | MIT | 2,065 | 404 | 2026-04-04 | Runs Hermes "as a managed employee in a Paperclip company" — the shape the market is converging on: agents with a manager, a role and a review surface. |

Note the branch trap, which is the exact failure the fourth pass recorded: `paperclip`'s licence
file exists only on `master`. A probe that reads `main/LICENSE` and stops concludes a
115k-star repository is unlicensed.

### Searched and not found this pass

- **No LATAM-origin repository in the interaction layer.** The sweep's results were
  NA-origin (CopilotKit/Seattle, Vercel, Google, tambo) with one EMEA entry (Chainlit, Paris —
  and archived) and one APAC implementation (ByteDance's Lynx renderer for A2UI, Jun 2026).
  **Honest limit: this pass did not run a Spanish/Portuguese-vocabulary sweep**, so this is a
  gap in the measurement, not a measured zero. Next LATAM pass should run it before quoting a
  number.
- **Org location is unverifiable from this environment.** The `users/{org}` endpoint returns
  403 ("sessions are bound to their configured repositories"); only `search/repositories`
  works. Every region-origin attribution in this pass comes from web-search evidence about
  the company, not from GitHub metadata. Do not quote origin ratios to a client.
- **No foundation steward for the agent-to-user layer.** Searched; none exists. MCP, goose,
  AGENTS.md and the control plane are all under the Linux Foundation's AAIF. AG-UI is a
  vendor-held MIT protocol (CopilotKit, $27M Series A, May 2026) and A2UI is a Google-origin
  Apache-2.0 project. See `intel/trends.md` §15.


## 2026-11-20 — fourth pass

**Headline: the agent layer and the control plane are now both covered, and the thing still
missing was consequence. What is this agent allowed to *do* — spend money, read personal data,
believe a table?** Those three questions each turned out to be a layer this KB did not have.

The first three passes today moved through the stack in order: Tier-0 harnesses (pass 1), the
skill supply chain (pass 2), the control plane — gateway, quotas, cost, red-teaming (pass 3).
Each pass found the previous one had been looking one level too high. This pass went one level
*past* the control plane, to the blast radius, and found **sixteen repositories absent from the
KB entirely**, across four layers: agent payments, PII de-identification, catalog/lineage, and
graph RAG. The tables are in `repos/foundations.md`; the trend reading is in `intel/trends.md`
§13 and §14.

**1. There is now a payments layer, and it is not ready — which is itself the finding.**
Three permissively-licensed protocols compete at different layers:
[AP2](https://github.com/google-agentic-commerce/AP2) (Apache-2.0, 3,281 ★),
[ACP](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) (Apache-2.0,
1,607 ★) and the [A2A x402 extension](https://github.com/google-agentic-commerce/a2a-x402)
(Apache-2.0, 571 ★). **AP2 has 5.7× the stars of the x402 extension and has not been pushed
since 2026-06-17; the extension was pushed 2026-11-11.** The star ranking inverts the activity
ranking inside one protocol family. The client-facing consequence is specific: *the signed-mandate
model is the durable idea, the settlement rail is still contested, and no agent should reach a
payment rail in 2026 without a human approval step.* Anyone who says "AP2 is the standard" is
reading stars, not commits.

**2. Agent identity is the unsolved half of agent payments.** The payment specs answer *how
much* and *on whose mandate*; none answers *is this agent who it claims to be*.
[forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol)
(MIT, 180 ★) is the only entry addressing it, and it is small. This connects directly to the
workload-identity section already in `repos/foundations.md` (SPIFFE) — the same problem, now
with money attached, which is how it gets budget.

**3. Presidio left Microsoft.** The de facto PII engine is now
[data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) (MIT, 11,989 ★),
not `microsoft/presidio`. Evidenced rather than assumed: the old path still serves files, but
`LICENSE` from both paths is **byte-identical (1,083 bytes, md5 `cef898d1…`)**, four other paths
return 200 on both, the copyright line now reads **"Presidio Contributors"**, and the search
index carries only the new org. **A redirect, not a deletion** — so existing installs keep
working, and that is exactly why nobody notices. Fourth repo in two passes to change
organisation; see the rename ledger.

**4. The data catalog category rebranded itself as agent infrastructure.**
[OpenMetadata](https://github.com/open-metadata/OpenMetadata) (Apache-2.0, 15,823 ★, **new to
this KB**) calls itself "The Open **Context Layer** for Data and AI";
[DataHub](https://github.com/datahub-project/datahub) (Apache-2.0, 13,006 ★) calls itself "The
**Context Platform** for your Data and AI Stack". Two independent vendors, pushed the same day,
converging on the same word. For an agent that writes to a system of record, the catalog is what
says which table it may *believe*, and lineage is how you answer "where did this number come
from?" after it has already acted. Commercially this is the best news in the pass: it is usually
**already installed** at the client.

**5. A 36,699-star MIT repo was missing.** [microsoft/graphrag](https://github.com/microsoft/graphrag)
had zero mentions across all eight files. Vector search finds the passage; graph retrieval answers
what connects entities across a whole corpus — an entity's exposure across contracts, suppliers or
incidents, which is the shape of the questions clients actually ask. **Scope the graph-construction
indexing cost explicitly**; it is paid per corpus, re-paid on refresh, and clients do not expect it.

**6. ISO/IEC 42001 is moving from a standard to cite to a gate you pass.** The KB already named it
as a standard to anchor on. The new reading is procurement: buyers are reported to be scoring it in
vendor questionnaires and RFPs, and to be asking for the **scope statement and sample risk
registers**, not just the certificate. Sources disagree on mandatory versus preferred, and
certification is reported to take **6–18 months** — so it is a pipeline question for Globant now,
not a 2027 one. Recorded with its disagreement intact in `intel/trends.md` §14.

**7. LATAM-origin: fifth consecutive zero, now measured in four new layers.** Payments, PII,
catalog and graph RAG were each searched in English, Spanish and Portuguese. Everything returned
was 0–3 stars and **NOASSERTION** — no usable licence. The gap is measured, not unexamined, and it
is the same answer five passes running.

**Evidence standard for this pass:** 16/16 licences read from each repository's own `LICENSE` over
`raw.githubusercontent.com`, none taken from a GitHub badge. Every non-GitHub host still fails to
resolve in this session, so **every market statistic below and in `intel/` remains second-hand** and
is attributed rather than asserted.

## 2026-11-20 — third pass (later still)

**Headline: the agent choice stopped being the interesting decision. The control plane is the
decision, and this KB did not have one.**

The earlier two passes today tracked the agent layer (Tier 0 harnesses) and the skill supply
chain. This pass went looking for the *traffic* layer — where a model or tool call is actually
authorised, routed, rate-limited, attributed and paid for — and found that the KB had no entry
for it at all. Not a thin section: nothing. No gateway, no quota point, no usage attribution,
no cost governance, no red-teaming, no eval-in-CI, no OpenTelemetry instrumentation. Six
sections now exist in `repos/foundations.md`; the twelve most important repositories were
absent from this KB entirely.

That gap is also the market's. **IDC FERS Wave 4 (July 2026): 95% of enterprises run at least
one company-funded agent-enabled workflow in production, and only 45.4% have real-time
dashboards tracking token consumption by workflow** — while **61.8% rate their own cost
governance as "defined" or "optimizing".** Self-assessment is running well ahead of
instrumentation, which is the most sellable gap in this KB.

**1. Envoy AI Gateway became Agent Router, and joined the Agentic AI Foundation.** The single
most consequential discovery of the pass:

| Repo | License | Stars | Pushed | What changed |
|------|---------|-------|--------|--------------|
| [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 | 2,423 | 2026-11-19 | "The open source control plane for AI and agent traffic, powered by Envoy." **Formerly Envoy AI Gateway.** Now an **Agentic AI Foundation** project under LF Projects, LLC — `README`: *same code, same maintainers, same release cadence and Apache 2.0 license*. |

Why it matters beyond the rename: the AAIF now stewards **MCP, goose, AGENTS.md and the
control plane**. `intel/market.md` flagged that the agent-governance toolchain this KB
recommends is almost entirely NVIDIA's, including a repo whose vendor-neutral org name hides an
NVIDIA copyright. Agent Router is the **structural mitigation** — Apache-2.0, Envoy-based,
foundation-governed. For the first time a client can be told that the layer holding their
model credentials is not owned by a single vendor, and have it be true.

**2. The gateway field, verified and licence-read.** All metadata from the GitHub search API on
2026-11-20; carve-outs read from each `LICENSE`:

| Repo | Real license | Stars | Note |
|------|--------------|-------|------|
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT core + `litellm/enterprise/` carve-out** | 63,615 | The adoption leader; now a Rust core with a Python SDK. Virtual keys, spend tracking and budgets are in the MIT core — SSO/RBAC reportedly are not. |
| [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 | 44,402 | "The API and AI Gateway." Core permissive; AI features reportedly enterprise-gated — verify per feature. |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | **MIT, no carve-out found** | 13,421 | 1,600+ LLMs and **50+ guardrails enforced at the gateway**, not in application code. Cleanest licence in the category. |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 | 9,818 | LLM gateway and MCP gateway in one. Much of the comparative praise is published by its own vendor — discount accordingly. |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 | 6,291 | Observability-first. **Not** to be confused with `Helicone/ai-gateway` — **GPL-3.0, 647 ★, last pushed 2025-11-21**. |

**3. Cost governance is now a governance control, not a finance report.** New, and it is the
pass's commercial thesis — see `intel/trends.md` trend 12. **Gartner: spend on AI models and
platforms +63.4% YoY to $64B in 2026. FinOps Foundation: 98% of FinOps practitioners now manage
AI spend, up from 31% two years ago. EY: agentic AI converts fixed labour cost into variable
compute consumption**, and predicts 40% of agentic projects cancelled by 2027 (a prediction,
not a measurement). **McKinsey's framing is the one to use in a pitch: the unit of governance
should be the completed business outcome, not the token** — which is precisely how Globant's
**Glob.AI** already bills. The permissive tooling exists:
[openmeterio/openmeter](https://github.com/openmeterio/openmeter) (Apache-2.0, 2,457 ★) for
metering and entitlements, [opencost/opencost](https://github.com/opencost/opencost)
(Apache-2.0, 6,824 ★) for the GPU and pod cost that token counting never sees.

**4. Three large MIT agent repos were simply missing from this KB.** Recorded plainly, because
it is the same method failure the second pass admitted to — tracking frameworks by name misses
new shapes:

| Repo | License | Stars | Why it belongs |
|------|---------|-------|----------------|
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121,597 | AI browser agents. The answer when the client's "integration surface" is a vendor web portal with no API — insurance, logistics, public-sector filing. |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | MIT | 85,545 | "Long-horizon SuperAgent harness." **APAC-origin.** A fourth MIT harness larger than every Tier-1 framework. |
| [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | Stateful agents with learning memory (MemGPT lineage). **Pushed 2026-10-18** — verify activity. |

**5. Red teaming exists, is permissive, and has one licence trap.** Static skill scanning is
already being bypassed (see the second pass below); the dynamic control is adversarial testing.
[NVIDIA/garak](https://github.com/NVIDIA/garak) (Apache-2.0, 10,114 ★) and
[microsoft/PyRIT](https://github.com/microsoft/PyRIT) (MIT, 4,980 ★) are both real and active —
**note PyRIT moved**: `Azure/PyRIT` is the stale old home at 128 ★ / 2026-03-25.
[promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) (MIT, 27,494 ★) does eval **and**
red-teaming and is built to run as a CI gate. **The trap:**
[meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) (4,486 ★) is routinely
proposed as an open guardrail — its `LICENSE` is the **Llama 3.2 Community License Agreement**,
not OSI open source. GitHub shows it as `NOASSERTION`, which is why the mistake is common.

**6. Two more unusable-at-scale repositories, and one mis-scoped one.**
[daytonaio/daytona](https://github.com/daytonaio/daytona) — infrastructure for running
AI-generated code, **71,307 ★** — has **no `LICENSE` file** and was last pushed 2026-07-24.
[getzep/zep](https://github.com/getzep/zep) (Apache-2.0, 5,010 ★) still gets scoped as
self-hosted memory; its `README` now reads *"Zep: Examples and Integrations"* and Zep itself is
a hosted product. For self-hosted memory use
[topoteretes/cognee](https://github.com/topoteretes/cognee) (Apache-2.0, 33,431 ★) or Mem0.

**7. Method note that paid for itself: three of ~35 repos checked had moved, two changed
organisation.** Envoy AI Gateway → Agent Router, `Azure/PyRIT` → `microsoft/PyRIT`,
`explodinggradients/ragas` → `vibrantlabsai/ragas`. An ownership change is a supply-chain event,
not a cosmetic one. Full ledger in `repos/foundations.md`. **This is sellable as a
dependency-provenance review line item.**

**Verification note.** Every repository fact above is first-hand (search API metadata plus
`LICENSE` read from `raw.githubusercontent.com`). Every market figure is from WebSearch result
summaries and **not read at source** — this session's network policy resolves GitHub only;
`curl` and page fetches to Gartner, IDC, Menlo, OECD and Stanford all failed, so the same
caveat as the earlier passes applies, and several of the sources above are vendor or analyst
marketing.


## 2026-11-20 — second pass (later same day)

**Headline: the harness won, and it arrived carrying a skill supply chain nobody has
secured. This is the enterprise opening of the quarter.**

Earlier today this file recorded the foundation-governance story and treated OpenClaw as a
singular breakout. Both stand, but a wider sweep of the GitHub star ceiling shows the
category is now *three* MIT harnesses of comparable scale plus an enormous, largely
ungoverned skills economy on top of them.

**1. Three harnesses, not one.** All verified today, licenses read from each `LICENSE` file:

| Harness | Repo | License | Stars | Pushed |
|---------|------|---------|-------|--------|
| OpenClaw | [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,891 | 2026-11-20 |
| DeepSeek Harness | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | MIT | 284,581 | 2026-11-18 |
| Hermes Agent | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT | 264,904 | 2026-11-20 |
| Deep Agents | [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) | MIT | 31,472 | 2026-11-20 |

DeepSeek Harness and Hermes Agent were **entirely absent from this KB** until this pass —
a 284k-star and a 264k-star MIT repository in the exact category the KB exists to cover.
Recorded plainly because it says something about method: the KB was tracking *frameworks*
by name and missed a new *category*.

**2. The skills economy is now the biggest thing on GitHub, and it is a supply chain.**
[openclaw/clawhub](https://github.com/openclaw/clawhub) (MIT, 9,557 ★) is the official
skill + plugin registry; [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills)
(MIT, 53,885 ★) curates **5,400+ skills** filtered from it. Individual skill collections are
larger still — [mattpocock/skills](https://github.com/mattpocock/skills) (MIT, 328,581 ★),
[obra/superpowers](https://github.com/obra/superpowers) (MIT, 322,580 ★),
[affaan-m/ECC](https://github.com/affaan-m/ECC) (MIT, 307,599 ★). Two of the biggest have
**no license at all**: [anthropics/skills](https://github.com/anthropics/skills) (197,931 ★)
and [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
(234,677 ★) — both checked against `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENSE-MIT` and
`COPYING` on `main` and `master`.

**3. NVIDIA quietly shipped the governance toolchain for all of it — Apache-2.0.** This is
the single most useful discovery of the pass, because it is exactly the layer Globant sells
and it is now permissively licensed and off the shelf:

| Repo | License | Stars | Role |
|------|---------|-------|------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 | 27,027 | Security scanner for agent skills — **71 vulnerability patterns across 17 categories** (read from its README; a secondary roundup said 64/16 — the README is authoritative). Covers prompt injection, data exfiltration, privilege escalation, memory poisoning, MCP tool poisoning, MCP least privilege. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 | 4,224 | Quality gates for skills: security scanning, harness-compatibility checks, semantic overlap detection, synthetic eval datasets, live agent evaluation. **Ships reusable CI templates.** |
| [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) | Apache-2.0 | 21,829 | "The safe, private runtime for autonomous AI agents" (Rust). Note: the neutral org name hides vendor provenance — its `LICENSE` reads **"Copyright (c) 2026 NVIDIA CORPORATION & AFFILIATES"**, and [NVIDIA/OpenShell-Community](https://github.com/NVIDIA/OpenShell-Community) (Apache-2.0, 193 ★) mirrors it. |
| [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | Runs Hermes, Deep Agents and OpenClaw inside OpenShell with managed inference — the bridge from a developer's harness to a governed one. |
| [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 | 254 | Multi-language agent runtime: execution-scope management, lifecycle events and **middleware on tool and LLM calls** — i.e. the interception point where a policy decision can actually be enforced. |
| [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 | 14,026 | Semantic, graph-based reasoning layer over data: deterministic query generation, better retrieval, explainable agent workflows. |

**4. The research says the scanners are already being bypassed.** Figures below come from
WebSearch result summaries — **this session's network policy allows GitHub only, so the
underlying papers could not be opened and these are second-hand**. Flagged as such rather
than dropped, because the direction is consistent across four independent samples:
an arXiv study (2601.10338, Jan 2026) analysing **31,132 skills found 26.1% with at least
one vulnerability** across 14 patterns; Snyk's *ToxicSkills* research found **36% of 3,984
ClawHub skills contained prompt-injection techniques**; a third analysis of the same sample
put **critical-severity flaws at 13.4%**; a fourth found **80% of skills had a mismatch
between declared and actual behaviour** (mostly bad documentation, not malice). And on the
defences: Trail of Bits reportedly bypassed the malicious-skill detectors of ClawHub, Cisco
and Vercel's skills.sh, and the Cloud Security Alliance notes **five malicious skills evaded
updated ClawScan *and* VirusTotal between February and May 2026**. Consensus remedy is
layered: scan, pin provenance, check declared capability against observed behaviour, and
sandbox — because skills run with the agent's own OS permissions.

**So what, for an engagement:** every client who adopted a harness this year also adopted an
unaudited dependency tree of natural-language skills that execute with their agent's
privileges. Nobody sold them a control for it. SkillSpector + SkillEvaluator + OpenShell are
Apache-2.0 and exist today. That is a scoped, demonstrable, repeatable engagement — written
up as `compose/patterns.md` **Receta 7**.

*Regional note:* every repo in this section is Global or North-America-origin (NVIDIA,
LangChain, Nous Research) or APAC-origin (DeepSeek). **No EMEA-origin and no LATAM-origin
project appears anywhere in the harness or skill-security layer** — searched
`agentes IA empresa` (one hit, 38 ★, unlicensed) and the `latam-gpt` org (8 repos, 7 of them
unlicensed, most last pushed in 2024–2025). A measured absence, not an unchecked one.

---

## 2026-11-20

**Headline: agent governance moved from vendor to foundation, and it is visible in the repo URLs.**

- **Block's `goose` now lives at [aaif-goose/goose](https://github.com/aaif-goose/goose)**
  (Apache-2.0, 56,815 ★). The org prefix is the story: the project has moved under the
  Linux Foundation's **Agentic AI Foundation (AAIF)**, formed 9 Dec 2025, to which
  Anthropic donated MCP and OpenAI donated AGENTS.md. Any integration pinned to the old
  `block/goose` path needs updating.
- **AGENTS.md became its own governed standard**: [agentsmd/agents.md](https://github.com/agentsmd/agents.md)
  (MIT, 25,620 ★) — a single open format for instructing coding agents, now the de facto
  way to ship repo-level agent context to a client's codebase.
- **MCP is relicensing MIT → Apache-2.0.** The `LICENSE` of
  [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
  (92,133 ★) now opens by declaring the transition explicitly. Consistent with the
  foundation move; Apache-2.0's patent grant is the enterprise-relevant part.
- **AutoGen is effectively over as a starting point.** [microsoft/autogen](https://github.com/microsoft/autogen)
  (61,955 ★) has not been pushed since 2026-11-12 and GitHub reports its license as
  CC-BY-4.0. Successors: [ag2ai/ag2](https://github.com/ag2ai/ag2) (Apache-2.0, 5,076 ★)
  and Microsoft Agent Framework — **but see the MAF 404 gap in `agents/top.md`.**
- **PraisonAI repositioned onto regulated industries**: its description now reads
  "Private AI agents for highly regulated teams" ([MervinPraison/PraisonAI](https://github.com/MervinPraison/PraisonAI),
  MIT, 9,365 ★). A small repo, but the clearest signal that 2026's differentiator is
  compliance posture rather than capability.
- **APAC frameworks are now top-tier, not followers.** [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope)
  (Apache-2.0, 36,363 ★) plus a dedicated JVM port
  [agentscope-ai/agentscope-java](https://github.com/agentscope-ai/agentscope-java)
  (Apache-2.0, 6,435 ★) — the Java port matters because APAC enterprise cores are JVM.
- **Observability consolidated into the data layer.** The `LICENSE` of
  [langfuse/langfuse](https://github.com/langfuse/langfuse) (37,671 ★) now carries
  **"Copyright (c) 2023-2026 ClickHouse, Inc."** — confirming ClickHouse's acquisition
  of Langfuse, announced 16 Jan 2026 alongside its $400M Series D. Langfuse core stays
  MIT with `ee/` carve-outs.

*Regional note:* every item above is Global or APAC-origin. **No LATAM-origin agent
project appeared in this week's sweep** — searching `agente IA empresa open source`,
`agentes IA español framework` and `ERP brasil open source nota fiscal` returned one
repo with 0 stars. That is a measured absence, not an unchecked one.

---

## Historical — 2026-07-02 (automated pipeline snapshot)

> Kept for trend history, deliberately fenced as plain text so the compiler does **not**
> ingest it as entities. These rows came from a keyword-matching ingest pipeline and are
> low quality — several are sub-10-star or unrelated to enterprise AI (an Excel-based farm
> ERP, a food-delivery suite). Superseded by the curated sections above.
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
