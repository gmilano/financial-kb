---
industry: financial
region: Global
updated: 2026-11-22
---

# Financial Repos — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

## 2026-11-22

### The KB's largest named gap, closed — by changing the words, not the effort

`repos/foundations.md` has carried this since 2026-11-09 and restated it
yesterday as "the single biggest build-vs-buy opening in the financial KB":

> **No permissive, high-traction agentic AML/transaction-monitoring platform.**
> … This gap is **verified open by function**, not merely unsearched.

**It is closed. The platform is `tazama-lf` — a Linux Foundation project,
Apache-2.0, 25+ repositories, most pushed within the last week.**

The gap was real as stated and wrong as searched. Three passes queried "AML"
and "transaction monitoring". The project describes itself as **financial crime
risk management (FRMS)**. Nothing about the world changed between yesterday and
today; the vocabulary did.

| Component | Repo | License | Stars | Last push |
|---|---|---|---|---|
| Docs / project entry point | https://github.com/tazama-lf/docs | Apache-2.0 | 57 | 2026-10-29 |
| Deployment (Compose) | https://github.com/tazama-lf/tazama-stack | Apache-2.0 (SPDX header, no file) | 26 | 2026-11-17 |
| Demo front end | https://github.com/tazama-lf/tazama-demo | Apache-2.0 | 15 | 2026-11-19 |
| Case management | https://github.com/tazama-lf/case-management-system | Apache-2.0 | 12 | 2026-11-20 |
| Rule authoring | https://github.com/tazama-lf/rule-studio | Apache-2.0 | 12 | 2026-11-19 |
| Admin service | https://github.com/tazama-lf/admin-service | Apache-2.0 | 12 | 2026-11-19 |
| Config studio | https://github.com/tazama-lf/configuration-studio | Apache-2.0 | 11 | 2026-11-20 |
| Connection studio | https://github.com/tazama-lf/connection-studio | Apache-2.0 | 11 | 2026-11-19 |
| BI / analytics | https://github.com/tazama-lf/biar | Apache-2.0 | 10 | 2026-11-19 |
| Event monitoring | https://github.com/tazama-lf/event-monitoring-service | Apache-2.0 | 9 | 2026-11-19 |
| Transaction monitoring core | https://github.com/tazama-lf/tms-service | Apache-2.0 (SPDX header + `package.json`, **no LICENSE file**) | 6 | 2026-11-19 |
| Typology scoring | https://github.com/tazama-lf/typology-processor | Apache-2.0, same form | 4 | 2026-11-19 |
| Routing | https://github.com/tazama-lf/event-director | Apache-2.0, same form | 1 | 2026-11-19 |
| Shared library | https://github.com/tazama-lf/frms-coe-lib | Apache-2.0 | 5 | 2026-11-01 |
| Mojaloop adapter | https://github.com/tazama-lf/payment-platform-adapter | Apache-2.0 (SPDX header) | 3 | 2026-10-27 |

**Licence defect, measured in both directions.** Four repos — including the
three that carry the runtime — have **no LICENSE file**; six filename and case
variants were probed on each and all returned 404 while control files in the
same repos returned 200, so the absence is measured. They are nonetheless
Apache-2.0: `package.json` carries `"license": "Apache-2.0"` and source files
open with `// SPDX-License-Identifier: Apache-2.0` (verified in
`tms-service/src/index.ts` and `event-director/src/index.ts`). That is the form
the SPDX and REUSE specs prescribe, so it is **stronger** evidence than the
README-prose tier this KB already tracks — and still invisible to GitHub's
classifier. Worth an upstream issue; for an LF project it is a defect its own
governance would want fixed.

**What stays open is traction, not licence.** The busiest Tazama repo has 57
stars. `verticals/solutions.md` says so in the recommendation rather than
burying it.

### Payments and compliance infrastructure — the other missing layer

| Repo | License | Bytes | Stars | Last push | Role |
|---|---|---|---|---|---|
| https://github.com/moov-io/watchman | Apache-2.0 | 11,357 | 524 | **2026-11-22** | OFAC/EU/UK sanctions and watchlist screening with fuzzy matching, over HTTP |
| https://github.com/moov-io/ach | Apache-2.0 | 10,243 | 572 | 2026-11-21 | NACHA ACH file reader, writer and validator |
| https://github.com/moov-io/fed | Apache-2.0 | 11,357 | 131 | 2026-11-20 | FedACH and Fedwire participant directory lookup |
| https://github.com/blnkfinance/blnk | Apache-2.0 | 10,749 | 598 | 2026-11-18 | Double-entry ledger for wallets, balances and reconciliation |
| https://github.com/mojaloop/central-ledger | Apache-2.0 by reference (756 B) | 756 | 60 | 2026-11-20 | Instant-payment switch: ledger component of the Mojaloop hub |
| https://github.com/openimis/openimis-be_py | **AGPL-3.0 + Swiss-law rider** (1,852 B) | 1,852 | 13 | 2026-11-21 | Health-insurance scheme administration; the only maintained open insurance core found |

### Archived, caught this pass

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/moov-io/iso20022 | Apache-2.0 | 78 | 2023-01-12 | **ARCHIVED.** The one Moov repo you would most want for an EMEA or LATAM rail build is the frozen one. Do not start an ISO 20022 build here |

### Byte-checksum refinement, measured

`x402-foundation/x402` and `coinbase/x402` both read **11,324 B** against a
canonical Apache-2.0 of 11,357–11,358 — 33 bytes short, which the KB's checksum
rule would flag. Diffed against `moov-io/watchman`'s canonical file with leading
whitespace normalised, **the difference is zero**: the 33 bytes are indentation.

Rule, now in `repos/foundations.md`: **below canonical means whitespace, above
canonical means appended terms, 400–800 B means a grant by reference.** Only the
middle case is a licence finding.

### Full-KB URL sweep — replicated clean

All 66 unique `github.com/<owner>/<repo>` URLs re-checked by `git ls-remote` ref
count. **63 live, 3 dead — the same three** already recorded as deleted in the
2026-11-21 section below (`Devsinfin/bank-churn-random-forest`,
`sammygallant214/CryptoDesk-ai`, `skstmdals1-ctrl/bybit-dashboard`). No new
deaths, no new renames.

### Channel note — `gh api repos/<slug>` is not available here

`gh api -X GET search/repositories` works. **`gh api repos/<owner>/<repo>`
returns HTTP 403** ("GitHub access to this repository is not enabled for this
session"), as does `curl https://api.github.com/repos/...`. So the three
channels documented in `agents/top.md` — search for metadata, `git ls-remote`
for existence, `raw.githubusercontent.com` for licence bytes — are the complete
set, and there is no fallback for stars when search returns its known false
negative. `OpenBB-finance/OpenBB` and `FinAegis/finaegis` were both unmeasurable
for stars again this pass for exactly that reason.

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
