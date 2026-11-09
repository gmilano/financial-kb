---
industry: financial
region: Global
updated: 2026-11-09
---

# Financial AI Agents — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

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
