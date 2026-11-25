---
industry: financial
region: Global
updated: 2026-11-25
---

# Financial Services AI Agents — Curated Top Set

> Open source agents and agentic platforms for financial services.
> Preference order for Globant build-on: **MIT / Apache 2.0 / BSD**.

## Verification method (2026-11-21) — read this before trusting a row

Three independent channels, because each one has a measured blind spot:

1. **Metadata** — `gh api -X GET search/repositories -f q='repo:<slug>'` returns
   stars, SPDX license, `pushed_at` and `archived` in one call. **It produces
   false negatives on live repos** (see below), so a miss here is not evidence.
2. **Existence** — `git ls-remote <url>` ref count and HEAD SHA. This is the
   only channel that is authoritative about whether a repo exists.
3. **License** — the LICENSE file read **byte by byte** from
   `raw.githubusercontent.com/<slug>/HEAD/<path>`. Byte length discriminates:
   MIT ≈ 1.05–1.1 kB, Apache-2.0 ≈ 11.35 kB, AGPL-3.0 ≈ 34.5 kB, GPL-3.0 ≈ 35 kB.

**`curl -sI https://github.com/<slug>` is useless here.** It returns 403 through
this environment's proxy for live, renamed and nonexistent repos alike, so it
cannot discriminate and carries zero information. The brief's prescribed URL
check does not work in this environment; the three channels above replace it.

### Three channel defects measured this pass — they change how rows are read

- **`search/repositories` has false negatives on live repos.** `OpenBB-finance/OpenBB`
  and `FinAegis/finaegis` both return HTTP 422 "resources do not exist or you do
  not have permission", and `stefan-jansen/zipline-reloaded` returns
  `total_count: 0` — yet all three are live (5,537 / 1,645 / 291 refs and a
  resolving HEAD SHA). So **stars and SPDX from this channel are a precision
  filter, never a coverage filter.** A row must never be dropped because search
  missed it.
- **`raw.githubusercontent.com` paths are case-sensitive.** `bacen/pix-api`
  returns 404 for `README.md` and 200 for `readme.md`. A case-blind probe
  reports "file absent" when the file is merely spelled differently — which
  would silently corrupt any license-absence finding. Absence is only
  "measured" when the probe tried case variants **and** a control file in the
  same repo returned 200.
- **SPDX `None`/`NOASSERTION` is not "no license", it is "GitHub's classifier
  could not".** Three cases this pass: OpenBB (11,476 B = canonical Apache-2.0
  plus a 129 B copyright preamble), `OpenFin8/openfin8-br` (12,066 B = Apache-2.0
  plus three copyright lines), `bacen/pix-api` (no file at all, but an Apache-2.0
  badge in the readme). Same classifier output, three different realities.

## Agents and agentic platforms — 11 permissive, re-measured 2026-11-22

| Agent | Repo | License | Stars | Last push | What it is |
|---|---|---|---|---|---|
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 123,393 | 2026-11-17 | Multi-agent LLM trading framework that simulates the roles of a trading firm (analyst, researcher, trader, risk manager) |
| OpenBB | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 | 75,600 | active | Open data platform for analysts, quants and AI agents — the de facto open market-data access layer |
| ai-hedge-fund | https://github.com/virattt/ai-hedge-fund | MIT | 64,796 | 2026-11-09 | An AI hedge fund team: LLM agents modelled on named investor styles, debating and voting on positions |
| qlib | https://github.com/microsoft/qlib | MIT | 50,481 | 2026-11-04 | AI-oriented quant investment platform from Microsoft; supervised learning, market-dynamics modelling and RL, with RD-Agent for automated research |
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,059 | 2026-04-13 | Foundation model for "the language of financial markets" — pretrained on market series rather than text. **See the staleness flag below** |
| ccxt | https://github.com/ccxt/ccxt | MIT | 44,950 | 2026-11-20 | Unified trading API across 100+ crypto exchanges and prediction markets (JS/TS, Python, C#, PHP, Go, Java, Rust) |
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 38,652 | 2026-11-21 | Personal trading agent from HKU Data Science lab; natural-language strategy authoring |
| FinGPT | https://github.com/AI4Finance-Foundation/FinGPT | MIT | 21,661 | 2026-11-18 | Open financial LLMs with released weights on HuggingFace; sentiment, NER and forecasting heads |
| hummingbot | https://github.com/hummingbot/hummingbot | Apache-2.0 | 21,337 | 2026-11-20 | Framework to build and deploy high-frequency crypto market-making and arbitrage bots |
| FinRL | https://github.com/AI4Finance-Foundation/FinRL | MIT | 17,158 | 2026-11-18 | Financial reinforcement learning library — environments, agents and backtests for RL-driven portfolio policies |
| FinRobot | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 | 8,461 | 2026-10-24 | Agent platform for financial applications: equity research, report drafting and decision workflows over LLMs |

All 11 are MIT or Apache-2.0 — usable as a Globant starting point with no
copyleft contamination.

**24-hour drift, measured 2026-11-22:** +90 TradingAgents, +66 FinGPT, +31
Vibe-Trading (which also pushed yesterday), +26 qlib, +24 Kronos, +19
hummingbot, +16 ai-hedge-fund, +10 ccxt, +6 FinRL, +4 FinRobot. Nothing moved
more than 0.3%, nothing changed licence, nothing was archived. **OpenBB could
not be re-measured** — `search/repositories` returned the same false negative
documented above, and `git ls-remote` confirms it live. One day is below this
catalogue's noise floor; the pass value is in the two tiers added below, not in
these numbers.

## Region-placed agents — new this pass

The 11 rows above are globally-sourced research frameworks. **None of them touch
a regional payment rail or an open-banking API**, which is what a real
engagement in EMEA, APAC or LATAM actually integrates with. These close that
gap. Traction is low and is stated per row rather than hidden.

| Agent | Repo | License | Stars | Region | What it is |
|---|---|---|---|---|---|
| BankMCP | https://github.com/noskillish/bankmcp | MIT | 327 | EMEA | Self-hosted read-only MCP server that lets an agent read real bank accounts over the Enable Banking PSD2 API. MIT verified at 1,066 B |
| idx | https://github.com/fzn0x/idx | MIT | 234 | APAC | Indonesian stock market (IDX/IHSG) analysis from the terminal. MIT verified at 1,093 B. The only Indonesia-specific asset found in this whole sweep |
| accountant24 | https://github.com/machulav/accountant24 | Apache-2.0 | 70 | Global | Personal-finance agent that runs against any LLM including local ones. Apache-2.0 verified at 11,358 B. No bank sync — works from imported statements |
| open-banking.io MCP | https://github.com/open-banking-io/mcp-server | MIT | 0 | EMEA | Read-only MCP server over the open-banking.io PSD2 API: accounts, balances, transactions. MIT verified at 1,072 B. **0 stars** — included because it is function-matched and license-clean, not because it is proven |

**Why a 0-star row is here at all.** The prior pass excluded every low-star repo
on principle. That rule is right for *ranking* and wrong for *coverage*: it
guarantees that a gap stays open even after something fills it, because
anything new has no stars yet. The honest framing is that stars measure social
proof, so "no permissive X exists" can only ever mean "no permissive X **with
social proof** exists". Both PSD2 MCP servers above are read-only by design,
which is also the only shape a bank will let near production first.

## Declared-but-not-filed licenses — a third category this KB needs

Two assets this pass state a permissive license in prose while shipping **no
LICENSE file**. That is neither "MIT, safe to use" nor "unlicensed, avoid", and
collapsing it into either one is wrong.

| Asset | Repo | Declared | Filed | Stars | Measurement |
|---|---|---|---|---|---|
| Dexter | https://github.com/virattt/dexter | MIT, in the README body ("This project is licensed under the MIT License") | **No LICENSE file** | 27,988 | Probed 11 filename and case variants across HEAD, main and master; all 404 while `README.md` and `package.json` returned 200. `package.json` has **no** `license` field. SPDX from search: `None`. **Re-measured 2026-11-22: still no file, and the repo has now gone cold — last push 2026-09-23, two months** |
| Pix API spec | https://github.com/bacen/pix-api | Apache-2.0, via a shields.io badge in `readme.md` | **No LICENSE file** | 3,010 | Root listing is `openapi.yaml`, `readme.md`, `changelog.md`, `.gitignore`, `.github/`. Sidebar shows no license name |

**How to treat them.** A README sentence is a real statement of intent from the
copyright holder, but it is not a license text: there is no copyright line, no
warranty disclaimer and no grant wording, and GitHub's classifier reads nothing.
For Globant that means: fine to read, fine to prototype against, **not** clean
enough to vendor into client deliverables until upstream adds the file or
confirms in writing. Dexter at 27,988 stars was the one worth chasing —
a one-line fix for the maintainer that unblocks a top-20 asset. **Downgraded
2026-11-22:** the repo has not been pushed since 2026-09-23, so there may be no
maintainer attention to chase. Treat it as read-only reference material.

