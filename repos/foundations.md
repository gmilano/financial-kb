---
industry: financial
region: Global
updated: 2026-11-09
---

# Foundational Repositories — Financial Services

> The layer *under* the agents: pricing, risk, market data, backtesting and
> ledgers. These are the libraries a studio engagement stands on.
> Verified individually on 2026-11-09 (`git ls-remote` for existence, repository
> page for license and stars — the GitHub API is proxy-blocked in this
> environment, see `agents/top.md` for the method note).

## Quant, risk and market data — 9 verified and maintained

| Repo | License | Stars | Role in a build |
|---|---|---|---|
| https://github.com/ranaroussi/yfinance | Apache-2.0 | 25.9k | Market data from Yahoo! Finance. The fastest path to a working price feed for a prototype; not a licensed data source for production |
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17.3k | Financial transactions database built for mission-critical safety and performance. Double-entry accounting primitives at high throughput — the ledger of record under a payments or wallet build |
| https://github.com/goldmansachs/gs-quant | Apache-2.0 | 14.0k | Python toolkit for quantitative finance from Goldman Sachs. Derivatives pricing, risk and portfolio analytics with institutional conventions |
| https://github.com/TA-Lib/ta-lib-python | BSD-2-Clause | 12.4k | Python wrapper for TA-Lib. 150+ technical indicators — the standard feature-generation layer for a trading model |
| https://github.com/lballabio/QuantLib | BSD-3-Clause | 7.7k | The QuantLib C++ library. The reference open source library for derivatives pricing, term structures, curve bootstrapping and day-count conventions |
| https://github.com/robertmartin8/PyPortfolioOpt | MIT | 6.2k | Portfolio optimization: classical efficient frontier, Black-Litterman, Hierarchical Risk Parity |
| https://github.com/dcajasn/Riskfolio-Lib | BSD-3-Clause | 4.6k | Portfolio optimization in Python with a much wider risk-measure set (CVaR, CDaR, drawdown-based) than PyPortfolioOpt |
| https://github.com/skfolio/skfolio | BSD-3-Clause | 2.6k | Portfolio optimization, factor model construction and risk management built on scikit-learn — fits an existing sklearn pipeline directly |
| https://github.com/stefan-jansen/zipline-reloaded | Apache-2.0 | 2.0k | Maintained fork of Zipline. **This is the backtesting engine to use**, not the original — see the flags below |

Nine rows, all permissive (MIT / Apache-2.0 / BSD), all maintained.

## Flagged — real repos, but do not start here

| Repo | License | Stars | Why flagged |
|---|---|---|---|
| https://github.com/google/tf-quant-finance | Apache-2.0 | 5.6k | **ARCHIVED.** The README states "This library is no longer maintained and has been archived." The previous revision of this KB listed it as the top foundational repo with "¿Base para AI? Sí" — that recommendation is withdrawn |
| https://github.com/quantopian/zipline | Apache-2.0 | 20.2k | **Effectively stale.** The README says it "is not a community-led project" and that maintainers "may not attend to your pull request, issue, or direct mention in months, or even years." Install docs still target Python 2.7 / 3.5 / 3.6; Quantopian wound down. Use `stefan-jansen/zipline-reloaded` above |
| https://github.com/formancehq/ledger | **unverified** | 1.5k | "The programmable open source core ledger for fintech" — genuinely interesting for a payments build, but **no license is shown** on the repository sidebar and no LICENSE file was reachable (the `/blob/main/LICENSE` path returned 404). Resolve the license before any use. Not recommended until then |

## Removed from the previous revision

The 2026-07-02 revision listed three different repositories all named **zipline**,
of which two have nothing to do with finance and were pure keyword matches:

- `https://github.com/diced/zipline` (MIT, 3.3k) — a ShareX **file upload server**
- `https://github.com/cashapp/zipline` (Apache-2.0, 2.3k) — a **Kotlin/JS runtime**

Both exist and both were listed with "¿Base para AI? Sí" against a financial KB.
Also removed: `jialuechen/torchquant` (193 stars), `mgroncki/IPythonScripts`
(179 stars, a tutorial notebook collection, not a library) and `amaggiulli/QLNet`
(427 stars, a C# port of QuantLib — keep only if the engagement is .NET-bound).
All were re-verified as existing; they were dropped on relevance and maturity,
not on reachability.

## Gap worth naming

There is **no permissively-licensed open source general-ledger or core-banking
library with real traction** in this set. TigerBeetle covers the transaction
store and Apache Fineract (see `verticals/solutions.md`) covers core banking as
an application, but between them — a ledger *library* a team can embed — the
honest answer after this pass is that Formance is the main candidate and its
license could not be verified. This is a genuine gap, not an omission.

---
*Verified and rewritten 2026-11-09. See also `verticals/solutions.md` for
full platforms rather than libraries.*
