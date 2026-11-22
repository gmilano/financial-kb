---
industry: financial
region: Global
updated: 2026-11-22
---

# Financial AI Agents — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

## 2026-11-22 (pass 4)

Pass theme: **the plane where the money moves had no agents in this KB at all.**
Pass 3 (eleven hours earlier) added agentic *payment protocols* — agents that
move money. This pass adds the layer underneath: agents that **read the file the
bank sends and close the books against it**.

### The survey finding that reframes the whole catalogue

The Cambridge CCAF *2026 Global AI in Financial Services Report* (628
institutions, vendors and regulators across 151 jurisdictions):

| Finding | Figure |
|---|---|
| Firms adopting AI at some level | 81% |
| Reporting advanced adoption | 40% |
| Fintechs vs incumbents, advanced adoption | 47% vs 30% |
| **Top-five AI use cases that are back-office functions** | **4 of 5** |
| Top perceived risk: data privacy and protection | 73% |
| Large institutions finding AI value hard to measure | 76% |

**Four of the top five use cases are back-office, and before this pass the
agents catalogue had zero back-office reconciliation rows.** The KB has been
indexing where AI is *interesting* while the industry spends where AI is
*boring*. Deloitte's March 2026 figure for at least moderate agentic adoption in
financial services is 21%, slightly **below** the cross-industry average — so
the gap is not that finance is ahead on agents, it is that finance is spending
on operations.

### New rows — the back-office and message tier

Seven agents added to `agents/top.md`, every licence read byte-for-byte. The
highest-leverage one is the least impressive on paper:
`sebastienrousseau/bankstatementparser-mcp` (Apache-2.0, **3 stars**) exposes
BAI2, MT940, camt.053 and OFX parsing as an **MCP server**. Three stars, and it
is the difference between an agent that reasons over structured transactions and
one that guesses at a PDF.

`FoundrySoftHQ/agent-for-accounting` (MIT, 5 stars) is worth reading for its
design statement rather than its code: *reconcile a month of bank and ledger
CSVs and see only the lines that need a decision.* That is the correct
architecture for this entire plane and it is the same one the legal KB arrived
at independently — **rules do the arithmetic, the model handles the exception,
a human decides.**

### Traction here is low, and the reason is structural — second confirmation

The legal KB (pass 8) found that the revenue plane of a law firm had an order of
magnitude less social signal than contract review, because *people who bill
hours do not browse GitHub*. Measured again here, in a second industry:

| Plane | Representative asset | Stars |
|---|---|---|
| Trading agents | TradingAgents | ~123,000 |
| Payment message layer (14 repos, combined) | — | ~2,700 |
| Back-office reconciliation agents (7 repos, combined) | — | ~66 |
| Verification of Payee (entire world, 2 repos) | — | **0** |

**This is now a cross-industry regularity, not a finance observation.** A
discovery process ranked by stars will find the operator plane last in every
industry, and that is the plane with the budget. Any KB in this family that has
spent three passes concluding "nothing new is being built" should test the
claim against the vocabulary of its clients' operations before believing it.

### Correction carried from `repos/trending.md`

Pass 3's advice *"do not start an ISO 20022 build here"*, derived from one
archived repository, is withdrawn. Fourteen permissive, maintained message-layer
repositories, 0 archived. Details and the licence tiers 6 and 7 that came with
them are in `repos/trending.md` and `repos/foundations.md`.

---

## 2026-11-22

Pass theme: **a category, not a catalogue refresh.** Twenty-four hours is below
this catalogue's noise floor, so nothing here is a star-count story. What
changed is that the KB gained a tier it did not have, and learned why it did not
have it.

### The metric that replicated and the conclusion that did not

`finance AI agent created:>2026-08-01 stars:>=80` returned `total_count: 4` on
2026-11-21 and returns **the same 4 repositories** today: `open-net-worth`
(660), `fzn0x/idx` (235), `kingdee/lingee-bench` (190),
`Yunfan-Wang/Scalable-Agentic-Market-Simulator` (83). A clean replication.