This also corrects a prior record: earlier rotation notes carried
"Dexter (MIT, ~27k stars)" as settled fact. The license was never filed.

## Flagged — real and permissive, but check before you build

| Agent | Repo | License | Stars | Flag |
|---|---|---|---|---|
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,059 | **Last push 2026-04-13 — seven months cold**, while every other top row pushed within the last three weeks. It is a published foundation model (AAAI 2026), so a frozen artefact is defensible, but do not plan on upstream fixes |

## Reference lists, not agents

| Resource | Repo | License | Stars | Note |
|---|---|---|---|---|
| awesome-ai-in-finance | https://github.com/georgezouq/awesome-ai-in-finance | CC0-1.0 | 6,700 | Curated index of LLM / DL strategies and tools in financial markets. A discovery feed, not something to build on |
| awesome-open-finance-brasil | https://github.com/ciro-maciel/awesome-open-finance-brasil | CC0-1.0 | 0 | Open Finance and Open Insurance in Brazil: BCB norms, official specs, open data, aggregators, open code. **0 stars**, updated 2026-11-10. The best single entry point to the LATAM regulatory corpus found this pass |
| awesome-pix | https://github.com/ciro-maciel/awesome-pix | CC0-1.0 | 1 | Pix for integrators: Central Bank norms, APIs, SDKs, providers, in Portuguese plus 14 languages. Companion to the above |

## Agentic payment and commerce protocols — the tier this KB did not have (2026-11-22)

**How it was missed, stated plainly.** `intel/trends.md` §7 concluded from
`finance AI agent created:>2026-08-01 stars:>=80` returning `total_count: 4`
that new financial-agent creation "has largely stopped at any scale that
matters". **That query was re-run today and returns exactly the same 4 repos** —
the measurement replicates. The inference did not survive. An entire permissive,
actively-maintained category worth **more than 15,000 stars** was invisible to
it, because none of these repos contain the phrase "finance AI agent" and all
but one were created before the date window. The metric answered the question
asked; the question was vocabulary-shaped. **Discovery debt, not an ecosystem
stall, was the dominant term.**

This is the layer that moves money when an agent decides to spend. It is where
"agentic money" in `intel/trends.md` §3 stopped being a narrative.

| Asset | Repo | License | Stars | Created | Last push | Layer |
|---|---|---|---|---|---|---|
| x402 | https://github.com/x402-foundation/x402 | Apache-2.0 | 6,820 | 2025-02-21 | 2026-11-20 | **Settlement.** HTTP `402 Payment Required` turned into a working payment protocol; a facilitator settles. The neutral-governance home of the spec |
| AP2 | https://github.com/google-agentic-commerce/AP2 | Apache-2.0 | 3,283 | 2025-05-30 | **2026-06-17** | **Authorization.** Agent Payments Protocol: signed Intent, Cart and Payment mandates that carry the user's authority to the merchant. **See the staleness finding below** |
| Solana Pay | https://github.com/solana-foundation/pay | MIT | 1,810 | 2021-10-19 | 2026-11-09 | **Client.** CLI and spec that now covers agentic payments (x402, MPP, AP2) as well as its original QR/transfer flow |
| ACP | https://github.com/agentic-commerce-protocol/agentic-commerce-protocol | Apache-2.0 | 1,609 | 2025-09-29 | 2026-07-18 | **Checkout.** Interaction model connecting an agent to a merchant's existing checkout. Four months since last push |
| AgentKit | https://github.com/coinbase/agentkit | Apache-2.0 (short form) | 1,359 | — | 2026-11-10 | **Wallet/tooling.** Gives an agent on-chain capabilities. SPDX reads `NOASSERTION`; see the licence note below |
| a2a-x402 | https://github.com/google-agentic-commerce/a2a-x402 | Apache-2.0 | 572 | — | 2026-11-11 | **Bridge.** x402 as an A2A extension, so agent-to-agent messaging can carry payment. The only *active* repo in Google's agentic-commerce org |
| AgentPay SDK | https://github.com/worldliberty/agentpay-sdk | MIT | 460 | — | 2026-11-16 | **Wallet/tooling.** MCP server plus SDK: wallets, x402 payments, market data |
| Trusted Agentic Commerce | https://github.com/forter/trusted-agentic-commerce-protocol | MIT | 180 | — | 2026-07-08 | **Trust.** Authentication and payload encryption between agent, merchant and processor. Vendor-authored (Forter), four months cold |
| agent-payment-node | https://github.com/nuanu-ai/agent-payment-node | MIT | 73 | — | 2026-11-19 | **Runtime.** Local-first payment runtime for agents |
| agentcash-router | https://github.com/Merit-Systems/agentcash-router | MIT | 32 | — | 2026-07-20 | **Routing.** Routes agent payments across facilitators. Small and quiet |
| awesome-agentic-payments | https://github.com/bitrefill/awesome-agentic-payments | CC0-1.0 | 27 | — | 2026-06-29 | **Index, not code.** Curated list of the protocols and SDKs in this tier |

Eleven rows, all permissive, every licence read byte-for-byte today.

### The measurement that changes which one you build on

**AP2 (3,283 stars) has not been pushed since 2026-06-17 — five months.
x402 (6,820 stars) was pushed two days ago.** Both are Apache-2.0 and both are
in every "agentic payment stack" explainer as co-equal layers. They are not
co-equal by maintenance.

Two qualifiers, because this is a recommendation and not a verdict:

- Google's agentic-commerce org has **one other repo and it is active**:
  `a2a-x402`, pushed 2026-11-11. So the organisation is working; the AP2
  reference repository specifically is not where the work is landing.
- A protocol specification can legitimately freeze once published, the same
  argument this KB accepts for Kronos. The difference is that AP2 is sold as an
  implementable stack with SDKs, and SDKs rot.

**Practical reading for an engagement:** take the *mandate shape* from AP2 — an
intent mandate, a cart mandate and a payment mandate, each signed — because that
is the right model for "what did the human actually authorise", and it is
exactly the artefact MAS's SAFR and OSFI's 2026 bulletin ask you to produce.
Take the *running code* from x402 and `a2a-x402`.

### Hard exclusion, measured — a LICENSE file that is not a licence

| Asset | Repo | What the file contains | Verdict |
|---|---|---|---|
| Visa Trusted Agent Protocol | https://github.com/visa/trusted-agent-protocol | `LICENSE.md` is **398 bytes** and grants nothing: "By using, downloading, or installing this code, you agree to the terms and conditions contained in the Visa Developer Center Terms of Use (including the related Visa Trusted Agent Protocol Product Terms)." | **Not open source.** 223 stars, no push since 2025-10-28. Read the spec; do not vendor the code |

This is a **new failure shape for this KB** and the inverse of the
`virattt/dexter` case. There, a permissive grant existed in prose with no file.
Here a file exists, in the expected place, with the expected name — and it is a
click-through pointer to commercial terms. SPDX reports `NOASSERTION` for both.
A pipeline that treats "has a LICENSE file" as evidence passes this row.

### Licence note — grant by reference is a third evidence tier

`coinbase/agentkit` ships `LICENSE.md` at **571 bytes**: the Apache-2.0 title,
a copyright line, and the standard "Licensed under the Apache License,
Version 2.0 … You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0" paragraph. That is a real and
conventional Apache-2.0 grant — the full terms are incorporated by reference —
but GitHub's classifier needs the full text and so reports `NOASSERTION`.

For Globant this is **usable**, with one process consequence: a vendoring step
that copies `LICENSE*` into a client deliverable copies an incomplete file.
Attach the full Apache-2.0 text yourself. `mojaloop/*` (756 B) uses the same
pattern; see `verticals/solutions.md`.

## Back-office agent suites — new 2026-11-22

`intel/market.md` has said since 2026-11-09 that four of the top five
financial-services AI use cases are back-office, and that a back-office pitch is
pitching where the budget already is. The KB had **no back-office agent asset**
to point at. It does now, and the largest one is the fourth most-starred repo in
this entire knowledge base.

| Agent suite | Repo | License | Stars | Last push | What it is |
|---|---|---|---|---|---|
| Claude for Financial Services | https://github.com/anthropics/financial-services | Apache-2.0 | 41,441 | 2026-11-12 | Ten named workflow agents plus the skills and connectors under them. Back-office set: **GL Reconciler** (finds breaks, traces root cause, routes for sign-off), **Month-End Closer** (accruals, roll-forwards, variance commentary), **Statement Auditor**, **Valuation Reviewer**, **KYC Screener**. Front-office set: Pitch Agent, Model Builder (DCF/LBO/3-statement in Excel), Earnings Reviewer, Market Researcher, Meeting Prep. Apache-2.0 verified at 11,358 B |
| agent-safe-pipeline | https://github.com/decionis/agent-safe-pipeline | Apache-2.0 | 661 | 2026-11-21 | Gateway that puts an authorization decision in front of **every** action an agent takes. Created 2026-08-13 and pushed yesterday. This is the missing piece in every "keep the agent out of the write path" recommendation in this KB — the enforcement point, rather than the discipline |
| CloddsBot | https://github.com/alsk1992/CloddsBot | MIT | 3,123 | 2026-11-13 | Autonomous trading agent across prediction markets and 1,000+ venues. MIT verified at 1,065 B. Listed for completeness as a *front-office* counterweight; nothing in this KB is authorised to move money |

