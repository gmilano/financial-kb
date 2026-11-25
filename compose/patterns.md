---
industry: financial
region: Global
updated: 2026-11-25
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

---

## Pattern 19 — Reporting assurance either side of the ARM (the pattern for a plane with no parser)

**Applies to:** MiFIR RTS 22, EMIR REFIT, SFTR (EMEA); CAT, Form PF, N-PORT
(North America); ASIC/MAS/HKMA derivative reporting rewrites (APAC).

**Why this pattern exists.** Every other reporting pattern in this KB starts by
adopting a permissive format library. Here there is none and there never will
be — pass 6 measured it (MiFIR 2 results, EMIR 6 with a 1-star best, CAT zero)
and `intel/trends.md` §21 explains why: these are one-way submissions to a
single destination that publishes no reader, usually reached through a licensed
ARM or trade repository that sells exactly that layer.

**So do not build the format layer.** The client already pays for it. Build on
**both sides of it**, where the client's actual exposure is: reportable
accuracy, not transport.

**The wiring.**

1. **Trade store → pre-submission reconciliation.** Before the extract goes to
   the ARM, reconcile it against the firm's own books: does every reportable
   trade appear, does every appearing trade exist, do notional, counterparty,
   venue, timestamp and instrument identifier agree with the front-office
   record? This is deterministic and needs no model.
2. **Field-level validation from a design reference.**
   `amol-vishwarupe/EMIR` (1★, **no licence file**, pushed 2026-08-08) packages
   50 ESMA-style functional validation rules. **Read it for the rule shapes and
   reimplement** — unlicensed means not adoptable, and this KB's maturity rule
   bars a 1-star repo from a client deliverable regardless.
   `shyamramamoorthy/mifir-transaction-reporting-engine` (0★, unlicensed) is the
   equivalent design reference for RTS 22's field set.
3. **Counterparty identity resolved, not guessed.** `ggravlingen/pygleif` (MIT,
   23★) or `olgasafonova/gleif-mcp-server` (MIT, 8★) against the GLEIF register.
   A reporting break caused by a stale or wrong LEI is one of the most common
   and most avoidable rejection classes.
4. **Submit through the client's existing ARM / TR.** Unchanged. Do not touch
   it.
5. **Post-submission acknowledgement reconciliation — the half everyone
   skips.** Pull the ARM/TR acknowledgements, rejections and reconciliation
   feedback and match each one back to the originating trade. An unmatched
   acknowledgement is an open item; a rejection that nobody routed back to an
   owner is an unreported trade.
6. **Model, strictly on the narrative side.** The LLM triages rejection
   clusters, drafts the explanation of *why* a class of trades is failing, and
   proposes the mapping fix. It is **obliged to cite the trade id and the
   field**; a finding whose citation does not resolve is discarded by the
   verifier. The model never edits a report, never submits and never closes an
   item.
7. **Append-only reporting log** keyed by trade id and reporting date, with the
   human decision recorded against each item.

**Why this closes.** The deliverable is a reconciliation with a number in it —
*N trades reportable, N submitted, N acknowledged, N rejected, N unmatched* —
available in week one, defensible to a reviewer, and not competing with any
incumbent. It is the §21 corollary applied: the format layer is bought, the
judgement layer is built.

**Platform note.** Run the deterministic half on `finos/tracdap` (Apache-2.0)
if the client will have it: immutable versioned inputs mean each reporting run
is reproducible on demand, which is the question a regulator asks after a
reportable-accuracy finding.

## Pattern 20 — Sanctions screening with a differential oracle and an honest data licence

**Applies to:** all regions. The licence constraint is global.

**The assets, and the split that has to be understood before anything is
proposed.**

| Component | Repo | Licence | Stars |
|---|---|---|---|
| Screening API (self-hosted) | https://github.com/opensanctions/yente | MIT **(code)** | 189 |
| Second implementation of the same scoring contract | https://github.com/apognu/motiva | MIT | 16 |
| Entity resolution / dedup | https://github.com/opensanctions/nomenklatura | MIT | 274 |
| Entity data model | https://github.com/opensanctions/followthemoney | MIT | 122 |
| Name/identifier cleaning | https://github.com/opensanctions/rigour | MIT | 74 |
| Recall benchmark harness | https://github.com/Divine16/Sanctions-screening-benchmark | MIT | 33 |
| Alternative screener, 35+ lists | https://github.com/AbgarSim/sieve-aml | MIT | 16 |
| **The data** | OpenSanctions datasets | **CC BY-NC 4.0**, some files unlicensable | — |

**Step zero, before any technical work: price the data licence.** The code is
MIT and genuinely free. The data is **non-commercial**, and screening a
client's customers is commercial by definition — `yente`'s own README says
commercial use "may require a data licence for OpenSanctions data". A pilot
that works on CC-BY-NC data and cannot go to production is the worst possible
place to discover this. (`opensanctions.org/licensing` does not resolve from
this session's network policy, so the tiers must be obtained directly.)

**The differential oracle, which is what makes this pattern worth a number.**
`yente` and `motiva` implement **the same matching and scoring contract
independently**, both MIT. Feed both the same entity set and the same query
load and **diff the scores and the match sets**. Divergence is a free
correctness signal on the hardest part of screening — fuzzy name matching
across transliterations, orderings and corporate suffixes — with no vendor
oracle required.

This is Pattern 16's mechanism (two permissive implementations of one
specification give a correctness oracle for free) applied to a **scoring
contract** rather than a file format, which is the first time this KB has been
able to do that.

**Then calibrate against a published benchmark.**
`Divine16/Sanctions-screening-benchmark` (MIT, 33★) measures **recall** for
name screening. Recall is the number that matters and the number vendors avoid:
a screener with a conveniently low false-positive rate may simply be missing
people. Run it before and after any threshold change, and keep the series.

**Where the model goes, and where it does not.**

- Deterministic: list ingestion, name normalisation (`rigour`), candidate
  generation, scoring, threshold application, the audit record.
- Model: **alert narrative and triage ordering only** — drafting why a
  candidate resembles a listed entity, ranking a queue by likely relevance. It
  must cite the list, the entry id and the matched field.
- **The model never clears an alert, never adjusts a threshold, and never
  decides a relationship.** A cleared sanctions alert is a regulatory decision
  with personal liability attached.

**What the client gets in week one:** a recall figure for their current
screening configuration, measured on a published benchmark, plus a diff between
two independent implementations of the matching contract. Both are numbers, and
neither requires the client to have adopted anything yet.

## Pattern 21 — Depend on the implementation, not the standard (a procurement gate, not an architecture)

**Applies to:** every engagement that touches FINOS, and by extension any
standards-body repository.

**The failure this prevents.** An architect adds `finos/common-domain-model` to
a build. It has 297 stars, 142 forks, a push dated today and a `LICENSE.md`.
Nothing looks wrong. But that file is the **Community Specification License
1.0** (99 lines) — it governs a *specification document* and makes a patent
commitment to implementers. It is **not** a software licence and does not grant
what an Apache-2.0 grant grants. GitHub's API reports `NOASSERTION`, which most
tooling renders as "unknown" and most reviewers read as "probably fine".

