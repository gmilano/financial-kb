---
industry: financial
region: Global
updated: 2026-11-25
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

---

## The servicing and reporting backbone — new 2026-11-22 (pass 5)

Passes 3 and 4 catalogued the rails that **carry** money: ACH, ISO 8583,
ISO 20022, Pix, `pain.001`, `camt.053`. This pass catalogues the plane where
money is **disputed, reported and booked** — and it was empty. A term census
across all eight files before this pass:

| Term | Occurrences before this pass |
|---|---|
| `chargeback` | 0 |
| `general ledger` | 0 |
| `accounts payable` / `accounts receivable` | 0 / 0 |
| `three-way` match | 0 |
| `dunning` | 0 |
| `loan servicing` / `mortgage` | 0 / 0 |
| `interchange` / `card issuing` / `EMV` / `tokeniz` | 0 / 0 / 0 / 0 |
| `CECL` / `IFRS 9` / `stress test` | 0 / 0 / 0 |
| `cash forecast` / `FP&A` | 0 / 0 |
| `XBRL` | 1 (prose, no repo) |

Twelve zeroes. This is the fourth consecutive pass in this KB, and the fifth
across the KB family, to find that **the catalogue was built from the
vocabulary of the product and never from the vocabulary of the client's
ledger.** The remedy each time is the same and costs one pass.

### Moov's unlisted two-thirds — twelve Apache-2.0 repos, all live

`moov-io` has 60 repositories. Before this pass the KB listed seven of them.
Every repo below is Apache-2.0, byte-verified, **not archived**, and pushed
within the last four days.

| Repo | License | Stars | Forks | Last push | What it is |
|---|---|---|---|---|---|
| https://github.com/moov-io/metro2 | Apache-2.0 | 130 | 59 | 2026-11-22 | **Metro 2 consumer credit-history reporting.** The file format every US lender must send to Equifax/Experian/TransUnion. FCRA accuracy liability attaches to this file |
| https://github.com/moov-io/fincen | Apache-2.0 | 36 | 20 | 2026-11-20 | **FinCEN BSA E-Filing forms.** SAR and CTR construction — the filing end of every AML programme this KB already covers on the detection end |
| https://github.com/moov-io/imagecashletter | Apache-2.0 | 78 | 64 | 2026-11-20 | X9 Image Cash Letter / Check 21. Cheques are not dead in US commercial banking |
| https://github.com/moov-io/bai2 | Apache-2.0 | 27 | 12 | 2026-11-20 | BAI2 and X9.121 BTR3 cash-management balance reporting — reader, writer **and validator**. The corporate-treasury statement format |
| https://github.com/moov-io/x12 | Apache-2.0 | 23 | 8 | 2026-11-21 | ASC X12 EDI reader/writer. Remittance advice (820/835) and enrolment |
| https://github.com/moov-io/achgateway | Apache-2.0 | 86 | 49 | 2026-11-22 | Distributed, fault-tolerant ACH operations gateway — the service layer above `moov-io/ach` |
| https://github.com/moov-io/ach-test-harness | Apache-2.0 | 17 | 11 | 2026-11-20 | **Programmatic ACH returns, NOC/corrections and reconciliation scenarios.** A test rig for the failure paths, which is where servicing agents actually break |
| https://github.com/moov-io/rtp20022 | Apache-2.0 | 90 | 17 | 2026-11-20 | ISO 20022 for TCH Real Time Payments, in Go. **Live, 90 stars** |
| https://github.com/moov-io/fedwire20022 | Apache-2.0 | 12 | 9 | 2026-11-21 | ISO 20022 Fedwire. Supersedes `moov-io/wire` (archived — the FAIM format was deprecated July 2025) |
| https://github.com/moov-io/pinblock | Apache-2.0 | 17 | 9 | 2026-11-21 | PIN block management and security — ISO 9564 |
| https://github.com/moov-io/dukpt | Apache-2.0 | 17 | 11 | 2026-11-20 | ANSI X9.24 DUKPT key management. With `pinblock` and `iso8583`, this is the card-acceptance cryptography plane |
| https://github.com/moov-io/cadeft | Apache-2.0 | 11 | 6 | 2026-11-20 | **Canadian Payments Association CPA-005, 1464-byte EFT file** |

### Canada: the twice-measured gap, closed

`intel/market.md` records Canada as a gap searched across two passes that
"produced ~nothing both times", with the instruction to target OSFI by name.
The instruction was right about the method and wrong about the layer: the
Canadian asset is not a regulator document, it is `moov-io/cadeft`, a
**parser for the CPA-005 EFT file every Canadian direct-deposit and
pre-authorised-debit batch is written in.** It has 11 stars, so no regional
query would ever surface it; it is reachable only by enumerating an org that
the KB already trusted for one repo in seven.

**Generalisable:** when a region has been searched twice and returned nothing,
stop searching by region and **enumerate the orgs the KB already cites.** A
national payment format is maintained by whoever maintains the other national
payment formats, not by someone who tags their repo with the country.

### `moov-io/fincen` and the zero-result trap, measured a third time

Two functional queries run this pass:

| Query | `total_count` |
|---|---|
| `BSA SAR suspicious activity report filing` | **0** |
| `chart of accounts agent LLM posting` | **0** |

A zero that looks like proof the category does not exist. `moov-io/fincen`
builds **exactly** BSA E-Filing forms, has 36 stars and was pushed two days
ago. It is invisible to the query because a library that implements FinCEN
forms is named after the agency, not after the sentence a consultant would
write. This is the same failure the legal KB published as P31 (`LEDES legal
billing` = 6 results and excludes the only usable asset) and it has now been
measured in a second industry.

**Single-digit `total_count` is a symptom of a bad query far more often than
evidence of an empty category.** Before writing down "measured gap", re-run as
`{standard-or-agency-name} + {artefact noun}`: `FinCEN form`, `Metro 2
report`, `BAI2 statement`, `X12 remittance`.

## The ledger and books tier — new 2026-11-22 (pass 5)

