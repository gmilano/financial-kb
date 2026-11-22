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
measured on 2026-11-22: **`moov-io/iso20022` is ARCHIVED** (78 stars, last push
2023-01-12).

> **Correction, same day, pass 4.** The sentence that followed this measurement
> in the pass-3 revision — *"the one Moov repo you would most want is the one
> that is frozen. Do not start an ISO 20022 build there."* — was withdrawn
> within the day. The archive fact is correct; the conclusion drawn from it was
> not. See **The payment message layer** below. `moov-io` itself is much larger
> than the four repos listed above: `moov-io/iso8583` (539 stars, pushed
> 2026-11-22) and `moov-io/paygate` (133) were never in this KB.

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

## The payment message layer — a dead end this KB wrote, reopened the same day

**This is the third consecutive finding of the same shape, and the first time
this KB made the error itself rather than inheriting it.**

One section above, this file celebrates closing its largest named gap by
discovering that the AML platform it said did not exist was filed under
*financial crime risk management*. Eleven hours later, the same pass's own
conclusion — *"Do not start an ISO 20022 build there"* — was found to generalise
one archived repository into a dead category.

ISO 20022 tooling is not scarce, frozen or immature. It is mature, permissive,
actively maintained, and it is filed **under the names of the messages**
(`pain.001`, `camt.053`, `pacs.008`, `MT940`, `BAI2`) rather than under the name
of the standard. This is the P31 rule from the legal KB — *the industry word is
a filter, not a clarification* — confirmed in a fourth industry: `ISO 20022
agent LLM` returns **1** repository worldwide, while `camt.053` returns **154**
and `pain.001` returns **223**.

Every row below was verified on 2026-11-22: existence by `git ls-remote`,
licence read byte-for-byte from `raw.githubusercontent.com`, metadata by
`search/repositories`. **0 of 14 archived.**

| Repo | License (bytes read) | Stars | Last push | Role in a build |
|---|---|---|---|---|
| https://github.com/prowide/prowide-iso20022 | Apache-2.0 (11,357) | 240 | 2026-11-20 | **The direct replacement for the archived Moov repo.** Business model and parser for *all* ISO 20022 message definitions. Java, 99 forks, pushed two days ago. This single row retires the "do not start here" verdict |
| https://github.com/moov-io/iso8583 | Apache-2.0 (10,243) | 539 | **2026-11-22** | **The card rail**, and the single largest absence this census found. Marshal and unmarshal ISO 8583 — the message format behind card authorisation everywhere. Pushed today, 168 forks |
| https://github.com/moov-io/iso8583-connection | Apache-2.0 (10,246) | 121 | 2026-11-20 | Connection handling for ISO 8583: binary framing, message matching, idle handling. The part teams underestimate after the codec works |
| https://github.com/moov-io/paygate | Apache-2.0 (11,357) | 133 | 2026-11-20 | ACH origination as a RESTful service, so the application never learns the NACHA file layout. The service-shaped companion to `moov-io/ach` |
| https://github.com/sebastienrousseau/bankstatementparser | **Apache-2.0 OR MIT** (dual) | 64 | 2026-11-18 | One parser across **CAMT, pain.001, MT940/MT942, OFX/QFX, BAI2, CSV and PDF**. The broadest single-dependency answer to "ingest whatever the bank sends" |
| https://github.com/sebastienrousseau/pain001 | Apache-2.0 (11,061) | 49 | 2026-11-18 | Generates **and validates** pain.001 v03–v12 and pain.008 from CSV, SQLite or JSON — credit-transfer and direct-debit *initiation* files |
| https://github.com/sebastienrousseau/askiso | Apache-2.0 (10,173) | 1 | 2026-11-19 | Validator, linter and converter for pacs.008, pain.001 and camt.053 against the schemas. New and unproven; listed because validation-as-a-step is the scarce piece |
| https://github.com/sebastienrousseau/bankstatementparser-mcp | Apache-2.0 (10,287) | 3 | 2026-11-18 | The same parser exposed **as an MCP server** — the shortest path from a bank file to an agent that can read it |
| https://github.com/wolph/mt940 | BSD-3-Clause (1,490) | 106 | 2026-11-16 | MT940 statement parser, Python, 58 forks. Twelve years old and pushed last week |
| https://github.com/viafintech/camt_parser | MIT (1,082) | 23 | 2026-11-11 | camt.052 / camt.053 / camt.054 parser, Ruby, by viafintech GmbH (Berlin) |
| https://github.com/ministryofjustice/bai2 | MIT (1,128) | 30 | 2026-03-01 | **BAI2** parser and writer, Python. Copyright **HM Government (Ministry of Justice Digital & Technology)** — a government department maintaining a bank-file parser in the open, which is a provenance argument a bank's procurement team understands |
| https://github.com/inisos/bank4j | MIT (1,076) | 20 | 2026-06-13 | Generates ISO 20022 payment-initiation XML, with IBAN and BIC validation. Java |
| https://github.com/RiverFinancial/nacha | Apache-2.0 (11,357) | 18 | 2026-03-12 | NACHA file generation and parsing in Elixir, for a stack that is not Go |
| https://github.com/quickfix-j/quickfixj | **Custom — see note** (2,096) | 1,161 | **2026-11-22** | The de-facto open FIX engine: 679 forks, pushed today. Securities-side counterpart to everything above. **Its licence is not Apache or MIT — read the note before shipping** |