**The gate — three checks, mechanical, add to Pattern 9's script.**

1. **Read the licence name from the FIRST NON-BLANK LINE.** Not from a
   body-wide grep. Pass 6 caught its own probe labelling `danielep71/K-CVA` as
   **AGPL** when it is **MPL-2.0**, because MPL-2.0's Exhibit B names the GNU
   GPL, LGPL and AGPL as secondary-licence options. Any licence with a
   compatibility exhibit trips a body grep.
2. **Classify the artefact before classifying the licence.** If the first line
   is `# Community Specification License 1.0` (99 lines) the repo is a
   **standard**; if it is `Attribution 4.0 International` (395 lines) it is a
   **document**; if `Mozilla Public License Version 2.0` (373 lines) it is
   weak-copyleft **code**. Only Apache-2.0 (201–202 lines), MIT (19–23) and
   BSD-3 (~28) are permissive code grants.
3. **If the artefact is a standard, find its implementation repo.** It is
   almost always a sibling in the same org, lower-starred, properly
   Apache-2.0:

| Standard (do not depend on) | Implementation (depend on this) |
|---|---|
| `finos/common-domain-model` (CSL-1.0, 297★) | `finos/rune-dsl`, `finos/rune-common`, `finos/cdm-object-builder` — all Apache-2.0 |
| `finos/FDC3` (CSL-1.0, 275★) | `finos/FDC3-Sail`, `finos/fdc3-dotnet`, `finos/backplane` — all Apache-2.0 |
| `finos/ai-governance-framework` (CC-BY-4.0, 121★) | `finos/aigf-mcp-server` — Apache-2.0 |

**The generalisation, because it is not about FINOS.** In a standards
organisation **the repo with the stars is the standard and the repo with the
rights is the implementation**, and they are different repos with different
licences. Star count is a popularity signal for the *standard*, which is
exactly backwards as a dependency signal.

**Fourth check, for data repositories.** If the repository ships or produces
**data**, read the data licence separately. `opensanctions/opensanctions` is
MIT code producing **CC BY-NC 4.0** data with some third-party files its own
maintainers state they cannot license at all. An OSI badge on a data repository
describes the software that moves the data. See Pattern 20.

## Pattern 22 — Loss-reserving assurance with a three-language differential oracle

**Applies to:** P&C / general insurers and reinsurers, all regions. The method
is global; only the regulatory sign-off differs.

**Why this pattern is the strongest-shaped insurance engagement in this KB.**
Reserving is the rare insurance workload that is **arithmetic on a published
method**, not a private judgment. Given the same development triangle and the
same method — chain ladder, Bornhuetter-Ferguson, Cape Cod, Mack — the answer
is determined. That means, uniquely on this plane, **a free correctness
oracle exists**, and this KB's standing rule (pass 5: *check whether a second
permissive implementation exists before writing a validator*) is satisfied
three times over.

**The assets, and the licence split that must be settled before day one.**

| Role | Repo | Licence (read) | Note |
|---|---|---|---|
| Primary engine | https://github.com/casact/chainladder-python | **MPL-2.0** (373 L, 16,724 B) | Casualty Actuarial Society. Pushed 2026-11-23 |
| Oracle A | https://github.com/mages/ChainLadder | **GPL (>= 2)** via `DESCRIPTION`, no `LICENSE` file | R, on CRAN since 2008 |
| Oracle B | https://github.com/JuliaActuary/ChainLadder.jl | **MIT** | 6 stars, dormant since 2022 — use as a third opinion only |
| Cross-language harness | https://github.com/actuarialopensource/benchmarks | **MIT** (20 L, 1,087 B) | Exists expressly to compare implementations |
| ML reserving comparator | https://github.com/casact/tryangle | **MPL-2.0** | Automatic development-factor selection |
| Stochastic / Bayesian | https://github.com/casact/rp-bnn-claims | **MPL-2.0** | CAS research-paper code |
| Data model | https://github.com/casact/PCDM | **MPL-2.0** | Open P&C data model — the triangle's schema |
| Clean-licence fallback | https://github.com/casact/actsim | **Apache-2.0** (200 L, 11,341 B) | The only fully permissive `casact` repo |

**Step zero — settle MPL-2.0 with counsel, in writing, before any code.**
MPL-2.0 is **file-level** copyleft: shipping it inside a commercial deliverable
is permitted, and the obligation attaches only to the MPL-licensed files
themselves. **Architecture consequence, and it is mechanical: wrap, do not
patch.** Call `chainladder-python` across a process or module boundary, keep
every line of client logic in client-owned files, and the copyleft never
touches the client's IP. If counsel refuses MPL outright, the method is
*published* — reimplementing chain ladder is lawful, is roughly two weeks, and
Oracles A and B make it testable from the first commit. **Say the price out
loud rather than discovering it in month three.**

**The wiring.**

1. **Triangle extraction, deterministic.** Claims transactions from the
   carrier's PAS → development triangle, on the `casact/PCDM` schema. No model.
   Every cell traceable to the claim and transaction rows that produced it.
2. **The oracle gate, and this is the deliverable.** Run the *same* triangle
   through `chainladder-python` and through `mages/ChainLadder`, method by
   method, and **diff factor-by-factor and ultimate-by-ultimate**. Agreement to
   rounding is the pass condition. Wire it into CI on the carrier's own
   historical triangles. Disagreement is a bug in the pipeline, in the data, or
   in a method selection — all three are findings worth money.
3. **Diagnostics, deterministic.** Negative incrementals, triangle holes,
   late-reported distortion, tail factors outside a configured band, calendar
   effects. Rules, not a model, each with a named actuarial reference.
4. **Model only where judgment lives, and only with a citation.** Narrative
   drafting of the reserve memo, candidate explanations for diagnostic
   failures, and triage of which accident years need an actuary's attention.
   **The model must cite accident year, development period and method**, and a
   verifier drops any finding whose citation does not resolve to a triangle
   cell.
5. **The model never selects the booked reserve.** It proposes; the signing
   actuary selects. The reserve is a regulatory filing with personal
   professional liability attached — same posture this KB takes on Reg E clocks
   and procedural deadlines.
6. **Append-only log** keyed on valuation date, segment and method, holding the
   triangle hash, both engines' outputs, the diff, the diagnostics and the
   actuary's acceptance.

**Why this closes.** The week-one deliverable is **a number**: the count of
segments where two independent implementations of the same published method
disagree on the carrier's own historical data. That is measurable by
construction — the corollary pass 5 derived for format work applies here even
though this is a *method*, because the method is published and therefore
checkable. It funds the judgment layer from inside the engagement.

**What this pattern is not.** It is not reserve-setting automation, and it must
not be sold as one. It is assurance of the reserving *pipeline*.

---

## Pattern 23 — The insurance engagement: buy the format, adopt the method, build the judgment

**Applies to:** P&C, life and specialty carriers, all regions. **This pattern
exists to stop an architect applying Pattern 18 to insurance**, where it fails
for a reason no other plane in this KB shares.