**What the first row is and is not.** It is a set of prompt-and-skill agent
definitions with connectors — not a platform, not a model, and not a ledger. Its
value to a studio engagement is that the workflow decomposition has already been
done by people who sell into these desks, and it is Apache-2.0, so the
decomposition can be lifted and re-implemented against a client's own stack and
its own model provider. Read it as a **requirements document that happens to
run**. The repository states its agents stage output for human sign-off and do
not execute transactions or post to a ledger — which is the same boundary
`verticals/solutions.md` recommends, arrived at independently.

## Back-office and message-layer agents — new 2026-11-22 (pass 4)

The tier above covers agents that *decide* (trade, advise, initiate). This tier
covers agents that **close the books and reconcile the file** — the work the
Cambridge CCAF 2026 survey puts at four of the top five AI use cases in
financial services, and the work this KB had no rows for.

Traction here is low and is stated per row, not hidden. That is the honest
shape of the category: the people who reconcile bank statements for a living do
not star GitHub repositories, which is the same measurement artefact the legal
KB recorded for billable-hours tooling. **Read these as reference designs and
starting points, not as dependencies to adopt on their star count.**

| Agent | Repo | License (bytes) | Stars | Last push | What it does |
|---|---|---|---|---|---|
| bankstatementparser-mcp | https://github.com/sebastienrousseau/bankstatementparser-mcp | Apache-2.0 (10,287) | 3 | 2026-11-18 | **The highest-leverage row in this table.** Exposes BAI2, MT940/MT942, camt.053, OFX and CSV parsing as an **MCP server**, so an agent reads a bank file as structured transactions instead of guessing at a PDF |
| agent-for-accounting | https://github.com/FoundrySoftHQ/agent-for-accounting | MIT (1,070) | 5 | 2026-08-05 | Reconciles a month of bank and ledger CSVs and **surfaces only the lines that need a decision**. The design is the point: the agent triages, the human decides, and the volume that needs no judgement never reaches a person |
| payment-reconciliation-agent | https://github.com/adithyaathreya2264/payment-reconciliation-agent | Apache-2.0 (11,357) | 7 | 2026-08-29 | **APAC-placed.** Reconciliation over Indian payment data — UPI, NEFT and payment-gateway settlements. The only region-anchored asset found on this plane outside NA, EMEA and LATAM |
| financial-inteligence-agent | https://github.com/leojg/financial-inteligence-agent | Apache-2.0 (11,357) | 19 | 2026-11-01 | LangGraph agent that ingests bank statements and answers questions over them. Useful mainly as a **worked LangGraph wiring** for statement data |
| motiva | https://github.com/apognu/motiva | MIT (1,073) | 16 | 2026-11-21 | Reimplementation of the **OpenSanctions scoring API**. Pushed yesterday. Pairs with `moov-io/watchman`: Watchman holds the lists, this scores the match |
| sieve-aml | https://github.com/AbgarSim/sieve-aml | MIT (1,071) | 16 | 2026-11-16 | Sanctions and AML screening over **35+ official lists** with a nightly-refreshed database and a dashboard |
| payee-match | https://github.com/softvasco/payee-match | MIT (1,068) | 0 | 2026-11-21 | **Verification of Payee** name matching for .NET against the EPC VOP scheme, with explainable and close-match outcomes. Zero stars, one day old, and it addresses an obligation that has been **in force in the euro area since 9 October 2025** |

### The benchmark row — the testability argument, again

| Asset | Repo | License (bytes) | Stars | Forks | Why it matters |
|---|---|---|---|---|---|
| Sanctions screening benchmark | https://github.com/Divine16/Sanctions-screening-benchmark | MIT (1,069) | 33 | 38 | Reproducible benchmark for sanctions **name-screening effectiveness**, measuring recall across documented transliteration and spelling cases |

Note the ratio: **33 stars and 38 forks.** More people cloned it than starred
it, which is the signature of a tool being *run* rather than bookmarked. This is
the third time this KB family has found that the honest-evaluation asset is the
one that converts a compliance conversation: `kingdee/lingee-bench` for business
value, `SantanderAI/gen-fraud-graph` for synthetic fraud topology, and now a
recall benchmark for name screening. **A screening engine with no recall
measurement is unsellable to a second-line risk function**, and the benchmark
costs nothing to adopt.

### What this tier does not include

No row here is an autonomous back-office agent that posts entries unsupervised,
because none was found that is permissive, maintained and honest about its
failure modes. `regulatory reporting automation bank` returns **`total_count:
3`**, all zero-star. **COREP, FINREP and XBRL regulatory reporting have no
permissive agentic tooling at all** — searched this pass, stated as a gap rather
than filled with a listicle result.

## What is deliberately NOT here

- **Generic agent frameworks** (LangChain, LangGraph, CrewAI, AutoGen, Pydantic AI).
  MIT and widely used in finance, but they carry no market data, no instrument
  model and no compliance surface. They belong in the technology KB; see
  `compose/patterns.md` for how to wire them underneath the agents above.
- **Unlicensed portfolio projects.** The AML/fraud search surfaced a cluster of
  agentic fraud-detection repos that are demos: `afkpiyush/offline-agentic-ai-fraud-detection`
  (0 stars, no LICENSE file), `Yunfan-Wang/Scalable-Agentic-Market-Simulator`
  (83 stars, no LICENSE file, control README 200 so the absence is measured).
  Both exist; neither is a starting point.
- **Model weights.** GLM 5.3 Flash (MIT) led open-weight models on Vals AI
  Finance Agent v2 at 57.9% as of 2026-09-23; Ant Group's Ling 3.0 Flash Fin is
  a finance-continued-pretrain. These are models, not agents, and finance use
  turns on data terms as well as weight license. Tracked in `intel/trends.md`.

## Caveats

- Star counts are popularity, not production-readiness. TradingAgents at 123,303
  is a research simulation framework, not a deployable trading system, and
  nothing here is authorised to move money.
- Published roundups are materially stale. Searches run today still return
  "over 80,000 stars" for TradingAgents against a measured 123,303, and quote
  ai-hedge-fund at 63,752 from a late-September snapshot against 64,780 today.
  Every figure in this file was measured, not quoted.

---
*Re-measured and extended 2026-11-22 (prior passes 2026-11-21, 2026-11-09).
This pass: 10 of 11 global rows re-measured for drift; a new **agentic payment
and commerce protocol** tier of 11 permissive rows added, which the KB's own
discovery metric could not see; a **back-office agent suite** tier added,
including the 41,441-star `anthropics/financial-services`; one hard exclusion
measured (`visa/trusted-agent-protocol` — a LICENSE file that grants nothing);
"grant by reference" separated out as a third licence-evidence tier; Dexter
downgraded from "chase the maintainer" to "read-only reference" on a measured
two-month silence.*

---

## The servicing plane — agents for after the payment clears (2026-11-22, pass 5)

The KB now has agents that **move** money (pass 3: agentic payment protocols)
and agents that **read the rail file** (pass 4: message-layer agents). It had
none for the plane where money is **disputed, reported and booked**.

Every row below is byte-verified MIT or Apache-2.0 and live. **Read the star
counts before the descriptions** — they are the finding.

| Agent | Repo | License | Stars | Last push | What it does |
|---|---|---|---|---|---|
| dispute-agent | https://github.com/opensyndicate/dispute-agent | MIT (1,076 B) | 1 | 2026-08-21 | Triages a payment dispute **by reason code** and assembles chargeback representment evidence |
| reg-e-timing | https://github.com/dleonard-data/reg-e-timing | MIT (1,071 B) | 1 | 2026-09-19 | **Regulation E §1005.11 dispute timing rules as testable code.** Institution-configurable. Provisional-credit and investigation clocks, deterministic |
| mcp-three-way-match | https://github.com/zovo-one/mcp-three-way-match | MIT (1,071 B) | 0 | 2026-10-26 | MCP server for supplier-invoice / PO / goods-receipt matching |
| reconcile-mcp | https://github.com/sebastienrousseau/reconcile-mcp | Apache-2.0 | 1 | 2026-11-18 | MCP server reconciling `camt.053` statements against expected `pain.001` payments. Same author as the `pain001` and `bankstatementparser` rows this KB already carries |
| edinet-mcp | https://github.com/ajtgjmdjp/edinet-mcp | Apache-2.0 | 20 | 2026-10-26 | Japanese EDINET XBRL filings behind an MCP server — a regulator's corpus already agent-addressable |