It is still blind to more than 15,000 stars of permissive, actively-maintained
financial agent infrastructure, because none of it says "finance AI agent". See
`intel/trends.md` §13.

### New tier — agentic payment and commerce protocols

All measured 2026-11-22; licences read byte-for-byte.

| Agent / protocol | Repo | License | Stars | Created | Last push |
|---|---|---|---|---|---|
| x402 | https://github.com/x402-foundation/x402 | Apache-2.0 | 6,820 | 2025-02-21 | 2026-11-20 |
| AP2 | https://github.com/google-agentic-commerce/AP2 | Apache-2.0 | 3,283 | 2025-05-30 | **2026-06-17** |
| Solana Pay | https://github.com/solana-foundation/pay | MIT | 1,810 | 2021-10-19 | 2026-11-09 |
| ACP | https://github.com/agentic-commerce-protocol/agentic-commerce-protocol | Apache-2.0 | 1,609 | 2025-09-29 | 2026-07-18 |
| AgentKit | https://github.com/coinbase/agentkit | Apache-2.0 (571 B, by reference) | 1,359 | — | 2026-11-10 |
| a2a-x402 | https://github.com/google-agentic-commerce/a2a-x402 | Apache-2.0 | 572 | — | 2026-11-11 |
| AgentPay SDK | https://github.com/worldliberty/agentpay-sdk | MIT | 460 | — | 2026-11-16 |
| Trusted Agentic Commerce | https://github.com/forter/trusted-agentic-commerce-protocol | MIT | 180 | — | 2026-07-08 |
| agent-payment-node | https://github.com/nuanu-ai/agent-payment-node | MIT | 73 | — | 2026-11-19 |
| agentcash-router | https://github.com/Merit-Systems/agentcash-router | MIT | 32 | — | 2026-07-20 |
| awesome-agentic-payments | https://github.com/bitrefill/awesome-agentic-payments | CC0-1.0 | 27 | — | 2026-06-29 |

**Divergence worth acting on:** AP2 is the protocol everyone cites for
authorisation and its repository has been silent for five months, while x402 —
twice the stars — was pushed two days ago. Google's org has one other repo and
it is active (`a2a-x402`), so the organisation is working; the AP2 reference
repository is not where.

### Also newly recorded

| Agent | Repo | License | Stars | Last push | Why it is here |
|---|---|---|---|---|---|
| Claude for Financial Services | https://github.com/anthropics/financial-services | Apache-2.0 | **41,441** | 2026-11-12 | Ten named workflow agents, five of them back-office (GL Reconciler, Month-End Closer, Statement Auditor, Valuation Reviewer, KYC Screener). The KB has argued "pitch the back office" since 2026-11-09 and had nothing to point at |
| agent-safe-pipeline | https://github.com/decionis/agent-safe-pipeline | Apache-2.0 | 661 | 2026-11-21 | Authorization gateway in front of every agent action. The enforcement point this KB kept recommending in prose |
| CloddsBot | https://github.com/alsk1992/CloddsBot | MIT | 3,123 | 2026-11-13 | Autonomous trading agent across prediction markets and 1,000+ venues. Front-office counterweight, recorded not recommended |

### Hard exclusion, measured

| Asset | Repo | Finding |
|---|---|---|
| Visa Trusted Agent Protocol | https://github.com/visa/trusted-agent-protocol | `LICENSE.md` is 398 B and grants nothing — it points at the Visa Developer Center Terms of Use. **Not open source.** 223 stars, no push since 2025-10-28. A file in the right place with the right name and the wrong content |

### Drift on the existing top set, for the record

TradingAgents 123,393 (+90), Kronos 48,059 (+24, still no push since
2026-04-13), ccxt 44,950 (+10), qlib 50,481 (+26), Vibe-Trading 38,652 (+31,
pushed 2026-11-21), FinGPT 21,661 (+66), hummingbot 21,337 (+19), FinRL 17,158
(+6), ai-hedge-fund 64,796 (+16), FinRobot 8,461 (+4). OpenBB not measurable —
`search/repositories` false negative again, `git ls-remote` confirms live.

