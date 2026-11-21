---
industry: financial
region: Global
updated: 2026-11-21
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

## Flagged — real repos, but do not start here

| Repo | License | Stars | Why flagged |
|---|---|---|---|
| https://github.com/freqtrade/freqtrade | **GPL-3.0** | 57,113 | Very much alive (pushed 2026-11-19) and the largest crypto trading bot in open source, with 50+ exchange integrations. **GPL-3.0 makes it a licensing decision, not a default**: fine for a self-hosted client deployment, a problem for a proprietary derivative. Ranked by stars it would be the second-largest asset in this KB, which is exactly why its license needs stating loudly |
| https://github.com/stefanoamorelli/sec-edgar-mcp | **AGPL-3.0** | 388 | MCP server that lets agents read SEC filings directly — functionally the cleanest US-filings grounding tool found. AGPL reaches across the network boundary, so hosting it as a service for a client triggers source obligations. Note the slug: `sec-edgar/sec-edgar-mcp` does **not** exist |
| https://github.com/google/tf-quant-finance | Apache-2.0 | 5,600 | **ARCHIVED.** "This library is no longer maintained and has been archived." A 2026-07-02 revision of this KB listed it as the top foundational repo; that recommendation stays withdrawn |
| https://github.com/quantopian/zipline | Apache-2.0 | 20,200 | **Effectively stale.** README says it "is not a community-led project" and maintainers "may not attend to your pull request, issue, or direct mention in months, or even years." Install docs still target Python 2.7 / 3.5 / 3.6. Use `stefan-jansen/zipline-reloaded` |

## Still genuinely open — stated, not padded

- **No permissive, high-traction agentic AML/transaction-monitoring platform.**
  The best functional match, `jube-home/aml-fraud-transaction-monitoring`
  (116 stars, pushed 2026-11-18), is **AGPL-3.0** — see `verticals/solutions.md`.
  Everything permissive in this space is a portfolio demo: measured this pass,
  the candidates were 0–83 stars with no LICENSE file at all. This gap is
  **verified open by function**, not merely unsearched, and it is the single
  biggest build-vs-buy opening in the financial KB.
- **No permissive SEPA or Pix payment-*initiation* agent.** Reading is solved in
  both regions (BankMCP and the open-banking.io MCP for PSD2; the BACEN spec for
  Pix). Initiating a payment is not, and that asymmetry is a product decision by
  every project in the space rather than an accident — read-only is what a bank
  approves first.

---
*Re-verified and extended 2026-11-21. One named gap closed, two gaps re-tested by
function and confirmed open. See `verticals/solutions.md` for full platforms
rather than libraries.*
