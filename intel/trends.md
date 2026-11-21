---
industry: financial
region: Global
updated: 2026-11-21
---

# Financial Services AI — Current Trends

> Researched 2026-11-09, re-verified and corrected 2026-11-21. Repo figures in
> this file were measured directly (method in `agents/top.md`), not quoted from
> roundups.

## 1. The pilot-to-production line has been crossed — unevenly

Lloyds Banking Group calls 2026 the turning point, with agentic AI moving from
experimentation to enterprise-wide deployment, and Backbase frames the year's
shift as agentic AI graduating from controlled environments into live banking
operations. The CCAF/BIS/IMF/WEF data puts **52% actively adopting agentic AI
but under 25% at advanced maturity** — so the crossing is real and most of the
cohort is still early. **Fintechs lead incumbents 57% to 45%.**

Treat the widely-republished "**70%+ of institutions will deploy agentic
decisioning by 2026**" line as a vendor-intermediated forecast. It conflicts
with the only measured dataset in this file.

## 2. The money is in the back office, not the chat window

Four of the top five financial-services AI use cases are back-office functions.
The public narrative is customer-facing agents; the spend is reconciliation,
audit, document processing and controls. Accenture adds a sharper version:
**57% of banking executives expect AI agents fully embedded in risk, compliance,
audit, fraud detection and transaction monitoring within three years.** Treat a
customer-facing agent pitch as the harder sell.

## 3. "Agentic money" — agents that transact, not just advise

Accenture's 2026 banking trends describe the next step as agentic money that
acts on its own: executing payments and optimising liquidity without human
intervention. Finastra adds a genuinely new consequence — banks may soon need to
appeal to **both human customers and their digital representatives**, as
consumer agents gain autonomy over personal finances. Optimising bank product
data for *other people's agents* is a coming discipline.

Measured counterweight: **every permissively-licensed open-banking agent asset
found in this KB is read-only by design** (BankMCP, the open-banking.io MCP
server, the SEC EDGAR MCP). The write path is where the narrative is and the
read path is where the code is.

## 4. AgentOps is becoming a named function

Accenture recommends a dedicated AgentOps function for agent oversight;
Capgemini's World Cloud Report FS 2026 found nearly half of banks and insurers
creating roles to supervise AI agents. Oversight is moving from a governance
document to an org chart line — and to a tooling budget.

## 5. Regulation split three ways in one year, then one of the three moved

As of 2026-11-21 the picture is:

- **EMEA — the deadline moved.** The **Digital Omnibus, Regulation (EU)
  2026/1744**, deferred Annex III high-risk obligations, including
  **creditworthiness assessment and credit scoring**, from 2 August 2026 to
  **2 December 2027**; Annex I embedded systems move to 2 August 2028.
  **Article 50 transparency has been in force since 2 August 2026** and the
  **2 December 2026 watermarking deadline stands.** DORA, in force since
  17 January 2025, did not move at all.
- **APAC — strictest on agents, by supervision rather than statute.** Singapore
  remains the first jurisdiction with a published AI-agent framework for finance
  (SAFR, July 2026), and the **MAS Guidelines on AI Risk Management (7 October
  2026)** cover ML, generative AI and autonomous agents together, with
  implementation running to **7 October 2027**. Singapore has no AI statute;
  these are guidelines that bind through supervision. HKMA and APRA moved to
  supervisory-ready expectations over March–July 2026.
- **North America — moved the other way and stayed there.** **SR 26-2** and
  **OCC Bulletin 2026-13 (17 April 2026)** place generative and agentic AI
  **outside** model-risk guidance. No agent-specific rules in US banking
  supervision. The constraint is at state level (Colorado) and in surviving
  consumer-protection duties (ECOA adverse-action reasons).

**The trend inside the trend:** the EU deferral is the first time this KB has
recorded a major AI deadline moving *backwards*. A KB that treats regulatory
dates as durable facts will go wrong; dates need re-measuring every pass, and
any pitch whose urgency rests on one needs a second leg. The **recast Consumer
Credit Directive, in application since 20 November 2026**, is the EMEA leg that
is actually live today.

## 6. The open core is now a stated AI prerequisite

Finastra argues modern core banking platforms with open APIs have become
essential prerequisites for deploying AI at scale, and Oracle expects
lightweight composable cores to make agents easier to plug in. Both are vendors
arguing for their own products, but the technical claim is sound and it is
equally an argument for Apache Fineract.

**New evidence for the claim, from the open side:** `FinAegis/finaegis`
(Apache-2.0, 212 stars) is a core banking platform built on **event sourcing and
CQRS** that ships an **MCP server with 20+ banking tools** and an Agent Protocol
domain as first-class domains, not add-ons. It is early and lightly adopted, but
it is the first open core in this KB designed after agents existed — and event
sourcing hands you the per-decision audit trail DORA wants **by construction**.