Five rows, five real repos, five verified licences. **Four of the five are
under two stars.** That is not a sampling accident and it is the most useful
thing in this file.

### The law this KB can now state with numbers: supply follows the file format

Twenty-one GitHub searches this pass, split by whether the work has a
**byte-level specification** or is a **judgement**. The column that matters is
not the result count — it is what the *top* repository looks like.

**Work defined by a file format — mature, permissive, maintained:**

| Query | Results | Top repo | Stars | Licence | Last push |
|---|---|---|---|---|---|
| `double-entry ledger accounting` | 809 | `ledger/ledger` | 6,078 | BSD-3-Clause | 2026-11-21 |
| `Peppol invoice` | 316 | `josemmo/einvoicing` | 180 | MIT | 2026-11-07 |
| `XBRL filing` | 262 | `manusimidt/py-xbrl` | 154 | GPL-3.0 | 2026-11-09 |
| `ISO 8583 message` | 245 | `moov-io/iso8583` | 539 | Apache-2.0 | 2026-11-22 |
| `MT940 parser` | 74 | `wolph/mt940` | 106 | BSD-3-Clause | 2026-11-16 |
| `Metro 2 credit reporting` | 10 | `moov-io/metro2` | 130 | Apache-2.0 | 2026-11-22 |

**Work defined by a judgement — nothing above a hobby project:**

| Query | Results | Top repo | Stars | Licence | Note |
|---|---|---|---|---|---|
| `cash flow forecasting treasury` | 47 | `DaveVoyles/Cash-forecasting` | 7 | none | — |
| `bank reconciliation agent LLM` | 36 | `adithyaathreya2264/payment-reconciliation-agent` | 7 | Apache-2.0 | already in this KB |
| `IFRS 9 impairment` | 16 | `naenumtou/ifrs9` | 135 | **none** | no licence file |
| `CECL expected credit loss` | 15 | `rkhuran/CECL-Modelling-Implementation` | 14 | **none** | last push 2019 |
| `accounts payable invoice extraction agent` | 13 | `tahasiddiquii/invoice-ap-agent` | 5 | MIT | — |
| `three-way match invoice purchase order` | 12 | `aditya-technophile-06/three-way-match-engine` | 1 | **none** | — |
| `chargeback representment evidence` | 10 | `opensyndicate/dispute-agent` | 1 | MIT | best in category |
| `loan servicing amortization schedule` | 9 | `HimathKc/Loan-Repayment-Calculator` | 1 | **none** | — |
| `dunning collections invoice` | 8 | `itsroshanharry/AR-Collections-agent` | 1 | **none** | — |
| `Regulation E dispute` | 6 | `dleonard-data/reg-e-timing` | 1 | MIT | best in category |
| `chart of accounts agent LLM posting` | **0** | — | — | — | — |

`Metro 2` returns ten results and has a 130-star Apache-2.0 library.
`cash flow forecasting treasury` returns forty-seven and has nothing above
seven stars. **Result count predicts nothing; the existence of a specification
predicts everything.**

The mechanism is plain once stated. A file format is an *obligation shared by
every institution in a jurisdiction*: the format is published, conformance is
binary, and one correct implementation serves everyone — so it gets written
once and starred. A judgement — which invoices to chase first, whether this
chargeback is worth representing, what the cash position will be in 30 days —
is **specific to one institution's data, policy and risk appetite**, cannot be
validated against a published spec, and has no shared artefact to converge on.
Nobody open-sources it because there is nothing general to open-source.

### What this means for an engagement, and it is the build-vs-buy line

**Adopt the parser. Build the decision.**

- Everything with a format — ACH, ISO 8583, ISO 20022, Metro 2, BAI2, X12,
  EN 16931, iXBRL, SAF-T, CPA-005 — is **solved, permissive and free**.
  Writing one of these is rework, and reviewers will find the library you
  should have used.
- Everything that is a judgement is **greenfield**, and it is where the
  client's margin is. There is no incumbent open-source answer to displace and
  no community to keep pace with.

This also sets the honest expectation for the five agent rows above. They are
not platforms. They are **design references and prototyping seeds**: read
`reg-e-timing` for how a regulatory clock is expressed as testable code, read
`dispute-agent` for a reason-code taxonomy, then build on the client's data.
The rule this KB applied to `virattt/dexter` applies here with more force —
**prototype yes, vendor into a client deliverable no.** `moov-io/metro2` at
130 stars under an Apache-2.0 grant from an organisation maintaining 60 repos
is a different proposition from a one-star personal project, and the KB should
not flatten the two into one table row.

### Counter-check: is this just "the back office is early"?

No, and the test is in the same data. `moov-io/ach-test-harness` (17 stars) and
`moov-io/bai2` (27) are deeply back-office, barely starred, and both are
production-grade, validated and maintained — because both have specifications.
Meanwhile `IFRS 9 impairment` returns a **135-star** top repo that ships **no
licence file at all**: plenty of attention, no convergence, nothing adoptable.
Maturity in this plane tracks the specification, not the attention.

---

## Pass 6 (2026-11-25) — the capital-markets plane, and the licence class nobody checked

Pass 5 left this KB with a law: *open-source supply follows the file format,
not the decision.* This pass tested it on the one plane the KB had never
touched — **securities and derivatives** — and the law survived but needed a
second clause, because half the formats in this plane are specified to the
byte and have **nothing** behind them.

### Verification method, pass 6 — two corrections to the gate in §"Verification method"

**Correction 1 — read the licence name from the TITLE LINE, not from the body.**
This KB ships Pattern 9 (the licence hygiene gate) as an executable check in
eight industry KBs. Pass 5 corrected it from byte-bands to line-counts. This
pass found a defect in the line-count version too, **in our own probe, against
a real repo**: `danielep71/K-CVA` was labelled **AGPL** when it is
**MPL-2.0**. Cause: MPL-2.0's *Exhibit B* names "the GNU General Public
License, the GNU Lesser General Public License, or the GNU Affero General
Public License" as secondary-licence options, so a body-wide grep for
`GNU AFFERO` matches the text of a weak-copyleft licence. Any licence with a
compatibility exhibit will trip the same wire.

The fix is one line: **take the licence name from the first non-blank line and
use body markers only to confirm it.** MPL-2.0's first line is
`Mozilla Public License Version 2.0`; it is never ambiguous.

**Correction 2 — the line table, extended by five entries measured this pass.**

| Licence | Lines | Title-line marker |
|---|---|---|
| MIT | 19–23 | `MIT License` / `The MIT License (MIT)` |
| BSD-3-Clause | ~28 | `Redistribution and use in source and binary forms` |
| QuickFIX Software License 1.0 | 45 | `The QuickFIX Software License, Version 1.0` |
| Community Specification License 1.0 | 99 | `# Community Specification License 1.0` |
| Apache-2.0 without appendix | 176 | `Apache License` |
| LGPL-3.0 | 187 | `GNU LESSER GENERAL PUBLIC LICENSE` |
| Apache-2.0 with appendix | 201–202 | `Apache License` + `APPENDIX: How to apply` |
| MPL-2.0 | 373 | `Mozilla Public License Version 2.0` |
| CC-BY-4.0 | 395 | `Attribution 4.0 International` |
| LGPL-2.1 (as `.md`) | 503 | `GNU LESSER GENERAL PUBLIC LICENSE Version 2.1` |
| AGPL-3.0 | ~661 | `GNU AFFERO GENERAL PUBLIC LICENSE` |
| GPL-3.0 | ~674 | `GNU GENERAL PUBLIC LICENSE` |

Byte counts for Apache-2.0-with-appendix ranged **10,922–11,357 B** across the
nine repos measured this pass (435 B spread) while the line count held at
201–202. Pass 5's correction replicates.

**Correction 3 — the false-abundance trap, the mirror of the zero trap.**
This KB has measured the zero trap three times (a `total_count` of 0 or 1 means
a bad query far more often than an empty category). Pass 6 measured its
opposite, and it is **more** dangerous because it looks like evidence:

| Query | `total_count` | What the top results actually were |
|---|---|---|
| `CAT reporter FINRA` | 0 | nothing — genuine zero |
| `Form PF` | 358 | a Mario Party 6 port, a userscript launcher, VPN spam |
| `N-PORT filing` | 156 | Nintendo Switch game ports, a PE-format C++ wrapper |
| `securities lending` | 243 | DeFi smart wallets and crypto token contracts |

`Form PF` and `N-PORT` are SEC filings specified to the field. They return
**more** results than `moov-io/metro2`'s query did — and not one result on the
first page is a financial filing library. Acronyms that collide with general
computing vocabulary (`PF`, `PORT`, `CAT`, `FIX`) manufacture abundance.

