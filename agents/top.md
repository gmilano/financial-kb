---
industry: financial
region: Global
updated: 2026-11-09
---

# Financial Services AI Agents — Curated Top Set

> Open source agents and agentic platforms for financial services.
> Preference order for Globant build-on: **MIT / Apache 2.0 / BSD**.
>
> **Verification method (2026-11-09):** the GitHub REST API and plain `curl` are
> blocked by this environment's proxy (every request returns 403, for real and
> fake repos alike, so `curl -sI` cannot discriminate). Existence was therefore
> verified with `git ls-remote` against each URL, and license / stars /
> description were read off the rendered repository page. Every row below was
> checked individually on 2026-11-09. Star counts are point-in-time.

## Agents and agentic platforms — 11 verified

| Agent | Repo | License | Stars | What it is |
|---|---|---|---|---|
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 121.5k | Multi-agent LLM trading framework that simulates the roles of a trading firm (analyst, researcher, trader, risk manager) |
| OpenBB | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 | 75.3k | Open data platform for analysts, quants and AI agents — the de facto open market-data access layer |
| ai-hedge-fund | https://github.com/virattt/ai-hedge-fund | MIT | 64.6k | An AI hedge fund team: LLM agents modelled on named investor styles, debating and voting on positions |
| qlib | https://github.com/microsoft/qlib | MIT | 50.2k | AI-oriented quant investment platform from Microsoft; supervised learning, market-dynamics modelling and RL, with RD-Agent for automated research |
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 47.4k | Foundation model for "the language of financial markets" — pretrained on market series rather than text |
| ccxt | https://github.com/ccxt/ccxt | MIT | 44.8k | Unified trading API across 100+ crypto exchanges and prediction markets (JS/TS, Python, C#, PHP, Go, Java, Rust) |
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 37.9k | Personal trading agent from HKU Data Science lab; natural-language strategy authoring |
| FinGPT | https://github.com/AI4Finance-Foundation/FinGPT | MIT | 21.5k | Open financial LLMs with released weights on HuggingFace; sentiment, NER and forecasting heads |
| hummingbot | https://github.com/hummingbot/hummingbot | Apache-2.0 | 21.1k | Framework to build and deploy high-frequency crypto market-making and arbitrage bots |
| FinRL | https://github.com/AI4Finance-Foundation/FinRL | MIT | 17.0k | Financial reinforcement learning library — environments, agents and backtests for RL-driven portfolio policies |
| FinRobot | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 | 8.4k | Agent platform for financial applications: equity research, report drafting and decision workflows over LLMs |

All 11 rows are MIT, Apache-2.0 — every one is usable as a Globant starting point
without copyleft contamination.

## Reference list, not an agent

| Resource | Repo | License | Stars | Note |
|---|---|---|---|---|
| awesome-ai-in-finance | https://github.com/georgezouq/awesome-ai-in-finance | CC0-1.0 | 6.7k | Curated index of LLM / DL strategies and tools in financial markets. Useful as a discovery feed; it is a list, not something to build on |

## What is deliberately NOT here

- **Generic agent frameworks** (LangChain, LangGraph, CrewAI, AutoGen, Pydantic AI).
  They are MIT and widely used in finance, but they are not financial-services
  agents — they carry no market data, no instrument model, no compliance surface.
  They belong in the technology KB; see `compose/patterns.md` for how to wire
  them underneath the agents above.
- **0-star and single-author repos.** The previous revision of this file and of
  `repos/trending.md` carried eight repos with 0–6 stars and `?` licenses
  (`CryptoDesk-ai`, `Fundo`, `split-checkout`, `bank-churn-random-forest`,
  `bybit-dashboard`, `lumen-core-public`, `clawock`, `auditLens`). All of them do
  exist — they were re-verified on 2026-11-09 and resolve — but a repo with no
  license and no community is not a studio starting point. They have been moved
  out of the curated set and into the dated trending log where unproven
  signal belongs.
- **Model weights.** GLM 5.3 Flash (MIT) scored highest among open-weight models
  on Vals AI Finance Agent v2 as of 2026-09-23 at 57.9%, and Ant Group's
  Ling 3.0 Flash Fin is a finance-continued-pretrain of Ling 3.0 Flash. These are
  models, not agents; licensing for finance use also turns on data terms, not only
  the weight license. Tracked in `intel/trends.md`.

## Caveats

- Star counts are a popularity signal, not a quality or production-readiness
  signal. TradingAgents at 121.5k stars is a research simulation framework, not a
  deployable trading system, and nothing here is authorised to move money.
- Several widely-cited third-party roundups were materially stale: one put
  TradingAgents at "over 80,000 stars" against the 121.5k the repository page
  showed on 2026-11-09, and the previous revision of this KB recorded
  Vibe-Trading at 16.9k against 37.9k today. Figures here come from the
  repository pages, not from roundups.

---
*Verified and rewritten 2026-11-09. Prior revision dated 2026-07-02 contained a
`PyPortfolio/PyPortfolioOpt` URL (a redirect) and no YAML frontmatter.*
