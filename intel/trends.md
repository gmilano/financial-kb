---
industry: financial
region: Global
updated: 2026-11-22
---

# Financial Services AI — Current Trends

> Researched 2026-11-09, re-verified and corrected 2026-11-21, extended
> 2026-11-22. Repo figures in this file were measured directly (method in
> `agents/top.md`), not quoted from roundups. **§7 is partly superseded by §13:
> its measurement replicates exactly and its conclusion about the ecosystem does
> not.**

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

## 12. The agentic payment stack is the part of "agentic money" that shipped

§3 of this file described "agentic money" as a consultancy narrative and noted
the measured counterweight: every permissive open-banking asset in this KB is
read-only. That was true of the *open-banking* corner and wrong about the
market. A permissive, multi-vendor **payment protocol stack** has been shipping
for eighteen months and this KB had none of it.

Three layers, each with a live Apache-2.0 or MIT repository (full table in
`agents/top.md`):

1. **Authority** — Google's **AP2** (3,283 stars): signed Intent, Cart and
   Payment mandates that record what the human actually authorised.
2. **Settlement** — **x402** (6,820 stars), now under neutral governance: HTTP
   `402 Payment Required` as a working payment protocol with facilitators.
3. **Checkout** — **ACP** (1,609 stars): connecting an agent to a merchant's
   existing checkout.

Around them: wallets and tooling (`coinbase/agentkit` 1,359,
`worldliberty/agentpay-sdk` 460), routing, local runtimes, and a CC0 index.

**The measurement that matters more than the taxonomy:** AP2's repository has
**not been pushed since 2026-06-17** while x402 was pushed two days ago. The
layer everyone quotes as the authorisation standard is the quiet one. Take the
mandate *shape* from AP2 — it is the right answer to "what did the human
authorise", and it is the artefact MAS SAFR and OSFI's July 2026 bulletin both
ask for — and take the running code from x402.

**Security caveat, from the literature rather than from vendors.** Academic
work on x402 reports practical attacks and concludes it is not yet secure by
construction, and a red-team analysis of AP2 makes the sharper point for
anything agentic: **cryptographic signing protects execution correctness while
prompt injection manipulates the reasoning that happens before the signature**.
A signed mandate proves what was authorised, not that the authorisation was
sound. This is the argument for an enforcement point in front of the agent —
`decionis/agent-safe-pipeline` (Apache-2.0, 661 stars) is the first such
component in this KB.

## 13. Discovery debt is vocabulary-shaped — measured twice in one pass

§7 of this file inferred, from `finance AI agent created:>2026-08-01
stars:>=80` returning `total_count: 4`, that new financial-agent creation had
"largely stopped at any scale that matters".

Re-run on 2026-11-22: **the same query returns the same 4 repositories.** The
measurement replicates perfectly. The inference does not survive, because two
large permissive categories were invisible to it:

- **Agentic payments** (§12) — over 15,000 stars across eleven repos, none of
  which contains the phrase "finance AI agent".
- **Real-time AML** — Tazama, a Linux Foundation platform with 25+ Apache-2.0
  repositories pushed this week, which this KB had declared **verified open by
  function** as its biggest build-vs-buy gap. Three passes of queries said
  "AML" and "transaction monitoring"; the project says **financial crime risk
  management (FRMS)**.

Both were missed the same way, and neither was a search-effort problem. The
rule that falls out, and that belongs in every industry KB in this family:

> A keyword metric measures the vocabulary, not the world. Before concluding
> that a category is empty, re-run the query **in the words the practitioners
> in that category use about themselves** — and when a gap has survived three
> passes, suspect the query before you believe the gap.

A corollary for this KB specifically: the same failure may be hiding Canadian
rules, where OSFI reportedly writes **"autonomous decision making"** rather than
"agentic AI". A keyword sweep for "agentic" over Canadian regulation would
return a confident and false zero.

## 14. Licence evidence now has five tiers, not two

Three passes have turned this from a footnote into a classification. Every tier
here is held by a real asset measured in this KB:

| Tier | What is on disk | Exemplar | Verdict |
|---|---|---|---|
| 1. Filed licence | Full canonical text | 50+ rows in this KB | Use it |
| 2. Grant by reference | 400–800 B: copyright line plus "Licensed under the Apache License, Version 2.0 … obtain a copy at …" | `coinbase/agentkit` (571 B), every `mojaloop/*` (756 B) | **Valid grant.** Classifier says `NOASSERTION`. Attach the full text when vendoring |
| 3. Machine-readable identifier, no file | `SPDX-License-Identifier` headers in source plus `"license"` in `package.json` | `tazama-lf/tms-service`, `typology-processor`, `event-director` | **Valid and standards-compliant.** Strongest of the no-file cases; raise it upstream anyway |
| 4. Prose only | A sentence in the README, nothing machine-readable | `virattt/dexter` (27,988 stars, and now cold since 2026-09-23), `bacen/pix-api` (badge) | Read and prototype; **do not vendor** |
| 5. A LICENSE file that is not a licence | 398 B pointing at a vendor's commercial Terms of Use | `visa/trusted-agent-protocol` | **Not open source.** Hard exclusion |

Tiers 2, 3 and 5 all report SPDX `NOASSERTION`. **Two of them are safe and one
is a trap**, so `NOASSERTION` carries no information at all until the file is
opened — and tier 5 is the one that defeats a pipeline checking merely that a
LICENSE file exists.

A refinement to the byte-count checksum, also measured this pass: both x402
repositories read **11,324 B** against a canonical Apache-2.0 of 11,357–11,358.
Diffed with leading whitespace normalised, the difference is **zero** — 33 bytes
of indentation. **Below canonical means whitespace; above canonical means
appended terms; 400–800 B means a grant by reference.** Three directions, three
meanings.

## 15. Agent autonomy is now measured, and it is ~2%

The single most useful number this pass, because it is the one a client's board
will ask about. From the BoE/FCA survey published 26 October 2026: about **80%
of responding firms have AI agents in production** — and about **2% run agents
with broad autonomy**. Generative AI is 56% of reported AI systems, up from 17%
for foundation models in 2024.

Three independent confirmations that the ceiling is deliberate, not temporary:

- **ECB, November 2026 FSR:** euro-area banks are in operational deployment for
  generative AI while **agentic AI is largely pilot or planning**, with autonomy,
  model drift and unexplainable *actions* named as the distinct risks.
- **OSFI, July 2026 bulletin:** treat AI outputs as **decision inputs**, keep
  human oversight for high-impact decisions, approval checkpoints before
  high-impact actions.
- **LATAM, in production:** Brazilian and Mexican open-banking initiators
  (Iniciador, Bipa, Fintoc) require the customer to confirm **each** payment by
  biometrics or in-app, even where agent-initiated payment already works at
  scale.

A supervisor, a central bank, a survey and a live market on three continents
all land on **agent proposes, human releases**. The commercial consequence is
that the sellable unit is not autonomy, it is the **approval rail**: the
mandate record, the enforcement gateway, the audit trail per decision. That is
unglamorous, scoped, fundable work — and every component for it in this KB is
permissively licensed.

---
*Researched 2026-11-09; re-verified and corrected 2026-11-21; sections 12-15
added 2026-11-22. The regulatory dates in section 5 supersede the 2026-11-09
revision; section 13 supersedes section 7's conclusion. Sources are largely
vendor and bank thought-leadership — with three exceptions now: the CCAF-led
survey, the BoE/FCA survey of 26 October 2026, and ECB/EBA supervisory
publications. Those three are the rigorous datasets in this KB and are cited as
such.*