**The failure this prevents.** Pattern 18 (statutory filing agent) and pass 5's
headline advice — *adopt the parser, build the decision* — both assume the
format layer is **free**, because a published format attracts permissive
implementations. On the insurance plane that assumption is false, and the
measurement is unambiguous:

| Check | Measured 2026-11-25 |
|---|---|
| `ACORD in:name,description`, by stars | 37 results; best relevant **8 stars**, no licence, last push 2017 |
| `AL3 insurance` | **0 results** |
| Why | ACORD gates Standards behind **membership and paid programmes** (EHR programme **$5,000/yr**; Forms licensed separately; terms dated 2025-10-27) |
| Permissive insurance core | `aposin/openinsuranceplatform`, Apache-2.0, 93★/34f — **last push 2019-11-27**. Consortium-built, abandoned |

**The third clause, which is what this pattern encodes:** open source follows
the file that more than one party must read **and whose specification can be
read without paying to join**. Insurance satisfies the first condition and
fails the second, so the population never forms.

**The gate — run these three checks before promising any format layer, on any
plane, in any industry.**

1. **Can you download the spec, today, without an account?** If not, the format
   layer is a **procurement line item**, not a sprint.
2. **Does a permissive implementation exist above ~50 stars with a push inside
   12 months?** If not, assume none is coming — a member-gated spec does not
   grow one.
3. **Has a consortium already tried?** Search the standards body's own GitHub
   org and read `pushed_at` and `archived`. A dead consortium repo is the
   cheapest due diligence available and it reframes the whole proposal.

**The corrected composition.**

| Layer | What goes here | Licence |
|---|---|---|
| System of record | The carrier's existing PAS. **Not replaced** — that is what `aposin` attempted | Commercial |
| Interchange | **ACORD membership.** Priced, scheduled, owned by the client | Commercial |
| Method | `casact/chainladder-python` (MPL-2.0), `lifelib` (MIT), `JuliaActuary/*` (MIT), `pyliferisk` (GPL — reference only) | MPL / MIT — **wrap, do not patch** |
| Correctness oracle | `mages/ChainLadder` + `actuarialopensource/benchmarks` | GPL / MIT — CI only, never shipped |
| Judgment | Built, client-owned. References in `agents/top.md` pass 7 | Client |
| Health / social protection schemes only | openIMIS — **AGPL-3.0 with a Swiss governing-law and Berne-forum rider** | AGPL + rider |

**Life vs P&C — a real procurement fork to put in front of the client.** A
**life** engagement can be executed **entirely under MIT** (`lifelib`, all of
`JuliaActuary`). A **P&C reserving** engagement cannot avoid MPL-2.0 without
reimplementing a published method. Two different conversations with counsel;
know which one you are in before the kickoff.

**The sales sentence that is true:** not "AI modernises your core insurance
platform" — the one consortium that tried that is seven years dead — but
**"your reserving pipeline gets a correctness oracle two independent
implementations agree on, and your actuaries keep the signature."**

---

## Pattern 24 — The licence probe, corrected twice (supersedes the Pattern 9 gate's licence step)

**Applies to:** every pass of every industry KB. Pattern 9 ships as an
executable gate in eight KBs; pass 5 corrected it from byte bands to line
counts, pass 6 corrected it to read the **title line**, and this pass adds two
cases that break it again. **Replace the licence step with the order below.**

**The order of operations — the title line is the authority, the line count
only corroborates.**

1. **Fetch**, trying these paths in order on
   `raw.githubusercontent.com/<slug>/HEAD/<path>`:
   `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENCE`, `LICENSE.rst`,
   `COPYING`, and — **added this pass** — `DESCRIPTION` for R/CRAN packages,
   where the grant lives in a `License:` metadata field and there is no licence
   file at all (`mages/ChainLadder`, 93 stars, `License: GPL (>= 2)`).
2. **Read the first non-empty line** and match it against the table.
3. **If the title line is not a recognised licence name, do not stop — grep the
   body for the grant clause.** *New cause this pass, the sixth:*
   `JuliaActuary/MortalityTables.jl` and `LifeContingencies.jl` report
   `NOASSERTION` because their licence files begin with the **project name**
   under a `====` underline, with plain MIT beneath. 81 stars of permissive code
   would otherwise be discarded. Known `NOASSERTION` causes now: a `.md`
   extension (`ledger/ledger`, 6,078★, BSD-3); a licence referenced rather than
   reproduced plus a rider (openIMIS); a project-name title line (this pass).
4. **Never let a body marker override the title line.** MPL-2.0 §1.12 defines
   "Secondary License" by naming the GNU GPL, LGPL **and AGPL**, so any
   precedence-ordered body grep reports MPL-2.0 as AGPL-3.0. This pass
   reproduced that failure on **nine** `casact` repositories after pass 6 had
   already documented it. It is settled: title line first.
5. **Use the line count only to decide whether to read the file.** It is stable
   *per rendering*, not per licence — MPL-2.0 measures **373 lines / 16,724 B**
   canonically (nine byte-identical readings this pass, zero dispersion) and
   **150 lines / 14,847 B** reflowed in `casact/raw_package`. Apache-2.0 showed
   the same split in pass 5 (201 vs 176 lines). **A count outside the table is a
   prompt to read, never grounds to downgrade an asset** — the expensive error
   is silently discarding a genuinely permissive asset.
6. **A licence badge with no file is `undetermined`, not `absent`.**
   `Systemorph/IFRS17CalculationEngine` reports MIT on the API while `LICENSE`
   and `LICENSE.md` 404 on both `main` and `master`.
7. **Never infer an org-wide licence.** `lifelib-dev/lifelib` is MIT;
   `lifelib-dev/lifelib-products`, pushed the same week, has **no licence
   file**. Probe every slug you intend to write.

**Line table, consolidated** (merging pass 6's and this pass's measurements):

| Licence | Lines | Bytes | Title-line marker |
|---|---|---|---|
| MIT | 19–23 | ~1,055–1,130 | `MIT License` / `The MIT License (MIT)` |
| MIT under a project-name header | 26 | ~1,349 | *project name* + `====`, grant in body |
| BSD-3-Clause | ~28 | ~1,500 | `Redistribution and use in source and binary forms` |
| QuickFIX Software License 1.0 | 45 | — | `The QuickFIX Software License, Version 1.0` |
| Community Specification License 1.0 | 99 | — | `# Community Specification License 1.0` |
| CC0-1.0 | 120 | 7,047 | `Creative Commons Legal Code` |
| MPL-2.0 (reflowed) | 150 | 14,847 | `Mozilla Public License` |
| Apache-2.0 without appendix | 176 | ~10,179 | `Apache License` |
| LGPL-3.0 | 187 | — | `GNU LESSER GENERAL PUBLIC LICENSE` |
| Apache-2.0 with appendix | 200–202 | 11,341–11,677 | `Apache License` + `APPENDIX: How to apply` |
| MPL-2.0 (canonical) | 373 | 16,724 | `Mozilla Public License Version 2.0` |
| CC-BY-4.0 | 395 | — | `Attribution 4.0 International` |
| LGPL-2.1 (as `.md`) | 503 | — | `GNU LESSER GENERAL PUBLIC LICENSE Version 2.1` |
| AGPL-3.0 | 660–661 | 34,522 | `GNU AFFERO GENERAL PUBLIC LICENSE` |
| GPL-3.0 | 673 | 35,130 | `GNU GENERAL PUBLIC LICENSE` |

