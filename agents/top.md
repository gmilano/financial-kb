---
industry: financial
region: Global
updated: 2026-11-22
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