**A high `total_count` is no more evidence of a populated category than a zero
is of an empty one.** Both traps have the same remedy and this KB already
wrote it: requery as `{agency-or-standard-name} + {artefact noun}`, then
**read the descriptions**. Never count.

### The second clause: open source follows the file that MORE THAN ONE PARTY MUST READ

Every format below is published, versioned and specified to the field. The
difference in supply is not a difference in specification quality.

| Format | Direction | Best permissive implementation | Stars |
|---|---|---|---|
| FIX protocol | counterparty ↔ counterparty | `quickfix-j/quickfixj` + `da4089/simplefix` | 1,161 / 255 |
| SWIFT MT (FIN) | bank ↔ bank | `prowide/prowide-core` (Apache-2.0) | 296 |
| ISO 20022 | bank ↔ bank | `prowide/prowide-iso20022` (Apache-2.0) | 240 |
| Metro 2 | lender → 4 bureaus, bureaus → lender | `moov-io/metro2` (Apache-2.0) | 130 |
| ISDA CDM | trade model, shared across firms | `finos/common-domain-model` + `finos/rune-dsl` | 297 / 50 |
| MiFIR RTS 22 | firm → one regulator (via an ARM) | **none** — 2 results, both unlicensed | 0 |
| EMIR REFIT | firm → one trade repository | **none** — 6 results, best 1 star | 1 |
| CAT (NA) | firm → one processor | **none** — 0 results | — |
| Form PF / N-PORT | fund → SEC, not republished | **none** — queries return game ports | — |

The split is clean and it is not about the spec. It is about **who else has to
read the file.**

- A **many-to-many** format is read by everyone who writes it. Reading another
  firm's message is how you find your own encoder's bugs, so a shared
  implementation has shared value, and one gets written and starred.
- A **one-way regulatory submission** is read by exactly one party, which does
  not publish its reader. The submitter gains nothing from a shared
  implementation, cannot test against a second one, and in MiFIR/EMIR usually
  cannot submit directly anyway — a licensed ARM or trade repository stands in
  between and sells that layer.

**Second clause, and it is the one that predicts:** where the regulator
*publishes what it collects*, a reader ecosystem appears even though the
submission is one-way — SEC EDGAR, Companies House (`kanedata/ixbrl-parse`,
72★), EDINET (`matthelmer/edinet-tools`, 59★). Where the regulator keeps the
data, nothing appears: MiFIR, EMIR, CAT, Form PF. **The published corpus, not
the published schema, is what creates the open-source population.**

This subsumes pass 5's law rather than replacing it. A judgement produces no
file at all, so nobody reads it, so there is nothing to share — the same
mechanism at the limit.

**Commercial consequence, and it inverts pass 5's advice for this one plane.**
Pass 5 said *adopt the parser, build the decision*. In capital-markets
regulatory reporting there is no parser to adopt and there never will be: the
client's ARM or trade repository owns that layer and is paid for it. The
engagement is therefore **on both sides of the vendor**: reconcile what you are
about to send against your own books *before* submission, and reconcile the
acknowledgements and rejections back against the trade store *after*. That is
judgement work with a deterministic oracle, it does not compete with the ARM,
and it is where the client's reportable-accuracy exposure actually sits.

### Agents and agentic assets added this pass — 7 rows, all verified

Existence confirmed by `git ls-remote` (54/54 resolved), licence read by line
count and title line, metadata from `search/repositories?q=repo:<slug>` on
2026-11-25.

| Agent / asset | Repo | Licence | Stars | Pushed | What it does |
|---|---|---|---|---|---|
| FINOS AI Governance Framework MCP server | https://github.com/finos/aigf-mcp-server | Apache-2.0 | 10 | 2026-11-09 | Serves the FINOS AI governance framework (risks + mitigations) to an agent over MCP — the governance text becomes a queryable tool instead of a PDF |
| CDM Object Builder | https://github.com/finos/cdm-object-builder | Apache-2.0 | 13 | 2026-11-23 | Builds and validates ISDA CDM trade objects; the executable counterpart to the spec repo |
| motiva | https://github.com/apognu/motiva | MIT | 16 | 2026-11-23 | Reimplementation of the OpenSanctions scoring/matching API — a second implementation of the same matching contract |
| sieve-aml | https://github.com/AbgarSim/sieve-aml | MIT | 16 | 2026-11-16 | Sanctions/AML screening over 35+ official lists with a nightly-refreshed database and dashboard |
| gleif-mcp-server | https://github.com/olgasafonova/gleif-mcp-server | MIT | 8 | 2026-11-20 | Exposes the GLEIF LEI register to an agent over MCP — counterparty identity as a tool call |
| risk-calculation-mcp | https://github.com/mselcukozturk/risk-calculation-mcp | MIT | 0 | 2026-11-23 | Local MCP server for IRB and standardised risk weights, RWA and capital ratios |
| Sanctions screening benchmark | https://github.com/Divine16/Sanctions-screening-benchmark | MIT | 33 | 2026-08-13 | Reproducible recall benchmark for name-screening effectiveness — an evaluation harness, not a screener |

Four of these seven are **MCP servers wrapping a register, a rulebook or a
calculation**, published in the last three weeks. That is a shift in shape
worth naming: the previous passes found agents that *did* financial work, these
wrap a **source of truth** so an agent can cite it. It is the same move the
legal KB recorded when a regulator's corpus arrived pre-exposed over MCP, and
it is the right shape — the model asks, the register answers, the answer has a
provenance.

Maturity caveat, unchanged and applied: `risk-calculation-mcp` at 0 stars and
`gleif-mcp-server` at 8 are **prototyping seeds and design references, not
dependencies**. `motiva` and `sieve-aml` at 16 each are interesting for a
different reason — see Pattern 20 in `compose/patterns.md`: two independent
implementations of the same screening contract is a differential oracle.

### The licence class nobody in this KB had checked: spec ≠ code ≠ data

Three artefact types, three licence regimes, **one organisation**, and GitHub's
badge is wrong or absent on all but one of them.

| Artefact | Example | Licence | Lines | What it actually grants |
|---|---|---|---|---|
| Specification | https://github.com/finos/common-domain-model | Community Specification License 1.0 | 99 | Rights over the **document** + a patent commitment for implementers. **Not** a software licence. GitHub reports NOASSERTION |
| Specification | https://github.com/finos/FDC3 | Community Specification License 1.0 | 99 | Same — the standard, not an implementation |
| Implementation | https://github.com/finos/rune-dsl | Apache-2.0 | 201 | Ordinary permissive software rights — the DSL and code generators that compile the CDM |
| Implementation | https://github.com/finos/FDC3-Sail | Apache-2.0 | 201 | Ordinary permissive software rights — a working FDC3 desktop agent |
| Document | https://github.com/finos/ai-governance-framework | CC-BY-4.0 | 395 | Rights over prose. Not a software licence (the legal KB's "CC is not a software licence", again) |
| Data | https://github.com/opensanctions/opensanctions | **code MIT, data CC BY-NC 4.0** | 23 (code) | See below — this is the expensive one |

**`finos/common-domain-model` has 297 stars and 142 forks and is not software
you can take.** Adding it as a dependency takes on a *specification* licence.
The code you want is `finos/rune-dsl`, `finos/rune-common` and
`finos/cdm-object-builder`, all Apache-2.0. Same for FDC3: the standard is
CSL-1.0, the implementations (`FDC3-Sail`, `fdc3-dotnet`, `backplane`) are
Apache-2.0. **In FINOS the standard and its implementation are different repos
with different licences, and the one with the stars is the standard.**

**The data trap, and it is the single most expensive mistake available in this
plane.** The OpenSanctions stack is 1,543 stars of genuinely MIT code —
`opensanctions` (884), `nomenklatura` (274), `yente` (189), `followthemoney`
(122), `rigour` (74). Its own README states the split:

> "The code within this repository is licensed under the MIT License. Data
> files produced by OpenSanctions are licensed under CC BY-NC 4.0, and some
> files under `datasets/` are unmodified copies of third-party material that we
> cannot license at all."

`yente`'s README is equally explicit: using it commercially "may require a data
licence for OpenSanctions data". **NC means non-commercial, and screening a
client's customers is commercial by definition.** The MIT badge covers the
loader, not the load.

Generalised rule for the twelve KBs: **read the licence of the data separately
from the licence of the code, and never infer either from the other.** An
OSI badge on a data repository describes the software that moves the data.
A screening or reference-data engagement must price the data licence as a
line item from day one, not discover it at go-live.

Verification gap, declared: `opensanctions.org/licensing` **does not resolve in
this session** — the host is outside the session's allowed network domains, so
the commercial tiers could not be read. The licence split above comes from the
repository's own `README.md` and `yente`'s, which state it unambiguously; the
*price* of the commercial data licence is not in this KB.

## Pass 7 (2026-11-25) — the insurance plane, and the clause that closes it: *membership*

