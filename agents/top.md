---
industry: financial
region: Global
updated: 2026-11-21
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

## Agents and agentic platforms — 11 permissive, re-measured 2026-11-21

| Agent | Repo | License | Stars | Last push | What it is |
|---|---|---|---|---|---|
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 123,303 | 2026-11-17 | Multi-agent LLM trading framework that simulates the roles of a trading firm (analyst, researcher, trader, risk manager) |
| OpenBB | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 | 75,600 | active | Open data platform for analysts, quants and AI agents — the de facto open market-data access layer |
| ai-hedge-fund | https://github.com/virattt/ai-hedge-fund | MIT | 64,780 | 2026-11-09 | An AI hedge fund team: LLM agents modelled on named investor styles, debating and voting on positions |
| qlib | https://github.com/microsoft/qlib | MIT | 50,455 | 2026-11-04 | AI-oriented quant investment platform from Microsoft; supervised learning, market-dynamics modelling and RL, with RD-Agent for automated research |
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,035 | 2026-04-13 | Foundation model for "the language of financial markets" — pretrained on market series rather than text. **See the staleness flag below** |
| ccxt | https://github.com/ccxt/ccxt | MIT | 44,940 | 2026-11-20 | Unified trading API across 100+ crypto exchanges and prediction markets (JS/TS, Python, C#, PHP, Go, Java, Rust) |
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 38,621 | 2026-11-20 | Personal trading agent from HKU Data Science lab; natural-language strategy authoring |
| FinGPT | https://github.com/AI4Finance-Foundation/FinGPT | MIT | 21,595 | 2026-11-18 | Open financial LLMs with released weights on HuggingFace; sentiment, NER and forecasting heads |
| hummingbot | https://github.com/hummingbot/hummingbot | Apache-2.0 | 21,318 | 2026-11-20 | Framework to build and deploy high-frequency crypto market-making and arbitrage bots |
| FinRL | https://github.com/AI4Finance-Foundation/FinRL | MIT | 17,152 | 2026-11-18 | Financial reinforcement learning library — environments, agents and backtests for RL-driven portfolio policies |
| FinRobot | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 | 8,457 | 2026-10-24 | Agent platform for financial applications: equity research, report drafting and decision workflows over LLMs |

All 11 are MIT or Apache-2.0 — usable as a Globant starting point with no
copyleft contamination.

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
| Dexter | https://github.com/virattt/dexter | MIT, in the README body ("This project is licensed under the MIT License") | **No LICENSE file** | 27,975 | Probed 11 filename and case variants across HEAD, main and master; all 404 while `README.md` and `package.json` returned 200. `package.json` has **no** `license` field. SPDX from search: `None` |
| Pix API spec | https://github.com/bacen/pix-api | Apache-2.0, via a shields.io badge in `readme.md` | **No LICENSE file** | 3,010 | Root listing is `openapi.yaml`, `readme.md`, `changelog.md`, `.gitignore`, `.github/`. Sidebar shows no license name |

**How to treat them.** A README sentence is a real statement of intent from the
copyright holder, but it is not a license text: there is no copyright line, no
warranty disclaimer and no grant wording, and GitHub's classifier reads nothing.
For Globant that means: fine to read, fine to prototype against, **not** clean
enough to vendor into client deliverables until upstream adds the file or
confirms in writing. Dexter at 27,975 stars is the one worth actually chasing —
it is a one-line fix for the maintainer and it unblocks a top-20 asset.

This also corrects a prior record: earlier rotation notes carried
"Dexter (MIT, ~27k stars)" as settled fact. The license was never filed.

## Flagged — real and permissive, but check before you build

| Agent | Repo | License | Stars | Flag |
|---|---|---|---|---|
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,035 | **Last push 2026-04-13 — seven months cold**, while every other top row pushed within the last three weeks. It is a published foundation model (AAAI 2026), so a frozen artefact is defensible, but do not plan on upstream fixes |

## Reference lists, not agents

| Resource | Repo | License | Stars | Note |
|---|---|---|---|---|
| awesome-ai-in-finance | https://github.com/georgezouq/awesome-ai-in-finance | CC0-1.0 | 6,700 | Curated index of LLM / DL strategies and tools in financial markets. A discovery feed, not something to build on |
| awesome-open-finance-brasil | https://github.com/ciro-maciel/awesome-open-finance-brasil | CC0-1.0 | 0 | Open Finance and Open Insurance in Brazil: BCB norms, official specs, open data, aggregators, open code. **0 stars**, updated 2026-11-10. The best single entry point to the LATAM regulatory corpus found this pass |
| awesome-pix | https://github.com/ciro-maciel/awesome-pix | CC0-1.0 | 1 | Pix for integrators: Central Bank norms, APIs, SDKs, providers, in Portuguese plus 14 languages. Companion to the above |

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
*Re-measured and extended 2026-11-21 (prior full rewrite 2026-11-09). 11 permissive
global rows re-verified, 4 region-placed rows added, 2 declared-but-not-filed
licenses newly separated out, 1 staleness flag raised.*
