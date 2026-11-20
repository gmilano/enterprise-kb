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
>
> **Second pass, 2026-11-20 (later same day):** process orchestration / BPM and ITSM &
> service-desk sections added, Dolibarr added to ERP, and Camunda's licence read in full —
> it is **not** open source, which matters because it now sells itself as an "Agentic
> Orchestration Platform" and will come up in exactly these conversations.
>
> **Third pass, 2026-11-20 (later still):** collaboration front-door and document/contract
> sections added. Mattermost's licence read in full — it is the most intricate in this KB and
> is routinely described simply as "open source", which is not wrong but is not usable without
> the detail below.

## ERP & business suites

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Odoo | [odoo/odoo](https://github.com/odoo/odoo) | **LGPL-3.0** (Community) | 55,981 | Python / PostgreSQL / OWL | The reference ERP to agent-enable. LGPL permits linking, so an external agent service over Odoo's XML-RPC/JSON-RPC API keeps Globant's code separate. |
| ERPNext | [frappe/erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | 41,472 | Python / Frappe / MariaDB | Full ERP. **APAC-origin (Frappe, Mumbai)** — the natural base for an India engagement. |
| Frappe Framework | [frappe/frappe](https://github.com/frappe/frappe) | **MIT** | 11,133 | Python / JavaScript | The permissive layer under ERPNext. Build custom apps here and the MIT license travels with them. |
| Apache OFBiz | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1,151 | Java / Groovy | Lowest star count here but the **only fully Apache-2.0 ERP+CRM+SCM suite.** When a client's legal team rejects copyleft outright, this is the answer. |
| Dolibarr | [Dolibarr/dolibarr](https://github.com/Dolibarr/dolibarr) | GPL-3.0 (read from `COPYING`) | 7,888 | PHP / MySQL | ERP+CRM aimed at mid-market and smaller entities, with a large module ecosystem. Easiest to stand up for a pilot or a proof-of-value; same copyleft containment rule as ERPNext. |

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

## Process orchestration & BPM — where an agentic workflow actually lands

Enterprises do not run processes in an agent framework; they run them in a BPM engine with
audit history, SLAs and human task lists. Agent-enabling a *process* means putting the agent
in a service task, not replacing the engine. This section is new this pass and the licence
column is the whole point.

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Flowable | [flowable/flowable-engine](https://github.com/flowable/flowable-engine) | **Apache-2.0** | 9,669 | Java | BPMN/CMMN/DMN engine, compact and embeddable. **The permissive BPM choice** — an agent can be a service task and Globant's wiring code stays Apache-2.0. Where a process-heavy engagement should start. |
| Kestra | [kestra-io/kestra](https://github.com/kestra-io/kestra) | **Apache-2.0** | 30,293 | Java / Vue | Declarative, YAML-first orchestration across data, infrastructure *and* business processes. Lower ceremony than BPMN; good fit where the "process" is really a pipeline with approvals. |
| Camunda | [camunda/camunda](https://github.com/camunda/camunda) | **Camunda License 1.0 — NOT open source** | 4,367 | Java | Now describes itself as an *"Agentic Orchestration Platform"*, so it will be proposed. Read the licence first: Zeebe, Operate and Tasklist are under the Camunda Licence 1.0; only named parts are Apache-2.0 — **Java Client** (`clients/java`), **Spring Boot Starter**, **Exporter API**, **Protocol**, **Gateway Protocol Implementation** and **BPMN Model API**. There is no `LICENSE` file at the repository root (checked `main` and `master` plus `licenses/`, `NOTICE` and five filenames); the terms are declared in the README and in `licenses/CAMUNDA-LICENSE-1.0.txt`. Useful carve-out: generating gRPC stubs from `gateway-protocol` is explicitly *not* a derivative work, so client-side stubs are unencumbered. |
| Apache OFBiz | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1,151 | Java / Groovy | Listed again here because it carries its own process/workflow engine — relevant when a client wants suite and orchestration under one permissive licence. |

**Scoping rule:** build on **Flowable** (Apache-2.0) unless the client already runs Camunda.
If they do, integrate against the Apache-2.0 Java client and generated gRPC stubs and keep
Globant code out of anything Camunda-Licence-1.0, exactly as with a copyleft ERP.

## ITSM, service desk & asset management

The highest-volume agent use case in a large enterprise is not a new product — it is ticket
triage, asset lookup and first-line response over systems that already exist.

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Chatwoot | [chatwoot/chatwoot](https://github.com/chatwoot/chatwoot) | **MIT ("MIT Expat") core + `enterprise/` carve-out** | 40,242 | Ruby / Vue | Omni-channel support desk (live chat, email, social). The cleanest licence in this section — the `LICENSE` file states everything outside `enterprise/` is MIT. The natural front door for a customer-service agent with human handoff. |
| GLPI | [glpi-project/glpi](https://github.com/glpi-project/glpi) | GPL-3.0 | 6,642 | PHP | Asset and IT management, data-centre and ITIL-style service desk. Widely deployed in EMEA public sector and mid-market. Agent opportunity: asset-aware incident triage over its API. |
| Zammad | [zammad/zammad](https://github.com/zammad/zammad) | AGPL-3.0 | 6,131 | Ruby | Web-based helpdesk. **AGPL — run it stock in the client's estate**, put the triage agent beside it over the REST API. |

**Licence shape of this section:** one MIT core (Chatwoot), one GPL, one AGPL. So the
pattern is the same as ERP — the service desk stays in the client's deployment, the agent and
its evaluation harness live in a separate permissive repository owned by the engagement.

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

## Collaboration platforms — the agent's front door inside the client

An enterprise agent that users must visit a new web app to use will not be used. The highest-
adoption surface is the messaging platform staff already keep open all day, and two of the three
large self-hostable ones have a permissive core.

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Rocket.Chat | [RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat) | **MIT (Expat) core + `apps/meteor/ee/` and `ee/` carve-outs** (read from `LICENSE`) | 46,512 | TypeScript / Meteor / MongoDB | Self-hosted messaging, voice and omnichannel; self-described "interoperable by design, governed by you". The cleanest licence of the three — a Globant-built agent bot stays MIT-compatible as long as it lives outside `ee/`. Strong fit where data residency rules out Slack or Teams. |
| Mattermost | [mattermost/mattermost](https://github.com/mattermost/mattermost) | **Tri-modal — read carefully** | 39,679 | Go / React | See the licence note below. Common in defence, public sector and regulated engineering orgs, which is exactly where sovereign agent deployments land. |
| Chatwoot | [chatwoot/chatwoot](https://github.com/chatwoot/chatwoot) | MIT core + `enterprise/` carve-out | 40,242 | Ruby / Vue | Already listed under ITSM; named again because it is the *customer*-facing front door where Rocket.Chat and Mattermost are the *employee*-facing one. |

**Mattermost's licence, read in full from `LICENSE.txt` — the most intricate in this KB.** It is
three licences at once, and which one applies depends on what you do:

1. **Compiled versions produced by Mattermost, Inc.** → **MIT**.
2. **Source code**, to create compiled versions *not* produced by Mattermost, Inc. → **AGPL-3.0**,
   or a commercial licence from Mattermost, Inc.
3. **Admin Tools and Configuration Files** — specifically `server/templates/`, `server/i18n/`,
   `server/public/`, `webapp/` and all subdirectories → **Apache-2.0**.

The `LICENSE.txt` also carries an explicit promise not to enforce AGPL copyleft where an
application **(a)** does not link to the Mattermost platform directly and uses only the Admin
Tools and Configuration Files, and **(b)** has not modified or adapted Mattermost source into a
"modified version" or "work based on" Mattermost.

**Scoping rule that follows:** build the agent as a **separate service that talks to Mattermost
over its API**, deploy the client's Mattermost from official builds, and touch nothing in the
server source. Do that and the stated carve-out plus the non-enforcement promise keep Globant's
code clear of AGPL. Fork the server and the engagement's IP position changes — escalate to legal
before anyone does. Same containment pattern as the copyleft ERPs, with more precision available.

## Document, contract & records platforms

The enterprise document estate is where agent value is most obvious and most often blocked by
having no clean text to work with. These are the systems that already hold the documents, plus
the MIT tooling that makes them machine-readable.

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| Paperless-ngx | [paperless-ngx/paperless-ngx](https://github.com/paperless-ngx/paperless-ngx) | GPL-3.0 | 48,390 | Python / Django | Community-supported document management: scan, index, archive. GPL — run stock in the client's estate, agent beside it over the API. The fastest way to demonstrate document-agent value on a real corpus in a pilot. |
| Documenso | [documenso/documenso](https://github.com/documenso/documenso) | AGPL-3.0 | 15,841 | TypeScript / Next.js | "The open source DocuSign alternative." AGPL, so the same containment rule applies — but it closes the loop that most agentic contract workflows cannot finish: an agent can draft, extract and route, and a human still has to **sign**. Pair with the Flowable service-task pattern so the signature step is a real process state, not a side effect. |
| GLPI | [glpi-project/glpi](https://github.com/glpi-project/glpi) | GPL-3.0 | 6,642 | PHP | Listed under ITSM; relevant here because it is also the asset and contract record in many EMEA mid-market and public-sector estates. |

**The ingestion layer that makes any of the above agent-ready — and it is MIT.**
[docling-project/docling](https://github.com/docling-project/docling) (**MIT**, 70,818 ★,
pushed 2026-11-20) converts PDF, Office and image documents into structured, layout-aware text,
and is **hosted in the LF AI & Data Foundation** (IBM-originated, ships alongside the
GraniteDocling VLM). MIT plus foundation governance plus 70k stars makes it the default choice,
and crucially its licence is permissive **while every document platform above is copyleft** — so
the conversion and enrichment pipeline is Globant IP even when the repository holding the
documents cannot be touched. Where ingestion is a scheduled ETL job rather than a request, use
[Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured) (Apache-2.0,
15,769 ★) instead. **This is the clearest example in this file of the licence asymmetry working
in Globant's favour.**

## Catalog & metadata platforms — the context layer a vertical agent needs

**New section, fourth pass 2026-11-20.** These belong in this file for the same reason Odoo and
ERPNext do: they are **real platforms the client is usually already running**, and an agentic
layer goes on top without forking them. The difference is what they contribute — not a business
process but the answer to *"which table is this agent allowed to believe, and where did this
number come from?"* All four are **permissive**, which is rare in this file.

| Platform | Repo | Real license | Stars | Stack | Agentic opportunity |
|----------|------|--------------|-------|-------|--------------------|
| OpenMetadata | [open-metadata/OpenMetadata](https://github.com/open-metadata/OpenMetadata) | **Apache-2.0** | 15,823 | Java / TypeScript | Self-described "**Open Context Layer for Data and AI**". Most-starred in the category. Already deployed at many data-mature clients — expose its metadata as agent tools and grounding is free. |
| DataHub | [datahub-project/datahub](https://github.com/datahub-project/datahub) | **Apache-2.0** (LICENSE on **`master`**) | 13,006 | Java / Python / React | "Context Platform for your Data and AI Stack." Same play as OpenMetadata; pick whichever the client already runs rather than migrating. |
| Unity Catalog | [unitycatalog/unitycatalog](https://github.com/unitycatalog/unitycatalog) | **Apache-2.0** | 3,581 | Java / Scala | "Open, Multi-modal Catalog for Data & AI." The open-governance option where the client is otherwise locked into a single vendor's catalog. |
| OpenLineage | [OpenLineage/OpenLineage](https://github.com/OpenLineage/OpenLineage) | **Apache-2.0** | 2,773 | Java / Python / SQL | A **standard**, not a product — which makes it the integration point instead of another migration. Emit lineage from agent actions and "what did the agent change?" becomes queryable. |

**Why this is the cheapest section in the file.** Every other platform here needs an agent built
*over* it. These need an agent *pointed at* them, and the client already paid for the deployment.
Two independent vendors in this table pushed on the same day and both now lead with the word
**"context"** — the category has re-positioned itself as agent infrastructure, which means the
client's data team is already budgeted for the thing Globant needs. Recipe: Receta 11.

## Agentic commerce — reference implementations, not yet platforms

**New section, fourth pass 2026-11-20, and deliberately short.** There is no mature open-source
*platform* for agent-led commerce the way Odoo is a platform for ERP. What exists is one runnable
reference implementation and a set of competing protocols:

| Thing | Repo | Real license | Stars | Pushed | Status |
|-------|------|--------------|-------|--------|--------|
| Retail Agentic Commerce blueprint | [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-18 | Reference implementation of **ACP + UCP**. Runnable architecture — the fastest way to show a client the shape. 89 stars: a demo asset, **not** a production base. |

**Say this plainly to a client:** the commerce platform stays whatever it is today (Odoo, a
vendor suite, custom), the agent sits above it exactly as in Receta 1, and the payment rail gets
a **human approval step** because the protocols are not settled — the most-starred of the three
has been idle five months. Protocol detail in `repos/foundations.md`; the reasoning is in
`intel/trends.md` §13; the build is Receta 11.

## Where the control plane sits relative to everything in this file

Every platform in this file is a system of record the client already runs, mostly copyleft, and
the rule throughout has been: run it stock, integrate over its API, keep Globant's code in a
separate permissive repository. The third pass added the missing piece — **the plane those
integrations actually run through**. Put
[theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) (Apache-2.0,
Agentic AI Foundation) or [litellm](https://github.com/BerriAI/litellm) (MIT core) between the
agent and every model, and [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge)
(Apache-2.0) between the agent and every platform API wrapped as MCP. That gives one place to
revoke a credential, cap a budget, enforce a quota and attribute cost per platform — which is
what makes "we agent-enabled seven systems" an auditable claim instead of seven integrations
nobody can see. Recipe: `compose/patterns.md` Receta 9.

## Internal developer portal — the platform the engineering organisation already logs into

Every other platform in this file is a system of record for the *business*. This one is the
system of record for the *software*, and it is the cheapest grounding source in a large client
because it already answers "what services exist and who owns them".

| Platform | Repo | Licence | ★ | Stack | Agentic angle |
|----------|------|---------|---|-------|---------------|
| Backstage | [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34,891 | TypeScript / React | CNCF developer-portal framework; software catalog, ownership, tech docs, scaffolder templates. The catalog is a ready-made, already-trusted grounding graph for an engineering agent. |
| Spotify Portal AI plugins | [spotify/portal-ai-plugins](https://github.com/spotify/portal-ai-plugins) | Apache-2.0 | 3,302 | TypeScript | Puts the Portal CLI inside coding agents: catalog search, service briefings from ownership/health/incident data, and action invocation **with help, dry-run and explicit confirmation**. Last push 2026-10-23. |

**Order of operations:** before proposing a new catalog for an engineering agent, ask whether
Backstage is already running. If it is, the ownership graph is free, politically accepted, and
better maintained than anything a six-week project will build. If it is not, this file's
`DataHub`/`OpenMetadata` rows remain the answer for data, not for services.

## Where the agent's user interface sits relative to everything in this file

The collaboration-platform section above covers the agent's **front door** — Slack, Mattermost,
a chat surface the user goes *to*. The layer found in the fifth pass is different: the agent
renders *inside* the business application the user is already in — the ERP screen, the ticket
form, the CRM record.

That distinction decides the deliverable:

- **Chat front door** (Slack/Mattermost/Open WebUI): fastest to ship, best for knowledge
  retrieval and Q&A, and it requires the user to leave their work to ask a question.
- **In-app generative UI** (AG-UI / A2UI / json-render / openui — see `repos/foundations.md`):
  the agent proposes an action as native components *in the screen where the work happens*.
  More integration work, far higher adoption, and the only shape in which an agent can realistically
  replace a step in a process rather than comment on it.

**The warning that belongs in this file specifically.** Open WebUI's licence already blocks
silent white-labelling (row above). The in-app layer has a different and larger risk: the
standalone-chat-shell projects in that category are being **archived** —
[Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★) among them.
If a client's vertical deployment has a Chainlit front end, that is an archived dependency
sitting in front of a production system, and the README does not say so. Check for it in
discovery; it is a credible, dated reason to open a modernisation conversation.

**For a vertical platform specifically**, the integration point is almost always the platform's
own component library: an ERPNext or Odoo screen that renders an agent's proposal using the
suite's own widgets looks like part of the product; the same proposal in a floating chat bubble
looks like a bolt-on and gets switched off after the pilot.

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
7. **Gate every skill the agent is given.** Platform vendors now publish agent skill
   bundles — [dbt-labs/dbt-agent-skills](https://github.com/dbt-labs/dbt-agent-skills)
   (Apache-2.0, 766 ★) and [NVIDIA/skills](https://github.com/NVIDIA/skills) (Apache-2.0,
   4,095 ★) are both real and useful. They are still third-party code that executes with
   the agent's permissions: scan with [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector)
   (Apache-2.0) and gate with [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator)
   (Apache-2.0) in CI before any of it reaches an environment that can write to an ERP.
   See `compose/patterns.md` Receta 7.
8. **Put the agent in a service task, not in place of the engine.** If the client has a BPM
   engine, the process stays there and keeps its audit trail; the agent is one step inside it
   (Flowable, Apache-2.0). This is what makes "agentic" auditable to a process owner.

---

## BI & analytics platforms — the vertical an enterprise data agent plugs into

**Added sixth pass, 2026-11-20.** This file already had Superset under "Internal tools,
workflow & BI." That single row understated a whole category: the client almost always
*already owns* a BI platform, and the agent engagement is to put a question-answering surface
in front of it, not to replace it. The licence spread in this category is unusually wide, so
the containment pattern matters more here than almost anywhere else in this file.

| Platform | Licence (verified by reading the file) | ★ | Customisation posture |
|----------|---------------------------------------|---|----------------------|
| [apache/superset](https://github.com/apache/superset) | Apache-2.0 | — (already catalogued above) | The permissive default. Embed, fork, re-skin, ship. |
| [evidence-dev/evidence](https://github.com/evidence-dev/evidence) | **MIT** | 7.1k | "BI as code": reports are SQL + markdown in git. The best fit when the *agent* should author or modify a report, because a pull request is a reviewable artefact and a dashboard click is not. |
| [lightdash/lightdash](https://github.com/lightdash/lightdash) | **MIT except `packages/backend/src/ee/`** | 6.2k | Open core, dbt-native, self-described "agentic BI". Build against the MIT paths and **pin the `/ee` exclusion in the build** so it cannot drift in during an upgrade. |
| [metabase/metabase](https://github.com/metabase/metabase) | **AGPL-3.0 outside `enterprise/`**, Metabase Commercial Licence inside | 50.4k | The one most clients already run, and the one with the strongest copyleft. **Deploy and configure it; do not embed or modify it inside something Globant delivers as the client's own product.** Put the agent *beside* it — reading the same semantic layer — rather than inside it. |

**The pattern that survives the licence here is the same one this file already states, applied
to a specific trap:** the agent does **not** integrate into the BI tool. Both the BI tool and
the agent read the **same semantic layer** (`cube-js/cube` or `dbt-labs/metricflow`). That one
decision does three things at once — it keeps the agent's numbers identical to the dashboard's
numbers, it keeps Globant's code out of an AGPL process, and it means swapping the BI tool later
does not touch the agent. If the agent is built *into* Metabase, the client has an AGPL
obligation and a rewrite the next time they change BI vendor.
