---
industry: financial
region: Global
updated: 2026-11-25
---

# Financial Services AI — Market Intelligence

> Researched 2026-11-09, re-verified and corrected 2026-11-21, **extended
> 2026-11-22**. Two corrections are flagged in place. (1) The EU AI Act
> high-risk deadline that the 2026-11-09 revision called "the strongest
> near-term regional play in this whole file" **has been deferred by 16 months**
> — see the EMEA section. (2) The 2026-11-21 conclusion that EMEA adoption
> figures **do not exist publicly** is withdrawn: they are published by
> supervisors rather than market researchers, and both the UK and euro-area
> numbers are now in the EMEA section. Canada, declared a twice-measured gap
> yesterday, is closed in the North America section and turns out to hold the
> strictest binding model-risk rule in the Americas.

## The one number that matters

The **2026 Global AI in Financial Services Report** — produced by the Cambridge
Centre for Alternative Finance with the BIS, IMF and World Economic Forum, and
the most rigorous source found in this pass (the rest of the field is vendor and
bank thought-leadership with self-reported figures) — puts:

- **81%** of surveyed financial firms adopting AI at some level
- **40%** reporting advanced adoption
- **52%** actively adopting *agentic* AI, but **fewer than a quarter** at
  advanced agentic maturity
- **Fintechs ahead of incumbents on agentic specifically: 57% vs 45%**
- **Four of the top five** financial-services AI use cases are **back-office**

That last point is the commercially useful one. The market narrative is
customer-facing agents; the actual spend is in the back office. A studio pitch
built on back-office reconciliation, audit and document work is pitching into
where the budget already is.

## Global players and positioning

| Player | Type | Position | Weakness to exploit |
|---|---|---|---|
| Accenture | Consultancy | Owns the 2026 "agentic money" narrative; pushes a dedicated **AgentOps** function for agent oversight | Framework-heavy and expensive; thin on open source build-out |
| Capgemini | Consultancy | World Cloud Report FS 2026 — found nearly half of banks and insurers creating roles to supervise AI agents | Same: diagnosis over delivery |
| Finastra | Core banking vendor | Argues modern cores with open APIs are a prerequisite for AI at scale | Proprietary core; the open-API argument is also the argument for Fineract |
| Oracle FS | Core banking vendor | Expects lightweight composable cores to make agent plug-in easier | Lock-in; composability pitched inside a closed stack |
| Backbase | Digital banking platform | Repositioned fully to AI in 2026, launched an "AI-native banking operating system" | A platform bet — a client wanting to own its IP needs an alternative |
| AI4Finance Foundation | Open source org | Stewards FinGPT / FinRL / FinRobot — the main open financial-agent lineage | Research-grade; no production hardening, no support contract |
| Tauric Research | Open source org | TradingAgents, **123,303 stars** (re-measured 2026-11-21) — the most-starred open financial agent framework | A simulation framework, not a deployable system |

**Globant's position:** the consultancies sell the governance framework and the
vendors sell the platform. The open gap is *delivery on permissively-licensed
foundations a client owns outright* — Fineract or TigerBeetle underneath,
verified MIT/Apache agents on top, AgentOps-grade audit trails built in because
the regulators now require them. That is a build practice, not a licence resale,
and it is what the repos in this KB are for.

## Opportunities by region

### North America

**Regulatory posture: permissive federally, active at state level.**

- Treasury, the Financial Services Sector Coordinating Council and the Cyber Risk
  Institute released a **voluntary** AI risk management framework in February
  2026, developed with input from 108 institutions. Comprehensive federal AI
  legislation for financial services is considered unlikely.
- **April 2026:** the FDIC, Federal Reserve and OCC issued revised model risk
  management guidance that **excludes generative and agentic AI from its scope**,
  on the grounds that those models are evolving too fast. This is a real opening
  and a real hazard — no model-risk ceiling, and no safe harbour either.
- The OCC's spring 2026 risk perspective explicitly supports genAI and agentic AI
  as a way to modernise and keep banks of all sizes competitive.
- **CFPB:** an April 2026 Regulation B final rule reportedly removes
  disparate-impact liability under ECOA — the fair-lending theory most often
  applied to AI credit models — while the duty to give **specific adverse-action
  reasons** remains. Explainability is still required; the discrimination
  exposure is reportedly reduced. Verify against the primary rule text before
  advising a client.
- **States are where the constraint lives.** Colorado's AI Act covers high-risk
  systems with a material effect on financial services, effective
  **June 30, 2026** (moved from an original February 2026 date — confirm current
  status).
- SEC FY2026 examination priorities and FINRA's 2026 oversight report both raise
  AI controls expectations.

- **Named deployments, from filings rather than press releases (new 2026-11-21):**
  bank holding companies including **Stifel** and **ServisFirst** have disclosed
  AI tools in production in **SEC filings**. Filing disclosure is a far better
  signal than a vendor case study, because it is made under liability.
- Treasury's February 2026 release included an **AI Lexicon** alongside the
  voluntary **FS AI RMF**, and participants in the Treasury/FSOC AI roundtables
  asked for **regulatory clarity and harmonisation** in order to scale adoption —
  i.e. the brake in North America is ambiguity, not prohibition.
- Treat the widely-republished forecast that "**over 70% of financial
  institutions will deploy agentic/autonomous AI decisioning by 2026**" as a
  **forecast, not a measurement**. It is cited to McKinsey and Accenture via
  intermediary blogs and conflicts with the CCAF survey's measured 52% adopting
  and under 25% at advanced maturity.

#### Canada — the twice-measured gap, closed 2026-11-22

The 2026-11-21 revision recorded Canada as a **twice-measured gap** and
prescribed the fix: "OSFI should be targeted directly by name in a future pass
rather than through regional queries, which is what has failed twice." That was
done this pass and it worked immediately. The gap was never about Canada being
quiet; it was about the query.

- **Guideline E-23 (Model Risk Management) takes effect 1 May 2027** and
  extends model-risk requirements to **every AI and machine-learning model** at
  federally regulated financial institutions, **including vendor-supplied
  models**. Reported requirements: an enterprise-wide model inventory,
  risk-based governance, lifecycle documentation and validation, and oversight
  of third-party models. Published 11 September 2025.
- **Guideline B-10 (Third-Party Risk)** applies when an institution brings in
  external AI services, so outsourcing cannot be used to thin out risk
  management or resilience.
- **A Technology Risk Bulletin on "Generative and Agentic Artificial
  Intelligence: Implications for Technology, Cyber Security, and Operational
  Resilience"** was issued in **July 2026**. It is supervisory guidance rather
  than a new binding guideline: it maps existing obligations (B-13, E-21, B-10,
  with model risk pointed at E-23) onto AI-specific scenarios, and it asks
  institutions to **treat AI outputs as decision inputs, keep human oversight
  for high-impact decisions, and apply approval checkpoints before high-impact
  actions**.
- OSFI's semi-annual risk outlook now treats **frontier AI as a growing source
  of cyber, third-party and reputational risk** while describing the system as
  resilient, and the regulator is reported to be weighing whether Canada's
  financial system needs an **AI safety code** setting a minimum safety level
  across supervised institutions. Commentary also expects more aggressive use of
  administrative monetary penalties in 2026.
- One secondary reading worth checking against the text: E-23 reportedly avoids
  the term "agentic AI" and uses **"autonomous decision making"** and
  **"autonomous re-parametrization"** instead. If accurate, keyword searches for
  "agentic" against Canadian rules will return a false negative — the same
  vocabulary failure that hid Tazama from this KB for three passes.

**Sourcing caveat, stated because it matters for advice.** Everything above is
from law-firm, consultancy and vendor commentary; **OSFI's own pages did not
appear in the results**, and this environment cannot reach many primary hosts
(see the EMEA note below). The dates and the 1 May 2027 effective date are
consistent across independent sources; verify against osfi-bsif.gc.ca before
putting any of it in a client deliverable.

**The consequence is the most useful thing in this section.** The North
American regulatory border now runs straight through model risk, and the two
sides moved in opposite directions in the same year:

| | United States | Canada |
|---|---|---|
| Model-risk instrument | SR 26-2 / OCC Bulletin 2026-13, 17 April 2026 | Guideline E-23, effective 1 May 2027 |
| Generative and agentic AI | **Excluded from scope** | **In scope** — all AI/ML models, including vendor models |
| Agent-specific supervisory text | None | Technology Risk Bulletin, July 2026 |
| Practical effect | No examiner playbook to inherit, no safe harbour | A dated, binding programme with 17 months to run |

A North American client with operations on both sides of the border cannot run
one model-governance programme and call it done — and the Canadian requirement
is the stricter one, so **building to E-23 satisfies both**. That is a concrete,
schedulable, fundable engagement with a date attached, and it is the only one in
North America that has a date at all.

**Opportunity:** adverse-action reason generation that is defensible to an
examiner — the ECOA duty survives even where disparate-impact liability does not.
A 50-state patchwork also makes jurisdiction-aware model governance a sellable
product in itself. And because SR 26-2 and OCC Bulletin 2026-13 (17 April 2026)
put generative and agentic AI **outside** model-risk guidance, there is no
examiner playbook to inherit — a bank that writes its own defensible agent
control framework now is setting the de facto standard rather than complying
with one.

#### Pass 4 (2026-11-22) — the deadline that moved, and the controls the banks wrote

**A market-infrastructure deadline is not a durable fact either.** Pass 2 of
this KB established that rule for *regulatory* dates, after finding its own
headline recommendation built on an EU AI Act date that had been deferred. The
same failure mode has now been measured on a **payments-infrastructure** date,
which generalises the rule beyond regulation:

| Milestone | Status as measured 2026-11-22 |
|---|---|
| SWIFT CBPR+ MT/MX coexistence ends | **Ended 22 November 2025** — a year ago today. Durable, passed, irreversible |
| Fedwire Funds Service ISO 20022 cutover | **Done, 14 July 2025**, single-day cutover |
| Fedwire structured/hybrid postal address release | **Deferred on 27 August 2026 to November 2027** |
| SWIFT SR2026 payment changes (incl. removal of unstructured addresses) | **Deferred 27 August 2026**; no replacement date published as of this pass |

**Many secondary sources still print 14, 16 or 23 November 2026 as live
deadlines — that is, this very week.** They predate the August deferral. A
pitch whose urgency rests on "the deadline is days away" will be corrected by
the client's own payments team.

The durable commercial leg is the opposite one: **coexistence already ended a
year ago**, so institutions are live on ISO 20022 for cross-border payments and
are now in the phase the BIS CPMI brief (April 2026) calls post-migration
*stability, reconciliation and governance* — which is data-quality and
exceptions work, not a cutover project. That is a better-funded and longer
engagement than a deadline scramble, and it does not evaporate when a date
moves.

