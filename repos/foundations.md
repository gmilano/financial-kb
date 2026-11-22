---
industry: financial
region: Global
updated: 2026-11-22
---

# Foundational Repositories — Financial Services

> The layer *under* the agents: pricing, risk, market data, backtesting and
> ledgers. These are the libraries a studio engagement stands on.
> Verification method, including the three channel defects measured this pass,
> is documented in `agents/top.md` — read it before trusting a license here.

## The gap this KB named on 2026-11-09 is now closed

The prior revision ended with: *"There is no permissively-licensed open source
general-ledger or core-banking library with real traction in this set… the
honest answer after this pass is that Formance is the main candidate and its
license could not be verified. This is a genuine gap, not an omission."*
`repos/trending.md` carried it as **Unresolved**, blocked on license
verification, explicitly forwarded to the next pass.

**Resolved today: `formancehq/ledger` is MIT.** 1,083 bytes, canonical MIT text,
identical on `HEAD`, `main` and `master`. 1,482 stars, pushed 2026-11-21 — today.
`search/repositories` now also reports `MIT`.

**The gap was a measurement artefact, not a fact about the world.** The prior
pass probed `github.com/formancehq/ledger/blob/main/LICENSE` — a *web* path,
which this environment's proxy answers with 403/404 regardless of truth — and
correctly refused to guess. The fix is one channel change: probe
`raw.githubusercontent.com/<slug>/HEAD/LICENSE`, which discriminates 200 from
404 correctly. Any gap in any industry KB of the form "license could not be
verified" should be re-run against raw before it is believed.

Do not confuse it with **`formancehq/stack`** (533 stars, SPDX `NOASSERTION`,
pushed 2026-11-10), which is the broader distribution and a separate licensing
question. The ledger is the MIT part.

## Quant, risk, market data and ledgers — 11 verified permissive

| Repo | License | Stars | Last push | Role in a build |
|---|---|---|---|---|
| https://github.com/ranaroussi/yfinance | Apache-2.0 | 25,900 | active | Market data from Yahoo! Finance. Fastest path to a working price feed for a prototype; **not** a licensed data source for production |
| https://github.com/stefan-jansen/machine-learning-for-trading | MIT | 21,921 | 2026-11-18 | The reference ML-for-trading codebase: data sourcing, feature engineering, strategy evaluation, deep-learning and RL chapters as runnable notebooks. The teaching layer under every model in this KB |
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17,411 | 2026-11-11 | Financial transactions database built for mission-critical safety and performance. Double-entry primitives at high throughput — the ledger of record under a payments or wallet build |
| https://github.com/goldmansachs/gs-quant | Apache-2.0 | 14,000 | active | Python toolkit for quantitative finance from Goldman Sachs. Derivatives pricing, risk and portfolio analytics with institutional conventions |
| https://github.com/TA-Lib/ta-lib-python | BSD-2-Clause | 12,400 | active | Python wrapper for TA-Lib. 150+ technical indicators — the standard feature-generation layer for a trading model |
| https://github.com/lballabio/QuantLib | BSD-3-Clause | 7,700 | active | The reference open source library for derivatives pricing, term structures, curve bootstrapping and day-count conventions |
| https://github.com/robertmartin8/PyPortfolioOpt | MIT | 6,200 | active | Portfolio optimization: classical efficient frontier, Black-Litterman, Hierarchical Risk Parity |
| https://github.com/dcajasn/Riskfolio-Lib | BSD-3-Clause | 4,600 | active | Portfolio optimization with a much wider risk-measure set (CVaR, CDaR, drawdown-based) than PyPortfolioOpt |
| https://github.com/skfolio/skfolio | BSD-3-Clause | 2,600 | active | Portfolio optimization, factor models and risk management built on scikit-learn — drops into an existing sklearn pipeline |
| https://github.com/stefan-jansen/zipline-reloaded | Apache-2.0 | 2,000 | active | Maintained fork of Zipline. **This is the backtesting engine to use**, not the original. Apache-2.0 re-verified byte-exact at 11,347 B after `search/repositories` falsely reported it missing |
| https://github.com/formancehq/ledger | MIT | 1,482 | 2026-11-21 | **Newly verified.** Programmable open source core ledger for fintech: a ledger *library and service* a team can embed, as opposed to TigerBeetle's storage engine or Fineract's full application. Closes the gap named above |

