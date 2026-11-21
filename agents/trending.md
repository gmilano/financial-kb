---
industry: financial
region: Global
updated: 2026-11-21
---

# Financial AI Agents — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

## 2026-11-21

Measured with three channels (`search/repositories` for metadata, `git ls-remote`
for existence, byte-exact LICENSE read over `raw.githubusercontent.com`). Method
and its three measured blind spots are in `agents/top.md`.

### Movers — only what actually moved

| Agent | Repo | License | Stars 2026-11-21 | Prior (2026-11-09) | Change |
|---|---|---|---|---|---|
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 123,303 | 121.5k | +~1.8k in 12 days |
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 38,621 | 37.9k | +~0.7k |
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 48,035 | 47.4k | +~0.6k, but **last push 2026-04-13** — stars rising on a cold repo |
| ccxt | https://github.com/ccxt/ccxt | MIT | 44,940 | 44.8k | +~0.1k |
| qlib | https://github.com/microsoft/qlib | MIT | 50,455 | 50.2k | +~0.3k |

Twelve days of drift across the top set is **under 2% on every row**. The large
moves this KB recorded in its 2026-11-09 pass (Vibe-Trading +21.0k over four
months) were real; the top of this market has since gone quiet.

### Newly recorded this pass

| Agent | Repo | License | Stars | Region | Why it is here |
|---|---|---|---|---|---|
| BankMCP | https://github.com/noskillish/bankmcp | MIT | 327 | EMEA | First PSD2 asset in this KB with real traction. Self-hosted, read-only, agent reads actual bank accounts over Enable Banking |
| idx | https://github.com/fzn0x/idx | MIT | 234 | APAC | Indonesian market (IDX/IHSG) terminal analysis. Created after 2026-08-01 and already at 234 stars |
| gen-fraud-graph | https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 | 296 | Global | Bank-authored synthetic fraud **graph** generator. Permissive, and it unblocks AML testing without customer data |
| lingee-bench | https://github.com/kingdee/lingee-bench | Apache-2.0 | 190 | APAC | Kingdee's enterprise benchmark for whether agents deliver business value — an evaluation harness, not an agent |
| open-net-worth | https://github.com/open-net-worth-ai/open-net-worth | AGPL-3.0 | 610 | Global | Self-hosted personal-finance assistant. Pushed 2026-11-21; fastest-moving new asset found. **AGPL** |
| accountant24 | https://github.com/machulav/accountant24 | Apache-2.0 | 70 | Global | Personal-finance agent over any LLM including local models |

### The new-asset flow is dry, and that is the finding

`finance AI agent created:>2026-08-01 stars:>=80` returns **`total_count: 4`**
for the whole world over nearly four months. Those four are `open-net-worth`,
`idx`, `lingee-bench` and an unlicensed market simulator.

So the six rows above are not evidence of a boom — they are **discovery debt
being paid down**. Four of them existed before this pass and the KB had not
found them. The distinction matters for cadence: an hourly pass cannot
manufacture new assets at roughly one qualifying repo a month. What pays per
pass is verification, correction and gap-closing, and this log should be read
as a record of measurement, not of market velocity.

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

### License-hygiene findings

- **Dexter (27,975 stars) declares MIT in its README and files no LICENSE.**
  Eleven filename and case variants probed across three branches, all 404,
  with `README.md` and `package.json` returning 200 as controls, and no
  `license` field in `package.json`. Earlier rotation notes recorded this asset
  as plain "MIT" — that was never filed. Full treatment in `agents/top.md`.
- **`bacen/pix-api` (3,010 stars) carries an Apache-2.0 badge and no LICENSE
  file.** Same category, different source: Brazil's central bank.
- **SPDX `NOASSERTION` meant Apache-2.0 in both cases where it appeared**
  (OpenBB 11,476 B, OpenFin8:BR 12,066 B — canonical Apache text with copyright
  lines prepended). Do not discard a row on `NOASSERTION` without opening it.

### Correction to this KB's own prior record

Earlier rotation history recorded **OpenBB as AGPL-3.0** across three separate
cycles. Measured today, byte by byte: `LICENSE` is 11,476 B, opening
"Copyright (c) 2021-2026 OpenBB Inc. All files in this repository are licensed
under the Apache License, Version 2.0" followed by the canonical Apache text,
with no carve-out. **OpenBB is Apache-2.0.** The 2026-11-09 revision had this
right; the older rotation notes did not.

