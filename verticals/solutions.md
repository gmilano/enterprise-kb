---
industry: enterprise
region: Global
updated: 2026-11-24
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
| Onyx | [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | **MIT core + `ee/` carve-out** | 33,488 | Python / React | Enterprise search and AI chat across every connector. The most reusable "day one" deliverable; keep strictly out of `ee/`. **But see "Enterprise search & the permission-sync carve-out" below: document permission sync is itself inside `ee/`, so the MIT build has no ACL enforcement.** |
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

---

## Enterprise search & the permission-sync carve-out — read this before quoting an "open source Glean" (added seventh pass, 2026-11-20)

Enterprise search over the client's own document estate is one of the most requested
agentic deliverables, and the open-source answer everyone reaches for is
[onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) — which this KB already lists in
`agents/top.md` Tier 2 as "MIT core + `ee/` enterprise carve-out", 33,488 ★. That row was
correct and is unchanged. What it did not say is **which feature is inside the carve-out**,
and the answer changes the engagement.

**Verified at file level this pass, on `main`, over `raw.githubusercontent.com`:**

| Path probed | Result | Meaning |
|-------------|--------|---------|
| `backend/ee/onyx/external_permissions/__init__.py` | **200** | The permission-sync package exists — **inside `ee/`**. |
| `backend/ee/onyx/external_permissions/sharepoint/doc_sync.py` | **200** | SharePoint document-permission sync: enterprise-licensed. |
| `backend/ee/onyx/external_permissions/google_drive/doc_sync.py` | **200** | Google Drive document-permission sync: enterprise-licensed. |
| `backend/onyx/external_permissions/__init__.py` | **404** | **There is no copy outside `ee/`.** The MIT tree does not contain this capability at all. |

And the root `LICENSE` states the boundary in its own words: *"All content that resides under
'ee' directories of this repository is licensed under the Onyx Enterprise License"* — naming
`backend/ee/LICENSE`, `web/src/app/ee/LICENSE` and `web/src/ee/LICENSE` — with everything
outside those directories "available under the 'MIT Expat' license".

**Probing seventeen candidate connector names, eleven have a `doc_sync.py` under `ee/`:**
`sharepoint`, `google_drive`, `confluence`, `jira`, `slack`, `gmail`, `teams`, `github`, `box`,
`linear`, `hubspot`. That is a **verified lower bound, not a count** — secondary blogs claim 12,
13 and 16 and do not agree, and the directory listing could not be enumerated from this
environment (repository scope), so this KB states the eleven it proved and does not pick a
number it cannot support.

**So what — and this is the commercially decisive sentence of the pass.** The single feature
that stops an enterprise search agent from overserving documents is precisely the feature
carved out of the MIT licence. A client who self-hosts "open source Onyx" to keep their
documents in-house gets retrieval over **everything that was ingested, flat, for every user**.
The privacy-motivated choice and the oversharing failure mode are the *same decision*, and the
client will not discover it until someone asks the agent a question about a colleague's salary.

**The three honest paths, which is what an engagement lead should be able to say in the room:**

1. **Buy the Onyx Enterprise Edition / Cloud.** The capability exists, it is theirs, it is not
   a Globant build. Fastest, and the correct recommendation when the client's connectors are
   the eleven proved above.
2. **Build the entitlement boundary on the permissive stack** — the components are in
   `repos/foundations.md` under "The entitlement boundary", and the build is
   `compose/patterns.md` **Receta 16**. This is the right answer when the client's systems are
   *not* mainstream connectors (a mainframe, a regional ERP, a government filing portal), which
   is exactly the LATAM and public-sector situation in `intel/market.md`.
3. **Ship the MIT build scoped to a genuinely flat corpus** — published policies, product
   documentation, the handbook. Legitimate, cheap, and honest, *provided* it is written down
   that the corpus is flat by design and no entitled content may enter it. This is the one that
   silently becomes option 2 when the pilot succeeds and someone connects SharePoint.

**Never quote path 3 and then let SharePoint be added without re-pricing.** That transition —
from flat corpus to entitled corpus — is the whole of Receta 16, and it is not a configuration
change.

---

## Integration platforms — the system the client already runs, and the cheapest agent surface they own (added eighth pass, 2026-11-21)

Every vertical in this file — ERP, CRM, ITSM, BPM, collaboration — is reached from
outside through an integration layer. In most enterprises of the size Globant sells
to, **that layer is already deployed, already connected and already owned by a team
with a change process.** Treating it as a platform to agent-enable, rather than
something to work around, is the single largest cost reduction available in a Receta 1
engagement.

| Plataforma | Repo | Licencia | Stars | Qué es | Cómo se customiza con AI |
|---|---|---|---|---|---|
| Apache Camel | [apache/camel](https://github.com/apache/camel) | Apache-2.0 (byte-read, 11,357 B) | 6,419 ★ | The enterprise integration runtime: 300+ components for SAP, Salesforce, JDBC, JMS, FTP, mainframe and message buses, expressed as routes. | **`camel-ai-tool` turns an existing route into a tool** callable from LangChain4j, Spring AI, OpenAI-shaped clients and any MCP client at once; `camel-mcp-server` publishes them; `camel-ai-resource` exposes a route as a read-only MCP resource; `camel-a2a` speaks A2A. No new integration code. |
| Conductor | [conductor-oss/conductor](https://github.com/conductor-oss/conductor) | Apache-2.0 (11,309 B) | 32,494 ★ | Netflix-origin workflow orchestration, now community-governed. | Agent steps as workers in an existing workflow definition, with the orchestration decision staying in Conductor rather than in the prompt. |
| Dapr | [dapr/dapr](https://github.com/dapr/dapr) | Apache-2.0 (11,411 B) | 26,212 ★ | CNCF. State, pub/sub, bindings and workflow as sidecar APIs. | [dapr/dapr-agents](https://github.com/dapr/dapr-agents) makes each agent a durable workflow and an actor — the write survives a restart. |

### Why this is a *different* claim from the one in `compose/patterns.md` Receta 1

Receta 1 agent-enables an ERP by writing an MCP server in front of it. That is correct
and still the right answer when no integration layer exists. But where one does:

- The connections, credentials and network paths **already exist and are already
  approved**. The security review you would otherwise run for a new MCP service has
  mostly been run already, years ago, for the route.
- The transformations **already encode the client's business rules** — field mappings,
  validation, the reason invoice posting needs three fields the API docs do not
  mention. A hand-written MCP server starts from the API; a Camel route starts from the
  accumulated institutional knowledge of how that API is actually used here.
- There is **an owning team with a change process**. This matters more than it sounds:
  the commonest reason an agent pilot stalls in month three is that nobody owns the
  integration it depends on.

**Star counts mislead badly here**, and this file's own trend 11 predicted it: Camel at
6,419 ★ is far below the agent frameworks, and it is the most enterprise-ready thing in
this table. The star count measures developer enthusiasm; Camel's constituency is
integration architects, who do not star repositories.

### What to check before quoting this

1. **Camel version.** The unified `camel-ai-tool` and the built-in MCP server are
   recent (the 4.2x line). A client on 4.8 or 3.x does not have them, and an upgrade
   across a Camel major is a project in itself. **Ask for the version before the
   proposal, not after.**
2. **The artefact name is `camel-mcp-server`.** Apache's blog says "camel-mcp"; the
   tree does not contain that. Verified by reading `components/camel-ai/pom.xml`.
3. **Routes are not tools just because they can be published.** A route that posts a
   financial transaction must not be exposed as a tool without the write-boundary
   controls in **Receta 17** — least of all on the strength of an MCP
   `destructiveHint`, which the specification itself says clients must treat as
   untrusted.

## Supply-chain platforms — the system of record for "what are we running" (added ninth pass, 2026-11-24)

Every other platform in this file is something the *client already runs* that an agent can plug into.
This section is the exception that proves the rule: **it is the platform a client with an agent estate
usually does not run yet**, and it is the one that every governance claim in `intel/trends.md` and every
regulatory deadline in `intel/market.md` silently depends on.

The `repos/foundations.md` AI-BOM section produces inventory documents. **Until this pass the KB had
nothing that *operates* them.** The difference matters commercially: generating an SBOM is a
deliverable you hand over once; running the platform that re-evaluates it against tomorrow's
advisories is **a managed service with a renewal**.

| Platform | Licence (byte-read) | ★ | Last commit | What it is, and why it is the customisable base |
|---|---|---|---|---|
| [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track) | Apache-2.0 | 4.5k | 2026-11-23 | **The Odoo-shaped entry in this layer**: an OWASP flagship "intelligent Component Analysis platform" with a server, UI, API and policy engine that ingests CycloneDX SBOMs and **continuously re-evaluates them as new advisories land**. The AI angle is not a fork: [`cdxgen`](https://github.com/CycloneDX/cdxgen) emits an **AI-BOM** (prompt files, AI services, **MCP configs**, model metadata) and **submits it directly to a Dependency-Track server**, so the client's existing component-analysis platform becomes the AI inventory with no new system. Caveat read from its own page: the repo page does **not** advertise ML-BOM/AI-BOM support — the AI capability lives in the *generator*, so **validate the round-trip before quoting it**. |
| [guacsec/guac](https://github.com/guacsec/guac) | Apache-2.0 | 1.6k | 2026-11-24 | The graph layer above it: SBOMs **and attestations** (CycloneDX, SPDX, in-toto ITE6, DSSE, SLSA, CSAF/OpenVEX) normalised into one queryable graph. Use it for the questions Dependency-Track cannot answer because they span systems — *"which deployed agents contain this component?"* Its own page states identifiers are often absent and linking is **heuristic**, so ingestion errors occur: a graph for investigation, not an authoritative register. |
| [stacklok/toolhive](https://github.com/stacklok/toolhive) | Apache-2.0 | 2.4k | 2026-11-23 | "Enterprise-grade platform for running and managing MCP servers." The **runtime enforcement point** — the place a server that failed admission can actually be refused rather than merely flagged. |
| [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) | Apache-2.0 | 1.1k | 2026-11-23 | Gateway **and** registry with OAuth and **security scanning at registration**, holding unsafe servers, agents and skills for review. AWS-oriented (EKS/ECS/EC2, Bedrock). **The architecture to copy is admission control at registration time**, not inspection at runtime — by runtime the credential has already been handed over. |

### The retired entry, kept deliberately

[NimbleBrainInc/mpak](https://github.com/NimbleBrainInc/mpak) (Apache-2.0) was an MCP package registry
with bundle signing, GitHub-OIDC provenance and an **L1–L4 trust ladder** ("Basic / Standard /
Verified / Attested"). It was **archived by its owner on 2026-11-23** — the day before this pass — with
`registry.mpak.dev` to be shut down and its servers moved to a vendor catalogue. It is listed here, in
a platforms file, **because its trust ladder is the best articulation of this layer's maturity model
that this pass found, and it is now a design reference rather than a dependency.** Do not build on it.
Do borrow the ladder when a client asks what "trusted MCP server" should mean contractually.

### What to check before quoting any of this

1. **Dependency-Track is a platform, so it has platform costs** — a database, an upgrade path, an owner.
   It is not a CLI you add to CI. Scope it as a system, or the engagement under-runs on effort.
2. **The AI-BOM round-trip is the thing to pilot in week one**: `cdxgen aibom` → Dependency-Track
   ingest → policy violation on an unapproved model or MCP server. If that loop closes on the client's
   real repositories, the rest of the governance story is credible. If it does not, say so early —
   `cdxgen`'s own page warns `--component-type` alone does **not** enable model discovery.
3. **None of these prove authorship.** They operate inventories and graphs. Publisher identity for MCP
   servers comes from the registry's namespace verification (DNS/OIDC) and artefact identity comes from
   `cosign` — see `repos/foundations.md` and `compose/patterns.md` Receta 18.

---

## The platform the containment layer plugs into — the client's existing Kubernetes, not a new product (added tenth pass, 2026-11-24)

Every other section of this file names a *system of record* an agent can be put on top of — an ERP,
a CRM, an ITSM, a BPM engine, a collaboration suite. This section names the platform the agent
itself **runs on**, because the tenth pass established that containment is not a product you install
beside those systems: it is a set of controls you attach to a cluster the client already operates.

**The commercial consequence is unusually favourable.** There is nothing to license, nothing to
procure and no new vendor to onboard — which also means there is no product budget to raise. The
engagement is funded as platform engineering, and the artefacts are CRDs, policies and rulesets in
the client's own GitOps repository.

### What the client already has, and what has to be true for this to be a short engagement

| Prerequisite | Why it decides the estimate | How to check before quoting |
|---|---|---|
| A Kubernetes estate the client controls nodes on | Isolation runtimes are installed per node and surfaced as a `RuntimeClass`. On a fully managed platform where node configuration is closed, `gVisor` may be the only option available — it needs **no hardware virtualisation** — and Kata/Firecracker may be off the table | Ask which `RuntimeClass` values exist today; if the answer is none, add a node-pool work package |
| A CNI that can express egress policy | Default-deny egress is the control that makes every other one load-bearing. Cilium supplies an **egress gateway** and therefore a fixed, allowlistable exit IP; a CNI without egress-gateway support changes the design | `kubectl get pods -n kube-system` and ask which CNI; confirm whether `CiliumEgressGatewayPolicy` or an equivalent exists |
| An admission controller already in the cluster | Kyverno or Gatekeeper is what makes "no agent pod without a `RuntimeClass` and a default-deny policy" mechanically unskippable rather than a runbook step | If one is present, this work package is policy authoring only — days, not weeks |
| Gateway API v1.5.0 CRDs | `kubernetes-sigs/agent-sandbox` requires the full Gateway API v1.5.0 CRD bundle for gateway-based client connections | `kubectl get crd \| grep gateway.networking.k8s.io` and check the bundle version |

### The one platform question worth asking before anything else

**Is there a supported downstream build?** Red Hat is reported (developers.redhat.com, July 2026) to
publish a **downstream build of the upstream `kubernetes-sigs/agent-sandbox` project**. **This is
secondary-sourced — the host could not be fetched in this session — and it should be verified for
any OpenShift engagement, because it changes the conversation completely.** A supported downstream
build means the client's platform vendor carries the support burden for the sandbox layer, and the
engagement becomes configuration against a supported product rather than integration of an upstream
subproject. On AKS, `Azure/kars` documents **Kata with AMD SEV-SNP** as an option, which is the
confidential-computing answer where the client's requirement is that the *operator* cannot read the
sandbox's memory.

### Where this sits relative to everything else in this file

The agent reaches the systems in the sections above **through** this layer, which means the order of
work is fixed and worth stating to a client who wants to start with the visible thing:

1. **Containment** (this section) — the cluster the agent runs in, with its four controls.
2. **Entitlement** (the enterprise-search carve-out section) — who the agent is acting for.
3. **The write channel** (the integration-platform section) — how its action reaches the ERP, CRM or
   ITSM named in this file.
4. **The surface** (the collaboration-platform and generative-UI sections) — where the employee
   meets it.

Steps 2, 3 and 4 are all demonstrable without step 1, and that is exactly why pilots stall at the
security review. **Containment is the step with no demo and the shortest critical path.**

## Platforms that were invisible to a GitHub-only inventory (added eleventh pass, 2026-11-24)

Every platform row in this file before this pass lived on `github.com`. That was an unmeasured
habit rather than a judgement, and this pass measured it: **314 of 314 addresses on one forge.** The
rows below are real, running enterprise platforms that were missing for that reason alone.

### On GitLab — verified, with the licence read rather than inferred

| Platform | Repo | Real licence | Stars | Default branch | Last activity | Agentic opportunity |
|---|---|---|---|---|---|---|
| **Mayan EDMS** | [mayan-edms/mayan-edms](https://gitlab.com/mayan-edms/mayan-edms) | **GPL-2.0-only** (byte-read from `LICENSE`; API said `other`) | **683** | `master` | **2026-11-24** | *"Advanced enterprise … DMS."* Belongs beside Paperless-ngx in the document section above, and is the **more enterprise-shaped** of the two (workflows, metadata, cabinets). Same containment rule as every copyleft platform here: agent beside it, over the API. Pair with **docling** (MIT) for ingestion and the conversion pipeline stays Globant IP. |
| **GitLab CE** | [gitlab-org/gitlab](https://gitlab.com/gitlab-org/gitlab) | **MIT** | **6,209** | `master` | 2026-11-24 | A platform the client very often already self-hosts, with a **permissive** community edition — rare in this file. The agent surface is the one place in the estate where an agent already holds credentials: CI. See `gitlab-opencode` in `agents/top.md`. |
| **Flectra** | [flectra-hq/flectra](https://gitlab.com/flectra-hq/flectra) | GPL-3.0 | 252 | **`3.0`** | **2026-07-15** (~4 months idle) | Odoo-lineage ERP+CRM. Listed for completeness of the ERP map; **lead with Odoo or ERPNext** unless a client is already on Flectra. Quote the idleness honestly. |
| **Dokos** | [dokos/dokos](https://gitlab.com/dokos/dokos) | GPL-3.0-or-later | 39 | **`develop`** | 2026-11-24 | ERPNext derivative on the Dodock/Frappe low-code framework, **French-origin and actively developed** — the EMEA-localised sibling of the APAC-origin ERPNext above. Where ERPNext's India-first localisation is the objection, this is the answer. |

**Read the default-branch column before cloning.** Across the GitLab projects verified this pass the
default branch was `master`, `main`, `develop` **and `3.0`**. The habit of assuming `main` and
falling back to `master` fails on Flectra outright; GitLab returns the branch in the same API call
as the licence.

### Mayan EDMS carries a constraint this file has not recorded before, and it is not the licence

Its `LICENSE` file states the copyleft grant and then adds two things no other platform in this KB
declares:

- a **US Copyright Office registration** — *"Registered … under Registration No. TX 8-577-731"*; and
- **registered trademarks** — *"The name 'Mayan EDMS' and the Mayan EDMS logo are registered
  trademarks of Roberto Rosario, U.S. Reg. Nos. 7,889,160 and 7,889,166. This is a copyright license
  and grants no rights in those trademarks. Their use is governed by `TRADEMARK_POLICY.md`."*

**Why this changes a proposal rather than a code review.** The GPL question ("may we modify and
deploy it?") and the trademark question ("may we call it that?") have different answers here. A
white-labelled or client-branded deployment is the normal shape of a Globant delivery, and for this
platform the branding is governed by a separate policy document and registered marks — while the
registered copyright strengthens the author's enforcement position on the code. Neither fact blocks
anything; both belong in the legal annex **before** someone proposes "our DMS, built on Mayan".
This is the first platform in this file where the **brand**, not the licence, is the binding
constraint.

## The sovereign workplace estate — the layer an agent is deployed *into* (added eleventh pass, 2026-11-24)

The forge audit pointed at a gap this file had in plain sight. The collaboration section above
covers **chat** (Rocket.Chat, Mattermost, Chatwoot) and the document section covers **document
repositories**. Neither covers the **workplace suite** — files, project, wiki, groupware — which is
where European sovereignty programmes actually land and where enterprise knowledge work actually
sits. All three rows verified 2026-11-24 via `gh api search/repositories`.

| Platform | Repo | Real licence | Stars | Last push | Agentic opportunity |
|---|---|---|---|---|---|
| **Nextcloud** | [nextcloud/server](https://github.com/nextcloud/server) | **AGPL-3.0** | **37,621** | 2026-11-24 | The default self-hosted file and groupware platform in European public sector and mid-market. AGPL, so the standing rule applies with force: **agent as a separate service over the API**, never a fork. The highest-volume source of real client documents available for a pilot. |
| **OpenProject** | [opf/openproject](https://github.com/opf/openproject) | GPL-3.0 | **17,676** | 2026-11-24 | Project and portfolio management, German-origin, heavily used in regulated and public-sector estates. The natural place for an agent that reads status and drafts reporting — which is the single most requested internal agent in this KB's experience of the category. |
| **XWiki** | [xwiki/xwiki-platform](https://github.com/xwiki/xwiki-platform) | **LGPL-2.1** | 1,336 | 2026-11-24 | The enterprise wiki, and **the most permissive licence of the three** — LGPL permits linking, so an extension can be built against it without the AGPL/GPL containment dance. Lowest stars, best licence position: the inverse ranking is the point. |

**Why this trio and not an arbitrary three.** They are the components European sovereign-workplace
procurement bundles together, and that bundling is why they belong in one section rather than three
scattered rows. The commercially useful observation is the **licence gradient inside one deployment**:
AGPL-3.0 for files, GPL-3.0 for project, LGPL-2.1 for wiki. An agent that spans the suite crosses
three copyleft regimes in a single engagement, so the integration must be **one external service
talking to three documented APIs** — the asymmetry rule this file already states, applied three times
at once.

### Named leads this session could not verify, recorded as leads and not as findings

- **openDesk** — the German sovereign-workplace programme that bundles components of exactly the kind
  above. Its source is hosted on **openCoDE** (`gitlab.opencode.de`), which **refuses connection from
  this session** (`CONNECT tunnel failed, 403`). No licence, version, component list or activity claim
  is made here. It is named so a future pass with a wider network policy knows where to look, and so
  that an EMEA engagement lead who hears the name from a client knows the KB has not assessed it.
- **Tryton** — a full ERP whose canonical home is `foss.heptapod.net`, also refused. Its GitHub
  presence, [tryton/tryton](https://github.com/tryton/tryton), is explicitly *"Mirror of tryton"*,
  247★, and reports **no licence** — so the mirror cannot be used to establish the licence either.
  **Not usable as a proposal base from this session's evidence.** This is the cleanest illustration in
  the KB of the difference between *"we looked and it is not there"* and *"we could not look"*.

### Where these rows sit relative to the rest of this file

The ERP/CRM map at the top of this file is now **complete across both reachable forges** for the
suites a client is likely to name: Odoo, ERPNext, OFBiz, Dolibarr, Krayin, Huly on GitHub; Flectra,
Dokos, Mayan EDMS, GitLab CE on GitLab. The workplace suite is new and sits **above** the catalog
layer and **beside** the chat layer: chat is where the employee talks to the agent, the workplace
suite is what the agent reads and writes while they do.

---

## Twelfth pass, 2026-11-24 — the base model as a vertical platform, and the licence that decides whether you may customise it

This file exists because of a simple proposition: a real system you can customise beats a greenfield
build. **Odoo, ERPNext and Tryton are in here for that reason — and an open-weights model is the same
kind of asset.** It is a platform you fine-tune, quantise, distil and redistribute. Which of those
four verbs you are permitted to perform is **not** a property of the model's quality; it is a property
of its licence, and for weights that licence is **not** in the `LICENSE` file.

Every licence below was byte-verified from `raw.githubusercontent.com` on **2026-11-24**.

| Base model | Origin / region | Weights licence | May you fine-tune and ship the result? |
|---|---|---|---|
| **Salamandra** ([langtech-bsc/salamandra](https://github.com/langtech-bsc/salamandra)) | Barcelona Supercomputing Center — **EMEA** | **Apache-2.0**, `LICENSE` 11,357 B | **Yes, unconditionally.** No AUP, no download gate, no inherited base licence, no naming obligation. Strong Iberian-language coverage. **The default recommendation for a European client who wants a non-US base** |
| **OLMo** ([allenai/OLMo](https://github.com/allenai/OLMo)) | AI2 — **North America** | **Apache-2.0**, `LICENSE` 11,359 B | **Yes.** And uniquely among the families probed, training data and code are published too, so it survives an OSAID-style openness test rather than merely an "open weights" claim |
| **Qwen3** ([QwenLM/Qwen3](https://github.com/QwenLM/Qwen3)) | Alibaba — **APAC** | **Apache-2.0**, per `README.md:397`; **no `LICENSE` file in the repo** | **Yes** — but expect to defend it, because the repository looks unlicensed to a scanner. Keep the README line in the engagement file |
| **NVIDIA Cosmos** ([NVIDIA/Cosmos](https://github.com/NVIDIA/Cosmos)) | NVIDIA — **North America** | **OpenMDW-1.1**, `LICENSE` 2,619 B | **Yes, and outputs are explicitly unrestricted.** Caveat: no SPDX identifier, so the client's SBOM tooling will report it as unlicensed. Budget one conversation with their security team |
| **SEA-LION** ([aisingapore/sealion](https://github.com/aisingapore/sealion)) | AI Singapore — **APAC** | **Depends on the checkpoint** — MIT where possible, otherwise Llama 3 or Gemma terms (`README.md:88`) | **Only after resolving the specific checkpoint.** The project's own paper claims "fully open MIT"; the README and the Gemma-variant card disagree. Excellent Southeast-Asian language coverage, so it is worth the resolution work |
| **Latam-GPT** (`latam-gpt/Llama-3.1-70B-LatamGPT-SFT-1.0`) | CENIA, Chile — **LATAM**; launched 2026-02-10 | **Llama 3.1 Community License** *(secondary-sourced; model card host unreachable from this session)* | **Yes, subject to Meta's terms** — which means the AUP, the "Llama" naming obligation and the 700M-MAU clause travel with it. Reported free to companies and public institutions, >300B tokens |
| **Apertus** (EPFL + ETH Zurich + CSCS) | Swiss AI Initiative — **EMEA**; v1.5 released 2026-07-24 | Reported **Apache-2.0 + a separate Apertus LLM Acceptable Use Policy**; v1.5 weights **gated** (login + acceptance) | **Probably yes, with an AUP to read.** Sources disagree on whether the AUP binds redistribution of unmodified weights. **The download gate is a procurement fact**: an air-gapped client cannot `wget` it |
| **Gemma** ([google-deepmind/gemma](https://github.com/google-deepmind/gemma)) | Google — **North America** | **UNRESOLVED.** Repo `LICENSE` is Apache-2.0 **for the code**; `README` states no licence at all | **Do not commit this week.** Secondary sources split on whether Gemma 4 moved to Apache-2.0 in April 2026 while 1–3 remain under the Gemma Terms of Use. `ai.google.dev` does not resolve from this session |

### The inheritance rule, because it is the one that catches people

**A fine-tune cannot be freer than its base.** Two of the three "sovereign" models above are
derivatives of US base models and inherit those licences in full. When a client says *"we want to
build on the national model"*, the resolution order is:

1. **The base model's licence** — and its acceptable-use policy, which is part of the licence.
2. **The fine-tune's own licence**, which can only add restrictions, never remove them.
3. **Any download gate**, which is not a licence term but will still stop an air-gapped deployment.

"It is a sovereign model" is a claim about the training data and the language coverage. **It carries
no information about the licence**, and in the LATAM case it is specifically a Meta licence.

### How this pairs with the ERP and CRM platforms above

The pairing a client will actually ask for is **Odoo or ERPNext plus a model that may be customised
and redistributed**. For an EMEA engagement that is **Salamandra (Apache-2.0)**; for an air-gapped one
it is Salamandra or OLMo, because both can simply be downloaded; for a LATAM engagement where
Spanish and Portuguese quality is decisive, Latam-GPT is the strongest linguistic option **and the
Llama terms must be in the statement of work**. The gate that produces this determination in a
repeatable way is **Receta 23** in `compose/patterns.md`.
