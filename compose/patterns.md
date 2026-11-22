---
industry: financial
region: Global
updated: 2026-11-22
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

**Target:** **EMEA** only.

> **CORRECTED 2026-11-21.** This pattern previously opened "the sharpest
> time-boxed opportunity in this KB — the deadline is external and
> non-negotiable." **The deadline moved.** The Digital Omnibus, Regulation (EU)
> 2026/1744, deferred Annex III obligations (credit scoring included) to
> **2 December 2027**. The pattern is still valid and still sellable — but lead
> with the **recast Consumer Credit Directive, in application since 20 November
> 2026**, which is binding today, and with **DORA**, which never moved. Sell
> the AI Act part as a properly-scoped 12-month programme, not a scramble. See
> `intel/market.md` EMEA.

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
   **Consumer Credit Directive** path for automated creditworthiness — **in
   application since 20 Nov 2026, so this is the binding leg today**.
6. Use **AI Act Art. 9(10)** deliberately: it permits folding AI risk management
   into existing DORA ICT procedures, so the dossier should extend the client's
   DORA artefacts rather than sit beside them. Note also that the AI Act grants
   derogations where equivalent financial-services requirements already exist —
   scope the overlap before quoting the work.
7. Check **substantial modification** status for every model already on the
   market: post-Omnibus, legacy systems are caught only if substantially
   modified after the new dates. "Is this change substantial?" is a live
   advisory question and a cheap first engagement.

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

**Updated 2026-11-22 — the "mandate reference" in step 2 now has a protocol
behind it.** When this pattern was written, the mandate was a schema field with
no standard shape. AP2's signed Intent / Cart / Payment mandates are that shape,
and `decionis/agent-safe-pipeline` is an off-the-shelf enforcement point. Build
step 2 from **Pattern 11**, which carries the repos, the licences and the
measured caveat that AP2's repository has been cold since 2026-06-17.

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

---

## Pattern 6 — Permissive AML triage that can be tested before it is trusted

**Target:** all regions; **LATAM first** (account-takeover reportedly +324% in
early 2026 in Mexico), then **EMEA** where DORA makes the audit trail mandatory.
**Premise superseded 2026-11-22 — read Pattern 10 first.** This pattern was
built for the gap this KB had verified open by function: no permissive,
maintained AML platform. **Tazama is that platform**, it is Apache-2.0, and
Pattern 10 is the version of this build that uses it. What survives here and is
inherited by Pattern 10 is the method — synthetic topology before agent, rules
and agent strictly separated, every claim anchored to a ledger entry. Use this
pattern unchanged only where the client refuses a 57-star dependency and wants
the triage layer without a platform underneath it.

**Stack**

| Layer | Component | License |
|---|---|---|
| Synthetic test data | https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 |
| Ledger of record | https://github.com/formancehq/ledger | MIT |
| High-throughput txn store | https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 |
| Agent value benchmark | https://github.com/kingdee/lingee-bench | Apache-2.0 |
| Reference design only (do not ship) | https://github.com/jube-home/aml-fraud-transaction-monitoring | **AGPL-3.0** |

**Wiring**

1. **Generate the graph before writing the agent.** `gen-fraud-graph` produces
   synthetic fraud *topology*, not just rows — mule networks, layering chains,
   shared-device clusters. This is the step every AML engagement stalls on,
   because real customer data cannot leave the bank and row-level fakes do not
   contain the structure fraud actually has.
2. **Keep rules and agent strictly separate.** Deterministic rules raise the
   alert; the agent only *investigates* it — gathers the counterparty history,
   the device overlap, the prior dispositions, and writes a cited case file. A
   human decides. This split is what makes the output defensible, and it is
   also the design the only permissive demos in this space converged on
   independently.
3. **Anchor every claim in the case file to a ledger entry id.** Formance or
   TigerBeetle holds the entry; the agent cites it. An assertion with no entry
   id behind it does not go in the file.
4. **Read `jube-home` for the domain model, do not deploy it.** It is AGPL-3.0,
   so hosting it for a client triggers source obligations — but it is the only
   maintained open AML platform, and its feature and outcome modelling is worth
   a day of reading before designing your own.
5. **Benchmark the thing honestly.** Run `lingee-bench` to answer the question
   the client will actually ask — does the agent deliver business value — rather
   than demoing a happy path.

**Deliverable:** an alert-triage agent with a synthetic-data test harness that
exists before the agent does. **Sales framing:** the testability *is* the
product. Any vendor can show an AML demo; almost none can show you the
synthetic adversarial graph they tested it against.

---

## Pattern 7 — EMEA open-banking agent, developed without a bank sponsor

**Target:** **EMEA**. Solves the problem that kills most PSD2 prototypes: you
cannot get a bank sandbox credential until you have something to show, and you
cannot build something to show without a sandbox.

**Stack**

| Layer | Component | License |
|---|---|---|
| PSD2 bank emulator | https://github.com/adorsys/XS2A-Sandbox | **AGPL-3.0** (test rig only) |
| Account read over MCP | https://github.com/noskillish/bankmcp | MIT |
| Alternative MCP server | https://github.com/open-banking-io/mcp-server | MIT |
| Personal-finance agent | https://github.com/machulav/accountant24 | Apache-2.0 |
| Ledger | https://github.com/formancehq/ledger | MIT |