Eleven rows, all MIT / Apache-2.0 / BSD, all maintained.

## Compliance and fraud data tooling — new this pass

| Repo | License | Stars | Last push | Role in a build |
|---|---|---|---|---|
| https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 | 296 | 2026-10-01 | Synthetic fraud **graph** generator for benchmarking, published by Santander. Permissive, bank-authored, and it solves the first blocker on every AML engagement: you cannot test a fraud agent on real customer data. Generates the topology, not just rows |
| https://github.com/kingdee/lingee-bench | Apache-2.0 | 190 | 2026-11-06 | Enterprise benchmark that evaluates whether AI agents deliver business value, from Kingdee (China). APAC-authored; useful as an evaluation harness when a client asks for proof rather than a demo |

## Payments and compliance infrastructure — new 2026-11-22

The KB had pricing, risk, market data, backtesting and ledgers. It had **no
payments rails and no sanctions screening**, which is what an engagement at a
bank, a PSP or a wallet actually touches first. All five rows are Apache-2.0,
all were read byte-for-byte today, and four of the five were pushed this week.

| Repo | License | Stars | Last push | Role in a build |
|---|---|---|---|---|
| https://github.com/moov-io/watchman | Apache-2.0 | 524 | **2026-11-22** | **Sanctions and watchlist screening** against OFAC SDN, consolidated and non-SDN lists, EU and UK lists, with fuzzy name matching over an HTTP API. Pushed today. This is the piece of an AML stack that is hardest to justify building and easiest to drop in |
| https://github.com/moov-io/ach | Apache-2.0 | 572 | 2026-11-21 | Reader, writer and validator for **NACHA ACH files** — the US batch payment rail. Turns a format that is normally a vendor dependency into a library |
| https://github.com/moov-io/fed | Apache-2.0 | 131 | 2026-11-20 | Lookup service over the **FedACH and Fedwire participant directories**: routing number to institution, with search. The small unglamorous dependency every US payment build needs |
| https://github.com/blnkfinance/blnk | Apache-2.0 | 598 | 2026-11-18 | **Double-entry ledger for wallets, balances and reconciliation**, API-first. Sits between TigerBeetle (storage engine) and Fineract (full application) alongside `formancehq/ledger`, with wallet/multi-currency modelling as its emphasis |
| https://github.com/tazama-lf/frms-coe-lib | Apache-2.0 | 5 | 2026-11-01 | Shared library of the Tazama fraud-risk platform (see `verticals/solutions.md`): typed message contracts, database and NATS plumbing. Only interesting if you are building *into* Tazama, in which case it is mandatory |

**On `moov-io` as an organisation.** It is the main open source payments
ecosystem in the United States and it is permissive throughout. One caution
measured this pass: **`moov-io/iso20022` is ARCHIVED** (78 stars, last push
2023-01-12). ISO 20022 is the rail that matters most for the next five years in
EMEA and increasingly in LATAM, so the one Moov repo you would most want is the
one that is frozen. Do not start an ISO 20022 build there.

### Byte-checksum refinement — whitespace, measured

`repos/trending.md` and `agents/top.md` carry a byte-count checksum for licence
identification (MIT ≈ 1.05–1.1 kB, Apache-2.0 ≈ 11,358 B with appendix /
10,173 B without). Two rows this pass sat **34 bytes under** canonical Apache
and would have been flagged: `x402-foundation/x402` and `coinbase/x402`, both
11,324 B.

Diffed against a known-canonical file (`moov-io/watchman`, 11,357 B) with
leading whitespace normalised, **the difference is zero**. The 33–34 bytes are
leading indentation on the heading lines, nothing else; both grants are
verbatim Apache-2.0.