**Verification note:** `www.frbservices.org` does not resolve in this
environment, so the Fedwire deferral rests on secondary sources that agree with
each other but conflict on the exact 2027 day (22 November 2027 in one, aligned
to Swift's then-planned 23 November 2026 date in another). **Confirm against the
Federal Reserve's own notice before putting a date in a client document.** This
is the second host-level research gap recorded for this KB, after
`bankofengland.co.uk` in pass 3.

**FINOS Common Controls for AI Services** — backed by Citigroup, Morgan Stanley
and Bank of America — is the North American governance artefact this KB had
missed entirely. Full write-up in `verticals/solutions.md`. It matters most here
because **SR 26-2 and OCC Bulletin 2026-13 (17 April 2026) place generative and
agentic AI outside existing model-risk guidance**: there is no examiner playbook
to inherit, and a peer-authored control catalogue is the strongest available
substitute.

**CCAF 2026 (628 institutions, vendors and regulators, 151 jurisdictions)** —
the most rigorous figures available this pass, and they point at operations:
81% adopting AI at some level, 40% advanced, fintechs ahead of incumbents 47% to
30%, **four of the top five use cases back-office**, data privacy the top
perceived risk at 73%, and 76% of large institutions finding AI value hard to
measure. That last number is the one to sell against: **a reconciliation or
screening build has a measurable baseline**, which is precisely what the
institutions say they are missing.


#### Pass 5 (2026-11-22) — the filing plane, and Canada closed with a parser

**The opportunity shape this region offers that no other does: three statutory
filings with permissive open-source libraries already written.**

| Obligation | Who it binds | Library | Licence |
|---|---|---|---|
| Metro 2 consumer credit reporting | every US lender reporting to Equifax / Experian / TransUnion | `moov-io/metro2` (130★), `teamupstart/metro_2` (23★) | Apache-2.0, MIT |
| FinCEN BSA E-Filing — SAR, CTR | every US bank, MSB and broker-dealer | `moov-io/fincen` (36★) | Apache-2.0 |
| Reg E §1005.11 dispute clocks | every US consumer account issuer | `dleonard-data/reg-e-timing` (1★) | MIT |

Metro 2 is the one to lead with. **FCRA accuracy liability attaches to the
contents of that file**, it is produced monthly by every lender, the format is
published, and two independently-written permissive implementations exist in
different languages — which means a differential conformance harness is
available at no cost (see `verticals/solutions.md`). An engagement that offers
a client evidence their bureau file is correct is selling against a liability
they already carry, not against a competitor.

Reg E is the opposite scale and still worth naming: §1005.11 is a set of
**deterministic clocks** — provisional credit, investigation windows — and
`reg-e-timing` expresses them as institution-configurable testable code. One
star. It is a design reference, not a dependency. The legal KB reached the
identical conclusion about court-deadline calculation: *the deadline is the
first thing an agent should be trusted with and the last thing it should
decide, because the rule is arithmetic and the liability is total.*

**Canada — the twice-measured gap, now closed, and the method was wrong not
the search.** Two previous passes searched Canada by region and OSFI by name
and returned effectively nothing. The Canadian asset is `moov-io/cadeft`
(Apache-2.0, 11★, pushed 2026-11-20): a parser for **CPA-005, the 1464-byte
Canadian Payments Association EFT file** that carries every Canadian direct
deposit and pre-authorised debit. At 11 stars it is invisible to any regional
or thematic query. It was found by enumerating an organisation the KB already
cited for seven other repos.

> **Method, generalisable to all twelve KBs:** when a region has returned
> nothing twice, stop querying by region and enumerate the organisations the
> KB already trusts. National payment and filing formats are maintained by
> whoever maintains the other national formats — not by someone who tags a
> repo with the country name.

**Context, all secondary sources, read accordingly.** The Cambridge CCAF 2026
report has regulators well behind industry on AI adoption (only ~20% of
regulators at advanced adoption against 40% of firms). Baker McKenzie expects
deregulation to gain momentum in 2026, led by the US — which, combined with
the SR 26-2 / OCC Bulletin 2026-13 position already recorded above (genAI and
agentic placed *outside* model risk guidance), keeps the conclusion this KB
already drew: **there is no examiner playbook to inherit, so whoever writes a
defensible agent control framework sets the de facto standard.** Industry is
moving on that: Citigroup, Morgan Stanley and Bank of America are reported to
back a *Common Controls for AI Services* initiative aiming at vendor-neutral
controls — reported in trade coverage, **not verified against a primary
source, do not cite to a client without checking.** Bank of America's CashPro
Chat is the most-cited named deployment.


#### Pass 6 (2026-11-25) — the examiner wrote a framework, and the capital-markets plane is closed to open source

**New supervisory artefacts, all 2026, none of them a deadline.**

| Artefact | Date | What it does | Status |
|---|---|---|---|
| SR 26-2 (Fed / OCC / FDIC) | Apr 2026 | Replaced prior model-risk guidance. **Expressly excludes generative and agentic AI** | In force |
| CSBS examination framework | Sep 2026 | Governance, **AI inventories**, three-tier risk classification | Published, examination-focused |
| Treasury sector framework | Feb 2026 | Described as the first federal, sector-specific AI governance toolkit for financial services | Published |
| NAIC model AI bulletin | ongoing | Adopted by **27 states + DC + Puerto Rico**; broader adoption on the Nov 2026 agenda | State-by-state |
| NY DFS cybersecurity rules | in force | Reaches AI through risk assessment and third-party oversight, without naming AI | In force |

The structural fact pass 5 recorded — genAI and agentic AI sit **outside** the
model-risk guidance — is confirmed and the mechanism is now visible: secondary
sources report examiners filling that gap **through direct supervisory
engagement** rather than through published rules. For an engagement that means
there is no examiner manual to inherit and no safe-harbour to point at, but
there *is* an examination framework with named components.

**The deliverable this names itself.** CSBS examines for an **AI inventory**
and a **three-tier risk classification**. Those are artefacts, not postures: a
complete register of AI in use, each item classified, each classification
evidenced. A bank that cannot produce one in an examination has a finding
regardless of how good its models are. This is week-one, defensible-number
work of exactly the shape pass 5 identified as the way to fund the judgement
layer.

**Two dates this KB must NOT build on, and saying so is the point.**

- **Colorado AI Act** — the effective date is *inconsistent across sources*:
  one says 1 Feb 2026, another 30 Jun 2026, a third that it was "slated to
  originally take effect in February 2026". That pattern means it moved, and
  pass 4 of this KB already published a headline recommendation on a date that
  moved. **Verify against the statute before it appears in any client
  material.** Not recorded here as a fact.
- **CFPB Regulation B disparate-impact amendments** — reported final April
  2026 and **under legal challenge**. A credit-model engagement should be
  designed to satisfy the underlying fair-lending obligation, which is not in
  doubt, rather than the amendment's specific text, which is.

**Capital markets: the one plane in NA where the usual advice inverts.**
CAT reporting returns **zero** open-source results; Form PF and N-PORT return
hundreds of results containing no financial filing library at all (see the
false-abundance table in `agents/top.md`). This is not a gap to fill. These are
one-way submissions to a regulator that does not republish the data, and the
reporting layer is sold by the client's existing vendor.

The NA capital-markets opportunity is therefore **beside the submission, not
inside it**: pre-submission reconciliation of the report against the firm's own
books, and post-submission reconciliation of acknowledgements and rejections
back against the trade store. Reportable-accuracy exposure is where the fines
land, and neither side of that is vendor territory.

**One NA-placed permissive asset worth naming:**
`finos/open-reg-tech-us-lcr` (Apache-2.0, 17★) expresses the **US Liquidity
Coverage Ratio as executable code**. Forks (23) exceed stars (17) — the
signature of a reference people adapt rather than import. Use it that way.
#### Pass 7 (2026-11-25) — the insurance supervisor asks for a programme, and the actuarial profession's code is American

**The insurance instrument, and it is an inventory not a threshold.** The
**NAIC Model AI Bulletin** is the operative US framework for insurers. It
expects a **written AI programme** covering governance, risk management,
internal controls and **third-party AI**, for any AI system that makes or
supports a regulated decision. Adoption is state by state and **the counts in
circulation conflict**: 23 states + DC by early 2026 (one source), 25 by July
2026 (another), 27 + DC + Puerto Rico as of 2026-10-08 (a tracker). **None is
confirmed against the NAIC itself.** For a client proposal, the number of
states is the wrong anchor anyway — the deliverable is identical in all of
them.

**Banking, corroborated not re-reported.** OCC Bulletin **2026-54**
(2026-11-04), the first federal **examiner** framework for AI, and OCC
**2026-13** (April 2026), the revised interagency model-risk guidance replacing
SR 11-7 with **generative and agentic AI expressly out of scope**, both
reappeared on an independent research path this pass. Pass 6 recorded them;
this is second-source confirmation, not new intelligence. Treasury's **FS AI
RMF and AI Lexicon** (Feb 2026) remain voluntary and NIST-aligned.

**State legislatures are now the moving part for insurers.** A New Jersey
Assembly committee advanced a bill that would **restrict certain AI uses in
denying homeowners, auto and flood claims** (trade press; bill status not
verified at source). This is the shape to watch in NA: not a federal AI rule,
but **line-of-business-specific limits on automated denial**, state by state.
It pairs with the consumer finding in `intel/trends.md` — only ~5% would accept
an AI claim decision without human review. **Straight-through denial is being
closed off legally and commercially at the same time.**

**NA is where the actuarial code lives, and this is the region's real asset.**
The **Casualty Actuarial Society** (`casact`, 45 repos) is a US professional
body and it maintains the reference loss-reserving implementation —
`casact/chainladder-python`, **MPL-2.0**, 292★, pushed 2026-11-23 — plus
`PCDM`, an open **Property & Casualty Data Model**. `actuarialopensource`
(benchmarks, MIT) is the same community. **So for a US P&C carrier the method
layer is not an import: it is maintained by the body their own actuaries belong
to**, which removes the usual objection that open source has no professional
standing. That is a materially easier conversation than any other plane in this
KB offers, and it should lead a US insurance pitch.

**The licence caveat that must travel with it:** MPL-2.0, not MIT. See Pattern
23 for the wrap-don't-patch posture and the life-vs-P&C procurement fork.

#### Pass 8 (2026-11-25) — the Fed signalled a third instrument, and Canada closed for the third time by not being searched for

**The regulatory picture gains a pending item, not a new deadline.** Pass 6
recorded OCC Bulletin **2026-54** (2026-11-04), the first federal *examiner*
framework for AI, filling the gap that **OCC 2026-13 / SR 26-2 / FIL-15-2026**
(April 2026) left when they replaced SR 11-7 and left generative and agentic AI
outside scope. New this pass, and genuinely additive:

- **The Federal Reserve has announced plans to issue a request for information
  on model risk management as it relates to banks' use of AI.**
- **Vice Chair for Supervision Michelle Bowman has called for a review of
  whether existing AI supervisory guidance is still fit for purpose.**

Both are **secondary-sourced** (law-firm commentary; no primary Fed document
was read this pass) and both are **signals, not obligations** — there is no
date and no requirement. The reason to record them: an RFI is the stage at
which an institution's own control framework can become an *input* to the
rule rather than a response to it. Pass 6's NA recommendation — write the
control framework first, because whoever writes a defensible one sets the de
facto standard — now has a named mechanism to aim at. That is the pitch: the
client's framework, documented, submitted.

**Canada: closed a third time, and a third time not by a regional query.**
Pass 5 closed the twice-measured Canada gap with `moov-io/cadeft` (Apache-2.0,
11★, CPA-005 parser), found by enumerating an org the KB already cited. This
pass adds the statistical side:

| Asset | Repo | Licence (verified) | ★ | Push |
|---|---|---|---|---|
| Statistics Canada, 7,000+ series | https://github.com/Aryan-Jhaveri/mcp-statcan | MIT (20 lines) | 8 | 2026-11-06 |
| 40+ US government data APIs | https://github.com/lzinga/us-gov-open-data-mcp | MIT (20 lines) | 113 | 2026-11-02 |
| FRED (Federal Reserve Economic Data) | https://github.com/stefanoamorelli/fred-mcp-server | **AGPL-3.0** (660 lines) | 135 | 2026-08-22 |

`mcp-statcan` was **not** found by searching for Canada. It surfaced from a
census of `mcp sdmx` — a query naming a format and a protocol, with no country
in it. **Pass 5's rule now holds three times: when a region has returned
nothing, stop querying the region.** Census the format, the protocol or the
organisation instead. A national statistical client is built by someone
interested in statistics, not by someone tagging their repo with a country.

**The licence split matters here more than elsewhere**, because FRED is the
series set a US engagement reaches for first and **`fred-mcp-server` is
AGPL-3.0**. The permissive route to the same data is
`lzinga/us-gov-open-data-mcp` (MIT) or a direct client; see Pattern 27.

**NA statistical gap, measured and left open:** no permissive MCP server or
SDMX client surfaced for the **Federal Reserve Board's own** data services
(H.15, Z.1) distinct from FRED, nor for **OSFI** or the **Bank of Canada**.
Searched via `mcp fred`, `mcp sdmx` and `sdmx`; not found. Stated as an
informed gap.

### EMEA

**Regulatory posture: the most demanding in the world, with a hard date.**

- **CORRECTION (2026-11-21): the Annex III high-risk deadline is 2 December
  2027, not 2 August 2026.** The **Digital Omnibus, Regulation (EU) 2026/1744**,
  deferred stand-alone Annex III obligations — which explicitly cover
  **creditworthiness assessment and credit scoring** and **life and health
  insurance underwriting** — to **2 December 2027**. Annex I embedded systems
  move to **2 August 2028**. The prior revision of this file stated 2 August
  2026 as a hard, non-negotiable date and built its headline recommendation on
  it; that date is no longer operative. This correction is corroborated across
  the gaming, enterprise and legal KBs in this family, which recorded the same
  post-Omnibus timeline independently.
- **What did *not* move, and is therefore what you can actually sell against:**
  **Article 50 transparency obligations have been in force since 2 August 2026**,
  the **2 December 2026 watermarking deadline stands** (eleven days away), and
  the new prohibitions remain on their own track. Legacy systems placed on the
  market before the new dates are caught only if **substantially modified**
  afterwards — which makes "is this change substantial?" a live advisory
  question right now.
  (Vendor blogs also list fraud detection as high-risk; that is a vendor claim,
  not an Annex III item.)
- **DORA** has been in force since **17 January 2025** and treats AI systems and
  AI vendors as ICT assets and services under its risk, incident-reporting and
  third-party rules. The two regimes are complementary: DORA covers ICT risk and
  resilience testing, the AI Act adds risk classification, conformity assessment,
  transparency and human oversight.
- **GDPR Article 22** on solely automated decisions still applies, and the recast
  **Consumer Credit Directive** covers automated creditworthiness assessment from
  **20 November 2026**.
- DORA imposes **no blanket EU-residency requirement** on ICT third parties.
  Vendors pushing on-premise AI as a compliance necessity are selling a
  commercial angle, not a legal one — worth knowing when a client has been told
  otherwise.
- **The designated critical ICT third-party providers are now named.** The first
  DORA list, published **18 November 2025**, names **19 providers**, including
  **Accenture, Amazon Web Services EMEA, Bloomberg, Capgemini, Deutsche Telekom,
  Google Cloud EMEA and IBM**. Two consequences: the model and cloud providers
  under a bank's agent stack are directly supervised entities, and **two of the
  consultancies in the players table above are themselves on that list** — which
  is a conflict a client can be walked through.
- **Supervisor-level signals:** Germany's **BaFin** issued non-binding guidance
  in **January 2026** placing AI inside DORA-compliant ICT risk frameworks.
  **AI Act Article 9(10)** expressly permits integrating AI risk management into
  existing DORA ICT procedures, and the Act grants derogations where equivalent
  financial-services requirements already exist — so the compliance work
  consolidates rather than doubling. For high-risk AI in finance the **national
  financial supervisor is generally the market surveillance authority**.

#### EMEA adoption numbers — the "does not exist publicly" gap, closed 2026-11-22

The 2026-11-21 revision closed with: *"Four searches across two passes have
produced regulation in depth and no reliable EMEA-specific adoption statistics…
An informed gap: the EMEA adoption number does not appear to exist publicly at
region-segmented granularity."* **That conclusion was wrong, and the correction
is instructive: the numbers are published by supervisors, not by market
researchers, so a market-research query will never find them.**

**United Kingdom — Bank of England / FCA, *Artificial intelligence in UK
financial services 2026*, published 26 October 2026.** The third edition of a
survey that is the single best region-segmented AI dataset in this file:

| Measure | 2026 | Prior |
|---|---|---|
| Firms using AI | **86%** | 75% (2024 survey) |
| Respondents | 196 total; 105 on the full questionnaire | — |
| Firms with **AI agents in production** | **~80%** (of full-survey respondents), mostly decision support | not asked in 2024 |
| Agents running with **broad autonomy** | **~2%** | — |
| Generative AI as a share of reported AI systems | **56%** | 17% foundation models (2024) |
| Firms with firm-wide AI policies | 94% (full-survey) | — |
| Firms with centralised AI/model-risk governance forums | 84% | — |
| Citing information security and operational resilience as the main third-party AI obstacle | 40% | — |

Two figures that look like the headline but are not: among short-form
respondents the adoption figure is **73%**, and for small firms specifically it
is also **73%**. Quoting 86% at a small firm overstates its peer group by 13
points. Sources also disagree on two secondary figures — "every responding UK
and international bank uses AI, 93% of insurers", and third-party share of key
systems at 53% — which are recorded here as **unconfirmed**.

**Euro area — ECB.** A February 2026 ECB Banking Supervision speech states that
**more than 85% of significant institutions already use AI in some form**, with
adoption rising year on year. The **November 2026 Financial Stability Review**
adds the maturity split: euro-area banks have moved from experimentation to
operational deployment, mostly generative AI, while **agentic AI remains
largely at pilot or planning stage**, with banks naming autonomy, model drift
and lack of explainability of *actions* as the distinctly agentic risks. The
ECB's Supervisory Board is reported to have asked significant institutions for
an **action plan on AI-related risk by 31 October 2026** — a dated supervisory
demand that has already fallen due.

**EBA / operational resilience.** The share of banks reporting no attack that
resulted in, or could have resulted in, a major ICT incident **rose to 56% in
H1 2026 from 49%** in the previous half; roughly **one in five bank cyber
incidents originates at a third-party provider**. That second number is the
DORA third-party argument in one statistic, and it is a supervisor's number
rather than a vendor's.

**Why this is better evidence than the global survey.** Three independent
supervisory sources in two jurisdictions converge on the same picture: adoption
**85–86%**, agents widely present but **~2% autonomous**, third parties as the
binding constraint. The UK 86% and the euro-area 85% are measured on different
populations and agree anyway.

**Measurement caveat, declared.** `bankofengland.co.uk` **does not resolve from
this environment** — it is outside the session's allowed network domains — so
the primary PDF could not be opened. Every figure above is from secondary
reporting, four independent outlets agreeing on the headline numbers. This is a
**declared gap, not a primary verification**, and it should be re-run from a
session that can reach the primary host before any figure is put in front of a
client.

**Opportunity, restated after the deferral.** The honest read is that the
time-boxed compliance scramble this file previously sold has been pushed to
**2 December 2027**, and some of that budget has moved with it. What replaces it
is better qualified, not weaker:

1. **The recast Consumer Credit Directive came into application on
   20 November 2026 — yesterday.** It covers automated creditworthiness
   assessment and it is live *now*, while the AI Act's credit-scoring
   obligations are not. For a lender client this is the binding instrument on
   the table today, and it is the one to lead with.
2. **Article 50 transparency (in force since 2 August 2026) and the
   2 December 2026 watermarking deadline** are immediate and unmoved.
3. **The deferral itself is sellable as runway.** Annex III conformity work for
   credit scoring is now a 12-month programme that can be done properly —
   technical documentation, conformity assessment, post-market monitoring —
   rather than a scramble. Clients who were told "August 2026 or else" have been
   mis-sold a deadline and will need the schedule rebuilt. **Go and tell them
   the date moved**: it is the most useful call anyone will make to a European
   head of credit risk this quarter, and it is a credible opening precisely
   because it costs the client nothing.
4. **DORA is the part with no deferral at all** — in force since January 2025,
   with named supervised providers. Per-decision audit trails for agent actions
   are a DORA deliverable regardless of what the AI Act does.

#### Pass 4 (2026-11-22) — an obligation in force with two zero-star repos against it

**Verification of Payee is the clearest open opportunity in this file.** Under
the Instant Payments Regulation, VoP has been **mandatory for euro-area payment
service providers since 9 October 2025**, on standard *and* instant transfers,
with the name-match returned inside a **five-second** budget. The Eurosystem's
own service builds on solutions developed by **Banco de Portugal and Latvijas
Banka**, aligned to the European Payments Council's VOP scheme.

Open source against that obligation, measured this pass:
`verification of payee VoP SEPA` → **`total_count: 2` worldwide**, both zero
stars (`softvasco/payee-match`, MIT, pushed 2026-11-21;
`untitledfinancial/dpx-compliance-public`, BSD-3-Clause).

A legally mandated, latency-bounded, name-matching problem — *explainable
fuzzy matching*, which is squarely an AI engagement — with essentially no
open supply. Compare the AML gap that took three passes to close and turned out
to be a vocabulary artefact: this one was tested under the standard's own name,
the scheme's name and the abbreviation, and it holds.

**Dates to handle with care.** Sources conflict on the non-euro-area extension:
the ECB gives **9 July 2027** for VoP in non-euro Member States (and 9 January
2027 for receiving instant payments), while KPMG writes **1 January 2027** for
the EEA extension. Published unresolved — check the regulation text or the
national supervisor before citing either. This is the same discipline applied to
the Colorado conflict in the gaming and legal KBs.

**The format layer is European-built and permissive**, which makes an EMEA
engagement unusually well-tooled: `viafintech/camt_parser` (MIT, Berlin),
`inisos/bank4j` (MIT, France), `wolph/mt940` (BSD-3), and
`ministryofjustice/bai2` (MIT) — the last **copyright HM Government, Ministry of
Justice Digital & Technology**. A UK government department maintaining a bank-file
parser in the open is a provenance argument that survives procurement review.

**Adoption context (consultancy sources, treat as directional):** Deloitte
reports growing model use among EMEA banks and insurers with the sharpest
growth among smaller institutions, fraud detection and customer experience as
the leading use cases, and persistent governance gaps. Celent, via AWS, puts
67% of banks planning customer-facing generative AI services in 2026. These sit
alongside the supervisor-published figures recorded in pass 3 (BoE/FCA 86%
adoption, ~2% broad autonomy), which remain the more rigorous numbers.


#### Pass 5 (2026-11-22) — e-invoicing is the region's agent surface, and it is already permissive

EMEA is the only region where the **statutory document formats are
multi-country**, and that single structural fact is why it has the best
permissive filing tooling in this KB.

| Format | Scope | Library | Licence | Stars |
|---|---|---|---|---|
| EN 16931 | EU semantic standard for electronic invoicing | `josemmo/einvoicing` | MIT | 180 |
| Peppol BIS 3 / UBL | the Peppol network, EU-wide plus AU/NZ/SG | `num-num/ubl-invoice` | MIT | 143 |
| Inline XBRL | UK statutory accounts → Companies House, HMRC | `kanedata/ixbrl-parse` | MIT | 72 |
| SAF-T | OECD tax audit file — PT, PL, NO, AO and others | `SimansoftMZ/SAF-T` | MIT | 8 |

A library for EN 16931 serves every EU member state; a library for Brazil's
SPED serves Brazil. The addressable developer population differs by an order
of magnitude, and the open-source supply tracks it exactly. **This is why an
EMEA filing engagement starts from adoption and a LATAM one starts from
integration** — see the regional comparison in `verticals/solutions.md`.

The normative Peppol specification repository, `OpenPeppol/peppol-bis-invoice-3`
(158★), carries **no determinable licence**: every root-path probe returns 404
across all four branches, so absence is not even measured. Treat as
specification, read-only; build against the two MIT libraries.

**Adoption and governance, secondary sources.** Deloitte's EMEA Model Risk
Management survey puts fraud detection and customer experience as the most
frequent AI use cases with governance gaps persisting, and has smaller
institutions closing the gap on larger ones. A Celent figure relayed by AWS has
**67% of banks planning to launch customer-facing generative AI services in
2026**. Deloitte also notes the UK and EU are diverging on AI-specific rules
while existing conduct, operational-resilience and GDPR obligations continue to
bind regardless — consistent with the DORA consolidation point this file
already records under AI Act Art. 9(10). CCAF has **data privacy and protection
as the top perceived AI risk at 73%**, which is the single most quotable number
for a European client conversation.

The region's own numbers already in this file stand and are the stronger
argument: 61% in-house adoption, the highest in the world, against **only 14%
with specialised legal/financial AI actually implemented**. Four of five
institutions using AI cannot document what it does, in the jurisdiction that
requires documentation.


#### Pass 6 (2026-11-25) — the ECB deadline has PASSED, and MiFIR/EMIR is the emptiest plane in this KB

**The deadline correction, applied the way pass 4 taught this KB to apply it.**
Secondary sources report that every significant European institution had to
submit **AI-cybersecurity action plans to the ECB by 31 October 2026**. That
date is **25 days in the past as of this pass.**

Pass 4 of this file built its headline regional recommendation on a date that
subsequently moved, and pass 6 of the KB named that as the flagship failure.
The same discipline applies in the other direction: **a date that has passed is
not a selling opportunity, it is a status.** The EMEA conversation is no longer
"we will help you prepare the plan". It is:

- the plan was filed — **can the institution evidence that it is executing it?**
- what did it commit to, and what is the gap between the commitment and the
  running estate?
- an action plan filed with a supervisor is a **testable artefact**. Reconciling
  a filed commitment against reality is precisely the control-and-evidence work
  this KB has identified as the convergent deliverable.

**AI Act calendar — cross-KB corroboration, and it matters.** An independent
EMEA source states the French regulator becomes a **Market Surveillance
Authority under the AI Act as of 2 December 2027**. The legal KB, researching
separately on 2026-11-25, recorded Regulation 2026/1744 as delaying Annex III
to **2027-12-02** and flagged the AI Act calendar as *in conflict, verify
against EUR-Lex*.

**Two independent research paths produced the same date.** That raises
confidence materially — but both are secondary sources, so the instruction
stands unchanged: **verify in EUR-Lex before this date enters client
material.** What it does settle is the direction: the Annex III financial
obligations are **later than the 2026 dates this KB once built on**, and any
engagement sequenced against an August 2026 Annex III date is sequenced wrong.

The AI Act reaches financial services through two named high-risk use cases —
**creditworthiness assessment** and **life/health insurance pricing** — with
DORA governing resilience and third-party AI dependency and GDPR governing
automated decision-making. Those three instruments, not an AI strategy, are
what an EMEA engagement is documented against.

**Adoption and the supervisory gap.** 81% of surveyed financial firms are
adopting AI at some level, while **48% of the 130 regulatory authorities
surveyed are still "Exploring" or not engaged with AI at all**. The UK FCA's
chief executive has argued publicly that the traditional rulemaking cycle
"doesn't work" in an era of fast-moving technology. Read together: the
institutions are ahead of their supervisors, and the supervisors know it. That
is the condition in which **a well-documented control framework becomes a
negotiating asset**, because the examiner has no better one to impose.

**MiFIR and EMIR: the emptiest plane this KB has measured.**

| Regime | Open-source supply measured 2026-11-25 |
|---|---|
| MiFIR RTS 22 transaction reporting | **2 results total**, both unlicensed, one archived |
| EMIR REFIT trade reporting | **6 results**, best has 1 star, no licence file |
| SFTR | nothing distinguishable from the above |

Both regimes are specified to the field. Both are one-way submissions to a
single destination — and in both the firm usually **cannot submit directly**: a
licensed ARM or trade repository stands in between and sells that layer. So
there is no library to adopt and no second implementation to test against.

This is the sharpest regional instance of the pass-6 law, and EMEA is where the
resulting engagement shape sells first, because MiFIR and EMIR are EMEA
regimes: **reconcile before the ARM and reconcile after it.**
`amol-vishwarupe/EMIR` (1★, no licence, pushed 2026-08-08) packages 50
ESMA-style functional validation rules — **a design reference for what those
checks are**, not a dependency. Read it, then implement against the client's
trade store.

**Middle East and Africa — secondary sources, placed honestly.** AI regulation
is described as nascent but fast-moving: the UAE's National AI Strategy 2031
and AI Ethics Guidelines, Saudi Arabia's SDAIA framework. In Africa, a
Ghana-focused review names ABSA Bank Ghana, Stanbic Bank and Ecobank deploying
AI for chatbots, predictive customer analysis and anti-fraud. None of these are
binding financial-sector AI rules, and this KB should not imply they are.
#### Pass 7 (2026-11-25) — EIOPA folds AI into Solvency II, and the dead consortium was European

**EIOPA had zero mentions in this KB before this pass.** That was the single
largest named-regulator gap in the file.

**The governance instruction, and it is the opposite of a separate AI regime.**
EIOPA's **Opinion on AI governance (August 2025)** tells insurers to govern AI
**inside the existing Solvency II governance and risk-management framework**,
not in a parallel AI track. For an engagement this is unusually good news and
should be said plainly: **the client already owns the control framework**; the
work is extending Solvency II system-of-governance artefacts to cover AI
systems, not inventing an AI governance function. That is a scoping argument,
and it is cheaper and more credible than a greenfield AI-governance programme.

**Adoption, and the PoC ceiling.** An **EIOPA survey (February 2026)**,
as summarised by secondary sources, found **approximately two-thirds of
European insurers using or actively piloting generative AI, with the majority
of deployments still at proof-of-concept stage**. That is the same
adoption-versus-production split this KB measured for EMEA banks (61% in-house
adoption against 14% with specialised AI actually implanted) — **so the EMEA
pattern now holds across both banking and insurance: high adoption, low
production, and the gap is governance evidence.**

**Pending, and worth watching with a date attached.** EIOPA's 2026 work
programme includes supporting AI Act implementation, delivering **Guidelines on
AI**, and developing measures against **discriminatory AI practices**. The
Guidelines are **not yet published**. An insurer pricing engagement started now
should be built so the documentation can be re-pointed at those Guidelines when
they land.

**Two prudential items, both secondary and both flagged.**
- EIOPA Chair **Petra Hielkema**, in a speech dated **2026-11-19**, warned that
  AI could **amplify correlated cyber losses across many firms at once**,
  challenging insurance models built for isolated rather than systemic shocks.
  This is a *pricing and capital* concern, not a compliance one, and it is the
  first item in this KB where AI is the **insured peril** rather than the tool.
- **Commission Delegated Regulation 2026/269** is reported to cut the
  spread-risk capital charge on securitisations (≈46% → ≈22% for a three-year
  non-STS position) from **2027-01-30**. Secondary source, illustrative figure.
  **Verify in EUR-Lex before any capital-impact claim.**
- **EU AI Act Annex III** classes **life and health insurance pricing and risk
  assessment** as high-risk, with obligations reported from **2026-08-02**. The
  AI Act calendar conflict pass 6 recorded (Reg 2026/1744) is unresolved —
  **check EUR-Lex, do not quote a date from a vendor page.**

**The regional finding on code: the permissive insurance core was a European
consortium, and it is dead.** `aposin` — the **Open Source Insurance
Alliance** — published `openinsuranceplatform` (Apache-2.0, 93★, 34 forks) and
`CalculusPrime-PnC`, a P&C rating engine (Apache-2.0). **Last pushes
2019-11-27 and 2019-11-28.** Five of the org's eight repos self-label
`ARCHIVED:`. Europe is therefore the region that *tried* the shared permissive
core and the region whose attempt stands as the cautionary precedent. Say it
that way to a European carrier: **the alliance route has been tested here.**

**EMEA-placed assets that are alive:**

| Asset | Repo | Licence (read) | Note |
|---|---|---|---|
| ChainLadder (R) | https://github.com/mages/ChainLadder | **GPL (>= 2)** in `DESCRIPTION`, no `LICENSE` file | On CRAN since 2008, still maintained. Copyleft — oracle, not dependency |
| turkactuary-mcp | https://github.com/afsharid/turkactuary-mcp | **Apache-2.0** (201 L) | **Türkiye insurance regulation search + actuarial calculation over MCP.** The only Turkey-placed insurance asset in this KB. 3★ — a seed, but it is the regulator's corpus as configuration |
| openIMIS | https://github.com/openimis | **AGPL-3.0 + Swiss governing-law / Berne-forum rider** | Swiss-governed; health and social protection only |

#### Pass 8 (2026-11-25) — the region's statistical code is copyleft, and a 2031 deadline entered the file

**The finding that changes how an EMEA proposal must be written.** This KB's
legal sibling established that in EMEA *the state publishes code, and it
publishes it MIT* (HMCTS, 1,827 repositories). The statistical layer **inverts
the licence half of that finding**:

| Publisher | Repos | Licence | Class |
|---|---|---|---|
| **Eurostat** (European Commission) | 95 | **EUPL-1.1 / EUPL-1.2**, near-uniformly | **Copyleft** |
| **BIS** (Basel) | 11 | **Apache-2.0**, uniformly | Permissive |

`eurostat/gridviz` (250★), `eurostat/searoute` (254★), `eurostat/eurostat-map`
(110★), `eurostat/Nuts2json` (92★) are all EUPL-1.2, and Eurostat's own SDMX
client `eurostat/restatapi` declares **EUPL** in its `DESCRIPTION` while GitHub
reports no licence at all. The permissive Eurostat route is the *community*
client, `rOpenGov/eurostat` (**BSD-2-Clause**, 257★ — the most-starred asset on
either side).

**EUPL-1.2** is an OSI-approved European Commission copyleft licence, published
in 23 languages, with a compatibility list permitting relicensing to specified
copyleft licences. **286 lines / 13,826 B**, newly entered in this KB's licence
table. It is usable and it is reciprocal: isolate it behind an interface, as
Pattern 18 prescribes for country-specific format libraries, and never link it
into a proprietary core.

> **Stated for a client conversation: "European public-sector code" is not a
> licence posture. The Commission's statistical office defaults to copyleft and
> the Basel-based bank for central banks defaults to permissive. Verify per
> publisher, every time — the default follows the institution's legal culture,
> not the sector.**

**The densest MCP coverage in any region is EMEA**, and it arrived in the last
few months:

| Authority | Repo | Licence (verified) | ★ | Push |
|---|---|---|---|---|
| ISTAT (Italy) | https://github.com/ondata/istat_mcp_server | MIT (20 lines) | 24 | 2026-11-22 |
| TÜİK (Türkiye) | https://github.com/orhoncan/tuik-mcp | **No licence file** | 16 | 2026-09-20 |
| ECB | https://github.com/scka-de/ecb-mcp | MIT (20 lines) | 4 | 2026-03-31 |
| Eurostat/ISTAT/OECD/ECB (library) | https://github.com/ondata/opensdmx | MIT (20 lines) | 58 | 2026-11-25 |

`tuik-mcp` has **no licence file** across 12 filenames and 3 refs — at 16★ it is
the most-starred unlicensed asset on this plane. If Turkish data is in scope,
write the client.

**A new dated item, long-horizon: the ECB's Integrated Reporting Framework
(IReF).** Announced June 2026, with a **one-year pilot from Q2 2030** and
**official IReF reporting commencing Q2 2031**. Recorded for two reasons: it is
a reporting-consolidation programme of exactly the kind this KB's Pattern 18
addresses, and it is far enough out that it belongs in a roadmap rather than a
pipeline. **The source does not state whether IReF relies on SDMX, and that has
not been assumed** — pass 6's lesson that a date is not a durable fact applies
equally to a dependency.

**UK — recorded, and flagged as unverified at source.** A **Financial Services
AI Adoption Plan** was published **14 July 2026**, framing scaling AI as a
strategic priority, with a cited figure that 21% of firms in the financial and
real-estate sectors had already adopted AI in early 2025. **`www.gov.uk` is
outside this session's permitted network domains**, so this could not be read
at its primary source and is secondary-sourced from search results. **Verify
before quoting it to a client**, and note that the UK plan sits alongside the
BoE/FCA survey of 26 October 2026 already recorded in this file — that survey
remains the rigorous UK dataset.

**EMEA adoption, building on pass 5 rather than restating it.** Pass 5
measured EMEA at 61% in-house adoption against 14% with specialised AI actually
deployed. The 2026 European Parliament framing adds the mechanism: institutions
have used classical machine learning for years and are **gradually
experimenting** with generative AI. One structural constraint worth carrying
into a pitch: much of the AI value chain — cloud infrastructure, semiconductor
manufacturing, frontier models — **remains concentrated outside both the UK and
the EU**, which is an argument for engagements that own the *control and
evidence* layer rather than the model layer.

### APAC

**Regulatory posture: the most advanced on agentic specifically.**

- **Singapore / MAS issued Guidelines on AI Risk Management on 7 October 2026**,
  setting supervisory expectations and letting firms tailor by risk profile.
  Deputy MD Ho Hern Shin framed it as giving institutions clearer room to
  innovate while protecting customer trust and system resilience.
- **MAS published SAFR in July 2026** — a white paper on safeguards for *agentic*
  finance, with the industry. **Singapore is the first jurisdiction with a
  published AI-agent framework for finance.**
- MAS is still consulting on AI risk guidelines covering **third-party AI
  providers**, with a response possible in late 2026, and an operational
  resilience consultation expected in 2026.
- **India:** principles-based and non-statutory. Regulators signal explainability
  and human-oversight expectations without sector-specific rules. On agentic
  payments, **NPCI said it is still examining a framework for AI agents** while
  Singapore has published one. MAS declined to say whether agent authorisation
  has been discussed with the RBI or NPCI given the UPI–PayNow linkage.
- APAC banking is described as the region's most advanced AI adopter.

- **Added 2026-11-21:** the MAS Guidelines of 7 October 2026 **cover
  traditional ML, generative AI and autonomous agents together**, apply to all
  financial institutions proportionately, and run an **implementation timeline
  to 7 October 2027**. Firms remain **accountable for third-party AI** and are
  expected to consider restricting, suspending or replacing a service whose
  risks cannot be brought within acceptable limits — which makes model-provider
  substitutability an architectural requirement, not a procurement preference.
  MAS also published an **AI Risk Management Toolkit (March 2026)** and has
  stood up a **Future of Finance Institute** starting with AI in finance.
- **They are guidelines, not a statute.** Singapore has no AI statute; this
  instrument is supervisory expectation. That is still the strictest agentic
  regime published anywhere, and it binds in practice through supervision.
- **Unverified claim, recorded so it is not repeated as fact:** one trade source
  describes a *binding* "Supervisory Notice on the Governance of Autonomous AI
  Agents" issued August 2026 with a December 2026 compliance deadline. **No
  other source mentions it and it conflicts with the October Guidelines and
  their 2027 timeline.** Do not cite it to a client without checking MAS's own
  media releases.
- **Beyond Singapore:** MAS, the **HKMA** and **APRA** moved from
  principles-based guidance to supervisory-ready expectations between March and
  July 2026. A January 2026 assessment that Australia, Singapore, New Zealand
  and Malaysia had no agentic-specific rules is now **out of date** for
  Singapore.
- **APAC-authored open source exists and this KB now carries it:**
  `fzn0x/idx` (MIT, 234 stars, Indonesian IDX/IHSG market analysis) and
  `kingdee/lingee-bench` (Apache-2.0, 190 stars, enterprise benchmark for
  whether agents deliver business value). Both in `agents/top.md` and
  `repos/foundations.md`.

#### Japan and India — added 2026-11-22

Both were effectively absent from this file, which had APAC meaning Singapore
plus a sentence each on Hong Kong and Australia.

**Japan — FSA, technology-neutral and therefore easy to under-rate.** The
FSA's **AI Discussion Paper v1.1 is dated 3 March 2026**. Japan has
deliberately **not** written finance-specific generative-AI rules; it applies
existing conduct and risk rules in a technology-neutral way. The two positions
that bind in practice:

- **AI-driven advice does not reduce the firm's suitability obligation or its
  duty to explain.** A robo-adviser or an agent is the firm acting, not a
  third party the firm can point at.
- Law-firm reviews read **agentic AI as the next real test** of that integrated
  model, with customer-facing generative and agentic systems in 2026–2027 as
  the proving ground. One secondary source reports the FSA also expecting
  **explainability for AI-driven credit scoring**; it rests on a single
  unconfirmed source and is recorded as unverified.

The commercial point: in Japan there is no AI compliance deadline to sell
against, so the sale is the **evidence** that an existing duty is still being
met once an agent is in the loop — suitability files, explanation records, and
the trail showing which agent action produced which customer outcome.

**India — RBI, framework published, agents still open.** The RBI's **FREE-AI
(Framework for Responsible and Ethical Enablement of Artificial Intelligence)
committee report was finalised in August 2025** and is the reference document
for supervised entities. Alongside it sit long-standing **payment-data
localisation** expectations, which constrain where an agent stack may run far
more concretely than any AI principle does. One report that the RBI plans to
make **AI-based bank-account verification mandatory** across banks could not be
confirmed and is recorded as unverified.

This sharpens rather than replaces the finding this file already carried:
**NPCI is still examining a framework for AI agents** while Singapore has
published one. So India has an AI framework (FREE-AI) and no *agent* framework,
and the UPI–PayNow linkage means somebody has to reconcile that with MAS's
published position.

**Wider APAC, for completeness:** HKMA's generative-AI principles (2024) and
sandbox, ASIC Report 798 (October 2024), and MAS's FEAT principles and Veritas
toolkit remain the other named instruments. Reports that regulators are
collecting industry input on extending supervision to **multi-agent systems**
are secondary and unconfirmed.

**Opportunity:** Singapore is the reference implementation. Build an
SAFR-aligned agentic control layer once in Singapore and it becomes the template
to carry into jurisdictions still drafting — India above all, where the
UPI–PayNow linkage makes agent authorisation an open question somebody will have
to answer. The third-party accountability clause is the concrete sale: an
institution that cannot swap its model provider under supervisory pressure is
non-compliant by design, and provider-abstraction work is unglamorous, scoped
and fundable.

#### Pass 4 (2026-11-22) — new binding dates, and a measured tooling gap

**Three regulatory movements not previously in this KB:**

| Jurisdiction | Measure | Status |
|---|---|---|
| Singapore (MAS) | **AI-assisted red teaming** required of key institutions on critical internet-facing systems | **From 1 July 2026** |
| South Korea | Basic Act on AI Development and Trust — the region's first comprehensive **binding** AI statute | Introduced January 2026 |
| Australia (APRA) | Boards and senior management told to strengthen oversight of AI risk, across banks, insurers and superannuation trustees | Supervisory expectation |

MAS red teaming is the actionable one: it names a **practice** rather than a
principle, it is dated and already in force, and it creates a repeatable,
scopeable engagement — adversarial testing of AI systems — rather than a
documentation exercise. It also sits alongside the MAS Guidelines of 7 October
2026 (implementation to 7 October 2027) already recorded here.

**Japan's ISO 20022 position is specific and worth knowing:** Japan held to its
original **November 2025** timeline for cross-border payments rather than
following the deferrals, the **cross-border Zengin format is being retired**,
and banks are steering corporate clients to XML. The displaced work lands in
**treasury and ERP systems** — which is an integration engagement, and one with
a defined trigger.

**Measured tooling gap, stated rather than left silent.** On the payments
message plane, APAC is the thinnest of the four regions:

| Query | total_count | Best result |
|---|---|---|
| `UPI NPCI settlement` | 6 | all 0–1 stars |
| `zengin format` | 12 | mostly unrelated (a game engine named ZenGin dominates the term) |

The single APAC-anchored asset found on this plane is
`adithyaathreya2264/payment-reconciliation-agent` (Apache-2.0, 7 stars,
UPI/NEFT/PG settlement reconciliation). **This is an informed gap, not an
unsearched one**: India and Japan run enormous domestic rails with essentially
no permissive open tooling against them, in contrast to Brazil's CNAB ecosystem
(629 stars, 434 forks) and EMEA's SEPA formats. For an APAC engagement, assume
format tooling is **build, not adopt** — and note that the `zengin` term is a
textbook case of the P31 trap, where a sector term collides with a far larger
unrelated namespace.

**Adoption:** APAC is uneven, with China and Singapore leading; FNZ/ThoughtLab
rank Asia Pacific the most mature region for AI in **wealth and asset
management** (500 firms, 155 in APAC). Deloitte projects up to US$4.8 trillion
of economic value added by the region's financial services industry by 2035
(vendor projection, long horizon — treat as directional).


#### Pass 5 (2026-11-22) — one country's filings are tooled, the rest are not

**Measured this pass.** APAC's statutory-filing tooling is Japan and nothing
else:

| Target | Result |
|---|---|
| Japan EDINET | `matthelmer/edinet-tools` (MIT, 59★, 42 document types as typed Python objects) and `ajtgjmdjp/edinet-mcp` (Apache-2.0, 20★, **parser plus MCP server**) |
| India account aggregator | 9 results, best usable is a 1-star MIT personal project; `Codexxa-Business-Solution/account-aggregator-sdk` has **no licence file** |
| India UPI libraries | 5 results, nothing above 0 stars |
| China, Australia, Korea filing formats | no permissive library surfaced |

`ajtgjmdjp/edinet-mcp` is the most interesting single asset in the region: a
**regulator's full disclosure corpus already exposed through MCP**, under
Apache-2.0. For a Japanese engagement that is a working agent data source on
day one, not a build.

India is the notable negative given the size of the market and the maturity of
the rails. The Account Aggregator framework is live and consent-based, and
there is **no permissive open-source SDK with traction against it** — the same
read-is-solved-initiation-is-not asymmetry this KB measured for SEPA and Pix,
one layer earlier. Recorded as an informed gap, searched, not inferred.

**Adoption, all secondary.** The FNZ / ThoughtLab study of 500 investment firms
(155 in APAC) ranks the region **most mature globally for AI in wealth and
asset management**, with generative-AI use among regional leaders projected to
go from 43% to 75% over three years. Money20/20 Asia reports **61.2% of
regional organisations have already adopted AI or ML**. Against that,
ComplyAdvantage's 2026 survey finds only about half of APAC firms have a fully
established AI assurance programme versus 59% globally, and Sumsub with the
Singapore FinTech Association report a widening gap between reliance on AI and
the ability to evidence what it does.

**That gap is the engagement.** The region leads on adoption and trails on
assurance, which is the exact inverse of EMEA's regulatory-pressure-first
posture, and it means an APAC pitch leads with **evidence and auditability**
rather than capability.

**Regulatory, reconciled against what this file already holds.** Korea's
general binding AI statute from January 2026 remains the region's only one.
APRA has pressed boards on AI risk oversight. The MAS Guidelines of
2026-10-07 with implementation to 2027-10-07 stand as recorded. One new item
from a Deloitte SEA regulatory round-up: **MAS requiring key financial
institutions to run AI-assisted red teaming on critical internet-facing
systems from 2026-07-01** — secondary source, consistent with the MAS
direction already recorded, **but not confirmed against a MAS primary
document; verify before citing.** The unverified "binding MAS Supervisory
Notice on Governance of Autonomous AI Agents, August 2026" recorded in a
previous pass remains uncorroborated and still must not be cited.


#### Pass 6 (2026-11-25) — two binding statutes in force, and the claim this KB must stop repeating

**Binding AI statutes now in force in the region.**

| Jurisdiction | Instrument | Effective | Shape |
|---|---|---|---|
| South Korea | AI Basic / Framework Act | **Jan 2026** | Described as the region's first comprehensive binding AI statute: risk-based, AI impact assessments, labelling for high-impact systems |
| Vietnam | Law 134/2025/QH15 | **2026-03-01** | Comprehensive risk-based framework for AI development, deployment and governance — **new to this KB this pass** |

Korea corroborates the legal KB's independently recorded 2026-01-22 date for
the Korean AI Framework Act. Vietnam is new here and matters for the obvious
reason: it is a delivery geography, and a comprehensive risk-based AI statute
has been in force there for most of 2026 without appearing in this KB.

**Singapore — the verified artefact, and the unverified one this KB must stop
carrying forward.** MAS has been **consulting on AI Risk Management
Guidelines** covering governance, explainability, lifecycle controls and
oversight of **third-party AI providers**, with a response to consultation
feedback possibly due late 2026. That is the real, citable artefact.

Pass 5 recorded a supposed **"MAS Supervisory Notice on Governance of
Autonomous AI Agents" (Aug 2026)** as uncorroborated, and pass 6 searched for
it again and **still found no primary source**. Two passes, no corroboration.
**It should now be treated as not existing** and removed from any client
material. The MAS consultation above is the thing to cite instead. Pass 5 also
flagged, unverified, a MAS requirement for AI-assisted red teaming of
internet-facing critical systems from 2026-07-01 — **also still
uncorroborated** against a primary MAS document.

Recording this explicitly is the point. An uncited claim that survives three
passes stops looking like a flag and starts looking like a fact.

**Hong Kong is the region's concentration point.** More than **500 AI-focused
organisations** and a **HK$3bn government subsidy** for AI computing capacity.
HKMA issued high-level generative-AI principles in 2024 and runs a generative-AI
sandbox; the SFC has issued circulars on AI use in licensed activities,
**including investment management**. For a capital-markets AI engagement, HK is
the APAC jurisdiction where the supervisor has actually written about AI in the
regulated activity itself rather than about AI in general.

**Japan** — the FSA is pursuing responsible AI adoption alongside tighter
oversight of crypto-assets and stablecoins and reinforced AML. Pass 5's EDINET
finding stands as the region's strongest technical asset and the pass-6 law now
explains *why* it exists: **EDINET publishes the corpus it collects**, so a
reader ecosystem formed (`matthelmer/edinet-tools`, `ajtgjmdjp/edinet-mcp`).
MiFIR and EMIR publish nothing and have nothing.

**Australia, New Zealand, Malaysia** — sectoral approach: mandatory guardrails
embedded in existing legal structures rather than standalone AI statutes.
Across **Australia, Singapore, New Zealand and Malaysia, supervisors have not
issued agentic-specific rules for financial institutions.** An agentic
deployment in those four is governed by existing outsourcing, operational-risk
and model-governance obligations — which is a *different* engagement from a
Korea or Vietnam one, and the difference should be priced.

**China** — a "strategic control" model distinct from the risk-based approach
elsewhere. Secondary analysis suggests the divergence is pushing multinationals
to reconsider **where their AI operations are located**. For a global delivery
partner that is a structural fact about engagement design, not a compliance
footnote: the data-residency and model-hosting decision may be driven by this
divergence rather than by technical preference.

**Adoption** — one forecast expects roughly **75% of APAC financial
institutions to adopt or plan to adopt generative AI between 2026 and 2028**.
Pass 5's measured picture — APAC the most mature region for AI in wealth and
asset management while roughly half of institutions lack a fully established AI
assurance programme — remains the sharper framing, and this pass adds nothing
that contradicts it.

**Capital markets** — the derivative-reporting rewrites across ASIC, MAS and
HKMA are one-way submissions to trade repositories, so the pass-6 law predicts
no permissive tooling, and none was found. Same engagement shape as EMEA:
reconcile either side of the repository.
#### Pass 7 (2026-11-25) — the region with the binding statute, and the survey that excluded insurers

**The regulatory spread is the widest of any region, and it is now measurable
in kind, not just in degree:**

| Jurisdiction | Instrument | Binding? | Date |
|---|---|---|---|
| **South Korea** | Basic Act on the Development of AI and the Establishment of a Trust Base | **Yes — the region's first comprehensive binding AI statute** | **In force January 2026** |
| **Singapore** | MAS AI Risk Management Guidelines — governance, explainability, third-party AI provider oversight | Not yet | **Consultation**; response possibly late 2026 |
| **Singapore** | Model AI Governance Framework for **Agentic AI**, introduced at Davos | Voluntary | 2026 |
| **China** | Mandatory pre-market registration for generative AI | **Yes** | In force |
| **India** | IRDAI **AI working group** convened | No — principles-based, non-statutory | June 2026 |
| **Japan** | FSA / national AI guidelines | Soft law. **Sources conflict:** voluntary aligned standards from **April 2026 (FY2026)**, phased mandatory reporting **from 2027** (one source) vs. continued soft-law approach (another) | **Unresolved — verify with the FSA** |

**Singapore is voluntary and Korea is binding and China is mandatory
registration, in the same region, in the same year.** A pan-APAC insurance AI
programme cannot be written once; what can be written once is the evidence
layer underneath it. This is the same conclusion pass 5 reached for APAC
banking by a different route, and it now holds for insurance.

**The adoption number, and a gap inside it that is the real finding.** A
**Bank of Japan survey of 153 financial institutions** (100% response rate)
found roughly **50% already using generative AI** — and, per the commentary,
**did not include a single insurer**. Separately, **Capgemini** (344
executives, 18 markets) reports **only ~10% of P&C insurers have successfully
scaled AI**.

> **Read those two together: the region's most rigorous financial-sector AI
> survey excluded insurers entirely, and the one insurance-specific number says
> roughly nine in ten have not scaled.** APAC insurance is not an
> under-adopting market — it is an **under-measured** one. For an engagement
> that is an argument for starting with a baseline and an inventory, because
> the client has no benchmark to be judged against and whoever builds the first
> defensible one sets it. Same logic this KB applied to NA banks writing the
> control framework first.

**Where APAC insurance AI is actually in production**, per secondary
commentary: customer service, **claims summarisation for a human adjuster**,
and agency/distribution enablement. One commentary states the AI renaissance in
APAC insurance "isn't happening in underwriting." Every production use keeps a
human as decision-maker.

**APAC-placed assets, verified:**

| Asset | Repo | Licence (read) | Stars | Note |
|---|---|---|---|---|
| labor-law-mcp | https://github.com/kentaroajisaka/labor-law-mcp | **MIT** (20 L, 1,071 B) | 67 | MCP server over **Japanese labour and social-insurance law**. The best-starred region-placed insurance-adjacent asset found, and the same shape pass 6 named: the statutory corpus arrives wrapped in MCP, so for a Japanese engagement that source is **configuration, not construction** |
| ClaimsProcessingAssistant-MCP | https://github.com/chbhargavareddy/ClaimsProcessingAssistant-MCP | **MIT** (20 L, 1,071 B) | 5 | Claims processing over MCP. Prototype seed |

**Informed gap, APAC:** no permissive **takaful / Islamic insurance** library
exists (355 results, best relevant 4 stars) despite Malaysia, Indonesia and the
Gulf being the natural markets. Read it the way this KB read SPED and CFDI: a
**monopoly-jurisdiction format** with a single addressable developer
population, where commercial vendors already hold the ground. **Integrate above
the incumbent; do not build the library.**

#### Pass 8 (2026-11-25) — the first APAC plane in this KB that is uniformly permissive, and the authorities with no client at all

**The statistical plane is MIT across the region, and that is new.** Every
previous APAC measurement in this file has been a story of a mature market with
a thin or awkwardly licensed open-source layer — pass 5 found India's Account
Aggregator framework live with no permissive SDK above 1★, and pass 5's EDINET
work was the exception that proved the rule. The statistical layer is the first
APAC plane here where **every asset measured is permissive**:

| Authority | Repo | Licence (verified) | ★ | Push |
|---|---|---|---|---|
| ABS (Australia), R | https://github.com/MattCowgill/readabs | **MIT** (via `DESCRIPTION`) | 114 | 2026-05-15 |
| ABS (Australia), Python | https://github.com/bpalmer4/readabs | MIT (20 lines) | 9 | 2026-11-24 |
| e-Stat (Japan), R | https://github.com/UchidaMizuki/jpstat | **MIT** (via `DESCRIPTION`) | 15 | 2026-07-21 |
| e-Stat (Japan), R | https://github.com/yutannihilation/estatapi | **MIT** (via `DESCRIPTION`) | 23 | **2020-04-12** — dormant |

**All three R packages were reported `NOASSERTION` by GitHub** and resolve to
MIT only in `DESCRIPTION`. Had this pass trusted the badge, the region's one
uniformly permissive plane would have been filed as "licence unclear" — which
is the expensive direction of that error, because it suppresses a usable asset
rather than flagging an unusable one.

**Why the region was invisible, and it is the sharpest vocabulary collision
this KB has measured.** Querying `abs` returns `abseil-cpp` (18,212★) and
`abstreet`; the Australian Bureau of Statistics does not appear. The same holds
for `imf` (returns `MeanFlow`, `ImFileDialog`, and Netflix `photon` — the
**Interoperable Master Format**) and `istat` (returns a Ruby gem for **mac CPU
stats**, 2,456★). The fix that worked was censusing the **format** (`sdmx`) and
the **package name** (`readabs`, `jpstat`, `estatapi`), never the institution's
initials.

**The informed gap, and it is the whole region's central banks.** No permissive
MCP server or SDMX client surfaced for the **Bank of Japan**, the **Reserve
Bank of India**, the **Monetary Authority of Singapore**, the **People's Bank
of China**, the **Reserve Bank of Australia** or the **Bank of Korea**.
Searched via `sdmx`, `mcp sdmx`, `mcp fred`, `estatapi`, `jpstat` and
`readabs`. The two Japanese and two Australian assets above are **statistical
office** clients, not central-bank clients. Stated explicitly so the silence is
not read as coverage: **APAC has national statistics well covered and its
monetary authorities not covered at all.**

For an engagement that needs APAC central-bank series today, the realistic
routes are the IMF and OECD servers (`cyanheads/imf-mcp-server`,
`cyanheads/oecd-mcp-server`, both Apache-2.0) which carry APAC aggregates, or
the BIS statistics via `bis-med-it/pysdmx` — i.e. **reach the region's data
through the international institutions rather than the national ones.** That is
a different integration shape and it should be priced as such.

**Regulation — one item moves from "unverified" toward corroborated.** Pass 5
flagged, and pass 6 recorded, the MAS requirement for **AI-assisted red teaming
on critical internet-facing systems from 1 July 2026**. It has now appeared on
a **third independent secondary path** this pass. It remains **secondary** — no
primary MAS document has been read by any pass — but three independent
secondary sources is a materially stronger position than pass 5's single
Deloitte round-up, and it is the region's one named *practice* obligation
rather than a governance expectation.

Pass 6's correction stands and must keep standing: the supposed **"MAS
Supervisory Notice on Governance of Autonomous AI Agents" (August 2026) has
never been corroborated and must not be cited.** Korea's **Basic Act on AI
Development and Trust** (in force January 2026) remains the region's first
comprehensive binding AI statute, and **APRA**'s board-oversight expectations
remain the Australian instrument.

A framing point for proposals, consistent with pass 5's adoption/assurance
inversion: analyses this pass continue to find **little explicit regulation
aimed at agentic AI** in major APAC markets, with Singapore's Model AI
Governance Framework as the main reference point. APAC therefore still leads
with **evidence and auditability**, because the obligation is to show your
working, not to meet a checklist that does not yet exist.

### LATAM

**Regulatory posture: thin on AI-specific finance rules, strong on payment rails.**

- **Brazil:** as of March 2026 there is still **no fully enacted
  finance-specific AI statute**. AI in finance is governed by general data
  protection law plus sectoral financial rules. Brazil has embedded
  **"explainable AI" principles into its Open Finance framework** — the most
  concrete AI hook in the region. One source notes the Banco Central, though a
  leader in AI oversight, faces resource gaps in auditing complex models.
- **Peru reportedly has the first AI rule in force for banking in the region** —
  Supreme Decree 115-2025-PCM, effective **22 January 2026**.
- **Argentina** has enforced a central bank communication on AI since 2023.
- **Mexico:** sources conflict. Counsel opinion says there is no AI-specific
  statute or binding framework for financial institutions or fintechs; a
  promotional blog claims the 2025 Fintech Law amendments were a watershed for AI
  regulation. Weight the counsel view. Separately, the 2018 Fintech Law's
  sandbox registry has received **9 applications**, of which 5 were rejected and
  4 withdrawn — **none approved**.
- **Rails:** Pix processed **3.09 billion** person-to-business transactions in
  March 2026 alone. Colombia's **Bre-B** is advancing as a local Pix equivalent,
  but **Pix and Bre-B are not interoperable** — payments cannot move between them.
- Adoption: one vendor-cited outlook claims 77% AI adoption among Mexican
  fintechs with 80% bank partnership rates. Treat with caution.

- **Named players (new 2026-11-21, closing a gap this file logged):** in Brazil,
  **Itaú** and **Bradesco** are pushing into embedded finance and API-driven
  distribution; in Mexico, **BBVA** and **CitiBanamex** have been explicit about
  large-scale transformation programmes.
- **A concrete Mexican regulatory precedent:** in **May 2026 the CNBV authorised
  FIDUZ as an Independent Investment Advisor with an AI-based business model**,
  accompanied by a governance manual. This matters more than the absence of a
  statute: it is a supervisor approving an AI-native business model and telling
  you, through the manual it accepted, what governance evidence it wants. The
  CNBV has approved roughly **50 fintech licences** out of hundreds of
  applications, and **Fintech Law 2.0** was reported due for update by October
  2026 (status unconfirmed — verify before citing).
- **Brazil's supervisory expectations are concrete even without an AI statute:**
  the **BCB** is described as among the most prescriptive regulators in the
  region, expecting a written model-risk framework, **explainability on credit
  and fraud decisions**, documented human oversight and quarterly monitoring
  reports. Brazil also launched **credit portability via Open Finance in
  February 2026**, letting consumers move debt between institutions fully
  digitally.
- **Brazil's AI bill status:** PL 2.338/2023 passed the Senate and sits in the
  Chamber; LATAM broadly follows the EU model and Brazil and Mexico have adopted
  the OECD AI Principles — so **EU compliance work transfers to the region**,
  and that transferability is itself sellable.
- **Fraud is the live, funded pain.** One vendor report puts **account-takeover
  incidents up 324% in early 2026 in Mexico**, attributed to generative AI
  tooling. The figure is vendor-sourced and unverified, but the direction is
  corroborated across LATAM fraud coverage.

#### Agentic payments are already live in LATAM — and the region chose the safe shape (2026-11-22)

The most commercially relevant LATAM finding this pass is not regulatory.

- **Mastercard is reported to have completed agent-initiated payments with 17
  banks and processors in the region in March 2026.** Vendor-adjacent reporting,
  not a primary source, and recorded as such — but if even directionally right
  it means agentic payment is in production in LATAM while EMEA and North
  America are still writing rules about it.
- **The design pattern the region settled on is per-payment human confirmation.**
  Open-banking initiators **Iniciador** and **Bipa** in Brazil and **Fintoc** in
  Mexico are reported to require the person to confirm **each** payment with
  biometrics or inside their own banking app. The agent assembles the payment;
  the human releases it.

**Three sources, three continents, one answer.** That LATAM pattern is the same
boundary as the BoE/FCA measurement that **~2%** of UK firms let agents run with
broad autonomy, and the same as OSFI's July 2026 bulletin asking for approval
checkpoints before high-impact actions. The market, the supervisors and the
engineers have independently converged on *agent proposes, human releases*. A
pitch that promises autonomous payment execution is arguing against all three.

**Regulatory status, updated:**

- **Brazil:** the BCB's head of regulation is reported to have said there will
  be **no formal central-bank AI rules before the end of 2026**. That is
  consistent with everything this file already records and it is useful
  negatively: in Brazil the binding surface remains the Open Finance
  explainability requirement and the BCB's model-risk expectations, not a
  forthcoming AI rulebook.
- **Chile — sources conflict and the conflict is left visible.** One LATAM
  technology newsletter refers to a general risk-tiered AI law approved in
  October 2025; a law-firm outlook states that Chilean law provides **no
  comprehensive statutory regime specifically addressing AI in financial
  services**. Weight the counsel view, as this file did for Mexico. What is not
  in dispute: the **Fintech Law and the CMF's NCG 514** are in force, and one
  assessment is that Chile now has **more regulation in place than capacity to
  implement it** — which is itself a market signal for delivery help.
- **Adoption, secondary:** Finnovista's Fintech Radar 2026 is cited for **77% of
  Mexican fintechs using AI** — the same figure this file already flagged as
  vendor-cited, now attributed to a named study. A Febraban/Deloitte survey is
  reported to put **generative AI as a priority for 84% of Brazilian banks**,
  with sector technology budgets up 8% year on year. Both are second-hand.

**Opportunity:** three distinct ones. (1) Brazil's explainable-AI requirement
inside Open Finance plus the BCB's explainability expectation on credit **and
fraud** decisions is a compliance surface that already exists and already binds
— unlike most of the region. (2) The Pix/Bre-B interoperability gap is an
integration problem, and agentic reconciliation across non-interoperable rails
is a concrete, unglamorous, fundable build. (3) **Fraud, not advisory, is where
LATAM budget is moving**, and it is the one place where a permissive open source
gap is verified open by function (see `repos/foundations.md`) — so it is build
work rather than integration work.

**LATAM is now the best-tooled region in this KB, which inverts the usual
picture.** `bacen/pix-api` is an official central-bank OpenAPI spec with 3,010
stars; `OpenFin8/openfin8-br` implements consent, Pix initiation and Pix
Automático on the FAPI-BR profile; `ciro-maciel/awesome-open-finance-brasil`
indexes the whole BCB regulatory corpus under CC0. Nothing equivalent exists for
EMEA's PSD2 at official-source level. Details and licence caveats in
`verticals/solutions.md`.

#### Pass 4 (2026-11-22) — the rail underneath Pix

**This KB's LATAM coverage has been Pix-shaped for four passes, and Pix is not
where a corporate client's reconciliation pain lives.** Brazilian collections
and payables still move on **CNAB 240/400 remessa and retorno files** and on
**boletos**, and that ecosystem is permissive, mature and has the highest
traction of any LATAM asset found in any pass of this KB:
`eduardokum/laravel-boleto` (MIT, 629 stars, **434 forks**),
`openboleto/OpenCnabPHP` (MIT, 214 stars, reads *and* writes CNAB 240/400). In
Mexico, `Angle/sat-cfdi` (MIT) validates **CFDI 4.0** against SAT rules.

Full table in `verticals/solutions.md`. The engagement shape this implies:
**AR/AP reconciliation against CNAB returns and CFDI matching**, not another Pix
integration. It is the back-office plane the CCAF survey says is four of the top
five use cases, placed in the region.

**The transferable rule, confirmed from the legal KB in the opposite
direction.** That KB found porting a US standard (LEDES) into LATAM was the
wrong work because the regional equivalent is the **national electronic fiscal
invoice**. Here the same rule says: do not assume a LATAM reconciliation build
needs ISO 20022 tooling. It needs CNAB, boleto and CFDI — which already exist
under MIT.

**Adoption and measurement:** Evident launched an **AI maturity index covering
20 major LATAM banks** in July 2026 (transparency, leadership, innovation,
talent) — a public, named-institution scorecard a client can be benchmarked
against, which is rare for the region. A Finnosummit post reports Mexican
adoption rising from 60% (2025) to 77% (2026); **that is a conference blog and
is published here marked as unverified**, consistent with this KB's handling of
vendor figures. UBS names the barriers as infrastructure gaps, implementation
cost, talent retention and regulatory uncertainty.

**Regulatory shape is unchanged from pass 3 and does not need re-verifying:**
decentralised, Pix-centred, no general AI statute in Brazil (PL 2.338/2023
passed the Senate, still in the Chamber) or Mexico. The disinformation pattern
recorded for three consecutive passes in the legal KB — compliance guides
asserting that Brazil and Mexico already have AI laws in force — applies here
too and remains false in both.


#### Pass 5 (2026-11-22) — the region leads on rails and is last on books

**The sharpest regional contrast in this KB, and it reverses the usual
picture.** LATAM has the best payment-rail tooling here — `bacen/pix-api` is a
central bank's own OpenAPI spec at 3,010 stars with no EMEA equivalent, plus
CNAB, boleto and `sat-cfdi`. For the *accounting* file the same company is
obliged to produce, measured this pass with the region's own vocabulary rather
than translated US terms:

| Query | Results | Best available |
|---|---|---|
| `SPED ECD contabil` (Brazil) | 6 | `nfephp-org/sped-ecd` — LGPL-3.0 (187 lines, GitHub reported `NOASSERTION`), 4★, **no commit since 2024-07-01** |
| `contabilidad electronica SAT XML` (Mexico) | 3 | `albertotrece/sat` — GPL-2.0, 19★, **last push 2015** |

One stale copyleft library and one abandoned nine years ago, for mandates that
are **older and more universal than Pix**.

**Do not read this as a build opportunity.** The structural reason is in the
EMEA section above: EN 16931, Peppol and SAF-T are multi-country formats and
attract permissive libraries; SPED and CFDI are single-country, so the
addressable population for a shared library is one market wide and commercial
fiscal-emitter vendors already own it. The realistic shape for a LATAM
engagement is **integrate with the fiscal emitter the client is already
required to use, and put the agent above it** — the same conclusion the legal
KB reached about porting LEDES into LATAM. The format does not transfer; the
semantics do.

**Adoption, secondary sources.** Finnovista's Fintech Radar has Mexico's
fintech AI adoption rising **from 60% in 2025 to 77% in 2026**, the fastest in
the region, with Colombia at 66% in 2025. Evident launched an **AI Index for
Banks in Latin America in July 2026 ranking 20 major regional banks** on
transparency, leadership, innovation and talent — the first regional
benchmark a client can be positioned against, and worth reading directly
before any LATAM banking pitch. UBS frames AI as narrowing the region's
digital gap, with marketing/sales, process automation and threat detection as
the leading use cases.

**Regulatory, consistent with what this file already holds.** Mexico still has
no dedicated AI regulation for financial services; supervisors review model
governance, explainability and bias under existing risk-management and
consumer-protection rules — which matches the CNBV/FIDUZ precedent recorded
above and is the reason that precedent is worth more than a statute would be.
Mexico's **Open Finance secondary rules remain unfinalised, with only open-data
obligations in force as of early 2026** — so an open-finance pitch in Mexico
is a readiness engagement, not a compliance one. Trade coverage notes
stablecoin growth outpacing rulebooks dating to the 2010s.


#### Pass 6 (2026-11-25) — Peru's financial deadline has PASSED, and the region's capital-markets plane is an informed gap

**Peru, and the framing this KB had wrong.** Supreme Decree 115-2025-PCM
approves the regulation of Law 31814 and is reported as making Peru **the first
country in Latin America with a general AI regulation in force**. It
**classifies banking and credit scoring as high risk**, and the reported
deadline for the financial sector was **10 September 2026**.

That is **two and a half months in the past.** Pass 5 of this KB carried Peru
as a forward-looking date (2026-01-22). It is no longer a preparation play.
A Peruvian bank either classified its credit-scoring systems as high-risk and
built the corresponding controls, or it is **non-compliant today**. The
engagement is remediation and evidence, under time pressure, and it should be
sold that way — which is a stronger position than preparation, not a weaker
one.

The secondary-source caveat matters here: the 10 September 2026 financial-sector
deadline comes from a vendor blog. **Verify against the decree before quoting
the date to a client** — but the direction (in force, banking and credit
scoring high-risk) is consistent across sources and with what the legal KB
recorded independently.

**Everywhere else, measured and stated as absence.** This is the region where
"nothing found" is a finding rather than a hole in the research:

| Jurisdiction | Status as reported, 2026 |
|---|---|
| Honduras | **No** legislation or regulatory guidance specifically addressing AI or generative AI in the financial sector |
| Panama | **No** specific regulation directly addressing AI (as of March 2026) |
| Argentina | Technology-neutral, risk-based supervision — **no** AI-specific regulation |
| Mexico | CNBV's capacity outstripped by fintech growth; **no publicly available draft** AI law, and **no bill before Congress or the Senate** |
| Brazil / Chile / Colombia | AI bill, framework and CONPES respectively, all at different speeds — none a financial-sector AI rule in force |

Mexico corroborates pass 5 exactly: no dedicated financial-sector AI
regulation, and open-finance secondary rules still unfinalised. The conclusion
pass 5 drew holds — **a Mexican open-finance pitch is a readiness engagement,
not a compliance one** — and now the AI side reads the same way.

**Adoption and the named players.** Financial services leads AI use in
the region: credit scoring for thin-file customers, real-time fraud
detection, AML and conversational banking. Named at scale: **Nubank, Mercado Pago,
Bancolombia, Itaú, Bradesco**. One vendor source makes a causal argument worth
keeping because it matches pass 5's rails finding — tighter margins forced LATAM
institutions into automation early as the only viable way to scale service.

**Barriers, and they are Globant's actual addressable work.** Regional AI
governance frameworks are described as **emerging and often informal**, and
specialised AI talent is **concentrated in three or four cities**.
Multinationals operating across the region carry cross-border compliance
overhead that single-country players avoid. A region that has adopted AI faster
than it has governed it, with governance expertise scarce and concentrated, is
the clearest possible description of a market for **governance-and-evidence
delivery** — which is the same deliverable the other three regions converge on,
reached here by a fourth distinct route.

**Informed gap — capital markets.** This pass searched the capital-markets
plane and found **no LATAM-placed permissive open source**: no B3 or CVM
reporting library, no regional FIX or trade-reporting tooling, nothing
analogous to `bacen/pix-api` for securities. Pass 5's inversion holds and
deepens: **LATAM leads this KB in payment rails and is last in both statutory
accounting and capital markets.** The explanation is the same one pass 5 gave
for SPED and CFDI — single-country formats have a single-country addressable
developer population — and the realistic shape is likewise the same: integrate
above the incumbent the client is already obliged to use.

**Informed gap — regulators as AI adopters.** Nothing was found this pass on
LATAM financial supervisors' own AI adoption. Globally only about a fifth of
regulators are at advanced adoption and 48% of 130 surveyed are still
exploring; no region-specific LATAM figure surfaced. Recorded as not measured,
not as zero.
#### Pass 7 (2026-11-25) — insurance is the region's thinnest plane, and the gap is honest

**The measurement first, because the conclusion depends on it being a measured
absence rather than an unsearched one.** Searching for LATAM-placed insurance
open source — actuarial, reserving, policy administration, claims — returned
**no permissive, maintained, region-placed asset**. Not one. The actuarial
code is American (`casact`) and Julian/Japanese (`JuliaActuary`,
`lifelib-dev`); the dead consortium core is European (`aposin`); the one
Turkey-placed MCP is EMEA.

> **Stated so a future pass does not re-walk it: LATAM has no region-placed
> insurance open source in this KB, and the search was run with the region's
> own vocabulary and with institutional-org enumeration, not only with
> translated US terms.** If a future pass finds one, the likely owner is a
> supervisor or a professional actuarial institute, not a vendor — that is
> where every other region's insurance code turned out to live.

**Regulation: general frameworks only, in both major markets, and both
confirmed by more than one source.**

| Country | Position as measured | Source quality |
|---|---|---|
| **Brazil** | **No specific, fully enacted AI law for the financial sector** as of March 2026. **PL 2338/2023 remains in Congress.** AI in insurance supervised through general frameworks: **SUSEP** on market conduct and prudential risk, plus **LGPD**. One compliance blog describes the bill's high-risk classification (which would cover insurance) and its penalties **as though already in force — that is wrong, and the blog contradicts the law-firm sources** | Law firm (Latham) + specialist trade; one blog rejected |
| **Mexico** | **No AI-specific law and no binding AI framework for financial institutions or fintechs.** Financial regulation held to be technology-neutral enough to accommodate AI inside existing licences. **CNSF had issued no AI-specific circular for insurers as of May 2026**; the applicable frame is derived by analogy from pre-existing rules (model governance, actuarial validation, methodological documentation) | Law firm (Latham) + 2026 trade article |

**What that means commercially, and it is the same shape this KB found for
Mexican open finance:** a LATAM insurance AI engagement is a **readiness and
evidence** engagement, not a compliance one. There is no deadline to sell
against. The defensible pitch is the one that survives PL 2338 passing: build
the model inventory, the actuarial validation trail and the methodological
documentation **now**, because those are already expected under SUSEP and CNSF
model-governance analogies and they are exactly what a high-risk
classification would later demand. **Compliance-by-anticipation, priced as
risk reduction rather than as obligation.**

**Market position, secondary:** Brazil retains regional insurtech leadership,
Mexico second by volume; investment favours solutions that cut acquisition
cost, sharpen risk selection or automate claims. That ordering — acquisition,
selection, claims — is worth respecting in a pitch, because it is the client's
ordering, not the technologist's.

**The regional inversion, continued from pass 5 and now sharper.** Pass 5
established that LATAM **leads** this KB on payment rails (`bacen/pix-api`,
3,010★, a central bank publishing its own spec) and is **last** on accounting
filing. Insurance extends the same line: the region's public institutions
publish **rails and data**, not **domain code**. Pix exists because a central
bank chose to publish a specification. **No LATAM insurance supervisor has made
the equivalent choice**, and until one does, the plane stays empty regardless
of market size. That is the one sentence to carry into a LATAM insurance
conversation: **the gap is not developer capacity, it is that nobody has
published the artefact to build against.**

#### Pass 8 (2026-11-25) — the region's statistical clients are the freest-licensed assets in this KB, and the central banks have none

**The inversion, continued and sharpened in a third direction.** Pass 5 found
LATAM leading the KB on payment **rails** (`bacen/pix-api`, 3,010★) and last on
**books** (SPED, CFDI tooling thin and stale). Pass 8 adds the statistical
layer, and the region does something no other region in this KB does: its
clients are licensed **more freely than MIT**.

| Publisher | Repo | Licence (verified) | ★ | Push |
|---|---|---|---|---|
| INEGI (Mexico) | https://github.com/Eflores89/inegiR | **CC0** (via `DESCRIPTION`) | 54 | 2026-10-15 |
| Banco de México | https://github.com/Eflores89/banxicoR | **CC0** (via `DESCRIPTION`) | 11 | 2026-10-15 |
| Brazil, official economic data | https://github.com/felipegambettadesouza6-jpg/open-economics | MIT (20 lines) | 2 | 2026-09-12 |
| Banxico CEP (payment receipts) | https://github.com/cuenca-mx/cep-python | MIT | 20 | 2026-09-22 |
| CoDi (Mexican digital payments) | https://github.com/portfedh/codi-api | Apache-2.0 | 18 | 2026-11-23 |

**CC0 is a public-domain dedication — freer than MIT**, with no attribution
obligation. Both Mexican clients were reported `NONE` by GitHub and resolve
only in `DESCRIPTION`. One caution for the client's third-party register: **CC0
carries no express patent grant** (it explicitly does not license patent
rights). For a data client that is close to immaterial, but it is worth a line
rather than a silence.

`open-economics` is worth more than its 2★ suggests: a **no-auth API plus MCP
server for official Brazilian economic data**. No-auth matters — it removes the
credential-provisioning step that usually makes a LATAM data integration a
three-week procurement conversation.

**The informed gap, measured and stated plainly: the region's central banks
have no permissive SDMX or MCP client.** Nothing surfaced for the **Banco
Central do Brasil** statistical series (distinct from the Pix API, which this
KB has covered since pass 4), the **BCRA** (Argentina), the **Banco de la
República** (Colombia), the **Banco Central de Chile** or the **BCRP** (Peru).
Searched via `sdmx`, `mcp sdmx`, `banxico`, `inegi` and `mcp econom`. **Mexico
is the only LATAM country in this KB with a central-bank data client at all**,
and it is a 11★ community R package under CC0.

Read it the way pass 5 taught rather than as a build opportunity: these are
**mono-country** integrations, so the addressable developer population for each
is a single market, which is exactly why no library accretes. The realistic
shape is the same as pass 5's conclusion on SPED and CFDI — **integrate above
what the client already has**, and reach regional aggregates through the
international institutions (IMF and OECD servers, both Apache-2.0) rather than
building five central-bank clients.

**The regional datum of this pass, and it is the one to put in front of a LATAM
client.** The CCAF 2026 survey (628 institutions, 151 jurisdictions) finds that
**advanced economies are nearly seven times more likely to reach the
"transforming" stage of AI use than emerging markets.** This KB has carried
CCAF's 81% / 40% adoption figures since pass 4 and its regulator figures since
pass 6; this one is new and it is different in kind, because it is not about
*whether* AI is adopted but about **how far adoption gets**.

It reframes the LATAM proposition precisely. The constraint is not appetite —
Finnovista measured Mexican fintech AI adoption rising **60% (2025) → 77%
(2026)**, the fastest in the region, with Colombia at 66% in 2025. The
constraint is **getting past pilot**, and a 7× gap in reaching the transforming
stage is a gap in **engineering, governance and evidence**, not in enthusiasm.
That is directly sellable: the deliverable is the thing that moves a working
pilot into a supervised production system, and it is the same control-and-
evidence layer pass 5 identified as the convergent deliverable across all three
other regions.

**Still current from prior passes, not restated here:** Mexico has no dedicated
AI regulation for financial services and its open-finance secondary rules
remain unfinalised, so an open-finance pitch there is a **readiness**
engagement; Peru's **DS 115-2025-PCM** financial deadline has passed; Chile's
**21.855** moved 21.719 to 2027-10-15; and the **Evident AI Index for Banks in
Latin America** (July 2026, 20 banks ranked) is the first regional benchmark to
position a client against — read it before any LATAM banking pitch.

### Global / cross-region

- **Agentic governance is the universal gap.** Accenture recommends a dedicated
  AgentOps function; Capgemini found nearly half of banks and insurers creating
  roles to supervise AI agents. Every region above lands on human oversight for
  credit decisions, by different legal routes.
- **The back-office finding is region-independent** and is the most reliable
  commercial signal in this file.


#### Pass 5 (2026-11-22) — open-source supply follows the file format, not the decision

A market-structure finding, measured over 21 GitHub searches and tabulated in
full in `agents/top.md`. It applies to every region and sets the build-vs-buy
line for every engagement in this KB.

Where a **byte-level specification** exists, the top repository is mature,
permissive and maintained — `ledger/ledger` 6,078★ BSD-3, `moov-io/iso8583`
539★ Apache-2.0, `josemmo/einvoicing` 180★ MIT, `moov-io/metro2` 130★
Apache-2.0. Where the work is a **judgement**, nothing exists above a hobby
project — three-way matching tops out at 1 star, dunning at 1, chargeback
representment at 1, cash forecasting at 7, and `chart of accounts agent LLM
posting` returns **zero results**.

Result counts predict nothing: `Metro 2 credit reporting` returns ten results
and a 130-star Apache-2.0 library; `cash flow forecasting treasury` returns
forty-seven and nothing above seven stars.

**Why:** a format is an obligation shared by every institution in a
jurisdiction — published, binary conformance, one implementation serves all,
so it gets written once and starred. A judgement is specific to one
institution's data, policy and risk appetite, cannot be validated against a
published spec, and has no shared artefact to converge on.

**Commercial consequence, and it is the single most useful sentence in this
file: adopt the parser, build the decision.** The format layer is free and
writing it is rework a reviewer will catch. The judgement layer is greenfield
with no open-source incumbent to displace — and it is where the client's
margin sits.

This also explains the CCAF value-measurement problem recorded above (55% of
industry respondents, 63% of regulators and 76% of large institutions find AI
value hard to measure). Format work is measurable by construction: the file
either conforms or it does not. Judgement work is what resists measurement —
so an engagement that starts at the format layer **has a defensible number on
day one**, and can fund the judgement layer from it.


#### Pass 6 (2026-11-25) — open source follows the file that more than one party must read

Pass 5 established: *open-source supply follows the file format, not the
decision.* Pass 6 tested that on securities and derivatives and found the law
needed a second clause, because **half the formats in that plane are specified
to the byte and have nothing behind them.**

| Format | Who must read it | Best permissive implementation |
|---|---|---|
| FIX | every counterparty | `quickfix-j/quickfixj` 1,161★, `da4089/simplefix` 255★ MIT |
| SWIFT MT | every bank | `prowide/prowide-core` 296★ Apache-2.0 |
| ISO 20022 | every bank | `prowide/prowide-iso20022` 240★ Apache-2.0 |
| Metro 2 | lender **and** four bureaus | `moov-io/metro2` 130★ Apache-2.0 |
| MiFIR RTS 22 | one regulator, via an ARM | **none** (2 results, unlicensed) |
| EMIR REFIT | one trade repository | **none** (6 results, 1★ best) |
| CAT | one processor | **none** (0 results) |
| Form PF / N-PORT | the SEC, not republished | **none** (queries return game ports) |

**The mechanism.** A many-to-many format is read by everyone who writes it, so
reading someone else's message is how you find your own encoder's bug — a
shared implementation has shared value and gets written and starred. A one-way
submission is read by one party that does not publish its reader: the submitter
gains nothing from sharing, cannot test against a second implementation, and
often may not submit directly at all.

**Second clause, the one that predicts.** Where a regulator **publishes the
corpus it collects**, a reader ecosystem forms even though the submission is
one-way — SEC EDGAR, Companies House (`kanedata/ixbrl-parse` 72★), EDINET
(`matthelmer/edinet-tools` 59★). Where it keeps the data, nothing forms. **The
published corpus, not the published schema, creates the open-source
population.**

This subsumes pass 5 rather than replacing it: a judgement produces no file at
all, so nobody reads it, so there is nothing to share — the same mechanism at
its limit.

**Falsifiable prediction for the other eleven industries.** Pass 5 predicted
mature permissive clustering on published interchange formats. Pass 6 says
**roughly half of those will be empty, and names which half**: one-way
regulatory submissions (healthcare quality reporting to a payer or CMS, energy
REMIT filings to ACER, automotive type-approval dossiers) will be as bare as
MiFIR, while many-to-many exchange formats (HL7/FHIR, IEC 61850, OpenTravel,
GS1/EDIFACT) stay mature. The legal KB already produced a consistent data
point without naming the mechanism: Brazil's DataJud publishes **metadata
only**, and the tooling around it is correspondingly thin.

**The commercial rule, which inverts pass 5's advice for exactly one plane.**
Pass 5: *adopt the parser, build the decision.* In one-way regulatory reporting
there is no parser to adopt and never will be — the client's ARM or trade
repository owns that layer and is paid for it. So the engagement sits **on both
sides of the vendor**: reconcile the submission against the firm's own books
before it goes, and reconcile acknowledgements and rejections back against the
trade store after. Deterministic oracle, no competition with the vendor, and it
is where reportable-accuracy exposure actually sits.

##### The licence taxonomy this KB had been missing: spec ≠ code ≠ data

One organisation, three artefact types, three licence regimes, and GitHub's
badge absent or wrong on most of them.

| Class | Example | Licence | What it grants |
|---|---|---|---|
| Specification | `finos/common-domain-model` (297★), `finos/FDC3` (275★) | Community Specification License 1.0 (99 lines) | Rights over a **document** plus a patent commitment. **Not software rights.** GitHub says NOASSERTION |
| Implementation | `finos/rune-dsl`, `finos/FDC3-Sail`, `finos/tracdap` | Apache-2.0 (201 lines) | Ordinary permissive software rights |
| Document | `finos/ai-governance-framework` (121★) | CC-BY-4.0 (395 lines) | Rights over prose |
| Data | `opensanctions/*` | **code MIT, data CC BY-NC 4.0** | Code free; **data non-commercial**, some files unlicensable at all |

**The two most-starred repos in the FINOS list are not software.** And the
OpenSanctions data trap is the expensive one: 1,543 stars of genuinely MIT
screening code whose data is non-commercial, in a use case — screening a
client's customers — that is commercial by definition.

**Rule for the twelve KBs: read the licence of the data separately from the
licence of the code, and never infer either from the other.** An OSI badge on
a data repository describes the software that moves the data.

##### Global numbers added this pass

All from secondary sources and marked as such. Pass 4 and 5 already used the
CCAF 2026 headline figures (81% adopting, 40% advanced, fintechs 47% vs
incumbents 30%, ~20% of regulators advanced, privacy the top perceived risk at
73%, four of the top five use cases in the back office) — **not repeated here.**
New this pass:

- **48% of the 130 regulatory authorities surveyed** are still "Exploring" or
  not engaged with AI at all. The sharper framing of the supervisory gap: it is
  not that regulators are behind, it is that **half of them have not started.**
- **Agentic AI is in active adoption among 52% of industry respondents** —
  the first figure in this KB putting agentic adoption above half.
- Gartner, via secondary coverage: **40% of business software will include AI
  that completes end-to-end tasks by the end of 2026.**
- The **WEF / Accenture "AI Playbook for Financial Services 2026"** and the
  **CCAF 2026 Global AI in Financial Services Report** (628 institutions, 151
  jurisdictions) are both published as PDFs. **Read them directly before any
  major pitch** rather than through roundups — this KB has now twice found
  roundup figures that did not survive contact with the primary document.
#### Pass 7 (2026-11-25) — the third clause: the spec must be readable without paying to join

Pass 5 established that **open-source supply follows the file format, not the
decision**. Pass 6 refined it: supply follows **the file that more than one
party must read**, and one-way submissions to a regulator who publishes no
reader stay empty — with the predictive second clause that where the regulator
**publishes the corpus** it collects, a reader ecosystem forms anyway.

This pass tested the law on a plane it had never touched and found a case that
**satisfies the multi-party condition and still produces nothing.**

**The controlled comparison — one variable, opposite outcomes:**

| Standard | Read by more than one party? | Spec readable free? | Best permissive implementation |
|---|---|---|---|
| FIX | Yes | **Yes** | 1,161★ |
| ISO 20022 | Yes | **Yes** | 240★ Apache-2.0 (+ `moov-io/rtp20022`, 90★) |
| SWIFT MT | Yes | **Yes** | 296★ Apache-2.0 |
| EN 16931 / UBL | Yes | **Yes** | 180★ MIT, 143★ MIT |
| Metro 2 | Yes | **Yes** | 130★ Apache-2.0 + a second MIT implementation |
| **ACORD** | **Yes** — carrier, agent, broker, reinsurer | **No — membership and paid programmes** | **8★, unlicensed, last push 2017.** `AL3 insurance` → **0 results** |

ACORD's own published terms: access to Standards requires joining the relevant
membership or participation programme and creating an acord.org account; Forms
are licensed separately; the EHR Digital Standards Programme is **$5,000 per
year** for eligible participants; not all programmes grant access to all
standards, some at additional charge. Terms document dated **2025-10-27**.

> **THIRD CLAUSE. Open source follows the file that more than one party must
> read AND whose specification can be read without paying to join.** Where the
> spec is member-gated, the multi-party condition is met and the population
> still does not form — because the person who would write the library may not
> lawfully read the spec. The gate is **governance, not technical difficulty**.

**The second, independent confirmation on the same plane.** The permissive
insurance core was not merely absent — it was **built by a consortium and
abandoned**: `aposin/openinsuranceplatform`, Apache-2.0, 93★/34 forks, last
push **2019-11-27**, with five of the org's eight repos self-labelled
`ARCHIVED:`. So the insurance plane is closed at **both** ends: its shared
format is paywalled and its shared code attempt is dead.

**The counter-case on the same plane, which is what makes the clause precise
rather than merely pessimistic.** Where the artefact is a **published method**
rather than a licensed document, the same industry's open source is mature,
institutional and alive: `casact/chainladder-python` (MPL-2.0, 292★, pushed
2026-11-23), `lifelib` (MIT, 229★), 16 `JuliaActuary` repos (MIT, three pushed
the day of this pass). **A method is published in a journal and cannot be
withheld; a format can be.**

> **So the fully-stated law, after three passes: open source accumulates on
> artefacts that are (1) shared across parties, (2) readable without payment,
> and (3) checkable — a file that conforms or does not, or a method whose
> output is determined. Remove any one and the population disappears, and
> which one is missing tells you what to do instead.**

**The commercial rule this yields, and it generalises past finance.** Pass 5's
advice was *adopt the parser, build the decision*. That advice assumes the
format layer is free. **It is free only when clause (2) holds.** So the
procurement gate, now Pattern 23's three checks: **before promising a format
layer on any plane in any industry, confirm you can download the spec today
without an account.** If you cannot, the format layer is a **line item**, not a
sprint — and the honest proposal says so in week one rather than discovering it
in month three.

**Three planes, three different reasons the default advice fails — this is now
itself the pattern:**

| Plane | Why *adopt the parser* fails | What to do instead |
|---|---|---|
| Servicing / filing (pass 5) | It does **not** fail — format layer is free and mature | Adopt the parser, build the decision |
| Capital markets (pass 6) | The client already **pays an ARM** for the format layer | Build assurance either side of it (Pattern 19) |
| **Insurance (pass 7)** | The spec is **member-gated**; no parser may lawfully be written | **Buy the format, adopt the method, build the judgment** (Pattern 23) |

#### Pass 8 (2026-11-25) — the law gains a boundary, and the licence follows the institution

**Clause four, and it is a limit rather than an extension.** Passes 5–7 built
the law in three clauses: open-source supply follows **the file format**,
specifically the file **more than one party must read**, where **the spec is
readable without paying to join**. Pass 8 tested it on the inbound data plane
and found it holds — and found where it stops.

- **Holds:** SDMX (ISO 17369) is published, multi-party and free to read, and
  carries a healthy institutional library population — `ondata/opensdmx` (MIT,
  58★), `bis-med-it/pysdmx` (Apache-2.0), `eblondel/rsdmx` (111★),
  `amattioc/SDMX` (99★), `dr-leo/pandaSDMX` (135★).
- **Stops:** FIGI is equally open and multi-party, and its permissive library
  population is `svyatov/sec_id` at **8★**, `philaris/figir` at 4★, and a
  GPL-3.0 R wrapper last touched in **2016**.

> **Clause four: the law predicts libraries for formats you must *parse*, and
> nothing for registries you merely *query*. Where the authority runs a free
> public API, the lookup is a network call — there is no file to implement, so
> no library accretes however open the standard is.**

The commercial consequence is a correction to how an empty plane is read.
This KB has repeatedly treated "no permissive libraries" as virgin ground with
margin in it. Clause four says: **check first whether the authority simply
answers HTTP.** If it does, there is no format layer to adopt *or* to sell —
the integration is a small piece of work and the engagement has to stand on
the judgment layer from day one, without a format-layer deliverable to produce
a number in week one.

**The other global finding: institutional provenance predicts nothing about
licence.** The statistical plane is the first in this KB where many
institutions publish the same artefact type, in the same format, for the same
purpose — and the licences diverge completely.

| Institution | Licence | Class | Studio can build on it? |
|---|---|---|---|
| **BIS** (Basel) — 11 repos incl. an agentic framework | **Apache-2.0** | Permissive | Yes, fully |
| **World Bank** | **MIT** | Permissive | Yes, fully |
| **ILO** (UN, Geneva) | **BSD-2-Clause** | Permissive | Yes, fully |
| **Eurostat** (European Commission) — 95 repos | **EUPL-1.1/1.2** | **Copyleft** | Isolate behind an interface |
| **SDMX-TWG** — the ISO standard itself | **None at all** | Unlicensed spec | Cite, never vendor |
| Mexican agency clients | **CC0** | Public domain | Yes, and freer than MIT |

Two international institutions 300 km apart have opposite defaults. This
supersedes an assumption the KB relied on without writing down — that an
institutional owner implies safe reuse. **The default follows the
institution's legal culture, not the sector, the language or the ecosystem,
and the only reliable procedure is per-publisher verification.**

**The adoption numbers for this plane, cited as what they are.** From the
**BIS Irving Fisher Committee, IFC Report 17, "SDMX adoption and use of open
source tools"** (February 2025): SDMX is implemented by **about eight tenths**
of respondents, up from two thirds ten years earlier. An **SDMX Pulse**
newsletter (June 2026) puts the central-bank version mix at **2.1 — 59%,
2.0 — 35%, 3.0 — 6%**, with about two thirds of the remainder planning to move
to 3.0. The adoption figure is a 2025 survey; the version split is a
newsletter, not a peer-reviewed survey.

Both point the same way and against the instinct: **build against SDMX 2.1,
because 94% of the installed base is on 2.x**, and treat the **2.1→3.0
migration as the engagement** — an externally published standard, a
machine-checkable output, and a client who cannot opt out. Pattern 26 is that
recipe, and it gets its correctness oracle free because two permissive
implementations of the same spec exist.

**One cross-region adoption datum, new and different in kind.** The CCAF 2026
survey (628 institutions, 151 jurisdictions) finds **advanced economies nearly
seven times more likely to reach the "transforming" stage of AI use than
emerging markets.** This KB has carried CCAF's 81%/40% adoption split since
pass 4 and its regulator figures since pass 6. This figure is not about
*whether* institutions adopt but **how far adoption gets** — which makes it the
most directly sellable number in the file, because the deliverable that closes
a transforming-stage gap is engineering and evidence, not strategy. It applies
to every emerging market in scope, not only LATAM.

## Regional asymmetry — the summary

| Region | Binding AI-in-finance rules | Hard date to sell against | Posture |
|---|---|---|---|
| EMEA | Yes — EU AI Act Art.50 + DORA + CCD | **CCD in force 20 Nov 2026**; watermarking 2 Dec 2026; **Annex III deferred to 2 Dec 2027**; ECB AI action plans were due 31 Oct 2026 | Strictest, but the credit-scoring deadline moved — demand is now DORA- and CCD-driven. Adoption **86% UK / >85% euro area**, agents ~2% autonomous |
| APAC | Supervisory expectation — MAS Guidelines + SAFR (not a statute); Japan FSA technology-neutral; India RBI FREE-AI | Issued 7 Oct 2026, **implementation to 7 Oct 2027** | Most mature on *agentic* specifically. Japan sells evidence, not deadlines; India has an AI framework and no agent framework |
| North America — US | Voluntary federally; binding at state level | Colorado 30 Jun 2026 | Permissive, fragmented, examiner-driven; genAI and agentic **excluded** from model risk |
| North America — Canada | **Yes — OSFI Guideline E-23, all AI/ML models incl. vendor models** | **E-23 effective 1 May 2027**; agentic bulletin July 2026 | The strictest binding model-risk regime in the Americas. Build to E-23 and the US is covered |
| LATAM | Mostly no; Peru and Brazil Open Finance excepted; BCB signals no AI rules before end-2026 | Peru 22 Jan 2026 (in force) | Rails-led, not rules-led — and **already running agent-initiated payments** with per-payment human confirmation |

**No region returned nothing.** Every one of the four produced at least one
dated, binding or near-binding instrument — and after this pass, every one of
the four also has at least one **measured adoption or deployment number**, which
was not true yesterday.

### Gap register — what closed this pass and what is still open

**Closed 2026-11-21:**

- **EMEA named institutions.** Previously "no named-bank AI deployments at all."
  Now named from the supervisory side instead of the marketing side: the DORA
  critical ICT third-party list of **19 providers** (18 November 2025) names the
  cloud, data and consulting firms under every European bank's agent stack, and
  **BaFin's January 2026 guidance** names the supervisory expectation. This is
  better evidence than a bank press release.
- **LATAM named players and primary expectations.** Itaú, Bradesco, BBVA,
  CitiBanamex; the **CNBV's May 2026 FIDUZ authorisation** as a decided
  precedent; the BCB's prescriptive model-risk and explainability expectations.
- **Mexico's contradiction, resolved in favour of the counsel view.** Multiple
  independent sources now agree: **no AI-specific statute**, supervision runs
  through the 2018 Fintech Law, the CNBV and Banco de México's generative-AI
  guidelines. The promotional "2025 watershed" claim stays rejected.
- **APAC regional detail** beyond Singapore: HKMA and APRA posture, the MAS
  implementation timeline, third-party accountability.

**Closed 2026-11-22 — both by changing the query, not by searching harder:**

- **~~Canada.~~** Closed. Naming OSFI directly, as the previous pass
  prescribed, returned E-23, B-10 and the July 2026 agentic bulletin on the
  first query. Canada turns out to have the **strictest binding model-risk
  regime in the Americas**, with a 1 May 2027 effective date. See the North
  America section.
- **~~EMEA adoption percentages.~~** Closed, and the stated conclusion that the
  number "does not appear to exist publicly" is withdrawn. It exists and is
  published by **supervisors** — BoE/FCA (86%, 26 October 2026) and the ECB
  (>85% of significant institutions) — which is why two passes of
  market-research-shaped queries never found it. See the EMEA section.
- **Japan and India** added to APAC, which previously meant Singapore plus two
  sentences.

**Still open, stated plainly:**

- **Named UPI-ecosystem players** with AI-specific payment products — still not
  found, third pass. NPCI's position (still examining an agent framework) and
  the RBI's FREE-AI report are the only firm India data points.
- **Primary-source access.** `bankofengland.co.uk` does not resolve from this
  environment and OSFI's own pages did not surface in search results. The UK,
  euro-area and Canadian figures in this file are therefore **corroborated
  secondary reporting, not primary verification**. This is a gap in the
  *instrument*, not in the world, and it is the one a future pass should attack
  first — ideally from a session whose network policy allows regulator domains.
- **Mexico's CNBV Fintech Law 2.0 update**, reported due October 2026, status
  still unconfirmed after two passes.

---
*Researched 2026-11-09; re-verified and corrected 2026-11-21; extended
2026-11-22. Adoption percentages outside the CCAF report, the BoE/FCA survey and
the ECB figures are self-reported vendor or bank numbers and should be treated
as directional. The EU AI Act Annex III correction in the EMEA section
supersedes the dates in the 2026-11-09 revision. The 2026-11-22 pass closed the
Canada and EMEA-adoption gaps, added Japan and India, and recorded
agent-initiated payments running in LATAM — and replaced the previous "no
EMEA adoption data exists" conclusion, which was a query artefact.*

### Gap register — pass 6 additions (2026-11-25)

**Closed this pass:**

- **~~The capital-markets plane.~~** Closed, and it was the largest vocabulary
  hole in this KB. A census before the pass returned **zero** mentions of FIX
  protocol work, FpML, MiFID/MiFIR, EMIR, SFTR, CAT, custody, securities
  lending, T+1, Form PF, N-PORT, UCITS, AIFMD, CVM or B3. The plane is now
  covered — including the finding that **half of it will never be populated by
  open source** and why.
- **~~FINOS, cited and never enumerated.~~** Closed. This KB referenced "FINOS"
  19 times while `FDC3`, `morphir`, `waltz`, `rune-dsl`, `tracdap` and
  `open-reg-tech-us-lcr` had **zero** mentions between them. The organisation
  has **194 repositories**. Second confirmation of the pass-5 rule: *when a KB
  cites an organisation by name, enumerate it.*
- **~~The control-and-evidence platform.~~** Closed. Three passes concluded all
  regions converge on a control and evidence layer without naming a permissive
  platform. It is `finos/tracdap` (Apache-2.0, 58★), built on the premise that
  a regulated model run must be reproducible from immutable versioned inputs.
- **~~Counterparty reference data.~~** Closed. Every reconciliation, screening
  and reporting pattern in this KB needed to answer "who is this counterparty"
  and the KB had no entry. GLEIF/LEI tooling is permissive and live.

**Corrections to entries already in this file — read these before quoting the
summary table above:**

- **Peru.** The table records "Peru 22 Jan 2026 (in force)". Pass 6 found a
  reported **financial-sector deadline of 10 September 2026** under DS
  115-2025-PCM, with banking and credit scoring classified **high risk**. That
  date is now past, which changes Peru from a preparation play to a remediation
  one. Secondary source — verify against the decree.
- **Colorado.** The table gives 30 Jun 2026. Pass 6 found **three different
  effective dates across three sources** (1 Feb 2026, 30 Jun 2026, and a
  reference to it having been "originally slated" for Feb 2026). Treat the
  Colorado date as **unresolved** and verify against the statute. This KB has
  already been burned once by building a headline on a date that moved.
- **EU AI Act Annex III.** The table's "deferred to 2 Dec 2027" is now
  **independently corroborated**: an EMEA source reports the French regulator
  becoming a Market Surveillance Authority under the AI Act on **2 December
  2027**, and the legal KB reached 2027-12-02 by a separate research path on the
  same day. Still both secondary — EUR-Lex verification remains outstanding —
  but the direction is settled.
- **MAS "Supervisory Notice on Governance of Autonomous AI Agents" (Aug 2026).**
  Searched again, **still no primary source, second consecutive pass**. Should
  now be treated as **not existing** and dropped from client material. The
  verified artefact is the MAS **consultation on AI Risk Management
  Guidelines**. The unverified MAS AI-assisted red-teaming requirement
  (2026-07-01) is likewise still uncorroborated.

**Still open, stated plainly:**

- **Primary-source access, third pass.** `opensanctions.org` joins
  `bankofengland.co.uk` on the list of hosts that **do not resolve from this
  session** — they sit outside the session's allowed network domains. The
  OpenSanctions licence split was recoverable from the repository READMEs, but
  the commercial data-licence **pricing** was not. Any screening proposal must
  obtain it before costing. This remains a gap in the instrument, not the world.
- **LATAM capital markets.** Searched, nothing found: no B3 or CVM reporting
  library, no regional FIX or trade-reporting tooling. Recorded as an **informed
  gap**, consistent with the single-country-format explanation this KB already
  uses for SPED and CFDI.
- **LATAM supervisors' own AI adoption.** No region-specific figure surfaced.
  Not measured, not zero.
- **Named UPI-ecosystem players** with AI-specific payment products — **fourth
  pass with nothing found.** At four passes this stops being a research gap and
  becomes a finding in its own right: India's rails are mature and its
  permissive agent-layer tooling is not, and a future pass should write that up
  as the conclusion rather than re-running the query.


### Gap register — pass 7 additions (2026-11-25)

**Closed this pass:**

| Gap | Status |
|---|---|
| Insurance plane entirely absent (ACORD 0, IFRS 17 0, Solvency II 0, reinsurance 0, EIOPA 0, IAIS 0, IRDAI 0, actuarial 1) | **Closed.** 16 foundational repos, 8 agentic assets, 5 platforms, 3 patterns, all five regions placed |
| EIOPA never named in this KB | **Closed.** Aug-2025 AI governance Opinion, Feb-2026 adoption survey, 2026 work programme, Hielkema 2026-11-19 speech |
| NAIC cited once, in passing | **Closed** — with the adoption count left explicitly in conflict (23 / 25 / 27+DC+PR) because no primary source confirmed it |
| Pass 6's claim that insurance core platforms return "nothing but portfolio demos" | **Corrected.** `aposin/openinsuranceplatform` is Apache-2.0, 93★, 34 forks — and dead since 2019-11-27. Conclusion upheld, reason replaced |
| Whether a professional body's code can sit outside the MIT/Apache set | **Closed.** `casact` standardised on **MPL-2.0**, measured 9× byte-identical at 373 L / 16,724 B |
| `NOASSERTION` cause list | **Extended** — sixth cause: the licence file's first line is the **project name** (`JuliaActuary`, 81★ of MIT code at risk of being discarded) |
| Licence probe paths | **Extended** — `DESCRIPTION` added for R/CRAN packages, where the grant lives in metadata and no licence file exists (`mages/ChainLadder`, 93★) |

**Open, and deliberately left open with the reason stated:**

| Gap | Why it is still open |
|---|---|
| **NAIC Model Bulletin adoption count** | Three conflicting secondary figures; **not verified against the NAIC**. A future pass should read the NAIC's own adoption map before any count is published in a client document |
| **EU AI Act calendar** | Still in conflict (Annex III from 2026-08-02 vs Reg 2026/1744 deferral recorded in pass 6). **Must be resolved in EUR-Lex**, not on vendor pages. Third consecutive pass carrying this |
| **Commission Delegated Regulation 2026/269** | Securitisation spread-charge reduction (≈46%→≈22%, from 2027-01-30) is **secondary and illustrative**. Verify in EUR-Lex |
| **Japan FSA AI timeline** | Sources conflict: voluntary from April 2026 with phased mandatory reporting from 2027, vs continued soft law. **Verify with the FSA** |
| **EIOPA Guidelines on AI** | In the 2026 work programme, **not yet published**. Watch for publication; it will become the EMEA documentation target |
| **New Jersey AI claims-denial bill** | Committee advancement reported in trade press only; **bill status not verified at source** |
| **Takaful / Islamic insurance** | Measured empty (355 results, best 4★). Classed as a monopoly-jurisdiction format — integrate above the incumbent. **Not re-searching unless a supervisor publishes a spec** |
| **IFRS 17** | No usable open implementation: top asset has **no readable licence file on any branch**, Python engine **archived**. Re-check only if a licence file appears |
| **LATAM insurance open source** | **Measured absent**, with region vocabulary and org enumeration. Will only change if a supervisor or actuarial institute publishes — that is where every other region's insurance code lives |
| **MAS red-teaming requirement (from pass 5)** | Still **not confirmed against a primary MAS document**. Carried forward a third pass |
| **"Common Controls for AI Services" (Citi / Morgan Stanley / BofA)** | Still **press-only, no primary source**. Carried forward a third pass |
| **"MAS Supervisory Notice on Governance of Autonomous AI Agents" (Aug 2026)** | Still **uncorroborated and still not cited anywhere in this KB**. Correctly withheld for a third pass |
| **AI-in-insurance vendor rankings, any region** | Searched; no current ranking found. Not invented |

### Gap register — pass 8 additions (2026-11-25)

**Closed this pass**

| Gap | How it closed | Channel that worked |
|---|---|---|
| The inbound data plane (SDMX) absent from the entire KB | 24 repos added across `agents/top.md` and `repos/foundations.md`, all `ls-remote`-verified with licences read | Censusing the **format** (`sdmx`), then `org:bis-med-it`, `org:sdmx-twg`, `org:eurostat` |
| No central-bank-published agent framework in the KB | `bis-med-it/marco-BIS`, Apache-2.0, 89★ — BIS agentic macroeconometric framework with >1,000 tests | `org:bis-med-it` |
| Canada statistical data (third Canada closure) | `Aryan-Jhaveri/mcp-statcan`, MIT, 7,000+ series | `mcp sdmx` — **no country in the query** |
| LATAM statistical clients | `inegiR` + `banxicoR` (**CC0**), `open-economics` (MIT, Brazil) | `banxico`, `inegi`, `mcp econom` |
| APAC statistical clients | `readabs` ×2, `jpstat`, `estatapi` — **all MIT** | Package names, not institution names |
| Licence posture of institutional publishers | Measured per institution: BIS Apache-2.0, World Bank MIT, ILO BSD-2, Eurostat EUPL, SDMX-TWG none, Mexican clients CC0 | Direct licence read + `DESCRIPTION` |

**Open, measured, and stated so silence is not mistaken for coverage**

| Gap | What was searched | Status |
|---|---|---|
| **APAC central banks** — BoJ, RBI, MAS, PBoC, RBA, BoK | `sdmx`, `mcp sdmx`, `mcp fred`, `estatapi`, `jpstat`, `readabs` | **No permissive client for any of them.** The four APAC assets found are *statistical office* clients. Reach the region via IMF/OECD/BIS instead |
| **LATAM central banks** — BCB series, BCRA, BanRep, BCCh, BCRP | `sdmx`, `mcp sdmx`, `banxico`, `inegi`, `mcp econom` | **None.** Mexico is the only LATAM country with any central-bank data client, at 11★ |
| **NA** — Federal Reserve Board's own services (H.15, Z.1), OSFI, Bank of Canada | `mcp fred`, `mcp sdmx`, `sdmx` | None found; FRED route is **AGPL-3.0** |
| `khaeru/sdmx` star count | `search/repositories` `repo:` query | **Unmeasurable via that channel** (`total_count: 0` for a repo `ls-remote` resolves). Recorded as unmeasured |
| Whether **ECB IReF** relies on SDMX | Source announcing the 2030/2031 timeline | **Not stated, not assumed** |
| **UK Financial Services AI Adoption Plan** (14 July 2026) | Primary source attempt | **`www.gov.uk` outside this session's permitted network domains.** Secondary-sourced; verify before quoting |
| **Fed RFI on model risk management for AI**; Bowman's fit-for-purpose review | Law-firm commentary | **Secondary, no date, no obligation.** Signals, not deadlines |
| **MAS red teaming from 1 July 2026** | Third independent secondary path this pass | Still **secondary**; no primary MAS document read by any pass |
| `OpenCyclos` licence (`NOASSERTION`) | Not pursued | Unresolved deliberately — 5-year-stale fork of a superseded major version |
| Alleged **"MAS Supervisory Notice on Governance of Autonomous AI Agents"** (Aug 2026) | Uncorroborated since pass 5 | **Do not cite.** Pass 6's correction stands |