**Wiring**

1. **Stand up XS2A-Sandbox as the bank.** It emulates a PSD2 bank on the Berlin
   Group **NextGenPSD2** standard — the actual EMEA interface specification, not
   a mock of one. AGPL-3.0 is near-zero risk here because **you never ship the
   sandbox**: it is your test double, and the obligation attaches to
   distribution, not to running it on a laptop.
2. **Point an MIT MCP server at it.** BankMCP (327 stars) is the more proven;
   `open-banking-io/mcp-server` (0 stars, MIT verified at 1,072 B) is the
   alternative if you want the open-banking.io API shape. Both are **read-only
   by design**, which matches what a bank will approve first.
3. **Keep the agent on the read path for the whole first phase.** Balances,
   transactions, categorisation, cash-flow questions. `accountant24` is a
   working Apache-2.0 reference for the agent side and runs against local
   models, which matters for a client that will not send statements to a hosted
   API.
4. **Mirror into Formance** so the agent reasons over your own normalised
   ledger rather than re-querying the bank for every question — and so you have
   a per-decision audit trail that satisfies DORA.
5. **Only then seek a real credential.** You arrive with a working read-only
   agent and a DORA-shaped audit trail, which is a completely different
   conversation from arriving with a slide.

**Deliverable:** a working EMEA open-banking agent built entirely on public
code. **Caveat to state up front:** payment *initiation* is not covered by any
permissive asset in this KB; it is a deliberate product choice across the space,
so plan that phase as custom work against a specific bank's API.

---

## Pattern 8 — LATAM Pix-native agent grounded on the central bank's own spec

**Target:** **LATAM** (Brazil). Uses the strongest official-source asset set in
this entire KB — Brazil is better tooled at the regulator level than EMEA is.

**Stack**

| Layer | Component | License |
|---|---|---|
| Authoritative API contract | https://github.com/bacen/pix-api | badge-declared Apache-2.0, **no LICENSE file** |
| Open Finance consent + Pix initiation | https://github.com/OpenFin8/openfin8-br | Apache-2.0 (verified 12,066 B) |
| Pix market analytics | https://github.com/StrategicProjects/pixbr | MIT |
| Regulatory corpus index | https://github.com/ciro-maciel/awesome-open-finance-brasil | CC0-1.0 |
| Ledger | https://github.com/formancehq/ledger | MIT |

**Wiring**

1. **Generate, do not vendor.** Fetch `openapi.yaml` (release 2.11.0-rc1) from
   BCB at build time and generate a typed client plus agent tool definitions
   from it. Do **not** copy the file into a client repository as Apache-licensed
   code: the grant is a shields.io badge in `readme.md`, not a filed licence.
   The generated client is your own work and carries your own licence. This one
   decision is the difference between a clean deliverable and an unanswerable
   question in a client's legal review.
2. **Take consent handling from OpenFin8:BR.** It implements Open Finance
   consent resources, Pix initiation and **Pix Automático** on the **FAPI-BR**
   security profile. At 0 stars it is a reference implementation, not a
   dependency — read it, then implement consent yourself against the spec.
3. **Satisfy the BCB's actual expectation, which is explainability on credit
   *and fraud* decisions.** Every agent decision needs a written reason, a
   documented human-oversight point and a monitoring record. This is more
   concrete than most of what EMEA requires today, and Brazil has no AI statute
   — it comes from supervision.
4. **Use `pixbr` for the market layer**, not the transaction layer: it reads the
   BCB Pix **Open Data** API into pandas, which is how you size a market or
   benchmark a client against the rail.
5. **Reconcile in Formance**, and if the engagement spans Colombia, see
   Pattern 4 — **Pix and Bre-B are not interoperable** and that gap is the build.

**Deliverable:** a Pix-native agent whose every API claim traces to the central
bank's own published contract. **Sales framing:** "grounded on BACEN's spec, not
on our interpretation of it" is a claim very few integrators can make, and it is
verifiable by the client in about two minutes.

---

## Pattern 9 — Licence-hygiene gate (copy this to every industry KB)

**Target:** every region, every industry. **Costs zero network calls per repo
beyond one HEAD request each**, and it catches the failure mode that cost this
KB a real asset for twelve days.

**The failure it prevents.** This KB declared "no permissive ledger library
exists" as a *genuine gap* for twelve days. `formancehq/ledger` had been MIT the
whole time; the prior pass probed a `github.com/.../blob/main/LICENSE` web path,
which this proxy answers 403/404 regardless of truth, and honestly reported it
could not verify. The gap was an artefact of the probe. In the other direction,
`virattt/dexter` (27,975 stars) is recorded in older rotation notes as plain
"MIT" when no LICENSE file was ever filed. **Both errors are invisible without
a byte-level check.**

**The gate**