The KB had transaction ledgers (`tigerbeetle`, `formancehq/ledger`,
`blnkfinance/blnk`). It had no **accounting** ledger — the double-entry book
of record with a chart of accounts, which is what every reconciliation,
close and audit agent has to post into.

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/ledger/ledger | **BSD-3-Clause** | 6,078 | 2026-11-21 | The original plain-text double-entry engine, C++. See the licence correction below |
| https://github.com/bex-co/beancount-io | MIT | 748 | 2026-11-22 | Plain-text double-entry, MIT at 1,078 B. Readme positions it explicitly for **AI agents** as well as humans — a text-file book of record is trivially diffable, reviewable and git-versioned, which is the audit trail an agent needs by construction |
| https://github.com/zhang-accounting/zhang | Apache-2.0 | 200 | 2026-11-22 | Beancount-compatible double-entry in Rust, with a server and web UI. Apache-2.0 verified at 11,357 B |
| https://github.com/manusimidt/py-xbrl | GPL-3.0 | 154 | 2026-11-09 | XBRL/iXBRL parser. **GPL-3.0 at 35,148 B — a licensing decision, not a default.** Listed because it is the most capable parser in the category, not because it is safe to vendor |

### Licence correction — `ledger/ledger` is BSD-3-Clause, not unlicensed

GitHub reports `NOASSERTION` for a 6,078-star repository. The file is at
`LICENSE.md`, 1,492 B, and opens:

> `Copyright (c) 2003-2025, John Wiegley.  All rights reserved.`
> `Redistribution and use in source and binary forms, with or without`
> `modification, are permitted provided that the following conditions are met:`

That is verbatim BSD-3-Clause, inside the 1.5 kB BSD band this KB already
records. **Fully permissive and usable.** This is the fourth consecutive pass
in which `NOASSERTION` resolved to a genuine permissive grant, and the first
in which the cause was simply the `.md` extension on the filename.

### The byte-count rule this KB published yesterday is wrong — use line count

`repos/foundations.md` (pass 4) sets: *"Apache-2.0 ≈ 11,358 B with appendix /
10,173 B without"*, and *"a byte count within ~50 B of a canonical length is a
whitespace question"*. Two repos found this pass break it:

| Repo | LICENSE bytes | Lines | `APPENDIX` present? | Truth |
|---|---|---|---|---|
| `moov-io/fincen` | 10,246 | **201** | **yes** | Full Apache-2.0, left-aligned |
| `moov-io/pinblock` | 10,246 | **201** | **yes** | Full Apache-2.0, left-aligned |
| `ajtgjmdjp/edinet-mcp` | 10,179 | **176** | **no** | Apache-2.0 with the appendix removed |
| `moov-io/metro2` | 11,357 | 201 | yes | Full Apache-2.0, canonical indentation |

`fincen` at 10,246 B sits **67 bytes** from `edinet-mcp` at 10,179 B. Under
the published rule both read as "Apache without appendix" — and the ~1,100 B
gap from canonical is far outside the ±50 B whitespace tolerance, so
`fincen` would instead have been flagged as a suspect or truncated grant and
the asset demoted. It is a complete, verbatim Apache-2.0; the entire 1,111 B
difference is the leading indentation on 201 lines.

**Rule change, and it is cheaper than the one it replaces:** identify a
licence by **line count plus a marker grep**, not by bytes. Line count is
invariant to indentation; byte count is not.

| Licence | Lines | Marker to grep |
|---|---|---|
| MIT | **21** | `Permission is hereby granted, free of charge` |
| Apache-2.0, full | **201** | `APPENDIX: How to apply the Apache License` |
| Apache-2.0, appendix stripped | **176** | `Licensed under the Apache License` and no `APPENDIX` |
| BSD-3-Clause | ~28 | `Redistribution and use in source and binary forms` |
| LGPL-3.0 | **187** | `GNU LESSER GENERAL PUBLIC LICENSE` |
| GPL-3.0 | ~674 | `GNU GENERAL PUBLIC LICENSE` + `Version 3` |
| AGPL-3.0 | ~661 | `GNU AFFERO GENERAL PUBLIC LICENSE` |

Measured this pass: MIT = 21 lines in 3 of 3 readings across unrelated repos
(1,067 / 1,071 / 1,078 B — a 11 B spread). Apache full = 201 lines in 4 of 4
(10,246 / 11,357 / 11,357 / 11,444 B — a **1,198 B** spread, 11.7%). The byte
count varies by two orders of magnitude more than the line count does.

Byte counts keep their one remaining job: a count **above** canonical means
text was added, and that text must be read.

**Copy this correction to every industry KB.** Pattern 9 (the licence-hygiene
CI gate) ships the byte-band logic as a runnable script in eight KBs; the
band check should become a line check with a marker grep. The failure mode it
prevents is the expensive direction — silently dropping a genuinely permissive
asset.

## Regulatory and statutory reporting — new 2026-11-22 (pass 5)

Filing is the one agent workload with a **hard external deadline, a machine-checkable
output and a named regulator** — the strongest possible shape for a first
engagement, and the KB had one prose mention of XBRL and no repo.

| Repo | License | Stars | Last push | Region | Note |
|---|---|---|---|---|---|
| https://github.com/kanedata/ixbrl-parse | MIT | 72 | 2026-10-16 | EMEA | iXBRL extraction in Python. The format UK statutory accounts are filed to Companies House and HMRC in |
| https://github.com/matthelmer/edinet-tools | MIT | 59 | 2026-10-13 | APAC | Japan's EDINET disclosures, **42 document types parsed as typed Python objects** |
| https://github.com/ajtgjmdjp/edinet-mcp | Apache-2.0 | 20 | 2026-10-26 | APAC | EDINET XBRL parser **and MCP server** — a Japanese filing corpus already wired for agents |
| https://github.com/josemmo/einvoicing | MIT | 180 | 2026-11-07 | EMEA | Read and create **EN 16931**-compliant European electronic invoices. MIT at 1,124 B |
| https://github.com/num-num/ubl-invoice | MIT | 143 | 2026-11-03 | EMEA | UBL and **Peppol BIS** documents in PHP. MIT at 1,070 B |
| https://github.com/SimansoftMZ/SAF-T | MIT | 8 | 2026-10-19 | EMEA | .NET generator for SAF-T (Standard Audit File for Tax). Mozambique/Portugal lineage; the OECD format adopted across Portugal, Poland, Norway, Angola |
| https://github.com/arnobotha/IFRS9-SICR-Definitions-Logit | MIT | 8 | 2026-01-22 | EMEA | R codebase behind a peer-reviewed article on defining SICR events under IFRS 9. **Research code, not a product** — the only permissive IFRS 9 asset found |

### `OpenPeppol/peppol-bis-invoice-3` — licence not determinable, stated as such