**New staleness flag:** `virattt/dexter` (27,988) has not been pushed since
2026-09-23. The previous pass recommended chasing the maintainer for a LICENSE
file; that advice is downgraded — there may be nobody to chase.

## 2026-11-21

Measured with three channels (`search/repositories` for metadata, `git ls-remote`
for existence, byte-exact LICENSE read over `raw.githubusercontent.com`). Method
and its three measured blind spots are in `agents/top.md`.

### Movers — only what actually moved

| Agent | Repo | License | Stars 2026-11-21 | Prior (2026-11-09) | Change |
|---|---|---|---|---|---|
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 123,303 | 121.5k | +~1.8k in 12 days |
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 38,621 | 37.9k | +~0.7k |
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,035 | 47.4k | +~0.6k, but **last push 2026-04-13** — stars rising on a cold repo |
| ccxt | https://github.com/ccxt/ccxt | MIT | 44,940 | 44.8k | +~0.1k |
| qlib | https://github.com/microsoft/qlib | MIT | 50,455 | 50.2k | +~0.3k |

Twelve days of drift across the top set is **under 2% on every row**. The large
moves this KB recorded in its 2026-11-09 pass (Vibe-Trading +21.0k over four
months) were real; the top of this market has since gone quiet.

### Newly recorded this pass

| Agent | Repo | License | Stars | Region | Why it is here |
|---|---|---|---|---|---|
| BankMCP | https://github.com/noskillish/bankmcp | MIT | 327 | EMEA | First PSD2 asset in this KB with real traction. Self-hosted, read-only, agent reads actual bank accounts over Enable Banking |
| idx | https://github.com/fzn0x/idx | MIT | 234 | APAC | Indonesian market (IDX/IHSG) terminal analysis. Created after 2026-08-01 and already at 234 stars |
| gen-fraud-graph | https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 | 296 | Global | Bank-authored synthetic fraud **graph** generator. Permissive, and it unblocks AML testing without customer data |
| lingee-bench | https://github.com/kingdee/lingee-bench | Apache-2.0 | 190 | APAC | Kingdee's enterprise benchmark for whether agents deliver business value — an evaluation harness, not an agent |
| open-net-worth | https://github.com/open-net-worth-ai/open-net-worth | AGPL-3.0 | 610 | Global | Self-hosted personal-finance assistant. Pushed 2026-11-21; fastest-moving new asset found. **AGPL** |
| accountant24 | https://github.com/machulav/accountant24 | Apache-2.0 | 70 | Global | Personal-finance agent over any LLM including local models |

### The new-asset flow is dry, and that is the finding

`finance AI agent created:>2026-08-01 stars:>=80` returns **`total_count: 4`**
for the whole world over nearly four months. Those four are `open-net-worth`,
`idx`, `lingee-bench` and an unlicensed market simulator.

So the six rows above are not evidence of a boom — they are **discovery debt
being paid down**. Four of them existed before this pass and the KB had not
found them. The distinction matters for cadence: an hourly pass cannot
manufacture new assets at roughly one qualifying repo a month. What pays per
pass is verification, correction and gap-closing, and this log should be read
as a record of measurement, not of market velocity.

### Full-KB URL sweep: 3 repos in the history below have been deleted

All 66 unique `github.com/<owner>/<repo>` URLs in this KB were checked by
`git ls-remote` ref count this pass. **63 resolve; 3 return zero refs and no
longer exist:**

| Repo (as recorded in history below) | Status 2026-11-21 |
|---|---|
| https://github.com/Devsinfin/bank-churn-random-forest | **Deleted** — 0 refs |
| https://github.com/sammygallant214/CryptoDesk-ai | **Deleted** — 0 refs |
| https://github.com/skstmdals1-ctrl/bybit-dashboard | **Deleted** — 0 refs |