```bash
#!/usr/bin/env bash
# For every github.com/<owner>/<repo> URL in the KB, verify the licence by bytes.
# Classifies into: VERIFIED | DECLARED-NOT-FILED | ABSENT | BLIND
grep -rhoE 'github\.com/[A-Za-z0-9._-]+/[A-Za-z0-9._-]+' . --include='*.md' \
  | sed 's|github\.com/||' | sort -u | while read -r slug; do
  # control first: if no known file resolves, the probe is BLIND, not the file absent
  ctl=0
  for c in README.md readme.md Readme.md README.rst package.json pyproject.toml; do
    [ "$(curl -s -o /dev/null -w '%{http_code}' \
        "https://raw.githubusercontent.com/$slug/HEAD/$c")" = 200 ] && { ctl=1; break; }
  done
  found=""
  # case variants matter: raw.githubusercontent.com IS case-sensitive
  for p in LICENSE LICENSE.md LICENSE.txt License License.md license license.md \
           LICENCE COPYING NOTICE; do
    code=$(curl -s -o /tmp/lic -w '%{http_code}' \
      "https://raw.githubusercontent.com/$slug/HEAD/$p")
    [ "$code" = 200 ] && { found="$p $(wc -c </tmp/lic)B"; break; }
  done
  if   [ -n "$found" ];  then echo "VERIFIED            $slug  $found"
  elif [ "$ctl" = 0 ];   then echo "BLIND               $slug  (no control file resolved)"
  else echo "ABSENT-OR-DECLARED  $slug  (no LICENSE file; check README/badge)"
  fi
done
```

**Byte bands for classifying what you find** — these let you spot a composite
licence without reading 11,000 lines:

| Licence | Canonical bytes | Reading |
|---|---|---|
| MIT | ~1,050–1,100 | Above the band = extra terms appended |
| Apache-2.0 | ~11,347 | Slightly above = copyright preamble (benign). Far above = composite, read it |
| BSD-3-Clause | ~1,500 | — |
| AGPL-3.0 | ~34,500 | — |
| GPL-3.0 | ~35,000 | — |
| Far below a band | — | A **pointer** to a licence, not the licence; read it |

**Rules the gate enforces**

1. `ABSENT-OR-DECLARED` is **not** a reason to drop a row. Check the README and
   any badge, then record it as **declared-but-not-filed** — a third category,
   neither safe nor unusable. `agents/top.md` has the table.
2. `BLIND` is never evidence of anything. Fix the probe and re-run.
3. Never discard on SPDX `NOASSERTION`. It resolved to genuine Apache-2.0 in
   2 of 2 cases opened this pass.
4. Never discard on a `search/repositories` miss — that channel returns false
   negatives on live repos (measured on OpenBB, FinAegis and zipline-reloaded).
   Existence is `git ls-remote`, and nothing else.

**Deliverable, for a client rather than for the KB:** this same gate run across
a client's dependency tree is a licence-provenance audit with byte-level
evidence per component. For any EMEA client it drops straight into the DORA
third-party register, which has to be produced anyway.

---

## Pattern 10 — Real-time financial crime stack on Tazama, with the agent outside the decision path

**Target:** all regions; strongest where a **national switch, a PSP or a
central bank** is the client — LATAM and Africa for Mojaloop-shaped rails, EMEA
where DORA makes the per-decision audit trail mandatory.

**This supersedes the premise of Pattern 6, not its method.** Pattern 6 was
built for a world with no permissive AML platform. That platform exists
(`verticals/solutions.md`), so the synthetic-data discipline and the
rules/agent separation below are inherited from Pattern 6 and the AGPL
workaround is dropped.

**Stack**

| Layer | Component | License |
|---|---|---|
| Transaction monitoring core | https://github.com/tazama-lf/tms-service | Apache-2.0 (SPDX header + `package.json`; no LICENSE file) |
| Routing | https://github.com/tazama-lf/event-director | Apache-2.0, same form |
| Rules as deployable units | https://github.com/tazama-lf/rule-901, https://github.com/tazama-lf/rule-902 | Apache-2.0 |
| Typology scoring | https://github.com/tazama-lf/typology-processor | Apache-2.0, same form |
| Rule authoring + simulation | https://github.com/tazama-lf/rule-studio, https://github.com/tazama-lf/simulation-service | Apache-2.0 |
| Investigation workflow | https://github.com/tazama-lf/case-management-system | Apache-2.0 |
| Sanctions / watchlist screening | https://github.com/moov-io/watchman | Apache-2.0 |
| Synthetic fraud topology | https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 |
| Payment switch (optional) | https://github.com/mojaloop/central-ledger via https://github.com/tazama-lf/payment-platform-adapter | Apache-2.0 by reference |
| Deployment | https://github.com/tazama-lf/tazama-stack (Compose), https://github.com/tazama-lf/tazama-helm (K8s) | Apache-2.0 |

**Wiring**

1. **Stand the platform up before writing a line of AI.** `tazama-stack` gives
   you the whole pipeline on Compose; `tazama-helm` is the same for a cluster.
   A demo that monitors real traffic shapes beats a slide about one.
2. **Screen the parties, score the transaction.** `watchman` answers "is this
   counterparty on a list" over HTTP with fuzzy matching; Tazama answers "is
   this transaction behaviour a known typology". They are different questions
   and a client will ask for both; nobody should build either.