Pass 6 established that open source follows **the file that more than one party
must read**, and that one-way submissions to a regulator who publishes no
reader stay empty. This pass took the one plane this KB had never opened —
**insurance** — and found a case that satisfies pass 6's condition and *still*
produces nothing. The reason is new, and it is the finding of this pass.

### The census that opened the plane

A vocabulary census of all eight files before any research: **ACORD 0,
IFRS 17 0, Solvency II 0, reinsurance 0, takaful 0, EIOPA 0, IAIS 0, IRDAI 0,
NAIC 1, actuarial 1**. The word "insurance" appeared 11 times, all incidental.
A whole regulated sub-industry — larger by premium than several planes this KB
covers in depth — was absent.

### The third clause: the spec must be readable without paying to join

ACORD is the insurance industry's interchange standard. It is read by carrier,
agent, broker and reinsurer — **more than one party must read the file**, so
pass 6's rule predicts a mature permissive library. There is none.

| Measurement | Result |
|---|---|
| `ACORD in:name,description`, sorted by stars | 37 results; best relevant hit **8 stars**, no licence file, last push 2017 |
| Top 4 results by stars | All `acordeon-*` — Spanish for *cheat sheet*. A pure vocabulary collision |
| `AL3 insurance` (the flat-file format) | **0 results** |

The mechanism is not technical. ACORD's own published terms gate the standards
behind membership and paid programmes: access to Standards requires joining the
relevant membership or participation programme and then creating an acord.org
account; Forms are licensed separately; the EHR Digital Standards Programme is
priced at **$5,000 per year** for eligible participants; and ACORD's terms note
that not all programmes grant access to all standards, some at additional
charge. The terms document in evidence is dated **2025-10-27**.

> **THIRD CLAUSE, added to pass 6's law: open source follows the file that more
> than one party must read *and whose specification can be read without paying
> to join*.** Where the spec is member-gated, the multi-party condition is
> satisfied and the population still does not form — because the person who
> would write the library may not lawfully read the spec. FIX, ISO 20022,
> EN 16931, UBL and Metro 2 are published at no cost and all have mature
> permissive implementations in this KB. ACORD is not, and has none.

This is falsifiable and it is the cleanest test the KB has run: the two cases
differ in *one* variable — the price of reading the spec — and the outcomes are
opposite.

### The second measurement: the permissive insurance core existed, and it died

Pass 6 wrote, in `verticals/solutions.md`, "there is no permissive insurance
equivalent of Fineract" and "for a P&C or life insurer engagement there is no
open starting point". **The conclusion holds. The reason given was wrong, and
the true reason is more useful.**

| Repo | Licence (read) | Stars / forks | Last push |
|---|---|---|---|
| https://github.com/aposin/openinsuranceplatform | Apache-2.0 (202 lines, 11,474 B) | 93 / 34 | **2019-11-27** |
| https://github.com/aposin/CalculusPrime-PnC | Apache-2.0 (202 lines, 11,677 B) | 6 / — | **2019-11-28** |

`aposin` is the Open Source Insurance Alliance — an industry consortium, not a
hobbyist. It shipped a **fully permissive core insurance platform** covering,
in its own description, "the complete scope of business capabilities for the
insurance industry across all lines of business and business models (B2C, B2B,
B2B2C)", plus a separate **P&C rating engine**. Both are Apache-2.0. Both have
been dead for seven years. Five of the org's eight repos carry `ARCHIVED:` as
the first word of their own description.

> **So the insurance core is not an untried idea. It is a consortium attempt
> that was made, licensed permissively, and abandoned.** That is a far stronger
> thing to tell a client than "nothing exists": the risk being priced is not
> novelty, it is a known failure mode. And it pairs with the ACORD finding —
> the industry's shared code attempt died, and its shared *format* is behind a
> membership fee. **The insurance plane is closed by governance, not by absence
> of effort.**

### The third measurement: where the artefact is a *method*, the plane is alive

The same census that found ACORD empty found a mature, institutional,
actively-maintained body of insurance open source. It was invisible to pass 6
because of how it is **named**.

Pass 6's probe was "insurance core platforms (policy, claims, underwriting,
actuarial) sorted by stars" — a multi-word query, which rule **G-L19** already
records as an AND that returns nothing, and which contains the word
*insurance*. The Casualty Actuarial Society's repositories are named
`chainladder-python`, `reinspy`, `tryangle`, `FASLR`, `PCDM`. The life side is
`lifelib`, `pyliferisk`, `MortalityTables.jl`. **Not one contains the word
"insurance".**

> **RULE, and it is the fifth time this KB has relearned it in a new costume:
> a professional body names its code after the METHOD, never after the
> INDUSTRY.** Pass 5 found libraries named after the *agency* (`fincen`); this
> pass finds them named after the *technique* (`chainladder`). Query the
> actuarial vocabulary — reserving triangle, chain ladder, mortality table,
> life contingency, economic scenario generator — not the sector noun.

### Agentic assets added this pass — 8 rows, all verified by `ls-remote` and licence read

| Agent / asset | Repo | Licence (read) | Stars | Last push | What it is, and how far to trust it |
|---|---|---|---|---|---|
| credibility-gated underwriting XAI | https://github.com/ftsboy1/credibility-gated-underwriting-xai | MIT (20 lines, 1,055 B) | 106 | 2026-07-28 | Underwriting explainability gated on **actuarial credibility** — the discipline's own answer to thin data. Highest-starred permissive agentic underwriting asset found |
| actuarial-skills | https://github.com/kalta-ai/actuarial-skills | MIT (20 lines, 1,064 B) | 17 | 2026-03-18 | Agent skills for **P&C actuaries**. The only asset found that packages actuarial workflow as skills rather than as a library |
| agentic claims adjudication | https://github.com/anandapurva55/agentic-claims-adjudication-aws | MIT (20 lines, 1,068 B) | 23 | 2026-11-23 | Multi-agent **motor claims adjudication**, full stack. Pushed two days before this pass |
| labor-law-mcp | https://github.com/kentaroajisaka/labor-law-mcp | MIT (20 lines, 1,071 B) | 67 | 2026-09-14 | MCP server over **Japanese labour and social-insurance law**. APAC-placed; the regulator's corpus as configuration, not construction |
| turkactuary-mcp | https://github.com/afsharid/turkactuary-mcp | Apache-2.0 (201 lines, 11,357 B) | 3 | 2026-11-20 | MCP over **Türkiye insurance regulation** plus actuarial calculation. The only Turkey-placed insurance asset in this KB |
| ClaimsProcessingAssistant-MCP | https://github.com/chbhargavareddy/ClaimsProcessingAssistant-MCP | MIT (20 lines, 1,071 B) | 5 | 2026-08-22 | Claims processing exposed over MCP. Prototype seed |
| niche underwriting automation skill | https://github.com/dungnotnull/niche-insurance-underwriting-automation-agent-skill | MIT (20 lines, 1,067 B) | 5 | 2026-07-01 | Agent skill for specialty-lines underwriting |
| openIMIS claim AI (research) | https://github.com/openimis/openimis-research-claim_ai_py | **AGPL-3.0** (660 lines, 34,522 B) | 2 | 2025-10-27 | Claim-AI research module inside openIMIS. Copyleft — **design reference only**, and it inherits the Swiss-law rider documented in `verticals/solutions.md` |

**Star counts, read honestly.** Six of eight are under 25 stars; four are under
6. By the rule pass 5 established for `virattt/dexter`, these are **design
references and prototype seeds, not dependencies** — with one qualification
this pass adds: the *underwriting* assets are weaker evidence than pass 5's
servicing assets, because underwriting has no shared file to validate against.
There is no `ach-test-harness` equivalent here. Nothing in this table can be
checked for correctness by anyone outside the carrier that wrote it.

### Licence correction — two extensions to pass 6's line table, and a new NOASSERTION cause

Pass 6's **Correction 1** (read the licence name from the *title line*, never
from body markers, because MPL-2.0 §1.12 defines "Secondary License" by naming
the GNU GPL, LGPL **and AGPL**) was independently reproduced this pass: a
body-marker probe written in precedence order reported nine `casact`
repositories as **AGPL-3.0** when every one of them is **MPL-2.0**. The
correction is confirmed and should be treated as settled.

**Extension 1 — MPL-2.0 is the most stable licence file this KB has measured.**

| Reading | Lines | Bytes |
|---|---|---|
| `casact/chainladder-python`, `PCDM`, `reinspy`, `tryangle`, `rp-bnn-claims`, `imaginator`, `double_lift`, `risky-router`, `covid_19_data` | 373 | **16,724** |

**Nine readings, byte-identical.** Zero dispersion. Compare pass 5's measured
dispersion: MIT 11 B over 3 readings, Apache-2.0 **1,198 B (11.7%) over 4**.

