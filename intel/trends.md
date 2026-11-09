---
industry: financial
region: Global
updated: 2026-11-09
---

# Financial Services AI — Current Trends

> Researched 2026-11-09. The prior revision of this file listed five repos as
> "most active this week" from 2026-07-02, four of which had 0–6 stars.

## 1. The pilot-to-production line has been crossed — unevenly

Lloyds Banking Group calls 2026 the turning point, with agentic AI moving from
experimentation to enterprise-wide deployment. The CCAF/BIS/IMF/WEF data puts
**52% actively adopting agentic AI but under 25% at advanced maturity** — so the
crossing is real and most of the cohort is still early. **Fintechs lead
incumbents 57% to 45%.**

## 2. The money is in the back office, not the chat window

Four of the top five financial-services AI use cases are back-office functions.
The public narrative is customer-facing agents; the spend is reconciliation,
audit, document processing and controls. Treat a customer-facing agent pitch as
the harder sell.

## 3. "Agentic money" — agents that transact, not just advise

Accenture's 2026 banking trends describe the next step as agentic money that acts
on its own: executing payments and optimising liquidity without human
intervention. Finastra adds a genuinely new consequence — banks may soon need to
appeal to **both human customers and their digital representatives**, as consumer
agents gain autonomy over personal finances. Search-engine-optimisation for
bank products, aimed at other people's agents, is a coming discipline.

## 4. AgentOps is becoming a named function

Accenture recommends a dedicated AgentOps function for agent oversight;
Capgemini's World Cloud Report FS 2026 found nearly half of banks and insurers
creating roles to supervise AI agents. Oversight is moving from a governance
document to an org chart line — and to a tooling budget.

## 5. Regulation has split three ways in one year

Covered in detail in `intel/market.md`, but as a trend: within 2026 the EU set a
**hard high-risk deadline (2 Aug 2026)**, Singapore became the **first
jurisdiction to publish an AI-agent framework for finance** (SAFR, July 2026;
Guidelines, 7 Oct 2026), and US federal regulators moved the other way —
**April 2026 revised model-risk guidance explicitly excludes generative and
agentic AI from scope**. Three major jurisdictions, three directions, same year.

## 6. The open core is now a stated AI prerequisite

Finastra argues modern core banking platforms with open APIs have become
essential prerequisites for deploying AI at scale, and Oracle expects
lightweight composable cores to make agents easier to plug in. Both are vendors
arguing for their own products, but the technical claim is sound and it is
equally an argument for Apache Fineract.

## 7. Open financial agents consolidated into a few large repos

The long tail of trading bots has given way to a handful of very large projects.
Measured 2026-11-09: TradingAgents **121.5k**, OpenBB **75.3k**, ai-hedge-fund
**64.6k**, qlib **50.2k**, Kronos **47.4k**, Vibe-Trading **37.9k**.

Two movements worth recording:

- **Vibe-Trading: 16.9k (2026-07-02, this KB) → 37.9k (2026-11-09).** More than
  doubled in about four months.
- **TradingAgents: third-party roundups still say "over 80,000 stars"; the
  repository page showed 121.5k.** Published roundups are lagging reality by a
  wide margin — a reason to measure repos directly, which is what this pass did.

## 8. Market-native foundation models, not just finance-tuned LLMs

Kronos (MIT, 47.4k) is positioned as a foundation model for "the language of
financial markets" — pretrained on market series rather than text. Separately on
the weights side, **GLM 5.3 Flash (MIT)** scored highest among open-weight models
on **Vals AI Finance Agent v2 as of 2026-09-23, at 57.9%**, and Ant Group's
**Ling 3.0 Flash Fin** is a finance-continued-pretrain of Ling 3.0 Flash.
Caution: finance use depends on data terms as well as weight licenses, and
MiniMax M3.1 Flash (MiniMax Community License) and Kimi K3 (own license) are
**not** permissively licensed despite appearing in finance-agent comparisons.

## 9. Counter-trend: archived projects still topping the charts

Three of the highest-star "options" in this space are dead or stalling —
`maybe-finance/maybe` (54.2k, **archived 2025-07-27**),
`google/tf-quant-finance` (5.6k, **archived**, and the previous revision of this
KB recommended it), and `quantopian/zipline` (20.2k, not community-led, docs
still targeting Python 2.7). Star count is now actively misleading as a
selection signal in financial open source.

---
*Researched 2026-11-09. Sources are largely vendor and bank thought-leadership;
the CCAF-led survey is the one rigorous dataset and is cited as such.*
