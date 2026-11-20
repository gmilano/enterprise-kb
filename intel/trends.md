---
industry: enterprise
region: Global
updated: 2026-11-20
---

# 📡 Tendencias — Enterprise

> Current trends with the evidence behind them. Where sources conflict, both are given.

## 1. Agents are the default unit of enterprise software

Gartner's forecast — **40% of enterprise applications will embed task-specific agents by
end of 2026, up from under 5% in 2025** — is the most-cited number in the category. The
open-source side corroborates it: a May 2026 survey of GitHub trending found **at least 18
of 30 trending entries were agent-related**, and the shift is characterised as "it isn't
research papers turning into repositories any more, it's agents."

**So what:** agent capability is no longer a differentiator. Assume the client has already
run a pilot and ask what stopped it from shipping.

## 2. The bottleneck is production, not capability

This is the clearest signal of the year and it comes from a competitor's own actions:
**Cognizant launched a dedicated EMEA AI unit on 28 July 2026 explicitly because enterprise
agent pilots were failing at scale.** TechRepublic frames 2026 as the push to break out of
"pilot purgatory". In LATAM one report puts **45% of ML models as never reaching
production**. BCG finds **only ~30% of APAC enterprise workflows are mature enough to
support AI safely at scale.**

**So what:** durable execution, data remediation and process readiness are the billable
work. [temporalio/temporal](https://github.com/temporalio/temporal) (MIT) belongs in the
default architecture, not as an optional extra.

## 3. Governance became a buying requirement, with a board-level trigger

IBM's October 2026 EMEA study: **80% of executives had an AI incident escalate to board or
C-suite in the past year — and only 40% changed governance policy in response.** That 40-point
gap is a live, funded, unmet need. StackAI expects AI governance platforms to become a
budget line item; **41% of EU executives are accelerating governance spend** ahead of the
AI Act's high-risk obligations.

**So what:** sell the evidence trail, not just the agent. Anchor on **NIST AI RMF** and
**ISO/IEC 42001**; instrument with
[Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) and
[NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) (both Apache-2.0).

## 4. Regulation fragmented globally, and the EU's big deadline moved

2026 has no single global AI law. **EU:** the Digital Omnibus, **Regulation (EU) 2026/1744**,
moved Annex III high-risk obligations to **2 December 2027** and Annex I to **2 August 2028**
— scope unchanged, dates deferred. **US:** no federal law; five state regimes already bind,
and June 2026's preemption draft stalled. **APAC:** Korea's AI Basic Act in force since
January 2026, Vietnam's since 1 March 2026, Japan deliberately light-touch. **LATAM:** Peru
first with an AI law, Uruguay first to sign the CoE treaty, privacy law (LGPD, *habeas
data*) doing the real regulating.

**So what:** "one global compliance posture" is not deliverable. Build the obligation set
as configuration — policy-as-code per jurisdiction over one agent implementation.
Full detail per region in `intel/market.md`.

## 5. Agent protocols moved from vendor control to foundation governance

The **Agentic AI Foundation (AAIF)** was formed under the Linux Foundation on
**9 December 2025**; Anthropic donated **MCP**, Block donated **goose**, OpenAI donated
**AGENTS.md**. This is now verifiable in the repositories themselves, which is what makes it
usable in a client conversation rather than a press release: `block/goose` is now
[aaif-goose/goose](https://github.com/aaif-goose/goose), AGENTS.md has its own org at
[agentsmd/agents.md](https://github.com/agentsmd/agents.md), and the `LICENSE` of
[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) now opens
by declaring a **MIT → Apache-2.0 transition** (Apache-2.0 adds the patent grant
enterprises want). Scale: **>10,000 MCP servers in production** by mid-2026, SDKs at ~97M
downloads/month.

**So what:** protocol lock-in is a weaker objection than it was in 2025, and MCP is the safe
integration bet. Put a gateway — [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge)
(Apache-2.0) — in front of it so tool access stays governed.

## 6. Consolidation: point tools are being absorbed into platforms

Unframe reports enterprises moving **away from fragmented AI point tools toward unified
platforms**. The sharpest single data point: **ClickHouse acquired Langfuse (announced
16 January 2026, alongside a $400M Series D)** — LLM observability folding into the data
platform. Langfuse's `LICENSE` now carries ClickHouse's copyright; core remains MIT.
Meanwhile AutoGen has been superseded (AG2 and Microsoft Agent Framework) and Semantic
Kernel is positioned as legacy by the same vendor.

**So what:** warn clients off tool choices with a short consolidation half-life. Prefer
foundation-governed protocols and Apache-2.0 infrastructure over venture-funded point tools.

## 7. Open-source licenses are quietly tightening — verify every one

Of the widely used "open source" enterprise AI tools checked this pass, a large share are
**not** OSI open source. Read from the actual `LICENSE` files on 2026-11-20:

- [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) — **Elastic License 2.0**, not open source.
- [nocobase/nocobase](https://github.com/nocobase/nocobase) — **proprietary EULA** (Singapore entity, rev. 2026-02-24).
- [n8n-io/n8n](https://github.com/n8n-io/n8n) — **Sustainable Use License**; non-`master` branches explicitly unlicensed.
- [open-webui/open-webui](https://github.com/open-webui/open-webui) — custom license with a **branding restriction**.
- [langgenius/dify](https://github.com/langgenius/dify) — **modified** Apache-2.0 with added conditions.
- `ee/` carve-out pattern now standard: Onyx, Mastra, Activepieces, Langfuse, Sim.

Conversely, GitHub's own badge is not reliable in the other direction either:
**NeMo Guardrails reads `NOASSERTION` on GitHub but its `LICENSE` is plain Apache-2.0.**

**So what:** never take a license from a GitHub badge, a directory listing or a blog
roundup. Read the `LICENSE`. This is the cheapest risk control in the studio and it has
already corrected four entries in this KB.

## 8. Smaller, domain-specific models and sovereign deployment

Stellium argues the dominance of massive general-purpose models gives way to
**specialised, domain-specific systems** in 2026. Alongside it, sovereignty: Spectrocloud
flags sovereign AI and "AI factories" as a 2026 enterprise theme, Mistral is letting
businesses **reserve future capacity** via long-term commitments, and the **Apertus**
initiative plus Aleph Alpha anchor an EU-origin option. APAC data-localisation
requirements push the same way.

**So what:** [vllm-project/vllm](https://github.com/vllm-project/vllm) (Apache-2.0) as the
serving layer keeps a deployment portable across sovereign, on-prem and cloud. Designing
API-only locks out EMEA and APAC sovereignty-constrained clients.

---

## Trend sources that disagree — recorded, not reconciled

- **North American adoption:** Stanford AI Index 2026 says **90%** organisational AI use;
  NVIDIA says **70%** active usage; US Census BTOS says **5.4–19.8%**. Different questions
  ("any use ever" vs "used in the last two weeks"), not different facts. Quote the one that
  matches the question being asked, and say which.
- **Enterprise AI spend:** Menlo Ventures' **$176.8B / 5.4x YoY (Sept 2026)** is a single
  vendor estimate and the only figure of its kind found. Treat as directional.
- **EU AI Act high-risk date:** older secondary sources still say August 2026. They predate
  the Digital Omnibus. **2 December 2027** (Annex III) is correct per Regulation (EU)
  2026/1744 — corroborated independently by this KB's energy pass.