**Rule change:** a byte count within ~50 B of a canonical length is a
*whitespace* question, not a licence question, and the comparison that settles
it is `diff <(sed 's/^[[:space:]]*//' candidate) canonical`. Reserve the
"appended terms" reading — the NVIDIA case recorded in the gaming KB — for
counts that are **above** canonical, where bytes have genuinely been added.
Three byte-count sizes now have three different meanings: below canonical means
whitespace, above canonical means added terms, far below canonical (≈400–800 B)
means a grant by reference or, as with `visa/trusted-agent-protocol`, no grant
at all.

## Flagged — real repos, but do not start here

| Repo | License | Stars | Why flagged |
|---|---|---|---|
| https://github.com/freqtrade/freqtrade | **GPL-3.0** | 57,113 | Very much alive (pushed 2026-11-19) and the largest crypto trading bot in open source, with 50+ exchange integrations. **GPL-3.0 makes it a licensing decision, not a default**: fine for a self-hosted client deployment, a problem for a proprietary derivative. Ranked by stars it would be the second-largest asset in this KB, which is exactly why its license needs stating loudly |
| https://github.com/stefanoamorelli/sec-edgar-mcp | **AGPL-3.0** | 388 | MCP server that lets agents read SEC filings directly — functionally the cleanest US-filings grounding tool found. AGPL reaches across the network boundary, so hosting it as a service for a client triggers source obligations. Note the slug: `sec-edgar/sec-edgar-mcp` does **not** exist |
| https://github.com/google/tf-quant-finance | Apache-2.0 | 5,600 | **ARCHIVED.** "This library is no longer maintained and has been archived." A 2026-07-02 revision of this KB listed it as the top foundational repo; that recommendation stays withdrawn |
| https://github.com/quantopian/zipline | Apache-2.0 | 20,200 | **Effectively stale.** README says it "is not a community-led project" and maintainers "may not attend to your pull request, issue, or direct mention in months, or even years." Install docs still target Python 2.7 / 3.5 / 3.6. Use `stefan-jansen/zipline-reloaded` |

## Still genuinely open — stated, not padded

- **~~No permissive, high-traction agentic AML/transaction-monitoring
  platform.~~ CLOSED 2026-11-22 — it exists and it is Apache-2.0.** The gap was
  real as *stated* and wrong as *searched*: the queries used "AML" and
  "transaction monitoring", and the platform that fills it calls itself a
  **financial crime risk management (FRMS)** system. **Tazama**
  (https://github.com/tazama-lf, a Linux Foundation project) is a complete
  real-time fraud and AML transaction-monitoring platform — rules engine,
  typology processor, case management, rule studio, Mojaloop adapter — under
  Apache-2.0, with 25+ repos pushed within the last week. Full write-up,
  including a licence-filing defect in three of its runtime repos, is in
  `verticals/solutions.md`. `jube-home/aml-fraud-transaction-monitoring`
  (AGPL-3.0, 116 stars) is no longer the only maintained option, and
  `moov-io/watchman` (Apache-2.0, above) covers the sanctions-screening half.
  **What stays open is traction, not licence:** Tazama's busiest repo has 57
  stars. This is now a "will the client accept a low-star LF project" decision,
  which is a completely different conversation from "nothing permissive exists".
- **No permissive SEPA or Pix payment-*initiation* agent.** Reading is solved in
  both regions (BankMCP and the open-banking.io MCP for PSD2; the BACEN spec for
  Pix). Initiating a payment is not, and that asymmetry is a product decision by
  every project in the space rather than an accident — read-only is what a bank
  approves first.

---
*Re-verified and extended 2026-11-22 (prior passes 2026-11-21, 2026-11-09).
This pass: a payments-and-compliance infrastructure tier added (5 permissive
rows, 4 pushed this week); the AML/transaction-monitoring gap **closed** by
Tazama after being re-tested under the vocabulary the industry actually uses;
one archived repo caught (`moov-io/iso20022`); the byte-checksum rule refined so
that sub-canonical counts are read as whitespace rather than as defects.*