158 stars, 5.2 MB, pushed 2026-11-06, `git ls-remote` resolves. Every root-path
probe returns 404 across `master`, `main`, `release-3` and `gh-pages`:
`README.md`, `readme.md`, `index.md`, `LICENSE`, `LICENSE.md`, `LICENCE`,
`license.txt`, `NOTICE`.

Under this KB's own rule, absence is "measured" only when a control file in the
same repo returns 200. **No control file returned 200, so absence is not
measured** — and this is a fifth channel defect worth recording: when a
repository keeps no files at its root, `raw.githubusercontent.com` cannot
distinguish "no licence file" from "nothing at this path". Treat as the
normative Peppol BIS 3 specification, **read-only, do not vendor**; build
against `josemmo/einvoicing` or `num-num/ubl-invoice`, both of which carry a
filed MIT licence.

### The measured gap: LATAM's accounting plane

Searched this pass with the region's own vocabulary, not translated US terms:

| Query | `total_count` | Best result |
|---|---|---|
| `SPED ECD contabil` | 6 | `nfephp-org/sped-ecd` — **LGPL-3.0** (8,851 B / 187 lines, GitHub said `NOASSERTION`), 4 stars, last push 2024-07-01 |
| `contabilidad electronica SAT XML` | 3 | `albertotrece/sat` — GPL-2.0, 19 stars, last push **2015** |

**This is an informed gap, and it is the inverse of the region's payments
picture.** LATAM is the best-tooled region in this KB for payment rails —
`bacen/pix-api` is a central bank's own spec repo at 3,010 stars, and the
CNAB/boleto layer is live. For the *accounting* file the same company must
file — Brazil's SPED/ECD, Mexico's contabilidad electrónica — there is one
copyleft library two years stale and one abandoned in 2015. The mandate is
older and more universal than Pix; the open-source supply is absent.

Do not read this as "build a LATAM SPED parser". Read it with the EMEA rows
above: EN 16931, Peppol and SAF-T are **multi-country formats with one
implementation each**, which is why permissive libraries exist for them.
SPED and CFDI are single-country formats, so the addressable developer
population for a shared library is one country wide, and the work has gone
into commercial fiscal-emitter products instead. The same conclusion the
legal KB reached about porting LEDES to LATAM applies: **the format does not
transfer, the semantics do.**

---

## Pass 6 (2026-11-25) — FINOS enumerated, and the capital-markets message layer

This KB has cited "FINOS" 19 times across its files and **had never enumerated
the organisation.** `legend` and `perspective` appeared once each;
`FDC3`, `morphir`, `waltz`, `rune-dsl`, `tracdap` and `open-reg-tech-us-lcr`
appeared **zero** times. FINOS has **194 repositories**.

This is the `moov-io` lesson from pass 5 repeating exactly: that pass found
moov-io had 60 repos while the KB listed seven, and closed the gap by
enumerating the org rather than querying by topic. **Rule, now measured twice
in the same KB: when a KB cites an organisation by name, enumerate it. The
citation is evidence the org matters and evidence nobody has listed it.**

Channel note: `GET /orgs/{org}/repos` returns 403 in this session
("sessions are bound to their configured repositories"), but
`search/repositories?q=org:finos` works and paginates. That is the same channel
that rendered moov-io's 60 repos in pass 5.

### Foundational repositories added this pass — 12 rows, all verified

Existence by `git ls-remote`, licence by line count **and title line** (see the
pass-6 corrections in `agents/top.md`), metadata as of 2026-11-25.

| Repo | Licence | Stars | Pushed | Why it is foundational |
|---|---|---|---|---|
| https://github.com/finos/legend | Apache-2.0 | 1,558 | 2026-11-25 | Goldman Sachs' data modelling and governance platform, FINOS-hosted: model a financial domain once, generate the stores, APIs and lineage from the model |
| https://github.com/quickfix-j/quickfixj | QuickFIX Software License 1.0 (BSD-derived, 45 lines) | 1,161 | 2026-11-24 | The reference FIX engine on the JVM, actively committed. **Custom permissive licence — review before redistribution** |
| https://github.com/finos/architecture-as-code | Apache-2.0 | 471 | 2026-11-25 | Architecture expressed as a machine-checkable model (CALM schema) — lets a controls review run against the architecture, not a diagram of it |
| https://github.com/prowide/prowide-core | Apache-2.0 | 296 | 2026-11-19 | Model and parsers for **all** SWIFT MT (FIN) messages |
| https://github.com/prowide/prowide-iso20022 | Apache-2.0 | 240 | 2026-11-20 | Business model and parser for **all** ISO 20022 messages — the second implementation that makes a differential oracle possible |
| https://github.com/da4089/simplefix | MIT | 255 | 2026-06-01 | FIX protocol for Python — the pragmatic choice when the FIX work sits beside a Python analytics stack |
| https://github.com/finos/morphir | Apache-2.0 | 219 | 2026-11-25 | Business logic as a portable intermediate representation: write a rule once, generate it into several runtimes, and keep it readable by a reviewer |
| https://github.com/finos/TimeBase-CE | Apache-2.0 | 132 | 2026-11-25 | High-performance time-series store built for market data |
| https://github.com/finos/traderX | Apache-2.0 | 110 | 2026-11-25 | A complete reference trading application across many services — the realistic integration sandbox for a capital-markets agent |
| https://github.com/finos/vuu | Apache-2.0 | 63 | 2026-11-25 | View server + HTML5 UI for large, fast-updating tabular data — the blotter layer |
| https://github.com/finos/tracdap | Apache-2.0 | 58 | 2026-11-22 | Data and analytics platform **built for regulated environments**: immutable model/data versioning with reproducibility as a platform property, not a convention |
| https://github.com/finos/rune-dsl | Apache-2.0 | 50 | 2026-11-25 | Grammar and code generators behind the ISDA CDM — **this** is the code, the 297-star `common-domain-model` is the specification |

### `finos/tracdap` is the repo this KB has been describing for three passes without naming

Pass 5 concluded that NA, EMEA and APAC arrive at an AI assurance deficit by
three different routes and converge on **one deliverable: a control and
evidence layer**. It then had nothing permissive to point at.

`tracdap` is that thing, Apache-2.0, pushed three days ago: a platform whose
design premise is that in a regulated environment every model run must be
reproducible from immutable, versioned inputs. The evidence is produced by the
platform rather than assembled afterwards by whoever is preparing for the
examiner. For an engagement whose sale is "we can show the regulator how this
decision was reached", starting here is a materially shorter path than building
lineage onto a general ML stack.