3. **Give the agent the two jobs that are safe.** (a) **Rule drafting:** the
   agent proposes a new rule repository from an investigator's description of a
   pattern, `simulation-service` replays it against historical traffic, a human
   merges it. (b) **Case assembly:** the agent writes the case file in
   `case-management-system` — counterparty history, device overlap, prior
   dispositions, every claim carrying the transaction id it came from. **The
   agent never participates in the live scoring decision.**
4. **Test on topology, not rows.** Keep Pattern 6's rule: generate the mule
   networks and layering chains with `gen-fraud-graph` first. Tazama's
   typologies are structural, so row-level fakes will not exercise them.
5. **Hand counsel the licence note, unprompted.** Three runtime repos carry no
   LICENSE file and are Apache-2.0 by SPDX header and `package.json`. Say so
   before the client's lawyer finds it; `verticals/solutions.md` has the
   measurement to attach.

**Deliverable:** a running, permissively-licensed financial-crime platform with
an agent that drafts rules and assembles cases and touches no live decision.
**Sales framing:** the audit evidence is structural. Every rule is a versioned
repository with a history and a simulation record — that is what a supervisor
asks for, and it is almost impossible to retrofit onto a monolithic engine.
**Open risk to state up front:** Tazama's busiest repo has 57 stars. The
licence question is settled; the adoption question is the client's call.

---

## Pattern 11 — Agent-initiated payment with an approval rail that can be audited

**Target:** **LATAM first** — agent-initiated payments are reported live with
17 banks and processors since March 2026, and the region has already settled on
per-payment human confirmation. Then **APAC** (MAS SAFR is the published
framework this maps onto) and **Canada** (OSFI's July 2026 bulletin asks for
approval checkpoints before high-impact actions in so many words).

**Stack**

| Layer | Component | License |
|---|---|---|
| Authorisation model | https://github.com/google-agentic-commerce/AP2 | Apache-2.0 — **spec only, repo cold since 2026-06-17** |
| Settlement | https://github.com/x402-foundation/x402 | Apache-2.0 |
| Agent-to-agent payment bridge | https://github.com/google-agentic-commerce/a2a-x402 | Apache-2.0 |
| Enforcement point | https://github.com/decionis/agent-safe-pipeline | Apache-2.0 |
| Ledger of record | https://github.com/formancehq/ledger or https://github.com/blnkfinance/blnk | MIT / Apache-2.0 |
| US rail formats, if ACH is in scope | https://github.com/moov-io/ach, https://github.com/moov-io/fed | Apache-2.0 |
| Screening before release | https://github.com/moov-io/watchman | Apache-2.0 |

**Wiring**