### Why this layer is worth more than its star counts

The whole table is ~2,700 stars, less than a fiftieth of what this KB's trading
agents carry. It is also the layer where a bank's **money and its regulatory
exposure actually move**, and the Cambridge CCAF 2026 survey puts the ratio
plainly: **four of the top five AI use cases in financial services are
back-office functions.** A KB whose discovery metric is star counts will
systematically under-weight exactly the work the client is funding.

These repos are also *deterministic components*, which is their second
advantage. A pain.001 either validates against the schema or it does not. That
makes them the correct substrate for the `MODELS READ, RULES DECIDE` rule this
KB family inherited from the legal pass: the agent interprets the exception, the
parser decides the format, and nothing about the decision is probabilistic.

### Two licence tiers this KB had not catalogued

`intel/trends.md` §14 records five tiers of licence evidence. Two more were
measured this pass, both on high-traction repositories, and both invisible to
GitHub's classifier (it reports `NOASSERTION` for each):

**Tier 6 — a specification licence, not a software licence.**
`finos/common-domain-model` (296 stars, 142 forks) ships a 16,142-byte
**Community Specification License 1.0**. It is a standards-body instrument with
patent and contribution commitments, written for a *specification*. It is not
OSI-approved and does not read like a code grant. Treat an implementation of the
spec and a copy of the spec as two different legal objects.

**Tier 7 — permissive with an advertising obligation.**
`quickfix-j/quickfixj` (1,161 stars, pushed today) ships the 2,096-byte
**QuickFIX Software License, Version 1.0**. It is BSD-4-clause-shaped, and
clause 3 is the one that matters commercially:

> *"The end-user documentation included with the redistribution, if any, must
> include the following acknowledgment: 'This product includes software
> developed by quickfixengine.org'"*

Clauses 4 and 5 further forbid using the QuickFIX name to endorse a derived
product or calling a derived product "QuickFIX". **Nothing here blocks
commercial use**, but it is not the drop-in that "permissive" implies: it adds a
documentation deliverable to every client handover and it is the classic
GPL-incompatible advertising clause. A KB row reading "QuickFIX/J, permissive"
would be true and would still have set a delivery team up to miss an obligation.

**Both tiers share one lesson:** `NOASSERTION` is not a licence finding, it is
the classifier declining to answer. Every `NOASSERTION` row in every industry KB
needs the file opened.

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
- **No permissive SEPA or Pix payment-*initiation* agent — narrowed 2026-11-22
  (pass 4), and the narrowing is the useful part.** Reading is solved in both
  regions (BankMCP and the open-banking.io MCP for PSD2; the BACEN spec for
  Pix). The gap as previously written conflated two different things. **File
  construction is solved and permissive**: `sebastienrousseau/pain001`
  (Apache-2.0) and `inisos/bank4j` (MIT) both build valid pain.001
  initiation messages today. What is open is the **bank-connected** leg —
  authenticating to an ASPSP and submitting. That asymmetry is a product
  decision across the space rather than an accident: read-only is what a bank
  approves first. Stated this way the gap is a *fundable integration*, not a
  missing category.
- **No permissive Verification of Payee (VoP) implementation with traction —
  new, measured, and the strongest EMEA opening in this file.** VoP has been
  **mandatory for euro-area payment service providers since 9 October 2025**
  under the Instant Payments Regulation: a payee name-match returned within five
  seconds, on standard *and* instant transfers. A `verification of payee VoP
  SEPA` search returns **`total_count: 2` worldwide** —
  `softvasco/payee-match` (MIT, 1,068 B, 0 stars, pushed 2026-11-21, .NET, EPC
  VOP scheme, explainable close-match handling) and
  `untitledfinancial/dpx-compliance-public` (BSD-3-Clause, 0 stars). A
  compliance obligation already in force across the euro area, carrying a hard
  latency budget, with two zero-star repositories against it. Compare the AML
  gap that took three passes to close: this one is open **by measurement, in the
  direction that matters** — the demand is legally mandated and dated, and the
  supply is empty.

---
*Re-verified and extended 2026-11-22 **pass 4** (same-day pass 3; prior passes
2026-11-21, 2026-11-09). Pass 3 added a payments-and-compliance infrastructure
tier (5 permissive rows) and closed the AML/transaction-monitoring gap with
Tazama. **Pass 4 reopened pass 3's own ISO 20022 dead end** — 14 permissive
message-layer rows, 0 archived, every licence read by bytes — catalogued licence
evidence tiers 6 and 7 (Community Specification License; QuickFIX advertising
clause), narrowed the SEPA-initiation gap to its bank-connected leg, and opened
a new measured gap on Verification of Payee.*