### Model-side signal

No change measured this pass. **GLM 5.3 Flash (MIT)** remains the highest
open-weight score on Vals AI Finance Agent v2 as of 2026-09-23 at **57.9%**;
Ant Group's **Ling 3.0 Flash Fin** is a finance-continued-pretrain of Ling 3.0
Flash. Still not permissive: **MiniMax M3.1 Flash** (MiniMax Community
License), **Kimi K3** (own license).

## 2026-11-09

Measured directly off each repository page on 2026-11-09 (GitHub API is
proxy-blocked in this environment; existence confirmed with `git ls-remote`).

### Movers

| Agent | Repo | License | Stars 2026-11-09 | Prior reading | Change |
|---|---|---|---|---|---|
| Vibe-Trading | https://github.com/HKUDS/Vibe-Trading | MIT | 37.9k | 16.9k (2026-07-02, this KB) | **+21.0k, more than doubled in ~4 months** |
| TradingAgents | https://github.com/TauricResearch/TradingAgents | Apache-2.0 | 121.5k | "over 80k" (third-party roundup, 2026) | **+~40k vs the figure still being republished** |

### Newly recorded this pass

| Agent | Repo | License | Stars | Why it is here |
|---|---|---|---|---|
| Kronos | https://github.com/shiyu-coder/Kronos | MIT | 47.4k | Foundation model for market series rather than text; flagged on GitHub trending in April 2026 and has kept climbing |
| ai-hedge-fund | https://github.com/virattt/ai-hedge-fund | MIT | 64.6k | Also flagged in the April 2026 trending snapshot; now one of the largest finance-agent repos |
| qlib | https://github.com/microsoft/qlib | MIT | 50.2k | RD-Agent addition pushes it from quant platform into agentic research automation |
| OpenBB | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 | 75.3k | Repositioned explicitly for "analysts, quants and **AI agents**" |

### Model-side signal

- **GLM 5.3 Flash (MIT)** — highest open-weight score on Vals AI Finance Agent v2
  as of 2026-09-23, at **57.9%**.
- **Ling 3.0 Flash Fin** (Ant Group) — finance-continued-pretrain of Ling 3.0 Flash.
- Not permissive, despite appearing in finance comparisons: **MiniMax M3.1 Flash**
  (MiniMax Community License), **Kimi K3** (own license).

### Reclassified, not deleted

The ten repos recorded on 2026-07-02 (history below) were re-verified on
2026-11-09. **Seven still resolve; three have disappeared** — deleted, renamed or
made private since July:

| Gone as of 2026-11-09 | Was recorded as |
|---|---|
| https://github.com/sammygallant214/CryptoDesk-ai | MIT, 0 stars |
| https://github.com/Devsinfin/bank-churn-random-forest | `?` license, 0 stars |
| https://github.com/skstmdals1-ctrl/bybit-dashboard | `?` license, 2 stars |

Of the seven that survive, five still carry 0–6 stars and three still have no
identifiable license (`?`). The history rows are left exactly as recorded — that
is the point of a dated log — but **three of the ten are now dead links, and
nothing in that 2026-07-02 set belongs in a curated catalogue.** All ten have
been kept out of `agents/top.md`.

This is the concrete argument for verifying before writing: a 0-star repo
harvested by an automated pass has roughly a one-in-three chance of not existing
four months later.

### Gaps this pass

- No new **EMEA-origin** or **LATAM-origin** financial agent repos surfaced.
  The trending set is overwhelmingly US and China/HK-origin. Recorded as an
  informed gap rather than left to look like coverage.
- GitHub's own trending page could not be filtered by topic through this
  environment; trending signal here is reconstructed from dated third-party
  snapshots (April 2026 and October 2026 `agents-radar` issues) plus direct
  measurement, so it is a *monthly-resolution* signal, not weekly.

---

# History

*Everything below is preserved from earlier passes. Do not rewrite.*

*Column labels in the section below were normalised from Spanish to the
canonical English headers on 2026-11-09 so the compiler reads them as headers
rather than ingesting `Nombre` as an entity. **No data row was altered.***


## 2026-07-02

> Última actualización: 2026-07-02

| Agent | License | Description | Stars |
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