Pair it with `finos/morphir` for the rule itself and the combination answers
both halves of a model-risk question: *what was the rule* (a readable IR, not
Python someone has to trust) and *what exactly ran* (an immutable, versioned
execution record).

### Regulation as code — and a real repo behind it

`finos/open-reg-tech-us-lcr` (Apache-2.0, 17★, pushed 2026-10-30) is the **US
Liquidity Coverage Ratio expressed as executable code** in Morphir. This is
the thing the phrase "regulation as code" usually gestures at without a
repository attached — searching `regulation as code Morphir` returns exactly
**one** result, an unlicensed workshop repo, so this plane is invisible to
topic queries and only reachable by enumerating FINOS.

Place it carefully. 17 stars and 23 forks is a **reference implementation**,
not a dependency: note that forks exceed stars, which is the signature of a
repo people copy and adapt rather than import. That is the correct way to use
it — read how a named US regulation is decomposed into testable functions,
then do the same for the client's rule under the client's data.

Contrast with what the open market offers for the same job: `Basel capital
calculation` returns 13 results whose best is a 4-star 2019 project;
`liquidity coverage ratio` returns 19 whose best permissive entry has 1 star.
The only serious permissive artefact in the regulatory-calculation plane is the
one inside a foundation.

### Counterparty identity — the reference-data layer the KB was missing

Every one of this KB's reconciliation, screening and reporting patterns needs
to answer "who is this counterparty", and the KB had no entry for it.

| Repo | Licence | Stars | Pushed | Role |
|---|---|---|---|---|
| https://github.com/WebOfTrust/vLEI | Apache-2.0 | 40 | 2026-10-15 | Open specifications for GLEIF's verifiable LEI — cryptographically verifiable legal-entity identity |
| https://github.com/ggravlingen/pygleif | MIT | 23 | 2026-11-24 | Python client for the GLEIF LEI register |
| https://github.com/opensanctions/followthemoney | MIT | 122 | 2026-11-20 | The entity/relationship data model underneath the whole OpenSanctions stack — usable on its own as a counterparty graph schema |
| https://github.com/opensanctions/nomenklatura | MIT | 274 | 2026-11-24 | Entity resolution and deduplication across FollowTheMoney streams |
| https://github.com/opensanctions/rigour | MIT | 74 | 2026-11-23 | Cleaning and validation for names, languages and identifiers — the unglamorous layer every screening false-positive traces back to |

The LEI is a **many-to-many identifier by construction** — issued by one body,
consumed by every counterparty — and the law in `agents/top.md` predicts
permissive tooling for it. It is there. Meanwhile `entity resolution KYC`
returns 10 results of which the two most complete are **AGPL-3.0** and the rest
are zero-star coursework: the *judgement* layer above the identifier is empty
again, exactly as predicted.

**Licence discipline, restated because this is where it bites:** every MIT row
in the OpenSanctions block covers **code only**. The data those tools load is
CC BY-NC 4.0 and parts of it cannot be licensed at all. See the data-trap
section in `agents/top.md`.

## Pass 7 (2026-11-25) — the actuarial method layer: an institutional ecosystem this KB had at zero

Census before research: `chainladder` 0, `casact` 0, `lifelib` 0, `actuarial` 1.
This is the largest single block of previously-unrecorded foundational code the
KB has added, and it is **not** a set of hobby projects — two of the four owners
are the profession's own bodies.

**Why it was missing:** every prior probe used the sector noun. None of these
repositories contains the word *insurance* in its name. See the naming rule in
`agents/top.md` pass 7.

### The owners, enumerated (the channel that worked: `search/repositories` with `org:`)

| Org | Repos | Dominant licence | Alive? |
|---|---|---|---|
| `casact` — **Casualty Actuarial Society** | 45 | **MPL-2.0** | Yes; flagship pushed 2026-11-23 |
| `JuliaActuary` | 16 | **MIT** | Yes; three repos pushed **2026-11-25**, the day of this pass |
| `lifelib-dev` | 12 | **MIT** | Yes; pushed 2026-11-23/24/25 |
| `actuarialopensource` | 18 | mostly **none** | No; newest push 2025-06-08 |

### P&C / general insurance — loss reserving and pricing

| Repo | Licence (read, title line + lines) | Stars | Last push | What it does |
|---|---|---|---|---|
| https://github.com/casact/chainladder-python | **MPL-2.0** (373 L, 16,724 B) | 292 | 2026-11-23 | The reference **loss-reserving** library: development triangles, chain ladder, Bornhuetter-Ferguson, Cape Cod, Mack and bootstrap stochastic reserving. Maintained by the Casualty Actuarial Society. This is the single most important repo added this pass |
| https://github.com/casact/FASLR | **GPL-3.0** (673 L, 35,130 B) | 60 | 2026-10-16 | Free Actuarial System for Loss Reserving — a GUI over the reserving workflow. **Strong copyleft: reference only** |
| https://github.com/casact/PCDM | **MPL-2.0** (373 L, 16,724 B) | 40 | 2022-06-22 | **Property & Casualty Data Model** — a published open data model for P&C. Dormant since 2022 but it is a *schema*, which ages far better than code |
| https://github.com/casact/tryangle | **MPL-2.0** (373 L, 16,724 B) | 30 | 2023-06-11 | Machine-learning reserving: automatic selection of development factors. Dormant |
| https://github.com/casact/reinspy | **MPL-2.0** (373 L, 16,724 B) | 9 | 2026-05-07 | **Reinsurance** structures in Python. Low stars, but it is the only maintained permissive reinsurance code found |
| https://github.com/casact/actsim | **Apache-2.0** (200 L, 11,341 B) | 11 | 2026-09-28 | Actuarial simulation. **The one fully permissive `casact` repo** — worth knowing when MPL is a procurement obstacle |
| https://github.com/casact/rp-bnn-claims | **MPL-2.0** (373 L, 16,724 B) | 17 | 2023-02-15 | Bayesian neural networks for individual claims reserving — CAS research paper code |
| https://github.com/mages/ChainLadder | **GPL (>= 2)**, declared in `DESCRIPTION`; **no `LICENSE` file** | 93 | 2026-08-13 | The original **R** chain-ladder package, on CRAN since 2008. Still maintained. Copyleft — **reference and oracle, not a dependency** |

### Life, annuity and mortality