**Extension 2, and it limits Extension 1 — the line count is stable per
*rendering*, not per licence.** `casact/raw_package` is also MPL-2.0 and
measures **150 lines / 14,847 B**: a reflowed copy whose first line reads
`Mozilla Public License` without the version. Same licence, 223 fewer lines.
This is the exact failure mode pass 5 found for Apache-2.0 (`fincen` 201 lines
vs `edinet-mcp` 176) now reproduced for MPL-2.0 — **so the title line is the
authority and the line count only corroborates it.** A count that misses the
table is a prompt to read the file, never grounds to downgrade an asset.

**Line-table additions measured this pass:**

| Licence | Lines | Bytes | Title-line marker |
|---|---|---|---|
| CC0-1.0 | 120 | 7,047 | `Creative Commons Legal Code` |
| MPL-2.0 (canonical) | 373 | 16,724 | `Mozilla Public License Version 2.0` |
| MPL-2.0 (reflowed) | 150 | 14,847 | `Mozilla Public License` |
| Apache-2.0 with appendix | 200–202 | 11,341–11,677 | `Apache License` + `APPENDIX: How to apply` |
| GPL-3.0 | 673 | 35,130 | `GNU GENERAL PUBLIC LICENSE` |
| AGPL-3.0 | 660 | 34,522 | `GNU AFFERO GENERAL PUBLIC LICENSE` |

**New NOASSERTION cause — the sixth, and the simplest yet: the licence file's
first line is the PROJECT NAME.**

`JuliaActuary/MortalityTables.jl` and `JuliaActuary/LifeContingencies.jl` both
report `NOASSERTION` on the API. Both files are 26 lines and open:

```
MortalityTables.jl
====================

Copyright (c) 2018-2020 Alec Loudenback

Permission is hereby granted, free of charge, to any person obtaining a copy
```

That is **MIT in substance**, with a two-line project header above it.
Pass 5's cause was the `.md` file extension (`ledger/ledger`). This one is a
title line that is not a licence name at all. **So the probe needs a fallback:
if the title line is not a recognised licence name, grep the body for the grant
clause — and only then report the licence as undetermined.** Both repos are
fully permissive and usable; 81 stars between them would have been discarded.

**Badge without a file — two cases, recorded as undetermined, not as absent:**

| Repo | API says | Measured |
|---|---|---|
| https://github.com/Systemorph/IFRS17CalculationEngine | MIT | `LICENSE` and `LICENSE.md` both **404 on `main` and `master`**. Four branches exist; `main` resolves. The top-starred IFRS 17 asset has **no readable licence file** |
| https://github.com/lifelib-dev/lifelib-products | none | No licence file, while `lifelib` itself is MIT. **Licence varies per repo inside one org** — never infer an org-wide licence |

## Pass 8 (2026-11-25) — the statistical plane: the data an agent must *cite*, and the central bank that shipped an agent

Passes 5–7 established this KB's law in three clauses: open-source supply
follows **the file format**, specifically the file that **more than one party
must read**, and only where **the spec is readable without paying to join**.
Every plane measured so far was an *outbound* one — the institution computes
something and files it (Metro 2, FinCEN SAR, iXBRL, EDINET, EN 16931, Solvency
II). Pass 8 measures the **inbound** plane for the first time: the
authoritative reference and macroeconomic data an institution *reads* in, and
the published format it arrives in — **SDMX, ISO 17369**.

This plane was at **zero** in this KB. Not thin: absent. `grep -ri sdmx` over
all eight files before this pass returned nothing.

### Why it was at zero, and it is not because it is empty

`sdmx` as a single term returns **494 repositories**, with institutional owners
and today's commits. The plane was missing because of **vocabulary collision,
in its sharpest form yet measured**: the acronyms of the world's principal
statistical publishers are all software words.

| Query | Top results actually returned | What was wanted |
|---|---|---|
| `ecb` | `ECBSR` (super-resolution, 391★), `cppDES` (DES/3DES **ECB cipher mode**, 117★) | European Central Bank |
| `abs` | `abseil-cpp` (18,212★), `abstreet` | Australian Bureau of Statistics |
| `imf` | `MeanFlow`/`iMF` (1,220★), `ImFileDialog`, Netflix `photon` (**Interoperable Master Format**) | International Monetary Fund |
| `istat` | `iStats` Ruby gem for **mac CPU stats** (2,456★), `istatd` | Istituto Nazionale di Statistica |

**Four of the five institutions that publish the macro data every credit and
treasury model consumes are unreachable by their own names.** This is the
`fincen` finding of pass 5 inverted: there, the library was named after the
agency and the consultant's phrase missed it; here, the agency's name is taken
by unrelated software. Both failures are the same root cause — **the query
vocabulary is not the artefact vocabulary** — and both are only fixed by
censusing the **format** (`sdmx`) and the **owner** (`org:bis-med-it`), never
the institution's initials.

### The headline: a central bank published an agentic AI framework, Apache-2.0

`bis-med-it/marco-BIS` — **MaRCo@BIS, the MAcroeconometric Research
Companion** — is an **agentic-AI skill framework released by the Bank for
International Settlements** as a public good alongside BIS Working Paper no
1395 (Lombardi, Park and Perez-Cruz, 2026). Apache-2.0, 89★, pushed
2026-11-12.

Read its own description of its shape, because it is the architecture this KB
has been arguing for across seven passes, published by the central banks' own
bank:

- A **7-stage workflow with human-in-the-loop confirmation at every important
  decision** — model selection, variables, lags, identification, sample,
  sensibility checks, reporting.
- **Each choice states its source** (the user, a dictionary entry, the
  knowledge base, or the literature). Provenance is structural, not a prompt
  instruction.
- The agent is instructed to **flag anomalies before they reach final
  results** — price puzzle, explosive root, weak instrument. Named failure
  modes, checked deterministically.
- Three parts: **skills as plain Markdown**, a **reference Python library
  covered by more than 1,000 tests**, and a **dictionary of canonical paper
  specifications paired with worked replications**.
- Verification is a command: `pytest tests/test_replications_smoke.py
  --runslow` runs **every replication against its paper targets**.

**Why this matters commercially, stated plainly.** This KB has repeatedly had
to argue that the deterministic layer must sit outside the model and that the
agent must cite. For any central-bank, supervisor or treasury engagement, that
argument no longer has to be made from first principles — **the BIS has
published a reference implementation of it, permissively licensed, with a
regression suite**. It is the strongest single citation in this KB for the
"model proposes, code decides, every figure cites" architecture.

Two cautions that must travel with it: the data CSVs are **not distributed**
(FRED panels are downloaded by the user, and the raw download needs metadata
rows stripped before the loader reads it), and the authors state it is **not
tested on macOS**.

### Agentic assets added this pass — 13 rows, all verified by `ls-remote` and licence read

The second finding of this pass is that **this plane grew an MCP layer in the
last ninety days.** Nine of the thirteen rows below were pushed within the last
month; the oldest non-trivial one dates from March 2026. This is the newest
agent surface in this KB.

| Agent / asset | Repo | Licence (verified) | ★ | Last push | Region | What it does |
|---|---|---|---|---|---|---|
| MaRCo@BIS | https://github.com/bis-med-it/marco-BIS | Apache-2.0 (175 lines) | 89 | 2026-11-12 | Global | BIS agentic macroeconometric research companion; skills + 1,000-test library + replication dictionary |
| `us-gov-open-data-mcp` | https://github.com/lzinga/us-gov-open-data-mcp | MIT (20 lines) | 113 | 2026-11-02 | North America | MCP server + TS SDK over 40+ US government data APIs |
| `istat_mcp_server` | https://github.com/ondata/istat_mcp_server | MIT (20 lines) | 24 | 2026-11-22 | EMEA | Italian official statistics (ISTAT) over the SDMX API |
| `tuik-mcp` | https://github.com/orhoncan/tuik-mcp | **No licence file** (12 names × 3 refs) | 16 | 2026-09-20 | EMEA | Turkish statistical institute (TÜİK) SDMX REST — **do not depend on it** |
| `mcp-statcan` | https://github.com/Aryan-Jhaveri/mcp-statcan | MIT (20 lines) | 8 | 2026-11-06 | North America | Statistics Canada, 7,000+ Canadian series |
| `oecd-mcp-server` | https://github.com/cyanheads/oecd-mcp-server | Apache-2.0 (200 lines) | 5 | 2026-11-16 | Global | 1,500+ OECD statistical datasets |
| `imf-mcp-server` | https://github.com/cyanheads/imf-mcp-server | Apache-2.0 (200 lines) | 4 | 2026-11-13 | Global | IMF **SDMX 3.0** macro dataflows |
| `ecb-mcp` | https://github.com/scka-de/ecb-mcp | MIT (20 lines) | 4 | 2026-03-31 | EMEA | ECB data: FX rates, interest rates |
| `open-economics` | https://github.com/felipegambettadesouza6-jpg/open-economics | MIT (20 lines) | 2 | 2026-09-12 | LATAM | No-auth API + MCP server for official **Brazilian** economic data |
| `gingado` | https://github.com/bis-med-it/gingado | Apache-2.0 (200 lines) | 41 | 2026-11-19 | Global | BIS machine-learning library for economics and finance |
| `fred-mcp-server` | https://github.com/stefanoamorelli/fred-mcp-server | **AGPL-3.0** (660 lines) | 135 | 2026-08-22 | North America | FRED (Federal Reserve Economic Data) — copyleft, see below |
| `openecon-data` | https://github.com/hanlulong/openecon-data | **AGPL-3.0** (660 lines) | 95 | 2026-11-21 | Global | 330K indicators (FRED, World Bank) packaged for agents — copyleft |
| `Equibles` | https://github.com/daniel3303/Equibles | **AGPL-3.0** (660 lines) | 248 | 2026-11-25 | Global | Self-hosted financial-data MCP server — copyleft |