## 7. Open financial agents consolidated into a few large repos — and have now gone quiet

Measured 2026-11-21: TradingAgents **123,303**, OpenBB **75,600**,
ai-hedge-fund **64,780**, qlib **50,455**, Kronos **48,035**, ccxt **44,940**,
Vibe-Trading **38,621**.

**Twelve days of drift on every top row is under 2%.** The explosive phase this
KB recorded (Vibe-Trading 16.9k → 37.9k over four months) has ended at the top
of the distribution.

The sharper measurement: **`finance AI agent created:>2026-08-01 stars:>=80`
returns `total_count: 4` worldwide** — roughly one qualifying new repo a month,
and one of the four is unlicensed. So new financial-agent *creation* has
largely stopped at any scale that matters, while **discovery debt** in a KB can
still be large. A pass that adds six rows means the KB was behind, not that the
ecosystem is booming. The practical consequence: `agents/top.md` and
`repos/foundations.md` earn a weekly or monthly refresh, not an hourly one, and
what pays per pass is verification, correction and gap-closing.

## 8. Market-native foundation models, not just finance-tuned LLMs

Kronos (MIT, 48,035) is positioned as a foundation model for "the language of
financial markets" — pretrained on market series rather than text, trained
across 45+ global exchanges and accepted at AAAI 2026. **Flag raised this pass:
its last push was 2026-04-13, seven months cold**, while stars keep climbing. A
published model artefact can legitimately be frozen; just do not plan on
upstream fixes.

On the weights side, **GLM 5.3 Flash (MIT)** scored highest among open-weight
models on **Vals AI Finance Agent v2 as of 2026-09-23, at 57.9%**, and Ant
Group's **Ling 3.0 Flash Fin** is a finance-continued-pretrain of Ling 3.0
Flash. Caution: finance use depends on data terms as well as weight licenses,
and MiniMax M3.1 Flash (MiniMax Community License) and Kimi K3 (own license) are
**not** permissively licensed despite appearing in finance-agent comparisons.

## 9. Counter-trend: archived and stalled projects still topping the charts

Re-measured this pass: `maybe-finance/maybe` (54.2k, **archived 2025-07-27**),
`google/tf-quant-finance` (5.6k, **archived**), `quantopian/zipline` (20.2k, not
community-led, docs targeting Python 2.7). New this pass: **`apache/ofbiz` is
archived with a last push of 2020-04-27** and is still recommended by current
ERP roundups; the live project is `apache/ofbiz-framework`.

Star count is actively misleading as a selection signal in financial open
source. **`pushed_at` is the better one**, and it is cheap to measure.

## 10. Licence hygiene is now a measurable trend, not a footnote

Two of the most-starred assets in this space **declare a permissive licence in
prose and ship no LICENSE file**: `virattt/dexter` (27,975 stars, MIT in the
README) and `bacen/pix-api` (3,010 stars, Apache-2.0 badge in `readme.md`). In
both cases GitHub's classifier reports no licence, so automated tooling — and
any KB built on that tooling — sees "unlicensed".

Meanwhile **SPDX `NOASSERTION` resolved to genuine Apache-2.0 in 2 of 2 cases
opened** (OpenBB 11,476 B, OpenFin8:BR 12,066 B — canonical Apache text with
copyright lines prepended). The two failure modes point in opposite directions:
trusting the classifier overclaims on one set and underclaims on the other. The
only reliable method is to open the file and read the bytes, which is now the
documented method in `agents/top.md`.

## 11. Fraud is where the AI-versus-AI fight is actually happening

The clearest regional signal this pass: account-takeover incidents reportedly up
**324% in early 2026 in Mexico**, attributed to generative AI tooling (vendor
figure, direction corroborated across LATAM fraud coverage). Fraud is also the
one capability area where this KB's permissive gap is **verified open by
function** — the only maintained open source AML platform found is AGPL-3.0
(`jube-home`, 116 stars) and every permissive candidate is a 0–83 star demo with
no LICENSE file.

Two permissive assets do exist at the edges and are worth knowing:
`SantanderAI/gen-fraud-graph` (Apache-2.0, 296 stars) generates synthetic fraud
**graphs** for benchmarking — bank-authored, and it solves the first blocker on
any AML engagement, which is that you cannot test on real customer data — and
`kingdee/lingee-bench` (Apache-2.0, 190 stars) evaluates whether agents deliver
business value at all.

---
*Researched 2026-11-09; re-verified, corrected and extended 2026-11-21. The
regulatory dates in section 5 supersede the 2026-11-09 revision. Sources are
largely vendor and bank thought-leadership; the CCAF-led survey is the one
rigorous dataset and is cited as such.*