The history below is **not being rewritten** — that is the point of an
append-only log, and the rows stay as the record of what was true when they were
written. This section is the correction layer.

All three came from the automated 0-star intake of 2026-07-02, and all three were
re-verified as existing on 2026-11-09. **Three of those eight repos vanished
within about four and a half months.** That is the empirical case for the
2026-11-09 decision to demote unlicensed single-author repos out of the curated
set: in this corner of the distribution, "it resolves today" has a measured
half-life. It also sets the honest expectation for the 0-star rows this pass
*did* adopt (`open-banking-io/mcp-server`, `OpenFin8/openfin8-br`,
`StrategicProjects/pixbr`) — they were adopted on verified licence and function
match, and each needs re-checking rather than assuming.

### License-hygiene findings

- **Dexter (27,975 stars) declares MIT in its README and files no LICENSE.**
  Eleven filename and case variants probed across three branches, all 404,
  with `README.md` and `package.json` returning 200 as controls, and no
  `license` field in `package.json`. Earlier rotation notes recorded this asset
  as plain "MIT" — that was never filed. Full treatment in `agents/top.md`.
- **`bacen/pix-api` (3,010 stars) carries an Apache-2.0 badge and no LICENSE
  file.** Same category, different source: Brazil's central bank.
- **SPDX `NOASSERTION` meant Apache-2.0 in both cases where it appeared**
  (OpenBB 11,476 B, OpenFin8:BR 12,066 B — canonical Apache text with copyright
  lines prepended). Do not discard a row on `NOASSERTION` without opening it.

### Correction to this KB's own prior record

Earlier rotation history recorded **OpenBB as AGPL-3.0** across three separate
cycles. Measured today, byte by byte: `LICENSE` is 11,476 B, opening
"Copyright (c) 2021-2026 OpenBB Inc. All files in this repository are licensed
under the Apache License, Version 2.0" followed by the canonical Apache text,
with no carve-out. **OpenBB is Apache-2.0.** The 2026-11-09 revision had this
right; the older rotation notes did not.

### Model-side signal

No change measured this pass. **GLM 5.3 Flash (MIT)** remains the highest
open-weight score on Vals AI Finance Agent v2 as of 2026-09-23 at **57.9%**;
Ant Group's **Ling 3.0 Flash Fin** is a finance-continued-pretrain of Ling 3.0
Flash. Still not permissive: **MiniMax M3.1 Flash** (MiniMax Community
License), **Kimi K3** (own license).

## 2026-11-09

Measured directly off each repository page on 2026-11-09 (GitHub API is
proxy-blocked in this environment; existence confirmed with `git ls-remote`).

### Movers

| Agent | Repo | License | Stars 2026-11-09 | Prior reading | Change |
|---|---|---|---|---|---|
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 37.9k | 16.9k (2026-07-02, this KB) | **+21.0k, more than doubled in ~4 months** |
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 121.5k | "over 80k" (third-party roundup, 2026) | **+~40k vs the figure still being republished** |

### Newly recorded this pass

| Agent | Repo | License | Stars | Why it is here |
|---|---|---|---|---|
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 47.4k | Foundation model for market series rather than text; flagged on GitHub trending in April 2026 and has kept climbing |
| ai-hedge-fund | https://github.com/virattt/ai-hedge-fund | MIT | 64.6k | Also flagged in the April 2026 trending snapshot; now one of the largest finance-agent repos |
| qlib | https://github.com/microsoft/qlib | MIT | 50.2k | RD-Agent addition pushes it from quant platform into agentic research automation |
| OpenBB | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 | 75.3k | Repositioned explicitly for "analysts, quants and **AI agents**" |

### Model-side signal

- **GLM 5.3 Flash (MIT)** — highest open-weight score on Vals AI Finance Agent v2
  as of 2026-09-23, at **57.9%**.
