---
industry: financial
region: Global
updated: 2026-11-09
---

# Composition Patterns — Financial Services

> Concrete recipes using only repos verified in this KB on 2026-11-09.
> Replaces the prior revision, whose single recipe read
> `### Receta 1: [Por definir]` with every field set to `—`.
>
> Licence rule applied throughout: the **base platform and every agent is
> MIT / Apache-2.0 / BSD**, so the client owns the result outright.

---

## Pattern 1 — Agentic lending assistant on an open core

**Target:** microfinance and SME lenders. Strongest fit: **LATAM** (Fineract's
original microfinance heritage) and **APAC** (India, Southeast Asia).

**Stack**

| Layer | Component | License |
|---|---|---|
| System of record | https://github.com/apache/fineract | Apache-2.0 |
| Front end | https://github.com/openMF/web-app | MPL-2.0 |
| Ledger (high-throughput option) | https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 |
| Agent runtime | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 |

**Wiring**

1. Stand up Fineract; **do not touch its schema**. Its REST API is the only
   integration surface — this is what keeps upgrades possible.
2. Wrap five Fineract endpoints as typed agent tools: `client.lookup`,
   `loan.application.create`, `loan.repaymentSchedule.get`,
   `account.statement.get`, `loan.arrears.list`.
3. Point FinRobot at those tools for the document-and-narrative work: income
   document extraction, affordability narrative, draft credit memo.
4. **Keep every write behind human approval.** `loan.application.create` is the
   only state-changing tool in the list and it submits for review — it does not
   decide.
5. Emit one audit record per agent action, keyed to the Fineract entity ID.

**Why the approval gate is not optional:** credit scoring is **EU AI Act Annex III
high-risk** from **2 Aug 2026**, the US **ECOA adverse-action reason duty
survives** the April 2026 Regulation B change, and **MAS's 7 Oct 2026
guidelines** expect human oversight. Every target region lands in the same place
by a different legal route.

**Effort:** Fineract deployment is the long pole, not the agent — budget most of
the time there and on the audit trail.

---

## Pattern 2 — EU AI Act conformity pack for an existing credit model

**Target:** **EMEA** only. The sharpest time-boxed opportunity in this KB — the
deadline is external and non-negotiable.

**Stack**

| Layer | Component | License |
|---|---|---|
| Model/portfolio analytics | https://github.com/goldmansachs/gs-quant | Apache-2.0 |
| Risk measures | https://github.com/dcajasn/Riskfolio-Lib | BSD-3-Clause |
| Pipeline-native modelling | https://github.com/skfolio/skfolio | BSD-3-Clause |
| Backtesting | https://github.com/stefan-jansen/zipline-reloaded | Apache-2.0 |

**Wiring**

1. Inventory the client's credit models against **Annex III** — creditworthiness
   assessment and credit scoring are named; life and health insurance
   underwriting are named. Fraud detection is *not* an Annex III item despite
   vendor claims, so do not scope it in by default.
2. Re-express each model in an sklearn pipeline via **skfolio** so that feature
   provenance is inspectable rather than asserted.
3. Generate the technical documentation set: intended purpose, risk
   classification, data governance, accuracy and robustness metrics,
   human-oversight design.
4. Add **DORA** artefacts in the same pass — the AI system is an ICT asset, so
   incident reporting and third-party-provider registers are in scope. Doing AI
   Act and DORA separately is duplicated work.
5. Add **GDPR Art. 22** handling for solely-automated decisions, and the recast
   **Consumer Credit Directive** path for automated creditworthiness from
   **20 Nov 2026**.

**Deliverable:** a conformity dossier, not a model. The engagement is
documentation and evidence generation — which is why it is sellable to clients
who will not buy an AI build.

---

## Pattern 3 — SAFR-aligned agentic payments control layer

**Target:** **APAC**, Singapore first. Singapore is the only jurisdiction with a
published AI-agent framework for finance (SAFR, July 2026).

**Stack**

| Layer | Component | License |
|---|---|---|
| Transaction store | https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 |
| Multi-party settlement | https://github.com/hyperledger/fabric | Apache-2.0 |
| Agent orchestration | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 |

**Wiring**

1. TigerBeetle holds double-entry state; it is the thing an auditor reads.
2. Every agent-initiated transfer carries an **agent identity, a mandate
   reference and a spend limit** — these are the SAFR safeguards made concrete,
   and they are schema fields, not policy prose.