One more, recorded for completeness and **not** recommended: `ValueCell-ai/valuecell`
(https://github.com/ValueCell-ai/valuecell, Apache-2.0, 200 lines, **11,068★**)
is a community multi-agent platform for financial applications whose last push
was **2026-03-09** — over eight months stale at a five-figure star count. It is
this KB's §9 counter-trend (archived and stalled projects still topping the
charts) in its purest form, and the reason every row in this table carries a
`Last push` column.

### The licence pattern on the MCP layer, and it has a commercial reading

Sorted by what the server wraps:

- **Single-institution servers are permissive.** ISTAT (MIT), ECB (MIT),
  StatCan (MIT), Brazil (MIT), OECD (Apache-2.0), IMF (Apache-2.0),
  US gov (MIT) — **seven of eight**, the exception being TÜİK, which has no
  licence file at all.
- **Multi-source aggregators are AGPL-3.0.** `Equibles` (248★),
  `openecon-data` (95★) — where the *aggregation across publishers* is the
  product, the licence protects it.
- **The honest counterexample:** `fred-mcp-server` (135★) wraps a *single*
  source and is still AGPL-3.0. So the pattern is a tendency with a named
  exception, not a rule — stated that way deliberately.

**What to do with it:** a per-institution server is a safe dependency for a
client deliverable; an aggregator is not, and the aggregation it performs is
precisely the part that is cheap to rebuild over permissive per-publisher
servers. Compose the MIT/Apache servers; do not link the AGPL aggregator into
a client codebase.

### Licence method — two new tiers, and a probe defect that would have published a wrong row

Pass 5 corrected the licence gate from byte-bands to **line counts**. Pass 6
added spec/code/data classes. This pass breaks the line-count gate twice and
fixes it.

**Tier 8 — the licence is declared in a package manifest, and there is no
licence file to read.** The statistical plane lives substantially in R, and
**CRAN declares licences in `DESCRIPTION`, not in `LICENSE`.** Seven
repositories, every one reported by GitHub as `NONE` or `NOASSERTION`:

| Repo | ★ | GitHub says | `DESCRIPTION` says | Reality |
|---|---|---|---|---|
| https://github.com/rOpenGov/eurostat | 257 | `NOASSERTION` | `BSD_2_clause + file LICENSE` | **BSD-2-Clause, permissive** |
| https://github.com/eblondel/rsdmx | 111 | `NONE` | `GPL (>= 2)` | **GPL-2+, copyleft** |
| https://github.com/expersso/OECD | 147 | `NONE` | `CC0` | **CC0, public-domain dedication** |
| https://github.com/eurostat/restatapi | 36 | `NONE` | `EUPL` | **EUPL, copyleft** |
| https://github.com/ilostat/Rilostat | 40 | `NOASSERTION` | `BSD_2_clause + file LICENSE` | **BSD-2-Clause, permissive** |
| https://github.com/MattCowgill/readabs | 114 | `NOASSERTION` | `MIT + file LICENSE` | **MIT** |
| https://github.com/Eflores89/inegiR | 54 | `NONE` | `CC0` | **CC0** |

**Seven repositories, one label, five different licences — BSD-2, GPL-2+, CC0,
EUPL and MIT — spanning permissive, copyleft and public domain.** You cannot
default-assume in either direction, and the two most-starred are on opposite
sides of the copyleft line (`rOpenGov/eurostat` BSD-2 at 257★, `rsdmx` GPL-2+
at 111★). Where a `LICENSE` file *does* exist in an R package it is often a
**two-line CRAN stub** (`ilostat/Rilostat`: `YEAR: 2026` / `COPYRIGHT HOLDER:
International Labour Organization`, 62 bytes) which names no licence at all —
so the probe does not merely miss the answer, it finds a file and learns
nothing. **Generalises to every ecosystem with a manifest: R → `DESCRIPTION`,
Python → `pyproject.toml`, Node → `package.json`, Rust → `Cargo.toml`, Java →
`pom.xml`.**

**Tier 9 — the short-form grant, where the pointer *is* the licence.**
`bis-med-it/pysdmx` and `bis-med-it/sdmx-rest4js` carry a **14-line, ~648-byte**
LICENSE reading `Copyright (c) 2023, Bank for International Settlements / The
pysdmx python library is licensed under the Apache License, Version 2.0` plus
the standard disclaimer. That is a **valid Apache-2.0 grant by incorporation**,
and a gate calibrated on 175–201 lines rejects it. It is distinct from pass 4's
pointer case (`bankstatementparser`), where the pointer led to a second,
fetchable full-text file: **here there is no second file, and the short text is
the whole grant.** A below-band count therefore means *read it*, and the
outcome is now one of three — a pointer to a real file, a self-contained short
grant, or a notice that grants nothing (`visa/trusted-agent-protocol`).

**The probe defect, and it is the one that would have published a wrong row.**
Probing `sdmx-twg/sdmx-rest` returned a **non-404 body of 44 lines / 1,522
bytes** at `LICENSE.rst`, which a length classifier would happily have
measured and filed. Re-fetching every ref directly returned **404 on all three
licence names across `main`, `master` and `develop`** while `README.md`
returned 200 on `master` — the repo has **no licence file**, and the 44-line
body was a transient proxy artefact. It was caught for exactly one reason:
**no licence marker matched**, so it was read instead of recorded.

> **Hardened rule, supersedes the length step of the Pattern 9 gate:
> a length measurement is valid only *after* a licence marker has matched.
> Marker first, length second. "Marker UNKNOWN" is never data — it means
> re-fetch and read.**

Line-count bands, refined (±1 line, depending on trailing newline — measured
across all 14 files read this pass): **MIT 20–21** · **Apache-2.0 short-form
14** · **Apache-2.0 without appendix 175–176** · **Apache-2.0 full 200–201** ·
**BSD-3 ~28** · **LGPL-3.0 187** · **AGPL-3.0 660–661** · **GPL-3 ~674** ·
**EUPL-1.2 286** (new this pass, 13,826 B, `amattioc/SDMX`).

### Census tabulated — what was asked and what came back

Recorded so the zeros are informed, per this KB's standing rule that silence
must not look like coverage.

| Query (single term) | Total | Best permissive, maintained result | Read |
|---|---|---|---|
| `sdmx` | 494 | `ondata/opensdmx` MIT 58★, pushed 2026-11-25 | **Alive and institutional** |
| `org:bis-med-it` | 11 | `marco-BIS` Apache-2.0 89★ | The channel that opened the plane |
| `org:sdmx-twg` | 16 | — (all specs, **no licence**) | Spec body publishes without licensing |
| `org:eurostat` | 95 | `gridviz` EUPL-1.2 250★ | **EUPL is the institutional default** |
| `pension` | 7,926 | `open-source-modelling/Open_Source_Economic_Model` MPL-2.0 30★ | Thin — informed gap |
| `payroll` | 57,994 | `Payroll-Engine/PayrollEngine` MIT 142★ | Alive but outside FS scope |
| `figi` | 403 | `svyatov/sec_id` MIT 8★ | **Identifier plane is API-served, not library-served** |
| `cyclos` | 563 | `cyclosproject/cyclos4-ui` MIT 47★ | Open UI, closed core — see `verticals/solutions.md` |

**`figi` is the sharpest small result.** FIGI is an *open* identifier standard
with a free OpenFIGI API, and the permissive library population is
`svyatov/sec_id` (MIT, **8★**) plus `philaris/figir` (4★) and a GPL-3.0 R
wrapper last touched in **2016**. The format is published and multi-party —
which by this KB's law should produce libraries — and it produced almost none.
The explanation is consistent rather than contradictory: **where the authority
runs a free public API, the lookup is a network call, not a parse**, so there
is no file to implement and no library accretes. That refines the law rather
than breaking it: **the law predicts libraries for formats you must *parse*,
not for registries you merely *query*.**
