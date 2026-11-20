---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 📈 Agentes trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

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