3. Mandates are enforced in the ledger layer, not in the prompt. An agent cannot
   exceed a limit it has no ability to write past.
4. Hyperledger Fabric only where participants are known and need shared state —
   trade finance, interbank settlement. Not for single-institution builds.

**Carry-forward:** build it once for MAS and it becomes the template for
jurisdictions still drafting. **NPCI has said it is still examining an AI-agent
framework**, and the UPI–PayNow linkage makes agent authorisation an open
question somebody will have to answer.

---

## Pattern 4 — Cross-rail reconciliation agent (Pix ↔ Bre-B)

**Target:** **LATAM**. Addresses a named, verified gap: **Pix and Bre-B are not
interoperable** — payments cannot move between them.

**Stack**

| Layer | Component | License |
|---|---|---|
| Ledger | https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 |
| Accounting app (if the client needs a UI) | https://github.com/frappe/erpnext | GPL-3.0 |
| Agent runtime | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 |

**Wiring**

1. Normalise both rails into one internal transfer representation in
   TigerBeetle. Scale context: **Pix did 3.09bn P2B transactions in March 2026
   alone**, so this is a throughput problem before it is an AI problem — which is
   the reason for TigerBeetle rather than a general-purpose database.
2. The agent's job is exception handling, not the happy path: match unmatched
   legs, propose a reconciliation entry, escalate what it cannot explain.
3. Attach Brazil's **Open Finance explainable-AI** requirement to every proposed
   match — the explanation is a deliverable, not a debug log.
4. **Licence note:** ERPNext is GPL-3.0. Fine for a self-hosted client
   deployment; a blocker if Globant intends to ship a proprietary derivative.
   Drop it and build the UI fresh if that is the case.

---

## Pattern 5 — Research and market-intelligence desk

**Target:** **North America** first — asset managers and the examiner-driven
explainability market.

**Stack**

| Layer | Component | License |
|---|---|---|
| Data access | https://github.com/OpenBB-finance/OpenBB | Apache-2.0 |
| Prototype price feed | https://github.com/ranaroussi/yfinance | Apache-2.0 |
| Indicators | https://github.com/TA-Lib/ta-lib-python | BSD-2-Clause |
| Pricing / curves | https://github.com/lballabio/QuantLib | BSD-3-Clause |
| Multi-agent debate | https://github.com/TauricResearch/TradingAgents | Apache-2.0 |
| Report generation | https://github.com/AI4Finance-Foundation/FinRobot | Apache-2.0 |

**Wiring**

1. OpenBB is the data layer — it is explicitly positioned for "analysts, quants
   and AI agents", so the tool surface already exists.
2. TradingAgents supplies the analyst/researcher/risk-manager debate structure.
   **Run it for the argument, not the trade.** It is a research simulation
   framework; nothing here is authorised to move money.
3. FinRobot turns the debate transcript into a cited research note.
4. **Replace yfinance before production.** It is a Yahoo scraper, not a licensed
   data source — fine for the prototype, a compliance and continuity problem
   live.

**Why North America:** federal model-risk guidance **excludes** generative and
agentic AI from scope as of April 2026, so there is no model-risk ceiling here —
and no safe harbour either. The sellable artefact is the defensible reasoning
trail an examiner will ask for.

---

## Cross-pattern rules

1. **Never let an agent hold write access to the ledger.** Patterns 1, 3 and 4
   all route writes through a gate; in Pattern 3 the limit is enforced in the
   schema.
2. **Do not build on an archived repo.** `maybe-finance/maybe` (54.2k stars,
   archived 2025-07-27), `google/tf-quant-finance` (archived) and
   `quantopian/zipline` (stalled) are the traps — all three look strong by star
   count. See `repos/foundations.md`.
3. **Generic frameworks go underneath, not in the catalogue.** LangChain,
   LangGraph, CrewAI, AutoGen and Pydantic AI (all MIT) are legitimate
   orchestration choices under any pattern above — they are simply not financial
   agents, and `agents/top.md` says why.
4. **Pitch the back office.** Four of the top five financial-services AI use
   cases are back-office. Patterns 2 and 4 are back-office by construction and
   are the easier sells.
5. **Resolve `formancehq/ledger`'s license** before it enters any pattern. It is
   the most promising unblocked item in this KB and it is blocked on a licence
   check, not on technical merit.

---
*Written 2026-11-09 from repos verified the same day.*