| Repo | Licence (read) | Stars | Last push | What it does |
|---|---|---|---|---|
| https://github.com/lifelib-dev/lifelib | **MIT** (20 L, 1,074 B) | 229 | 2026-11-23 | Life actuarial models — savings, term life, annuity, universal life, plus economic and asset models. Built on `modelx`. **The most-starred permissive life-actuarial library** |
| https://github.com/franciscogarate/pyliferisk | **GPL-3.0** (673 L, 35,120 B) | 127 | 2026-11-11 | Life contingencies: commutation functions, annuities, assurances, from standard mortality tables. Actively maintained but **copyleft** |
| https://github.com/JuliaActuary/LifeContingencies.jl | **MIT** (26 L, 1,350 B) — API reports `NOASSERTION`; see the project-name cause in `agents/top.md` | 46 | 2026-10-30 | Life contingencies and insurance/annuity valuation in Julia |
| https://github.com/JuliaActuary/MortalityTables.jl | **MIT** (26 L, 1,349 B) — API reports `NOASSERTION` | 35 | 2026-10-25 | Standard **mortality and disability tables** with a common interface. The table-loading problem solved once |
| https://github.com/JuliaActuary/ActuaryUtilities.jl | **MIT** (18 L, 1,058 B) | 44 | **2026-11-25** | Duration, convexity, present value, IRR, risk measures. Pushed the day of this pass |
| https://github.com/JuliaActuary/FinanceModels.jl | **MIT** (20 L, 1,115 B) | 44 | **2026-11-25** | Yield curves, bootstrapping, discounting, asset modelling |
| https://github.com/JuliaActuary/EconomicScenarioGenerators.jl | **MIT** (20 L, 1,115 B) | 16 | 2026-10-25 | **Economic scenario generation** — the input every stochastic reserving and capital model needs, and the piece clients most often buy |
| https://github.com/JuliaActuary/ExperienceAnalysis.jl | **MIT** (20 L, 1,115 B) | 11 | 2026-10-25 | Exposure calculation for experience studies — the unglamorous step that decides whether a mortality study is correct |
| https://github.com/actuarialopensource/benchmarks | **MIT** (20 L, 1,087 B) | 16 | 2025-06-08 | Cross-implementation **benchmarks** of actuarial projections across Python/Julia/R/JAX. Dormant, but it is the nearest thing this plane has to a correctness oracle |

### The licence posture, stated plainly — it is not the MIT/Apache set

This KB's standing brief is to prefer MIT / Apache-2.0 / BSD. **The P&C
actuarial profession standardised on MPL-2.0**, and that is not a detail to
gloss:

- **MPL-2.0 is file-level copyleft.** Linking into a proprietary product is
  permitted; the obligation attaches to the **MPL-licensed files themselves** —
  modify one of those files and that file's source must be made available. It
  is materially weaker than GPL and materially stronger than MIT.
- **The practical consequence for an engagement:** `chainladder-python` can sit
  inside a commercial deliverable, provided the client's changes to
  *chainladder's own files* are published. **Wrap it, do not patch it** — call
  it across a boundary and keep client logic in separate, client-owned files,
  and the copyleft never reaches the client's IP. This is the same posture this
  KB already records for `openMF/web-app` in `verticals/solutions.md`.
- **The clean escape hatches, if counsel refuses MPL entirely:**
  `casact/actsim` (Apache-2.0), the whole of `JuliaActuary` (MIT) and
  `lifelib` (MIT). A **life** engagement can be done entirely under MIT. A
  **P&C reserving** engagement cannot avoid MPL without reimplementing chain
  ladder — which is a published method, so reimplementation is lawful and
  about two weeks of work, and `mages/ChainLadder` plus
  `actuarialopensource/benchmarks` give two independent oracles to test it
  against. **That is a real, costed choice to put in front of a client, not a
  blocker.**

### Pattern note — the differential oracle applies here, and better than usual

Pass 5's rule, *check whether a second permissive implementation exists before
writing a validator*, is satisfied twice over on this plane: chain-ladder
reserving exists in **Python (`casact/chainladder-python`, MPL-2.0)**, **R
(`mages/ChainLadder`, GPL)** and **Julia (`JuliaActuary/ChainLadder.jl`, MIT,
6 stars, dormant 2022)**, and `actuarialopensource/benchmarks` exists expressly
to compare them. Reserving is **arithmetic on a triangle** — given the same
triangle and the same method, the answers must agree to rounding. That makes it
one of the few judgment-adjacent workloads in this KB with a free correctness
oracle. See Pattern 22.

## Pass 8 (2026-11-25) — the SDMX layer: the inbound data format, and the licence is set by the institution

The plane: **SDMX (Statistical Data and Metadata eXchange, ISO 17369)** — the
published format in which central banks, statistical offices and
international financial institutions exchange macro and reference data. Every
IFRS 9 ECL scenario, every stress test, every treasury forecast and every
macro-grounded agent reads this data. The KB had **zero** rows on it.

### How big the installed base is, and which version matters

From the **BIS Irving Fisher Committee, IFC Report 17, "SDMX adoption and use
of open source tools"** (February 2025): SDMX is implemented by **about eight
tenths of respondents**, up from two thirds ten years earlier. An **SDMX Pulse**
newsletter (June 2026) breaks the versions down among central banks as
**SDMX 2.1 — 59%, SDMX 2.0 — 35%, SDMX 3.0 — 6%**, with around two thirds of
the rest planning to migrate to 3.0.

Two engineering consequences, and they point in opposite directions:

1. **Build against 2.1.** 94% of the installed base is on SDMX 2.x. The
   library to lead with is the one whose README says *"any SDMX 2.1 REST
   API"* — `ondata/opensdmx`. A 3.0-only client addresses 6% of publishers.
2. **The migration is the engagement.** Two thirds of non-adopters plan to move
   to 3.0, and `cyanheads/imf-mcp-server` is already SDMX 3.0 — ahead of the
   installed base. A client's 2.1→3.0 migration is a dated, scoped,
   machine-verifiable piece of work, which is exactly the shape this KB's
   pass-5 corollary says produces a defensible number in week one.

The IFC report figure is **February 2025** and the version split is a
**newsletter, not a survey** — both are cited here as what they are.

### Core SDMX libraries — 13 rows, all verified by `ls-remote` and licence read