1. **Model the authority, then stop using AP2's code.** Implement the three
   mandates — Intent ("the user wants a flight under 400 USD"), Cart ("this
   flight, this price"), Payment ("release these funds") — as signed artefacts.
   AP2 is the right shape and the wrong maintenance profile; take the shape.
2. **Put the gateway in front of every action, not every payment.**
   `agent-safe-pipeline` authorises *actions*. Payments are the obvious ones;
   the dangerous ones are the quiet steps before — changing a payee, widening a
   limit, resolving an ambiguous merchant.
3. **Make the human confirmation a protocol step, not a UI afterthought.** This
   is what Iniciador, Bipa and Fintoc do and it is the only configuration a
   LATAM bank has already approved. Confirmation happens in the customer's own
   banking app or by biometrics, and the mandate records which human released
   which cart at what time.
4. **Assume the mandate can be sound and the reasoning poisoned.** The
   published red-team result on AP2 is that signing preserves execution
   correctness while prompt injection manipulates the pre-signature reasoning.
   So the mandate must be rendered back to the human in **their** words at
   confirmation time — amount, payee, purpose — never as a hash or an opaque
   token. The signature proves what was authorised; the render is what makes
   the authorisation informed.
5. **Settle, then screen, then post.** `watchman` before release;
   `formance`/`blnk` as the entry of record; the mandate id on the ledger entry.

**Deliverable:** an agent that can assemble and submit a payment it cannot
release on its own, with a per-payment record linking human, mandate, screening
result and ledger entry. **Sales framing:** this is the ~2% question with a
defensible answer. The BoE/FCA measured ~2% of firms running agents with broad
autonomy; this pattern sells the 98% configuration as an engineering deliverable
instead of a limitation.

---

## Pattern 12 — Back-office agent pilot, lifted from a reference implementation

**Target:** all regions. This is the pattern that matches where the money
actually is — four of the top five financial-services AI use cases are
back-office (`intel/market.md`), and 57% of banking executives expect agents
embedded in risk, compliance, audit, fraud and transaction monitoring within
three years.

**Stack**

| Layer | Component | License |
|---|---|---|
| Workflow decomposition + prompts | https://github.com/anthropics/financial-services | Apache-2.0 |
| System of record | https://github.com/apache/fineract | Apache-2.0 |
| Ledger for reconciliation targets | https://github.com/formancehq/ledger | MIT |
| Enforcement point for write actions | https://github.com/decionis/agent-safe-pipeline | Apache-2.0 |
| Honest evaluation | https://github.com/kingdee/lingee-bench | Apache-2.0 |

**Wiring**

1. **Start from GL Reconciler and Month-End Closer, not from a chatbot.** Those
   two agents in the reference repo describe a break-finding and root-cause
   workflow and an accruals/roll-forward/variance-commentary workflow. The
   decomposition is the valuable part and it is Apache-2.0.
2. **Re-implement against the client's stack and the client's model provider.**
   The repo is a Claude-specific distribution; the *workflow* is portable and
   the licence permits taking it. MAS's third-party accountability expectation
   makes provider substitutability an architectural requirement anyway
   (`intel/market.md`, APAC), so do not hard-wire one vendor at the bottom.
3. **Point the agent at Fineract's REST API, never at its schema.** Same rule
   as Pattern 1: stay out of the core's tables so upgrades remain possible.
4. **Stage every output for sign-off.** The reference repo states its agents
   draft work product and do not post to a ledger or approve onboarding — the
   same boundary `verticals/solutions.md` recommends, reached independently.
   Keep it, and enforce it with the gateway rather than with a prompt.
5. **Measure value, not fluency.** `lingee-bench` asks whether the agent
   delivered business value. A reconciliation agent's metric is breaks closed
   per hour with a correct root cause, not tokens produced.

**Deliverable:** a month-end or reconciliation agent running against a real
ledger, with a measured before/after on close time. **Sales framing:** the
workflow map came from people who sell into these desks, the licence lets the
client own the implementation outright, and the first deliverable is a number
the CFO already tracks.

---

## Pattern 13 — Bank-statement reconciliation agent that only shows you the exceptions

**For:** any corporate or mid-market client whose finance team reconciles bank
statements to a ledger by hand. This is the single most common instance of the
back-office work CCAF measures at four of the top five AI use cases, and it was
the largest hole in this KB before pass 4.

**The architectural rule, inherited from the legal KB and unchanged here:**
`MODELS READ, RULES DECIDE`. A statement file either parses or it does not; two
amounts either tie or they do not. **Nothing deterministic goes to a model.**

| Layer | Component | License |
|---|---|---|
| Ingest, any format | https://github.com/sebastienrousseau/bankstatementparser | Apache-2.0 OR MIT |
| Same, as agent tooling | https://github.com/sebastienrousseau/bankstatementparser-mcp | Apache-2.0 |
| EMEA statement formats | https://github.com/viafintech/camt_parser, https://github.com/wolph/mt940 | MIT, BSD-3-Clause |
| US formats | https://github.com/ministryofjustice/bai2, https://github.com/moov-io/ach | MIT, Apache-2.0 |
| LATAM returns | https://github.com/openboleto/OpenCnabPHP | MIT |
| Ledger of record | https://github.com/formancehq/ledger or https://github.com/blnkfinance/blnk | MIT, Apache-2.0 |
| Triage design to copy | https://github.com/FoundrySoftHQ/agent-for-accounting | MIT |

**Wiring:**

1. **Parse deterministically.** The statement goes through the parser for its
   format. A file that fails to parse is an **operational incident**, not an
   agent prompt — route it to a person with the parser's own error.
2. **Match deterministically.** Exact matches on amount + date + reference
   clear without a model ever seeing them. In most books this is the large
   majority of lines, and every one of them is free.
3. **The agent sees only the residue** — the lines that did not match — through
   the MCP server, as structured transactions. Its job is to *propose* a
   match or an explanation, each one citing the statement line id and the
   ledger entry id.
4. **A verifier drops any proposal whose cited ids do not resolve.** Same
   mechanism as Pattern 6 and the legal KB's P29.
5. **A human accepts or rejects.** Nothing posts to the ledger unattended.

**Why it sells:** the baseline already exists in the client's close calendar —
unmatched-line count, touch rate, days-to-close. Pattern 13 is the direct answer
to the CCAF finding that **76% of large institutions cannot measure AI value**.

**Honest limitation:** `billing-lint`'s README finding from the legal KB applies
here verbatim — **batch LLM review is inconsistent**: the same defect gets
flagged on line 3 and missed on line 47, and two runs over one extract
disagree. In reconciliation that inconsistency is money. It is the reason steps
1 and 2 are not negotiable.

---

## Pattern 14 — Verification of Payee: a mandated obligation with no incumbent

**For:** any euro-area PSP, and the clearest greenfield opening this KB has
measured in EMEA.

**The demand is legal, dated and in force.** VoP has been mandatory for
euro-area payment service providers since **9 October 2025** under the Instant
Payments Regulation, on standard and instant transfers, with the result returned
within **five seconds**. The supply, measured: **two repositories worldwide,
both zero stars.**

| Layer | Component | License |
|---|---|---|
| Scheme-aligned matcher to start from | https://github.com/softvasco/payee-match | MIT (1,068 B) |
| Second reference implementation | https://github.com/untitledfinancial/dpx-compliance-public | BSD-3-Clause |
| Name-matching engine (reuse, do not rebuild) | https://github.com/moov-io/watchman | Apache-2.0 |
| Scoring API | https://github.com/apognu/motiva | MIT |
| Recall measurement | https://github.com/Divine16/Sanctions-screening-benchmark | MIT |
| Initiation files | https://github.com/sebastienrousseau/pain001, https://github.com/inisos/bank4j | Apache-2.0, MIT |

**Wiring:**

1. **Do not build a name matcher.** `moov-io/watchman` already does fuzzy name
   matching at production quality for sanctions screening; VoP is the same
   primitive against a different list. Reuse the engine, swap the corpus.
2. **Make the outcome explainable by construction.** The EPC scheme needs
   match / close-match / no-match, and a close match must be presentable to a
   payer in the time they are staring at a confirmation screen.
   `payee-match` is built around exactly this and is the reason to start there
   rather than from scratch.
3. **Budget the five seconds explicitly**, end to end, and test it as a hard
   gate in CI. The latency budget is the requirement most likely to fail late.
4. **Measure recall before anyone asks.** Adapt the sanctions benchmark's
   method — transliteration, spelling and ordering variants — to payee names.
   **A match engine without a published recall figure cannot clear a second-line
   risk review**, and this is the cheapest part of the whole build.
5. **Keep the model out of the decision.** It drafts the explanation shown to
   the payer; deterministic scoring decides the outcome.

**Where the care is needed:** the non-euro-area extension date is **contested
in the sources** — the ECB gives 9 July 2027 for VoP in non-euro Member States,
KPMG writes 1 January 2027 for the EEA. Cite the regulation text or the national
supervisor, not a consultancy page, and note §17: **a date is not a durable
fact.** The euro-area obligation, already in force, is the leg that does not
move.

---

## Pattern 15 — Governance pack a bank's second line will actually accept

**For:** the review that decides whether anything else in this file ships. Four
passes of this KB catalogued what to build with and nothing about what gets
approved.

| Layer | Component | License |
|---|---|---|
| Control catalogue | https://github.com/finos/ai-governance-framework | **CC-BY-4.0** |
| Catalogue, queryable by the agent | https://github.com/finos/aigf-mcp-server | Apache-2.0 |
| Reference architectures | https://github.com/finos/ai-reference-architecture-library | Apache-2.0 |
| Licence provenance evidence | Pattern 9 in this file | — |
| Honest evaluation | https://github.com/Divine16/Sanctions-screening-benchmark, https://github.com/kingdee/lingee-bench | MIT, Apache-2.0 |

**Wiring:**

1. **Start from the FINOS catalogue, not from your own control list.** Its
   authority is that **Citigroup, Morgan Stanley and Bank of America** back the
   Common Controls work — the client's competitors wrote it. This is the same
   dynamic the legal KB found with Singapore MinLaw's guidance: the short,
   peer-authored, sector-specific document becomes the buying criterion.
2. **Serve it through `aigf-mcp-server`** so the controls are queryable during
   design and review, by the agent under review. "Show me the control that
   applies to this component" becomes a tool call rather than a meeting.
3. **Consolidate, do not duplicate.** EU AI Act Article 9(10) lets AI risk
   management fold into existing **DORA** ICT processes. Map once, cite twice;
   quoting the same obligation as two separate work packages is how a proposal
   loses credibility with a second line that knows its own regime.
4. **Attach licence provenance.** Pattern 9's byte-evidence audit drops
   straight into the DORA third-party register the client must produce anyway —
   and after this pass it must also resolve **seven** tiers of licence evidence,
   including `NOASSERTION` rows like `quickfix-j/quickfixj`, whose
   advertising clause creates a documentation deliverable nobody budgets for.
5. **Attach a measured recall or accuracy figure.** See §16: the institutions
   themselves say they cannot measure value. Arriving with the measurement is
   the differentiator.

**Two things to state plainly to the client, because they will find out
anyway:** `ai-governance-framework` is **CC-BY-4.0, a content licence** — you
adopt and attribute a document, you do not import a dependency. And **FINOS
publishes a framework, not a certification**; no supervisor has endorsed it. Its
value is as a defensible starting point in a space where **SR 26-2 and OCC
Bulletin 2026-13 leave agentic AI outside model-risk guidance entirely**, so
there is no examiner playbook to inherit and the first credible framework sets
the de facto standard.

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
5. **~~Resolve `formancehq/ledger`'s license~~ — RESOLVED 2026-11-21: it is
   MIT** (1,083 B, canonical, identical on HEAD/main/master; 1,482 stars, pushed
   2026-11-21). It is now cleared for use in any pattern and is used in P8
   below. The prior block was a measurement artefact — a `github.com/.../blob/...`
   probe, which this proxy answers 403/404 regardless of truth.
6. **Verify a licence by reading its bytes, never by trusting the badge or the
   classifier.** Two of the biggest assets in this space declare a permissive
   licence in prose and ship no LICENSE file (`virattt/dexter` 27,975 stars;
   `bacen/pix-api` 3,010 stars), while SPDX `NOASSERTION` meant genuine
   Apache-2.0 in 2 of 2 cases opened. P9 below makes this a CI gate.
7. **Prefer `pushed_at` over stars when choosing a component.** Stars pick
   archived repos; `pushed_at` does not. Four archived-or-stalled traps are
   named in rule 2 and in `repos/foundations.md`. Added 2026-11-22: this now
   cuts against a *protocol* as well — `google-agentic-commerce/AP2` has 3,283
   stars and no push since 2026-06-17, while `x402-foundation/x402` has 6,820
   and was pushed this week.
8. **Take the shape from the spec, the code from whatever is maintained.**
   Patterns 3, 11 and 12 all do this: AP2's mandate model without AP2's SDK,
   `anthropics/financial-services`' workflow decomposition re-implemented
   against the client's own provider, FinAegis's tool model implemented against
   Fineract's API. Permissive licences are what make this legitimate — it is
   lifting a design, not a dependency.
9. **The agent proposes; a human releases.** A supervisor (OSFI, July 2026), a
   central bank (ECB FSR, November 2026), a survey (BoE/FCA: ~2% of firms run
   agents with broad autonomy) and a live market (Iniciador, Bipa, Fintoc
   requiring per-payment confirmation) converge on this independently. Every
   pattern in this file that writes anything puts an enforcement point in the
   path — not a prompt instruction, an enforcement point.
10. **Before believing a gap, re-run the query in the practitioners' own
    words.** The AML gap in this KB survived three passes because the searches
    said "AML" and "transaction monitoring" while the platform says "financial
    crime risk management". The agentic-payment tier was missing because the
    discovery metric said "finance AI agent". Both gaps closed on vocabulary,
    not on effort. A gap that has survived three passes is evidence about the
    query.
11. **A repository's death is not a category's death.** Pass 3 measured
    `moov-io/iso20022` as archived — correctly — and concluded "do not start an
    ISO 20022 build here". Fourteen permissive, maintained message-layer
    repositories say otherwise, including a direct replacement
    (`prowide/prowide-iso20022`, Apache-2.0, 240 stars). The archived repo is a
    fact about a repo. **Generalising it took one sentence and cost a
    category**, in the same pass that correctly refused to generalise a
    zero-result query into a missing platform.
12. **Deterministic components first, and prefer the plane where correctness is
    checkable.** A pain.001 validates or it does not; a CNAB segment parses or
    it does not; two amounts tie or they do not. Patterns 13 and 14 put models
    strictly downstream of components that cannot be wrong in an interesting
    way. This is also the commercial argument: it is the plane where the client
    already has a baseline, and §16 records that **76% of large institutions
    say they cannot measure AI value**.

---

## Pattern 16 — Metro 2 bureau-file assurance with a differential oracle

**Problem.** Every US lender sends a Metro 2 file to Equifax, Experian and
TransUnion each month. FCRA accuracy liability attaches to its contents, and
the bureaus' own validators are not something the lender can run in CI. Defects
surface as consumer disputes months later, by which time the wrong data has
propagated to three bureaus and any number of downstream decisions.

**Why this is the best first engagement in the KB.** The obligation is
external, the output is machine-checkable, the client cannot opt out, and —
uniquely — **two independently written permissive implementations exist**, so
correctness can be demonstrated rather than asserted.

**Wiring.**

1. **Two generators, one spec.**
   `moov-io/metro2` (Go, Apache-2.0, 130★) and `teamupstart/metro_2`
   (Ruby, MIT, 23★) build the same Metro 2 file from the same published
   layout. Feed both from one canonical account extract.
2. **Differential oracle.** Diff the two outputs field by field. A divergence
   is either a spec ambiguity or a bug in one library — both are findings, and
   neither requires the bureaus. This is the whole trick and it costs one
   afternoon.
3. **Deterministic validation first.** Field-level rules — date coherence,
   account-status transitions that the layout forbids, balance versus
   scheduled-payment arithmetic, required-field presence per segment — run as
   code. **No model involved.** The arithmetic must be reproducible to the
   cent and the same input must always produce the same verdict.
4. **Model only where there is judgement.** Narrative and free-text segments,
   and the triage of *which* divergences matter, go to a model that must cite
   the specific account id and segment it is talking about. A verifier drops
   any finding whose citation does not resolve.
5. **Human gate.** Divergences are proposals. A credit-operations analyst
   accepts or rejects; the decision and its evidence are written to an
   append-only log keyed by account id and cycle date.
6. **Run it in CI, on the extract** — not at submission time. The point is to
   fail before the file leaves the building.

**Deliverable the client keeps.** A conformance harness with a dated evidence
trail per cycle. It is directly usable as FCRA reasonable-procedures evidence
and it is the kind of artefact a second line and an examiner can both read.

**Expectation setting.** `moov-io/metro2` is production-grade. `teamupstart/metro_2`
at 23 stars is adopted here as an **oracle, not a dependency** — if it is wrong,
the diff tells you, which is exactly the job it is being given.

**Transfers to:** ISO 20022 (`moov-io/rtp20022` vs `prowide/prowide-iso20022`),
EN 16931 (`josemmo/einvoicing` vs `num-num/ubl-invoice`), ACH
(`moov-io/ach` vs `RiverFinancial/nacha`). **Any format with two permissive
implementations gets a free correctness oracle.** Check for a second
implementation before writing a validator.

---

## Pattern 17 — Dispute and chargeback triage on a deterministic clock

**Problem.** A card dispute has two separable halves that firms routinely merge
and then get wrong. One half is **arithmetic**: Regulation E §1005.11 sets hard
clocks — acknowledgement, provisional credit, investigation windows — and
missing one is a compliance failure regardless of the dispute's merits. The
other half is **judgement**: whether a chargeback is worth representing, and
what evidence supports it.

**The architecture rule, stated once: clocks are code, merits are judgement,
and they never share a code path.**

**Wiring.**

1. **Clock engine — deterministic, no model.**
   `dleonard-data/reg-e-timing` (MIT, 1★) expresses §1005.11 timing as
   institution-configurable testable code. **Read it, do not depend on it** —
   one star and one contributor. Lift the rule shapes and the test cases,
   reimplement against the client's calendar, product set and cut-off times.
   Every clock gets a unit test with a named regulatory citation.
2. **Case intake and reason-code taxonomy.**
   `opensyndicate/dispute-agent` (MIT, 1★) triages by reason code and
   assembles representment evidence. Same status: **design reference**. Its
   value is the taxonomy and the evidence checklist per reason code, which is
   otherwise scattered across scheme manuals.
3. **Ground every case in the ledger.** Each dispute references a posted
   entry. With `moov-io/iso8583` for the original authorisation message and
   `moov-io/ach` or `moov-io/imagecashletter` for the settlement leg, the
   agent can cite **the actual message fields**, not a summarised description
   of them. An assertion that does not resolve to a message field is dropped.
4. **Model proposes, never decides.** The model drafts the representment
   narrative and ranks cases by expected recovery. It may not start a clock,
   stop one, issue provisional credit, or close a case.
5. **Two queues.** Clock-driven actions execute automatically and are logged.
   Merit decisions go to a human with the evidence pack attached.

**Why build rather than buy.** Per trend #19, this is a judgement layer: the
best open-source asset in the category has **one star**. There is no incumbent
to displace and no community to keep pace with — and the client's own dispute
history is the asset that makes it work.

**Sales line that is true.** Not "AI resolves disputes faster". It is **"no
clock is ever missed, and every representment cites the message field it rests
on"** — the first half is a compliance guarantee and the second is a recovery
argument, and both are verifiable by the client in an afternoon.

---

## Pattern 18 — Statutory filing agent, regionalised

**Problem.** A financial institution or its corporate client must file
machine-readable statutory documents on an external deadline. The format is
published, conformance is binary, and nobody gets to skip it. This is the
highest-certainty agent workload in the KB and it is **the same engagement in
four regions with a different format library swapped in**.

**The invariant pipeline.**

```
system of record  ->  format library (permissive, separate)  ->  conformance
gate (deterministic)  ->  judgement layer (model, cited)  ->  human sign-off
->  append-only filing log
```

Keep the format library **outside** the core. It isolates country-specific
churn and any copyleft, and it lets the conformance gate be tested against the
library's own fixtures without standing up the platform.

**The regional swap — everything else is identical.**

| Region | Filing | Format library | Licence |
|---|---|---|---|
| North America | Metro 2 to the bureaus; FinCEN SAR/CTR | `moov-io/metro2`, `moov-io/fincen` | Apache-2.0 |
| EMEA | EN 16931 / Peppol BIS e-invoice; UK iXBRL accounts; SAF-T | `josemmo/einvoicing`, `num-num/ubl-invoice`, `kanedata/ixbrl-parse`, `SimansoftMZ/SAF-T` | MIT |
| APAC | Japan EDINET disclosures | `matthelmer/edinet-tools`, `ajtgjmdjp/edinet-mcp` | MIT, Apache-2.0 |
| LATAM | SPED/ECD (BR), contabilidad electrónica (MX) | **no viable permissive library — integrate the client's fiscal emitter** | — |

**LATAM is not a gap to fill, it is a different shape.** The only candidates
are one stale LGPL-3.0 library (4★, no commit since July 2024) and one
abandoned in 2015. The structural reason is in `intel/market.md`: EN 16931,
Peppol and SAF-T are multi-country formats and attract permissive libraries;
SPED and CFDI are single-country and the ground is owned by commercial fiscal
emitters the client is already obliged to use. **Integrate above the emitter;
do not rebuild it.** The pipeline is unchanged — only the first box is a
vendor API instead of a library.

**Where APAC has an unfair advantage.** `ajtgjmdjp/edinet-mcp` ships the
regulator's corpus **behind an MCP server** under Apache-2.0. For a Japanese
engagement the data source is a configuration step, not a build.

**Licence discipline, measured.** `OpenPeppol/peppol-bis-invoice-3` (158★) has
**no determinable licence** — every root-path probe 404s on all four branches,
so absence is not even measured. It is the normative spec: read it, never
vendor it. Build against the two MIT libraries. Apply the same rule to
`moov-io/awesome-fintech` (409★, no licence file) — a useful index, not a
dependency.

**Why this closes better than a judgement pattern.** The deliverable is a
conformance gate with a dated evidence trail. It produces a number in week one
— files conforming, defects caught before submission — which per trend #19 is
exactly what the 76% of large institutions who cannot measure AI value are
missing, and it is what funds the judgement work above it.