**And the discovery rule that keeps paying, now five passes running:** when a
topic query returns nothing, **enumerate the organisation**. `org:moov-io` gave
60 repos in pass 5, `org:finos` 194 in pass 6, `org:casact` 45 in this one —
and in every case the topic query had already returned a false negative,
because a professional body names its code after the **agency**, the
**standard** or the **method**, never after the industry.

## Pattern 25 — Macro grounding that cannot state a figure without a key

**The problem this solves.** Any agent that touches credit provisioning,
stress testing, treasury forecasting or market commentary needs
authoritative macro series — unemployment, HICP, policy rates, FX. The failure
mode is not that the model fetches the wrong number; it is that **it states a
number with no resolvable provenance**, and a second line reviewer cannot
distinguish a fetched observation from a recalled one. Every figure in a
supervised institution needs to resolve to a publisher, a dataflow and a
period.

**The structural fix: make the key mandatory.** SDMX series are addressed by a
dataflow key, so an architecture that requires the key *before* the fetch makes
provenance a precondition rather than a prompt instruction.

**Wiring, concrete:**

1. **Metadata registry as the resolver.** Stand up the **Fusion Metadata
   Registry** (https://github.com/bis-med-it/FMR-releases, Apache-2.0, BIS) and
   load the data structure definitions, codelists and dataflows for the
   publishers in scope. This is the typed description of every series the
   engagement may cite.
2. **Resolution step, deterministic, no model.** The agent's request
   ("unemployment, Spain, monthly, seasonally adjusted") goes to a resolver
   that returns **an exact dataflow key or an error**. A natural-language
   phrase that does not resolve to a key is rejected here — it never reaches a
   fetch. The model may *propose* a phrase; it may not invent a key.
3. **Fetch over a permissive client.** `ondata/opensdmx`
   (https://github.com/ondata/opensdmx, MIT, 58★, any SDMX 2.1 REST API) or
   `bis-med-it/pysdmx` (https://github.com/bis-med-it/pysdmx, Apache-2.0,
   the BIS's own). Pin one; both are permissive, so the choice is engineering,
   not legal.
4. **Per-publisher access via the MCP layer**, where a server exists and is
   permissive: `ondata/istat_mcp_server` (MIT),
   `cyanheads/oecd-mcp-server` (Apache-2.0), `cyanheads/imf-mcp-server`
   (Apache-2.0, SDMX 3.0), `scka-de/ecb-mcp` (MIT),
   `Aryan-Jhaveri/mcp-statcan` (MIT),
   `felipegambettadesouza6-jpg/open-economics` (MIT, Brazil),
   `lzinga/us-gov-open-data-mcp` (MIT).
5. **Citation gate.** Every figure that reaches a human or a document carries
   `{publisher, dataflow key, period, retrieval timestamp}`. A verifier drops
   any claim whose key does not resolve against the registry — the same
   discipline Pattern 16 applies to account IDs and Pattern 17 to message
   fields.
6. **Analysis, if it is econometric, on a published reference.** For
   macroeconometric work use **MaRCo@BIS**
   (https://github.com/bis-med-it/marco-BIS, Apache-2.0, 89★) rather than
   writing the workflow: it already enforces human confirmation at model
   selection, variables, lags, identification and sample, states the source of
   each choice, and flags price puzzle, explosive root and weak instrument
   before results are reported. Its reference library carries **more than
   1,000 tests** and its replication suite is a command
   (`pytest tests/test_replications_smoke.py --runslow`).

**Do not use:** `hanlulong/openecon-data`, `daniel3303/Equibles` or
`stefanoamorelli/fred-mcp-server` as a dependency — all **AGPL-3.0**. They are
good reading for the aggregation design and bad choices for a client codebase.
`orhoncan/tuik-mcp` has **no licence file**; if Turkish data is in scope, write
the TÜİK client rather than adopting it.

**What you can say to a client, and it is true:** *"no figure appears in a
deliverable without a publisher, a dataflow key and a timestamp, and the
registry is what decides whether the key is real."*

**Operational caution:** MaRCo@BIS does **not** distribute the FRED data CSVs
(they are downloaded once, and the raw download needs metadata rows stripped
before the loader reads it), and the authors state it is **not tested on
macOS** — budget a container.

## Pattern 26 — SDMX 2.1→3.0 migration assurance with a differential oracle

**Why this pattern exists.** The measured installed base is **SDMX 2.1 at 59%,
2.0 at 35%, 3.0 at 6%** among central banks (SDMX Pulse, June 2026), with about
two thirds of the rest planning to migrate, against overall SDMX adoption of
roughly eight tenths (BIS IFC Report 17, February 2025). So the common client
situation is: **on 2.x, obliged to move, with no way to prove the move is
lossless.** That proof is the deliverable.

**This KB's standing rule applies first:** *check whether a second permissive
implementation exists before writing a validator.* On this plane it does —
which means the oracle is free.

**Wiring:**

1. **Two independent permissive readers of the same spec.**
   `ondata/opensdmx` (**MIT**, Python, 58★) and `bis-med-it/pysdmx`
   (**Apache-2.0**, Python, the standards-adjacent implementation).
   Licences are compatible, so both can sit in one test harness.
   Where a JVM/Excel path is in scope, `amattioc/SDMX`
   (https://github.com/amattioc/SDMX) is a third reader — but it is
   **EUPL-1.2 copyleft**, so it belongs in the *test* harness, isolated,
   never linked into the product.
2. **Differential read.** Feed both readers the same 2.1 payloads and diff the
   parsed result **observation by observation and attribute by attribute**.
   Disagreements are either a bug in one reader or an ambiguity in the client's
   data — both are findings worth money, and neither needs the regulator's
   validator to surface.
3. **Round-trip gate for the migration itself.** For each dataflow: read 2.1 →
   emit 3.0 → read 3.0 → compare against the original parse. **Series identity,
   observation values, periods and attribute completeness must match exactly.**
   This is the machine-checkable claim the migration is sold on.
4. **Structure first, data second.** Load the institution's DSDs and codelists
   into the **Fusion Metadata Registry** (Apache-2.0) and diff the 2.1 and 3.0
   structural representations before touching observations. Most migration
   surprises are structural — codelist cardinality, hierarchy, attribute
   attachment levels — and they are cheaper to find in metadata than in a
   billion observations.
5. **Model strictly outside the comparison.** The diff is arithmetic and
   deterministic. The model's only jobs are triaging the diff into
   human-readable classes and drafting the migration note, **obliged to cite
   dataflow key and observation period**; a finding whose citation does not
   resolve is dropped.
6. **Run it in CI over the extract**, not at submission time — the same
   placement Pattern 16 argues for the Metro 2 file.

**What this produces in week one:** a count of dataflows that round-trip
cleanly and a list of those that do not, with reasons. That is a number a CFO
can read and a supervisor can be shown, which is exactly the property pass 5
identified in format-layer work and could not find in judgment-layer work.

**Transfers to:** every format in this KB with two permissive implementations —
Metro 2 (`moov-io/metro2` Go vs `teamupstart/metro_2` Ruby), ISO 20022
(`moov-io/rtp20022` vs `prowide/prowide-iso20022`), EN 16931
(`josemmo/einvoicing` vs `num-num/ubl-invoice`), ACH (`moov-io/ach` vs
`RiverFinancial/nacha`).

## Pattern 27 — The per-publisher mesh: rebuild the aggregation, adopt the clients

**The decision this settles.** An engagement needs macro data from six
publishers. There is an off-the-shelf aggregator that already does all six —
and it is **AGPL-3.0** (`daniel3303/Equibles` 248★,
`hanlulong/openecon-data` 95★ with 330K indicators). Adopting it puts copyleft
in the client's data path; refusing it appears to mean building six
integrations.

**The measurement that makes the choice easy.** The per-publisher layer is
**already permissive and already written**: ISTAT, ECB, StatCan, Brazil and
US-gov servers are **MIT**; OECD and IMF are **Apache-2.0**. Seven of eight
single-institution servers carry a permissive licence. **The only thing the
AGPL projects add is the aggregation — a resolver, a normaliser and a cache.**
That is days of work, not months, and it is the part you want to own anyway
because it encodes the client's series taxonomy.

**Wiring:**

1. **Adopt, do not write, the publisher clients.** Permissive per-publisher MCP
   servers and SDMX clients as listed in Pattern 25 step 4, plus the R/Python
   clients where the analyst workflow is R: `rOpenGov/eurostat` (**BSD-2**),
   `ilostat/Rilostat` (**BSD-2**), `expersso/OECD` (**CC0**),
   `Eflores89/inegiR` and `banxicoR` (**CC0**, Mexico),
   `MattCowgill/readabs` (**MIT**, Australia), `UchidaMizuki/jpstat`
   (**MIT**, Japan).
2. **Check the manifest, not the badge, for every R component.** All seven of
   those were reported `NONE`/`NOASSERTION` by GitHub and resolve via
   `DESCRIPTION` to five different licences. Two of them are **copyleft** —
   `eblondel/rsdmx` is **GPL-2+** at 111★ and `eurostat/restatapi` is **EUPL** —
   so the most obvious R SDMX reader is the one you must not embed.
3. **Own the resolver.** One normalised series identity across publishers,
   backed by the Fusion Metadata Registry, with the client's own taxonomy. This
   is the asset; keep it.
4. **Cache with provenance.** Store `{publisher, dataflow key, period, value,
   retrieval timestamp}`. Never store a value without its key.
5. **Isolate anything reciprocal behind a process boundary**, per Pattern 18's
   rule for country-specific format libraries: EUPL and GPL components run as
   separate services or test-harness-only, never linked into the core.

**The sentence that wins the architecture review:** *"we adopted seven
permissively licensed publisher clients and built the one component that
encodes your series taxonomy — the aggregator we did not adopt is AGPL, and it
is also the only part that had to be yours."*

## Pattern 24 addendum (2026-11-25) — two more tiers and a marker-first rule

Pattern 24 corrected the licence probe twice (bytes → lines; `.md` variants).
Pass 8 breaks it twice more. **Apply these to the gate in all twelve industry
KBs:**

1. **Probe the package manifest, always, not only when no LICENSE is found.**
   R → `DESCRIPTION` (`License:`), Python → `pyproject.toml`/`setup.py`,
   Node → `package.json`, Rust → `Cargo.toml`, Java → `pom.xml`. Measured: **7
   of 7** R repositories reported `NONE`/`NOASSERTION` by GitHub resolved via
   `DESCRIPTION`, to **five distinct licences** spanning permissive, copyleft
   and public domain. A `LICENSE` file may exist and still name no licence —
   the CRAN stub (`YEAR:` / `COPYRIGHT HOLDER:`, 62 B) is a file that teaches
   you nothing, which is worse than no file.
2. **Accept the short-form grant.** A **14-line, ~648-byte** file reading
   `Copyright (c) YYYY, <holder>` + `licensed under the Apache License, Version
   2.0` + disclaimer **is a valid Apache-2.0 grant by incorporation**
   (`bis-med-it/pysdmx`, `bis-med-it/sdmx-rest4js`). A gate calibrated on
   175–201 lines rejects a clean institutional asset. Below-band now resolves
   to one of three outcomes: pointer to a fetchable full text, self-contained
   short grant, or a notice granting nothing.
3. **Marker first, length second — this is the hard one.** Probing
   `sdmx-twg/sdmx-rest` returned a **non-404 body of 44 lines / 1,522 bytes**
   that was **not a licence file at all**; direct re-fetch returned 404 on
   every licence name across `main`, `master` and `develop`. A length-based
   classifier would have recorded it. **Never measure a body until a licence
   marker has matched; "marker unknown" means re-fetch and read, never record.**

Line bands, consolidated (±1 line for trailing newline, measured across 14
files this pass): **MIT 20–21** · **Apache-2.0 short-form 14** ·
**Apache-2.0 no appendix 175–176** · **Apache-2.0 full 200–201** ·
**BSD-3 ~28** · **LGPL-3.0 187** · **EUPL-1.2 286** · **AGPL-3.0 660–661** ·
**GPL-3 ~674**.

Markers: MIT `Permission is hereby granted, free of charge` · Apache
`APPENDIX: How to apply the Apache License` (full) or `Apache License` (short
or no-appendix) · BSD `Redistribution and use in source and binary forms` ·
LGPL `GNU LESSER GENERAL PUBLIC LICENSE` · AGPL `GNU AFFERO GENERAL PUBLIC
LICENSE` · **EUPL `EUROPEAN UNION PUBLIC LICENCE`** · MPL `Mozilla Public
License` · **CC0 `CC0 1.0 Universal`**.

**And one existence rule, reconfirmed:** `gh api search/repositories` with
`q='repo:<slug>'` returned `total_count: 0` for `khaeru/sdmx`, a repository
`ls-remote` resolves and whose LICENSE fetches cleanly. **`ls-remote` is the
only existence oracle; `search/repositories` is a metadata channel that can be
silently incomplete.**

---

## Pattern 28 — XVA and valuation assurance with an independent differential oracle

**When to use it.** A bank or asset manager wants AI in the valuation or risk
function. This is the pattern to lead a **North American** engagement with,
because it is the one plane where the second line of defence already has a
framework to review it under (SR 26-2 / OCC 2026-13 covers valuation models;
it does **not** cover agentic workflows — see Trend 31).

**What you adopt, not build.**

| Layer | Component | Licence |
|---|---|---|
| Pricing core | `lballabio/QuantLib` | BSD-3-Clause |
| Language binding | `lballabio/QuantLib-SWIG` (pushed 2026-11-25) | same grant |
| Exposure / XVA / sensitivities | `OpenSourceRisk/Engine` (ORE), XML-configured | Modified BSD |
| **Independent cross-check** | `OpenGamma/Strata` (Java, **not** a QuantLib derivative) | Apache-2.0 |

**Explicitly excluded:** `FinancePy-Org/FinancePy` (3,239★, **GPL-3.0**) and
`frtb-net/FRTB` (**AGPL-3.0**). Both are the easiest thing to `pip install` in
their niche, and both are copyleft. Run Pattern 24's probe **before** the
prototype.

**The wiring.**

1. **Trade and market data** from the client's system of record into ORE's XML
   configuration — portfolio, netting sets, CSAs, scenario definitions. This is
   configuration, not code, which is what makes ORE a platform.
2. **Deterministic valuation** through QuantLib/ORE. No model in this path.
3. **The differential oracle.** For every instrument class both stacks cover,
   price it in **ORE and Strata** and diff. Independent implementations of the
   same published mathematics under compatible permissive licences give a free
   correctness oracle — the same construction as Pattern 16 (Metro 2) and
   Pattern 22 (loss reserving), now available in valuation for the first time.
   Set tolerances per instrument class and **fail the build on a breach**, not
   on a report.
4. **QuantLib's own regression suite as the floor.** It ships closed-form
   benchmarks; run them in CI on the client's build of the library, so a
   compiler or version change cannot silently move a number.
5. **The agent sits outside the pricing call.** It triages which trades moved
   and why, drafts the calibration commentary, explains sensitivities, and
   flags named pathologies — a calibration that failed to converge, a
   discounting curve with a negative forward, an instrument priced by a
   fallback engine. **Every claim must cite a trade id and a pricing engine
   name**, and a verifier drops any claim whose citation does not resolve.
6. **Human sign-off** before anything reaches a valuation committee, and an
   **append-only log** keyed by trade id and valuation date.

**What the model must never do:** choose the pricing engine, set a calibration
parameter, override a tolerance breach, or be in the code path that produces a
number that leaves the system. The model explains valuations; it does not
produce them.

**Why it closes.** The deliverable is a reconciled valuation with a documented
challenger implementation — which is precisely the artefact an independent
model validation function asks for, under guidance that already exists. It
produces a defensible number in week one, and the governance artefacts it
generates (differential benchmarking, reproducible suites, documented
challengers) are the same ones the client's later agentic work will need and
cannot yet justify on its own.

---

## Pattern 29 — The regulatory-capital engagement: the fixture IS the deliverable

**When to use it.** FRTB, SA-CCR, IFRS 9 / CECL, or any capital or provisioning
number. This pattern exists because the previous one does **not** transfer
here, and understanding why is the whole value.

**The measurement that defines the pattern.** Published formula (BCBS 279,
CRR2, FRTB standards), read by every bank in the jurisdiction, parsed not
queried — and the global permissive population is: `meenmo/ISDA_SIMM` (MIT,
32★), `henrik-lauritsen-ch/SACCR-BCBS279` (MIT, 2★), `danielep71/K-SACCR`
(MPL-2.0, 1★), `sa-ccr/SACCR` (**GPL-3.0**, 7★), `frtb-net/FRTB` (**AGPL-3.0**,
13★, the only FRTB calculator anywhere), and ISDA's own Apache-2.0 reference
implementation `Sleto/OpenSIMM`, **untouched since 2015-03-08**.

**Why: the formula is publishable and the fixture is not.** An FRTB charge
cannot be checked against a closed form — only against *this bank's trading
book under this regulator's national discretions*. No shared fixture can exist,
so no shared library accretes. (Trend 30, condition 3.)

**Therefore the engagement is inverted. Do not start with the calculator.**

1. **Deliverable one is the fixture**, and say so in the proposal: an agreed
   portfolio extract, a frozen market-data snapshot, a documented set of
   national discretions and model-approval boundaries, and a set of expected
   numbers signed off by the client's risk function. This is normally treated
   as preparation. **It is the asset**, it is what nobody can give the client
   off the shelf, and it is what every later number is judged against.
2. **Read, do not depend on, the permissive implementations.** `ISDA_SIMM`
   (MIT, 32★) is the best-shaped: lift its rule structure and test cases,
   reimplement against the client's product taxonomy. `SACCR-BCBS279` (MIT) and
   `K-SACCR` (MPL-2.0 — file-level copyleft, so keep it out of the core and
   behind a process boundary if used at all) are references for the add-on
   decomposition. **Do not link the GPL-3.0 or AGPL-3.0 ones into a hosted
   platform at all.**
3. **The capital calculation is deterministic code with a unit test and a named
   citation per rule** — the same construction Pattern 17 uses for Reg E
   clocks. A capital rule is arithmetic; the liability is total; the model has
   no place in it.
4. **The agent works on the inputs and the explanation, never the number:**
   reconciling the trade population against the source system, flagging
   positions whose risk-factor mapping is missing or ambiguous, explaining
   period-on-period movement by attributing it to named drivers, drafting the
   documentation pack. Each finding cites a trade id and a rule reference.
5. **Human sign-off, append-only log keyed by reporting date and legal entity.**

**The honest sentence for the client:** *"Nobody has an off-the-shelf capital
engine you can adopt — the one open implementation of FRTB in the world is
AGPL-licensed with thirteen stars, and ISDA's own reference implementation has
been abandoned for eleven years. What we build first is the thing that tells
you whether any engine is right."* That is a stronger position than claiming an
accelerator, and it is verifiable.

**Regional note:** this is the one plane where LATAM is **not** behind — the
global population is as thin as the regional one, so a Brazilian or Mexican
engagement starts level with a German one. The national discretions differ; the
absence of libraries does not.

---

## Pattern 30 — Corporate actions: bridge the closed format, build on the open one

**When to use it.** Custody, asset servicing, fund administration — anywhere
SWIFT MT564 corporate-action messages arrive and entitlements must be computed.

**The measurement that sets the architecture.** `iso15022 in:name` returns
**2 results**, both 0★, both unlicensed, one dead since **2017-02-09**. ISO
20022 has twelve Apache-2.0 libraries in `moov-io` alone. Both are multi-party
interchange formats. The difference is that ISO 20022's message definitions are
published and ISO 15022's MT definitions sit behind SWIFT's licensing — this
KB's clause 3, in its cleanest measurement.

**What open source actually did about it** — and it is the architecture,
handed over:

| Repo | Licence | What it is |
|---|---|---|
| `roberts-rudzitis/mt564-bridge` | MIT, 1★, 2026-11-01 | MT564 → ISO 20022 **`seev.031`** converter with **XSD validation** and conversion reports |
| `roberts-rudzitis/mt564-lens` | MIT, 1★, 2026-11-01 | Generator of **synthetic** MT564 messages — fixtures without a live SWIFT feed |

Both are single-author and three weeks old: **design references and prototype
seeds, not dependencies.**

**The wiring.**

1. **Treat MT564 as an inbound edge, not a domain model.** Convert at the
   boundary to `seev.031` and make the ISO 20022 form the only representation
   anything downstream reads. The target has a published schema, so every
   message can be XSD-validated in CI — a correctness gate the MT form cannot
   give you.
2. **Build your fixture corpus synthetically**, following `mt564-lens`. Real
   corporate-action traffic is client-identifying and usually cannot be
   redistributed even inside the client, which is why the open-source author
   wrote a generator rather than shipping samples. Cover the message's hard
   cases deliberately: mandatory vs voluntary events, multiple options,
   revisions and cancellations, fractional entitlements.
3. **Entitlement calculation is deterministic code** — ratio, rounding
   convention, record-date eligibility, tax withholding — with a unit test per
   event type and a citation to the event terms. **The model is not in this
   path.** Fractional-share rounding is arithmetic, and the error is a
   mis-paid client.
4. **The agent does the triage and the reading:** classifying inbound events,
   flagging messages that fail XSD validation or whose terms are internally
   inconsistent, comparing an event's terms against the issuer announcement and
   reporting discrepancies, drafting client notifications for human approval.
   Every claim cites a message reference and a field tag.
5. **Append-only log keyed by corporate-action reference and version**, because
   revisions are the common failure mode and the audit question is always
   "what did we know when we paid?"

**The sentence that sells it:** not *"AI automates corporate actions"* but
**"every inbound message is schema-validated before it reaches your
entitlement logic, every event revision is logged with what changed, and the
calculation that moves money is code with a test — not a model."**

---

## Pattern 31 — Credit scorecard assurance on a three-way differential oracle

**When to use it.** A lender asks for "an AI credit scorecard". **In most cases
the modelling layer is already built and permissively licensed, and proposing
to build it again is rework a reviewer will catch.** This pattern sells the
layer that is actually missing.

**What you adopt.** Three independent implementations of the same binning and
WOE mathematics, under compatible permissive licences:

| Component | Licence | ★ | Role |
|---|---|---|---|
| `guillermo-navas-palencia/optbinning` | Apache-2.0 | 538 | Optimal monotonic binning with constraints; batch and streaming; counterfactual explanations |
| `ShichenXie/scorecardpy` | MIT | 814 | End-to-end scorecard development |
| `amphibian-dev/toad` | MIT | 529 | Scorecard toolchain, feature selection |
| `itlubber/scorecardpipeline` | MIT | 266 | Pipeline modelling, rule mining, PMML export, Excel reporting |
| `eddyzzl/marvis-risk-agent` | MIT | 397 | **Design reference** for the agent surface: model development, validation, strategy workflows |

**The wiring.**

1. **Binning is computed by a library, never by the model.** Run the same
   feature set through `optbinning`, `scorecardpy` and `toad` and **diff the
   resulting bin edges and WOE values.** Three independent implementations of
   published mathematics give a differential oracle for free — the same
   construction as Patterns 16, 22, 26 and 28. Material disagreement on a
   feature is a signal about the *feature*, not about the libraries: it means
   the variable is unstable at the boundaries, and that is exactly what you
   want surfaced before the model is fit.
2. **Monotonicity and information value are the gate, and they are
   deterministic.** `optbinning` enforces monotonic constraints directly; make
   violation a build failure rather than a chart in a report. A scorecard that
   scores a worse borrower better is a fair-lending exposure, not a
   performance issue.
3. **Hold the oracle out properly.** Fit on train, select on validation, and
   keep a time-shifted out-of-time sample the agent never sees. A scorecard's
   oracle is only publishable because it is statistical — which means it is
   only valid if the holdout is genuinely held out.
4. **The agent's job is everything around the fit:** proposing candidate
   features with a stated rationale, explaining why a bin was merged, drafting
   the model development document, producing adverse-action reason codes from
   the WOE contributions, and monitoring drift per feature against the
   development sample. **Every claim cites a feature name and a bin index**;
   the verifier drops claims whose citation does not resolve.
5. **The model proposes, the constraint decides, the human signs.** No model
   output sets a cut-off, a bin edge, or an approval threshold.
6. **Append-only log keyed by model version and scoring date**, with the PMML
   export (`scorecardpipeline` produces one) as the immutable artefact of what
   was actually deployed.

**Regional note that changes the pitch.** Three of the four libraries are
**APAC-authored**, maintained, and widely used. In an APAC lending engagement,
the modelling stack is incumbent — **sell governance, drift monitoring,
adverse-action explanation and the supervisory evidence trail.** In North
America the same stack is adoptable but the regulatory frame is ECOA/Reg B
explainability, so lead with reason codes. In EMEA, `optbinning` is the local
asset and the frame is the AI Act's credit-scoring high-risk classification —
whose date this KB still has unresolved (2026-08-02 vs 2027-12-02).

---

## Pattern 24 addendum 2 (2026-11-25) — the licence probe, corrected a third time

Pattern 24 replaced byte bands with line counts after bytes misread
`moov-io/fincen`. **The line rule broke this pass on a larger asset, and a
second defect was found that no counting scheme can fix.** Both are
reproducible; both are now in the gate.

**Defect A — a contributor roster breaks the count.**
`lballabio/QuantLib`: licence at **`LICENSE.TXT`** (uppercase extension),
**239 lines / 8,960 B**, GitHub SPDX `NOASSERTION`. Published BSD-3 band ≈ 28
lines — **8.5× out**. Contents: 180 lines of contributor copyrights running to
`Copyright (C) 2026`, then attribution notes (Peter Jäckel's *Monte Carlo
Methods in Finance*, Argonne National Laboratory, the Joe–Kuo number sets),
then a verbatim three-clause BSD grant. **It is BSD-3-Clause**, and a
count-driven gate would have rejected a 7,804★ library.

**Defect B — a body grep for `GNU AFFERO` matches GPL-3.0.**
`FinancePy-Org/FinancePy` (3,239★): **673 lines / 35,148 B**, SPDX `GPL-3.0`,
title line `GNU GENERAL PUBLIC LICENSE` — and "GNU Affero General Public
License" appears at lines **552, 556 and 559**, because **GPL-3.0 §13 is titled
"Use with the GNU Affero General Public License."** Counts cannot separate
them: GPL-3 ≈ 673 lines, AGPL-3 ≈ 660, **13 apart**. Verified against a true
AGPL file — `Fincept-Corporation/FinceptTerminal`, title line `GNU AFFERO
GENERAL PUBLIC LICENSE`, 660 lines.

**This is the expensive confusion.** GPL-3.0 vs AGPL-3.0 is the difference
between shipping a modified binary with source and being obliged to publish
your source because you host the thing. Resolving AGPL as GPL creates an
unbudgeted obligation; resolving GPL as AGPL kills a usable asset.

**The corrected procedure.**

```bash
#!/bin/bash
# Pattern 24 licence probe, rev 3. Identify by TITLE LINE; counts only say "read it".
probe_licence() {
  local slug="$1" p out code body title lines
  # Filename tiers measured across nine passes of this KB:
  for p in LICENSE LICENSE.md LICENSE.txt LICENSE.TXT license license.txt \
           LICENCE LICENCE.md COPYING COPYING.txt NOTICE; do
    out=$(curl -s --max-time 25 -w '\n%{http_code}' \
          "https://raw.githubusercontent.com/$slug/HEAD/$p") || continue
    code=$(printf '%s' "$out" | tail -1)
    [ "$code" = "200" ] || continue
    body=$(printf '%s' "$out" | sed '$d')

    # 1. IDENTIFY: first non-blank line, whitespace stripped. This is the ruling.
    title=$(printf '%s' "$body" | grep -m1 -v '^[[:space:]]*$' | sed 's/^[[:space:]]*//;s/[[:space:]]*$//')
    lines=$(printf '%s' "$body" | wc -l)

    case "$title" in
      "GNU AFFERO GENERAL PUBLIC LICENSE") echo "$slug AGPL-3.0 COPYLEFT-NETWORK ($p, $lines L)"; return;;
      "GNU GENERAL PUBLIC LICENSE")        echo "$slug GPL-3.0 COPYLEFT ($p, $lines L)";        return;;
      "GNU LESSER GENERAL PUBLIC LICENSE") echo "$slug LGPL COPYLEFT-WEAK ($p, $lines L)";      return;;
      "Mozilla Public License"*)           echo "$slug MPL-2.0 COPYLEFT-FILE ($p, $lines L)";   return;;
      "Apache License")                    echo "$slug Apache-2.0 PERMISSIVE ($p, $lines L)";    return;;
      "MIT License")                       echo "$slug MIT PERMISSIVE ($p, $lines L)";           return;;
    esac

    # 2. FALL BACK to a body marker ONLY for licences with no title line.
    #    BSD has none at all; MIT's header is sometimes omitted.
    #    Read the TAIL: a roster sits at the top, the grant at the bottom.
    if printf '%s' "$body" | grep -q "Redistribution and use in source and binary forms"; then
      if printf '%s' "$body" | grep -q "Neither the name"; then
        echo "$slug BSD-3-Clause PERMISSIVE ($p, $lines L)"
      else
        echo "$slug BSD-2-Clause PERMISSIVE ($p, $lines L)"
      fi
      return
    fi
    printf '%s' "$body" | grep -q "Permission is hereby granted" && {
      echo "$slug MIT PERMISSIVE ($p, $lines L)"; return; }

    echo "$slug UNRESOLVED-READ-IT-BY-HAND ($p, $lines L, title='$title')"
    return
  done
  echo "$slug NO-LICENCE-FILE-AT-ANY-PROBED-PATH -- see absence rule below"
}
```

**Rules that go with it, and they are the part that matters more than the
script:**

- **Never grep the body for `AFFERO`.** GPL-3.0 §13 names it. Title line only.
- **Never treat a count as an identification.** A count out of band means
  *read the file*, in both directions: **below** band suggests truncation,
  **above** band suggests prepended text — a copyright roster, a preamble, or
  added terms that change the grant. Both must be read.
- **`wc -l` counts terminators**, so canonical Apache-2.0 reads **200 or 201**
  depending on the trailing newline. The band is 200–201.
- **Read the tail to confirm a BSD or MIT grant.** The roster is at the top.
- **Probe every filename tier.** Measured across nine passes: `LICENSE`,
  `LICENSE.md` (`ledger/ledger`), `LICENSE.txt` (Strata), **`LICENSE.TXT`**
  (QuantLib), **`license.txt`** (ORE), **`COPYING`** (`opencbdc-tx`), plus case
  variants. Three of these were added by this pass alone.
- **Absence is only measurable with a control.** A repo that keeps no files at
  the repository root (`OpenPeppol/peppol-bis-invoice-3`) returns 404 for
  every path, and `raw.githubusercontent.com` cannot distinguish "no licence"
  from "nothing at this path". Record **licence not determinable**, never
  "unlicensed", unless a control file in the same repo returned 200.
- **`NOASSERTION` is not a finding.** Five consecutive passes of this KB have
  resolved it to a real permissive grant — this pass: QuantLib (BSD-3 behind a
  roster), ORE (BSD at a lowercase filename), `opencbdc-tx` (MIT at `COPYING`).
- **A repo `search/repositories` refuses is not absent.** `OpenGamma` returns
  HTTP 422 for both `repo:` and `org:` queries while `ls-remote` resolves 3,029
  refs and the licence file serves canonical Apache-2.0. **`ls-remote` is the
  only existence oracle.**

**Where to run it:** on every candidate **before** the prototype, not after.
This pass found three high-traction copyleft assets sitting exactly where a
developer reaches first — `FinancePy` (3,239★, GPL-3.0, the easiest
`pip install` in derivatives pricing), `FinceptTerminal` (34,209★, AGPL-3.0)
and `frtb-net/FRTB` (the only FRTB calculator in existence, AGPL-3.0). Each
one is a week of rework if it is found at review instead of at selection.

**This script was executed, not just written.** Ten cases, including both
defects it exists to fix:

| Slug | Probe output | Why it is in the test set |
|---|---|---|
| `lballabio/QuantLib` | `BSD-3-Clause PERMISSIVE (LICENSE.TXT, 239 L)` | **Defect A** — 239 lines against a 28-line band, resolved correctly |
| `FinancePy-Org/FinancePy` | `GPL-3.0 COPYLEFT (LICENSE, 673 L)` | **Defect B** — body names Affero, title line rules it GPL |
| `Fincept-Corporation/FinceptTerminal` | `AGPL-3.0 COPYLEFT-NETWORK (LICENSE, 660 L)` | The true AGPL control for defect B |
| `OpenGamma/Strata` | `Apache-2.0 PERMISSIVE (LICENSE.txt, 201 L)` | Repo that `search/repositories` refuses with 422 |
| `OpenSourceRisk/Engine` | `BSD-3-Clause PERMISSIVE (license.txt, 29 L)` | All-lowercase filename tier |
| `mit-dci/opencbdc-tx` | `MIT PERMISSIVE (COPYING, 21 L)` | `COPYING` filename tier |
| `danielep71/K-SACCR` | `MPL-2.0 COPYLEFT-FILE (LICENSE, 372 L)` | File-level copyleft, correctly separated from the others |
| `NickCrews/mismo` | `LGPL COPYLEFT-WEAK (LICENSE.txt, 70 L)` | **70 lines, not the 187 this KB had recorded** — LGPL ships as a short additional-permissions grant over GPL as well as as full text, so the LGPL band is bimodal. The title line resolved it either way |
| `ShichenXie/scorecardpy` | `MIT PERMISSIVE (LICENSE, 20 L)` | MIT band is 20–21 lines (trailing newline) |
| `wilsonfreitas/awesome-quant` | `NO-LICENCE-FILE-AT-ANY-PROBED-PATH` | 30,903★ and genuinely unlicensed — the absence rule applies, and a control file is needed before calling it unlicensed rather than not determinable |

**Terminology note:** ORE describes its own licence as "Modified BSD" and the
probe returns `BSD-3-Clause`. These are the same grant — BSD with the
advertising clause removed. Both names appear in this KB; neither is an error.
