---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 📈 Agentes trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

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