- **Ling 3.0 Flash Fin** (Ant Group) — finance-continued-pretrain of Ling 3.0 Flash.
- Not permissive, despite appearing in finance comparisons: **MiniMax M3.1 Flash**
  (MiniMax Community License), **Kimi K3** (own license).

### Reclassified, not deleted

The ten repos recorded on 2026-07-02 (history below) were re-verified on
2026-11-09. **Seven still resolve; three have disappeared** — deleted, renamed or
made private since July:

| Gone as of 2026-11-09 | Was recorded as |
|---|---|
| https://github.com/sammygallant214/CryptoDesk-ai | MIT, 0 stars |
| https://github.com/Devsinfin/bank-churn-random-forest | `?` license, 0 stars |
| https://github.com/skstmdals1-ctrl/bybit-dashboard | `?` license, 2 stars |

Of the seven that survive, five still carry 0–6 stars and three still have no
identifiable license (`?`). The history rows are left exactly as recorded — that
is the point of a dated log — but **three of the ten are now dead links, and
nothing in that 2026-07-02 set belongs in a curated catalogue.** All ten have
been kept out of `agents/top.md`.

This is the concrete argument for verifying before writing: a 0-star repo
harvested by an automated pass has roughly a one-in-three chance of not existing
four months later.

### Gaps this pass

- No new **EMEA-origin** or **LATAM-origin** financial agent repos surfaced.
  The trending set is overwhelmingly US and China/HK-origin. Recorded as an
  informed gap rather than left to look like coverage.
- GitHub's own trending page could not be filtered by topic through this
  environment; trending signal here is reconstructed from dated third-party
  snapshots (April 2026 and October 2026 `agents-radar` issues) plus direct
  measurement, so it is a *monthly-resolution* signal, not weekly.

---

# History

*Everything below is preserved from earlier passes. Do not rewrite.*

*Column labels in the section below were normalised from Spanish to the
canonical English headers on 2026-11-09 so the compiler reads them as headers
rather than ingesting `Nombre` as an entity. **No data row was altered.***


## 2026-07-02

> Última actualización: 2026-07-02

| Agent | License | Description | Stars |
|--------|----------|-------------|-------|
| [Vibe-Trading](https://github.com/HKUDS/Vibe-Trading) | MIT | "Vibe-Trading: Your Personal Trading Agent" | 16.9k |
| [CryptoDesk-ai](https://github.com/sammygallant214/CryptoDesk-ai) | MIT | Build an AI desktop trading co-pilot for secure, simulation-first crypto analysi | 0 |
| [open-bank-oss](https://github.com/JiRaska/open-bank-oss) | Apache-2.0 | Cloud-native, open-source retail banking platform reference implementation (Kotl | 6 |
| [Fundo](https://github.com/Rahilralu/Fundo) | ? | Fundo is a college event payment platform that eliminates the chaos of collectin | 0 |
| [split-checkout](https://github.com/PremaanshVyas/split-checkout) | MIT | Pay for one order with two cards: multi-card payment orchestration on Airwallex | 0 |
| [bank-churn-random-forest](https://github.com/Devsinfin/bank-churn-random-forest) | ? | Random Forest classifier predicting bank customer churn — full-sample vs half-sa | 0 |
| [auditLens](https://github.com/SashaEee/auditLens) | MIT | Deep-research LLM agent + RAG platform for internal bank-product audit — cited r | 0 |
| [clawock](https://github.com/KCNyu/clawock) | ? | Multi-agent LLM analysis on a real HK + US stock portfolio: a bull-vs-bear debat | 4 |
| [bybit-dashboard](https://github.com/skstmdals1-ctrl/bybit-dashboard) | ? | Bybit TensorAI Dashboard | 2 |
| [lumen-core-public](https://github.com/robertashworth1986-debug/lumen-core-public) | MIT | Institutional quant AI + autonomous trading, built solo in a van for 3 kids. Pat | 2 |

---
*Pipeline automático — se actualiza cada hora.*