| Repo | Licence (verified, method in `agents/top.md`) | ★ | Last push | Note |
|---|---|---|---|---|
| https://github.com/ondata/opensdmx | MIT (20 lines) | 58 | 2026-11-25 | **Lead with this.** Python CLI + library for *any* SDMX 2.1 REST API: Eurostat, ISTAT, OECD, ECB, World Bank |
| https://github.com/dr-leo/pandaSDMX | Apache-2.0 (176 lines) | 135 | **2023-12-28** | Most-starred Python SDMX client and **dormant ~2 years** — see successor below |
| https://github.com/khaeru/sdmx | Apache-2.0 (176 lines) | *unmeasured* | — | The live `sdmx1` package; successor to pandaSDMX. **Star count unmeasured — see channel note** |
| https://github.com/eblondel/rsdmx | **GPL (>= 2)** via `DESCRIPTION` | 111 | 2026-10-01 | Most-starred **R** SDMX reader, and **copyleft** — a deliverable that embeds it inherits GPL |
| https://github.com/amattioc/SDMX | **EUPL-1.2** (286 lines) | 99 | 2026-04-13 | "SDMX Connectors" — Java core with Excel/R/Python/MATLAB bindings. Copyleft |
| https://github.com/bis-med-it/pysdmx | Apache-2.0 (**14-line short-form**, BIS copyright) | 32 | 2026-11-25 | **The BIS's own** "opinionated Python SDMX library", pushed today |
| https://github.com/bis-med-it/sdmx-rest4js | Apache-2.0 (14-line short-form) | 16 | 2026-09-16 | JavaScript client for SDMX services |
| https://github.com/bis-med-it/gingado | Apache-2.0 (200 lines) | 41 | 2026-11-19 | BIS machine-learning library for economics and finance |
| https://github.com/bis-med-it/FMR-releases | Apache-2.0 (175 lines) | 4 | 2026-11-24 | Release channel for the **Fusion Metadata Registry** — see `verticals/solutions.md` |
| https://github.com/bis-med-it/sdmx-blockchain | Apache-2.0 (200 lines) | 3 | 2026-11-04 | Research: permissioned registry for SDMX metadata and restricted datasets |
| https://github.com/clojure-finance/ecbjure | Apache-2.0 (201 lines) | 20 | 2026-07-08 | ECB data from Clojure — FX, EURIBOR, €STR, HICP |
| https://github.com/worldbank/metadata-editor | MIT (20 lines) | 278 | 2026-11-20 | **World Bank**: edit, validate and manage DDI Codebook microdata metadata |
| https://github.com/sdmx-twg/sdmx-rest | **No licence file** (404 on 3 names × 3 refs) | 146 | 2026-09-11 | **The specification itself** — see the spec-licence note below |

### The per-publisher client layer, placed by region — 11 rows

This is the layer that makes the plane regionally actionable: one client per
statistical authority, and the licence is **the institution's, not the
language's**.

| Publisher | Repo | Licence (verified) | ★ | Last push | Region |
|---|---|---|---|---|---|
| Eurostat (community) | https://github.com/rOpenGov/eurostat | **BSD-2-Clause** (`DESCRIPTION`) | 257 | 2026-09-24 | EMEA |
| Eurostat (official) | https://github.com/eurostat/restatapi | **EUPL** (`DESCRIPTION`) | 36 | 2026-10-09 | EMEA |
| ILO (UN agency) | https://github.com/ilostat/Rilostat | **BSD-2-Clause** (`DESCRIPTION`) | 40 | 2026-11-24 | Global |
| OECD | https://github.com/expersso/OECD | **CC0** (`DESCRIPTION`) | 147 | 2025-08-08 | Global |
| INEGI (Mexico) | https://github.com/Eflores89/inegiR | **CC0** (`DESCRIPTION`) | 54 | 2026-10-15 | LATAM |
| Banco de México | https://github.com/Eflores89/banxicoR | **CC0** (`DESCRIPTION`) | 11 | 2026-10-15 | LATAM |
| ABS (Australia), R | https://github.com/MattCowgill/readabs | **MIT** (`DESCRIPTION`) | 114 | 2026-05-15 | APAC |
| ABS (Australia), Python | https://github.com/bpalmer4/readabs | MIT (20 lines) | 9 | 2026-11-24 | APAC |
| e-Stat (Japan), R | https://github.com/UchidaMizuki/jpstat | **MIT** (`DESCRIPTION`) | 15 | 2026-07-21 | APAC |
| e-Stat (Japan), R | https://github.com/yutannihilation/estatapi | **MIT** (`DESCRIPTION`) | 23 | **2020-04-12** | APAC — dormant, use `jpstat` |
| Banxico CEP (payments) | https://github.com/cuenca-mx/cep-python | MIT | 20 | 2026-09-22 | LATAM |

### The finding this plane produces: the licence is a function of the institution

Across the two tables above, grouped by owner:

| Institution | Licence posture | Usable by a studio? |
|---|---|---|
| **BIS** (Bank for International Settlements) | **Apache-2.0**, uniformly, across all 11 repos | **Yes, fully** |
| **World Bank** | **MIT** | **Yes, fully** |
| **ILO** (UN) | **BSD-2-Clause** | **Yes, fully** |
| **Eurostat** | **EUPL-1.1/1.2**, near-uniformly across 95 repos | **Copyleft — isolate it** |
| **SDMX-TWG** (the standards body) | **No licence at all** on the specifications | Map, not merchandise |
| Mexican agencies (community clients) | **CC0** — public domain | Yes, and freer than MIT |

**"It comes from a statistical authority" predicts nothing about the licence.**
Two international institutions headquartered 300 km apart — the BIS in Basel
and Eurostat in Luxembourg — have opposite defaults: Apache-2.0 against
EUPL-1.2. This is the legal KB's EMEA finding (*the state publishes code, MIT*)
split in two: **in the statistical layer the European Commission publishes
code under a European copyleft licence, while the bank for central banks
publishes under a US permissive one.** The practical rule is per-publisher
verification, every time, because the default varies by legal culture rather
than by sector, language or ecosystem.

**EUPL-1.2 deserves its own line**, being new to this KB. It is an OSI-approved
**copyleft** licence published by the European Commission in 23 languages, with
a compatibility list permitting relicensing to specified copyleft licences. It
is not MIT-equivalent and it is not a blocker either — it is a reciprocal
licence that has to be *architecturally isolated* exactly as pass 5's
Pattern 18 prescribes for country-specific format libraries: keep it out of the
core, behind an interface, so the obligation stays with the component.

