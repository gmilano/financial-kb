---
industry: financial
region: Global
updated: 2026-11-21
---

# Financial Repos — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

## 2026-11-21

### Resolved — the item this log carried forward as blocked

The 2026-11-09 section ends with an **Unresolved** entry:
`formancehq/ledger`, "no license shown on the sidebar and `/blob/main/LICENSE`
returned 404… blocked on license verification. Carried forward to the next pass."

**Resolved: it is MIT.**

| Repo | License | Bytes | Stars | Last push | Evidence |
|---|---|---|---|---|---|
| https://github.com/formancehq/ledger | MIT | 1,083 | 1,482 | 2026-11-21 | Canonical MIT text, identical on `HEAD`, `main` and `master`; `search/repositories` independently reports `MIT` |

The prior 404 came from probing a **github.com web path**, which this proxy
answers 403/404 regardless of truth. Probing
`raw.githubusercontent.com/<slug>/HEAD/LICENSE` discriminates correctly. The
practical consequence is in `repos/foundations.md`: this closes the "no
permissive ledger library" gap this KB had named as genuine. **Every
"license could not be verified" note in every industry KB should be re-run
against raw before it is believed.**

Keep it distinct from `formancehq/stack` (533 stars, SPDX `NOASSERTION`,
pushed 2026-11-10) — a different repo and a separate licensing question.

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

### Infrastructure repos gaining in financial builds

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/freqtrade/freqtrade | GPL-3.0 | 57,113 | 2026-11-19 | Measured for the first time in this KB. By stars the **second-largest asset in the whole financial set**, and it is GPL-3.0 — recorded here precisely so a future pass does not promote it into a permissive table |
| https://github.com/stefan-jansen/machine-learning-for-trading | MIT | 21,921 | 2026-11-18 | The reference ML-for-trading codebase as runnable notebooks. MIT and still actively pushed |
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17,411 | 2026-11-11 | +~0.1k since 2026-11-09. Still the ledger-of-record choice under new payments builds |
| https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 | 296 | 2026-10-01 | Bank-published synthetic fraud graph generator |
| https://github.com/stefanoamorelli/sec-edgar-mcp | AGPL-3.0 | 388 | 2026-11-01 | SEC filings over MCP. Note the slug — `sec-edgar/sec-edgar-mcp` does not exist |

### Platform corrections measured this pass

| Repo | Status | Detail |
|---|---|---|
| https://github.com/apache/ofbiz | **ARCHIVED** | Last push **2020-04-27**, 804 stars. Still recommended by current ERP roundups. The live project is `apache/ofbiz-framework` (Apache-2.0, 1,151 stars, pushed 2026-11-20) |
| https://github.com/idurar/idurar-erp-crm | License claim wrong in sources | Listicles call it MIT; it is **AGPL-3.0** (8,963 stars) |
| https://github.com/aureuserp/aureuserp | Slug correction | MIT, 12,265 stars, pushed 2026-11-20. The slug cited in roundups, `aureus-erp/aureus-erp`, **does not exist** — `ls-remote` cannot resolve it |

### Channel defects found this pass — these affect how this log should be read

1. **`search/repositories` returns false negatives on live repos.** `OpenBB-finance/OpenBB`
   and `FinAegis/finaegis` return HTTP 422 "resources do not exist or you do not
   have permission"; `stefan-jansen/zipline-reloaded` returns `total_count: 0`.
   All three are live (5,537 / 1,645 / 291 refs, resolving HEAD SHAs). Treat this
   channel as **precision, never coverage**.
2. **`raw.githubusercontent.com` is case-sensitive.** `bacen/pix-api` gives 404
   for `README.md` and 200 for `readme.md`. A case-blind absence probe will
   report "no LICENSE file" on a repo that has one spelled differently. Absence
   counts as *measured* only when case variants were tried and a control file in
   the same repo returned 200.
3. **`NOASSERTION` resolved to Apache-2.0 in 2 of 2 cases opened.**

### Still open, verified by function rather than assumed

- **No permissive, maintained agentic AML / transaction-monitoring platform.**
  Best functional match is AGPL-3.0 (`jube-home/aml-fraud-transaction-monitoring`,
  116 stars). Permissive candidates measured at 0–83 stars with **no LICENSE
  file**. Biggest build-vs-buy opening in this KB.
- **No permissive SEPA or Pix payment-*initiation* agent.** Read paths are
  covered in both regions; initiation is not, and that is a deliberate product
  choice across the space rather than a gap waiting to be filled.

## 2026-11-09

### Infrastructure repos gaining in financial builds

| Repo | License | Stars | Note |
|---|---|---|---|
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17.3k | Purpose-built financial transactions database; the ledger-of-record choice appearing under new payments builds |
| https://github.com/ranaroussi/yfinance | Apache-2.0 | 25.9k | Still the default prototype price feed |
| https://github.com/stefan-jansen/zipline-reloaded | Apache-2.0 | 2.0k | Quietly became the live backtesting engine as `quantopian/zipline` stalled |
| https://github.com/skfolio/skfolio | BSD-3-Clause | 2.6k | Portfolio optimisation on scikit-learn; newest of the three optimisers tracked here |

### Falling out — measured, not assumed

| Repo | License | Stars | Status on 2026-11-09 |
|---|---|---|---|
| https://github.com/maybe-finance/maybe | AGPL-3.0 | 54.2k | **Archived by owner 2025-07-27, read-only.** Highest star count in the personal-finance category and completely dead |
| https://github.com/google/tf-quant-finance | Apache-2.0 | 5.6k | **Archived.** "No longer maintained and has been archived" |
| https://github.com/quantopian/zipline | Apache-2.0 | 20.2k | Not community-led; maintainers may not respond "in months, or even years"; docs target Python 2.7/3.5/3.6 |

### Unresolved

- https://github.com/formancehq/ledger (1.5k) — "programmable open source core
  ledger for fintech". **No license shown** on the sidebar and `/blob/main/LICENSE`
  returned 404. Genuinely relevant to payments work; blocked on license
  verification. Carried forward to the next pass.

---

# History

*Everything below is preserved from earlier passes. Do not rewrite.*

*Column labels in the section below were normalised from Spanish to the
canonical English headers on 2026-11-09 so the compiler reads them as headers
rather than ingesting `Nombre` as an entity. **No data row was altered.***


## 2026-07-02

**Re-verification note (2026-11-09):** three of the ten repos in the section
below no longer resolve — `sammygallant214/CryptoDesk-ai`,
`Devsinfin/bank-churn-random-forest` and `skstmdals1-ctrl/bybit-dashboard`.
The rows are preserved as the dated record; treat those three as dead links.

> Última actualización: 2026-07-02

| Repo | License | Description | Stars |
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
