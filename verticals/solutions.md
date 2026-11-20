---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 🏭 Verticales de partida — Enterprise

> Real, running platforms a client already recognises, that can be customised with an
> agentic layer on top. The model: **start from something that already works, add agents
> above it** — never greenfield a back office.
>
> All rows verified against the GitHub API on 2026-11-20. Licenses shown are the *real*
> ones, read from each repo's `LICENSE` file where GitHub reported `NOASSERTION`.
>
> **Read the license column before scoping.** In enterprise the base platforms are mostly
> copyleft (GPL/AGPL/LGPL) while the agent layer is permissive. That asymmetry is the
> single most important commercial fact in this file: Globant's IP belongs in the agent
> layer, integrating over a documented API, not in a fork of the base platform.

## ERP & business suites

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Odoo | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (Community) | 55,981 | Python / PostgreSQL / OWL | The reference ERP to agent-enable. LGPL permits linking, so an external agent service over Odoo's XML-RPC/JSON-RPC API keeps Globant's code separate. |
| ERPNext | [frappe/erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | 41,472 | Python / Frappe / MariaDB | Full ERP. **APAC-origin (Frappe, Mumbai)** — the natural base for an India engagement. |
| Frappe Framework | [frappe/frappe](https://github.com/frappe/frappe) | **MIT** | 11,133 | Python / JavaScript | The permissive layer under ERPNext. Build custom apps here and the MIT license travels with them. |
| Apache OFBiz | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1,151 | Java / Groovy | Lowest star count here but the **only fully Apache-2.0 ERP+CRM+SCM suite.** When a client's legal team rejects copyleft outright, this is the answer. |

## CRM & customer platforms

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Twenty | [twentyhq/twenty](https://github.com/twentyhq/twenty) | **AGPL-3.0** (+2 qualifications) | 61,244 | TypeScript / NestJS / React | Self-described "open alternative to Salesforce, designed for AI". Strong demo value; AGPL means integrate over API, do not fork into a client product. |
| Krayin CRM | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | **MIT** | 24,186 | PHP / Laravel | Permissive CRM — rare. For a client that wants an owned, embeddable CRM, this is the cleanest license in the category. |

## Internal tools, workflow & BI

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Appsmith | [appsmithorg/appsmith](https://github.com/appsmithorg/appsmith) | Apache-2.0 | 41,281 | Java / TypeScript | Admin panels and internal tools, 25+ data integrations. Apache-2.0 — safe to ship. The fastest route to a human-in-the-loop console over an agent. |
| Huly | [hcengineering/platform](https://github.com/hcengineering/platform) | **EPL-2.0** | 28,156 | TypeScript / Svelte | All-in-one project management (Linear/Jira/Slack alternative). Note: EPL-2.0, **not** Apache-2.0 as commonly listed. |
| NocoBase | [nocobase/nocobase](https://github.com/nocobase/nocobase) | **Proprietary EULA** (NocoBase License Agreement, Singapore entity, rev. 2026-02-24) | 24,972 | TypeScript / Node | No-code platform for business systems. **Not open source** despite appearances — commercial terms required. Flagged so no one scopes against it by accident. |
| Budibase | [Budibase/budibase](https://github.com/Budibase/budibase) | **GPL-3.0, per-package** | 28,427 | TypeScript / Svelte | Apps, automations and agents for operations. License varies *per package* — check each one individually. |
| Frappe Insights | [frappe/insights](https://github.com/frappe/insights) | AGPL-3.0 | 1,046 | Python / Vue | BI over the Frappe/ERPNext data model. **APAC-origin.** |

## Knowledge, HR & front door

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Onyx | [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | **MIT core + `ee/` carve-out** | 33,484 | Python / React | Enterprise search and AI chat across every connector. The most reusable "day one" deliverable; keep strictly out of `ee/`. |
| Open WebUI | [open-webui/open-webui](https://github.com/open-webui/open-webui) | **Open WebUI License** (BSD-3 derivative + branding clause) | 159,142 | Python / Svelte | Self-hosted chat front end. The branding clause blocks silent white-labelling — read it before promising a client-branded UI. |
| Frappe HR | [frappe/hrms](https://github.com/frappe/hrms) | GPL-3.0 | 9,088 | Python / Frappe | Open source HR and payroll. **APAC-origin.** |

## Regional localisation — what makes a suite actually deployable

A base platform is only usable in a market once tax, invoicing and payroll comply locally.
This is the layer that decides whether an ERP engagement is possible at all, and it is
where the only **LATAM-origin** code in this KB lives:

| Localisation | Repo | License | Stars | Region |
|--------------|------|---------|-------|--------|
| Odoo Brazil (official OCA localisation) | [OCA/l10n-brazil](https://github.com/OCA/l10n-brazil) | AGPL-3.0 | 376 | LATAM |
| Odoo Argentina | [OCA/l10n-argentina](https://github.com/OCA/l10n-argentina) | AGPL-3.0 | 30 | LATAM |
| Odoo Mexico | [OCA/l10n-mexico](https://github.com/OCA/l10n-mexico) | AGPL-3.0 | 20 | LATAM |
| Odoo Chile | [OCA/l10n-chile](https://github.com/OCA/l10n-chile) | AGPL-3.0 | 10 | LATAM |
| OCA server tools | [OCA/server-tools](https://github.com/OCA/server-tools) | AGPL-3.0 | 968 | Global |
| India GST / compliance | [resilient-tech/india-compliance](https://github.com/resilient-tech/india-compliance) | GPL-3.0 | 286 | APAC |

`l10n-brazil` was pushed the same day this pass ran — it is genuinely maintained, not
abandoned. **All of it is AGPL-3.0**, so treat it as deployment infrastructure for the
client's own instance, never as a component inside a Globant product.

## Cómo customizar con AI — the pattern that survives the license

1. **Do not fork the base platform.** Run it stock; copyleft stays contained in the
   client's own deployment.
2. **Expose it as tools, not as a database.** Wrap the platform's existing API behind an
   MCP server and put [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge)
   (Apache-2.0) in front as the gateway and registry.
3. **Put the agent layer in a separate, permissive repo** — CrewAI / LangGraph / Agno.
   This is where Globant's IP lives and it stays MIT/Apache.
4. **Give the agent an identity, not a shared key** — Keycloak for identity, OPA or Cerbos
   for which tools it may call.
5. **Keep the human in the loop on writes.** Reads can be autonomous; anything that
   mutates an ERP record goes through an Appsmith (Apache-2.0) approval console.
6. **Localise last and separately.** Pull the OCA `l10n-*` module for the target country
   into the client's deployment; never vendor it into Globant code.