**CC0 also deserves a caution.** `expersso/OECD`, `inegiR` and `banxicoR`
declare CC0 — a public-domain dedication, *freer* than MIT. It is unambiguously
usable, with one known gap relative to Apache-2.0: **CC0 contains no express
patent grant** (and explicitly does not license patent rights). For a data
client that is close to immaterial; it is worth a line in a client's
third-party register rather than a change of plan.

### The spec body publishes the standard and licenses nothing

`org:sdmx-twg` is 16 repositories holding the actual SDMX standard —
`sdmx-rest` (146★), `sdmx-json` (56★), `sdmx-ml` (13★), `sdmx-csv` (13★),
`sdmx-im` (the information model, 8★), `vtl` (15★) — and **every one reports no
licence**, confirmed by direct fetch across `main`/`master`/`develop`. The one
exception is `sdmx-twg/semver` (CC0-1.0), which is versioning guidance rather
than the standard.

This is pass 6's **spec ≠ code** class in its cleanest instance yet: the
specification repos are the most-starred things on the plane and are **not
software and not licensed**, while the implementations beside them (`pysdmx`,
`opensdmx`, `rsdmx`) are properly licensed software. It also means the plane's
most important asset — the SDMX standard — is readable at no cost and with no
membership, satisfying pass 7's third clause, which is precisely why the
implementation population is healthy.

> **Depend on `opensdmx` or `pysdmx`. Cite `sdmx-twg`. Never vendor it.**

### Channel note — `search/repositories` is not an existence oracle

`khaeru/sdmx` is the live successor to the dormant `pandaSDMX` (PyPI package
`sdmx1`, with a `conda-forge/sdmx1-feedstock` present and BSD-3 licensed).
`gh api search/repositories -f q='repo:khaeru/sdmx'` returns **`total_count:
0`**, while `git ls-remote` resolves the repository and
`raw.githubusercontent.com` serves its `LICENSE` (Apache-2.0, 176 lines,
10,173 B). **A `repo:` query returning zero does not mean the repository is
absent.** Its star count is recorded above as *unmeasured* rather than guessed.
This reinforces the standing channel rule: **`ls-remote` is the only reliable
existence channel**; `search/repositories` is a metadata channel that can be
silently incomplete.

---

## Pass 9 (2026-11-25) — the valuation stack, and the two repos that bridge a proprietary format

### The QuantLib stack — foundational, and absent from this KB until now

`QuantLib` appeared twice in prose across all eight files before this pass and
had no row anywhere. It is the single most widely depended-on open-source
library in financial services.

| Repo | Licence | ★ | Last push | Refs | Why it is foundational |
|---|---|---|---|---|---|
| https://github.com/lballabio/QuantLib | BSD-3-Clause (239-line `LICENSE.TXT`: 180-line copyright roster + verbatim 3-clause grant) | 7,804 | 2026-11-25 | 2,532 | Term structures, instruments, pricing engines, calibration, Monte Carlo. Latest tag `v1.44`. **Pushed to on the day of this pass** |
| https://github.com/lballabio/QuantLib-SWIG | same grant | 405 | 2026-11-25 | 826 | Official Python/Java/C#/R bindings — the only supported route for a non-C++ stack |
| https://github.com/OpenSourceRisk/Engine | Modified BSD (`license.txt`, 29 lines, 1,627 B) | 831 | 2026-09-15 | 248 | ORE: XVA, exposure simulation, sensitivities, capital analytics on top of QuantLib. 21 release tags, latest `v1.8.9.1` |
| https://github.com/OpenGamma/Strata | Apache-2.0 (`LICENSE.txt`, 201 lines, 11,357 B) | not measurable | tag `v2.9.4` | 3,029 | Java market-risk and analytics library. **Independent of QuantLib** — which is what makes a differential oracle possible |
| https://github.com/FinancePy-Org/FinancePy | **GPL-3.0** (673 lines, 35,148 B) | 3,239 | 2026-11-24 | 284 | Python derivatives pricing. Listed for completeness and **excluded from build-on**: copyleft |

**The licence spread in this plane is the whole decision.** Two BSD, one
Apache-2.0, one GPL-3.0 — and the GPL-3.0 one is the most convenient to install
(`pip install financepy`) and the second most starred. A team reaching for the
easiest import lands on copyleft. This is the clearest case in the KB for
running the Pattern 24 licence probe **before** the prototype, not after.

**`ORE` version numbering, measured, because the project's own communications
read like a conflict.** `opensourcerisk.org` and LSEG's posts describe "ORE
v15", "v16", "v17" and "the 15th release of Open Source Risk Engine", while the
repository's tags run `v1.8.6.1 … v1.8.9.1`. The repo carries **21 non-peeled
tags**, so the public numbering is a **release count, not a version string**.
Both readings are measured; no contradiction. Cite the tag when pinning a
dependency and the count never.

### `org:OpenSourceRisk` enumerated — snapshot 2026-11-25

Per the standing rule (when a plane looks thin, enumerate the org rather than
re-query the topic). Eight repos:

| Repo | Licence | ★ | Last push |
|---|---|---|---|
| `OpenSourceRisk/Engine` | Modified BSD | 831 | 2026-09-15 |
| `OpenSourceRisk/ORE-SWIG` | NOASSERTION | 60 | **2024-06-14** |
| `OpenSourceRisk/Dashboard` | NOASSERTION | 51 | **2016-11-14** |
| `OpenSourceRisk/Tools` | no licence file | 7 | 2025-02-23 |
| `OpenSourceRisk/QuantLib-SWIG` | NOASSERTION | 3 | 2026-09-11 |
| `OpenSourceRisk/explORE` | Apache-2.0 | 1 | 2026-02-19 |
| `OpenSourceRisk/QuantLibAddIn` | no licence file | 0 | 2026-10-12 |
| `OpenSourceRisk/OpenSourceRisk.github.io` | no licence file | 0 | 2026-09-15 |

**The useful negative: the Python binding is the stale part.** `ORE-SWIG` has
not been pushed since **2024-06-14** while `Engine` is current to September
2026. A Python-first engagement on ORE inherits an 18-month-old binding against
a moving C++ core. `lballabio/QuantLib-SWIG` (pushed the day of this pass) does
not have this problem — so **a Python ORE engagement is a binding-maintenance
commitment, and a Python QuantLib engagement is not.** That is a scoping fact
worth more than the star counts.

### The corporate-actions bridge — two MIT repos, three weeks old, and they prove the law

