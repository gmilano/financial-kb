---
industry: financial
region: Global
updated: 2026-11-21
---

# Financial Services AI — Market Intelligence

> Researched 2026-11-09, **re-verified and corrected 2026-11-21**. The
> correction this pass is material and is flagged in place: the EU AI Act
> high-risk deadline that the 2026-11-09 revision called "the strongest
> near-term regional play in this whole file" **has been deferred by 16 months**.
> See the EMEA section.

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

**Opportunity:** adverse-action reason generation that is defensible to an
examiner — the ECOA duty survives even where disparate-impact liability does not.
A 50-state patchwork also makes jurisdiction-aware model governance a sellable
product in itself. And because SR 26-2 and OCC Bulletin 2026-13 (17 April 2026)
put generative and agentic AI **outside** model-risk guidance, there is no
examiner playbook to inherit — a bank that writes its own defensible agent
control framework now is setting the de facto standard rather than complying
with one.

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

**Opportunity:** Singapore is the reference implementation. Build an
SAFR-aligned agentic control layer once in Singapore and it becomes the template
to carry into jurisdictions still drafting — India above all, where the
UPI–PayNow linkage makes agent authorisation an open question somebody will have
to answer. The third-party accountability clause is the concrete sale: an
institution that cannot swap its model provider under supervisory pressure is
non-compliant by design, and provider-abstraction work is unglamorous, scoped
and fundable.

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

### Global / cross-region

- **Agentic governance is the universal gap.** Accenture recommends a dedicated
  AgentOps function; Capgemini found nearly half of banks and insurers creating
  roles to supervise AI agents. Every region above lands on human oversight for
  credit decisions, by different legal routes.
- **The back-office finding is region-independent** and is the most reliable
  commercial signal in this file.

## Regional asymmetry — the summary

| Region | Binding AI-in-finance rules | Hard date to sell against | Posture |
|---|---|---|---|
| EMEA | Yes — EU AI Act Art.50 + DORA + CCD | **CCD in force 20 Nov 2026**; watermarking 2 Dec 2026; **Annex III deferred to 2 Dec 2027** | Strictest, but the credit-scoring deadline moved — demand is now DORA- and CCD-driven |
| APAC | Supervisory expectation — MAS Guidelines + SAFR (not a statute) | Issued 7 Oct 2026, **implementation to 7 Oct 2027** | Most mature on *agentic* specifically |
| North America | Voluntary federally; binding at state level | Colorado 30 Jun 2026 | Permissive, fragmented, examiner-driven |
| LATAM | Mostly no; Peru and Brazil Open Finance excepted | Peru 22 Jan 2026 (in force) | Rails-led, not rules-led |

**No region returned nothing.** Every one of the four produced at least one
dated, binding or near-binding instrument.

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

**Still open, stated plainly:**

- **Canada.** Searched again this pass as part of North America and it again
  produced effectively nothing; the material is overwhelmingly US-federal and
  US-state. This is now a **twice-measured gap**, not an untried one. OSFI
  should be targeted directly by name in a future pass rather than through
  regional queries, which is what has failed twice.
- **Named UPI-ecosystem players** with AI-specific payment products — still not
  found. NPCI's own position (still examining an agent framework) is the only
  firm India data point.
- **EMEA adoption percentages.** Four searches across two passes have produced
  regulation in depth and **no reliable EMEA-specific adoption statistics**. The
  CCAF global figures remain the only rigorous numbers in this file. An informed
  gap: the EMEA adoption number does not appear to exist publicly at
  region-segmented granularity.

---
*Researched 2026-11-09; re-verified and corrected 2026-11-21. Adoption
percentages outside the CCAF report are self-reported vendor or bank figures and
should be treated as directional. The EU AI Act Annex III correction in the EMEA
section supersedes the dates in the 2026-11-09 revision of this file.*