The ISO 15022 plane is empty (2 results, both 0★, both unlicensed, one dead
since 2017 — see `agents/top.md`). What exists instead is the **boundary**:

| Repo | Licence | ★ | Last push | What it does |
|---|---|---|---|---|
| https://github.com/roberts-rudzitis/mt564-bridge | MIT (20 lines, 1,073 B) | 1 | 2026-11-01 | **MT564 → ISO 20022 `seev.031` converter with XSD validation and conversion reports** |
| https://github.com/roberts-rudzitis/mt564-lens | MIT (20 lines, 1,073 B) | 1 | 2026-11-01 | Generator of **synthetic** SWIFT MT564 corporate-action messages — test fixtures without touching a live SWIFT feed |

Both resolve (2 refs each — single-author, single-branch, three weeks old).
**Recorded as design references and prototype seeds, not dependencies**, per
the maturity rule this KB applies to 0–1★ assets.

**Why they matter out of all proportion to one star each.** Open-source work on
a proprietary message format does not implement the format — it **converts out
of it into the published one**, and it builds its own fixtures because the real
messages cannot be redistributed either. That is clause 3 of this KB's law
observed in motion rather than inferred from a star count. For any custody or
asset-servicing engagement, the architectural implication is immediate: **do
not build on MT564; build on `seev.031` and treat MT564 as an inbound edge.**
The target format is published, has a schema, and can be validated in CI.

Also present and recorded for completeness:
`wdorninger/ddb_mt564-releases` (prebuilt DuckDB extension binaries for MT564,
no licence file, 2026-11-13) — **binaries without a licence, excluded.**

### EBA supervisory reporting — the plane `corep` could not find

| Repo | Licence | ★ | Last push | What it does |
|---|---|---|---|---|
| https://github.com/Meaningful-Data/xbridge | Apache-2.0 (200 lines, 11,356 B) | 10 | 2026-11-25 | **XBRL-XML → XBRL-CSV converter for EBA taxonomies** — the COREP/FINREP filing path. 129 refs |
| https://github.com/michelecirelli30-ai/eba-dpm-taxonomy-explorer | no licence file | 0 | 2026-11-23 | EBA Data Point Model and taxonomy explorer. Two days old, unlicensed — noted, not listed |
| https://github.com/bojaruniec/eba_taxonomy | MIT | 0 | 2026-08-10 | No description; 0★ |

`xbridge` was pushed at **16:34 UTC on the day of this pass**. At 10★ it is
invisible to every thematic query this KB has run, and it sits exactly on the
EBA's own 2026 migration from XBRL-XML to XBRL-CSV — a mandated format change
with a deterministic, machine-checkable output. **This is the best-shaped
EMEA filing asset found since `kanedata/ixbrl-parse`,** and it is placed under
EMEA in `intel/market.md`.

### Credit-scorecard libraries — the judgment plane that is not empty

| Repo | Licence | ★ | Last push | Refs |
|---|---|---|---|---|
| https://github.com/ShichenXie/scorecardpy | MIT | 814 | 2026-07-28 | 27 |
| https://github.com/guillermo-navas-palencia/optbinning | Apache-2.0 | 538 | 2026-11-22 | 194 |
| https://github.com/amphibian-dev/toad | MIT | 529 | 2026-06-16 | 112 |
| https://github.com/eddyzzl/marvis-risk-agent | MIT | 397 | 2026-11-10 | 129 |
| https://github.com/itlubber/scorecardpipeline | MIT | 266 | 2026-09-05 | 24 |
| https://github.com/jstephenj14/Monotonic-WOE-Binning-Algorithm | MIT | 118 | 2022-10-26 | 13 |
| https://github.com/boredbird/woe | MIT | 255 | **2019-10-29** | — |

Six live permissive implementations of the same judgment. **Three
independent ones (`optbinning`, `scorecardpy`, `toad`) make a differential
oracle possible on binning and WOE** — see `compose/patterns.md` Pattern 31.

### CBDC — permissive, Federal-Reserve-co-copyrighted, and dormant

| Repo | Licence | ★ | Last push |
|---|---|---|---|
| https://github.com/mit-dci/opencbdc-tx | MIT (`COPYING`, 21 lines, 1,139 B) | 931 | **2025-03-20** |
| https://github.com/mit-dci/opencbdc-tctl | NOASSERTION | 9 | **2024-08-08** |
| https://github.com/mit-dci/opencbdc-ui | NOASSERTION | 3 | **2024-09-03** |
| https://github.com/mit-dci/opencbdc-js | NOASSERTION | 2 | **2024-05-18** |
| https://github.com/mit-dci/terraform-aws-opencbdc-tctl | NOASSERTION | 7 | **2023-06-07** |

`opencbdc-tx`'s licence header reads *"Copyright (c) 2021 MIT (Digital Currency
Initiative) and the Federal Reserve"* — **an MIT grant co-held by a US central
bank**, which is a licence-provenance tier this KB has not recorded before
(pass 8's finding was that the institution sets the licence; here two
institutions co-set a permissive one).

**And the whole organisation is dormant.** Nothing in it has been pushed for
**20 months**; the satellites have been still for two years. 931★ on a
transaction processor for a hypothetical general-purpose CBDC, and no
maintenance. **Recorded as a reference architecture, explicitly not a
dependency.** For any CBDC or instant-settlement conversation it is the best
available public description of a two-phase-commit retail payment core — read
it, cite it, do not link it.

### Channel notes — unchanged except where stated

- `search/repositories` with `q='repo:<slug>'` and `q='org:<name>'`: **works**,
  and was again the channel that paid (eight ORE repos, twelve `lballabio`
  repos in two calls).
- **`OpenGamma` returns HTTP 422 for both `repo:` and `org:` queries** while
  `ls-remote` resolves 3,029 refs and `raw.githubusercontent.com` serves its
  licence. Sixth measured instance of a search false negative on a live repo.
  Strata's star count is recorded as **not measurable**, not guessed.
- `git ls-remote`: the only reliable existence channel. **27 of 28 new slugs
  resolved; the one that did not was `ultibi`, and it does not exist.**
- `raw.githubusercontent.com/<slug>/HEAD/<path>`: works. **Three new filename
  tiers this pass: `LICENSE.TXT`, `license.txt`, `COPYING`.** Add all three to
  every probe.
- `curl -sI github.com/<slug>`: **403 for everything, sixth consecutive pass.**
