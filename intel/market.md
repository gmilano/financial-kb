---
industry: financial
region: Global
updated: 2026-11-09
---

# Financial Services AI — Market Intelligence

> Replaces the 2026-07-02 revision, which contained a placeholder players row
> (`| — | — | — | Por completar |`) and "To research" / "Por identificar" under
> every region. Researched 2026-11-09.

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
| Tauric Research | Open source org | TradingAgents, 121.5k stars — the most-starred open financial agent framework | A simulation framework, not a deployable system |

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

**Opportunity:** adverse-action reason generation that is defensible to an
examiner — the ECOA duty survives even where disparate-impact liability does not.
A 50-state patchwork also makes jurisdiction-aware model governance a sellable
product in itself.

### EMEA

**Regulatory posture: the most demanding in the world, with a hard date.**

- **EU AI Act high-risk obligations apply from 2 August 2026** — within the next
  nine months of this writing. Annex III explicitly covers AI used in
  **creditworthiness assessment and credit scoring**, and in **life and health
  insurance underwriting**. (Vendor blogs also list fraud detection as high-risk;
  that is a vendor claim, not an Annex III item.)
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

**Opportunity:** conformity-assessment and technical-documentation work for
credit-scoring models ahead of the August 2026 date is time-boxed, mandatory and
currently under-served. This is the strongest near-term regional play in this
whole file, because the deadline is external and non-negotiable.

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

**Opportunity:** Singapore is the reference implementation. Build an
SAFR-aligned agentic control layer once in Singapore and it becomes the template
to carry into jurisdictions still drafting — India above all, where the
UPI–PayNow linkage makes agent authorisation an open question somebody will have
to answer.

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

**Opportunity:** two distinct ones. (1) Brazil's explainable-AI requirement
inside Open Finance is a compliance surface that already exists and is already
binding — unlike most of the region. (2) The Pix/Bre-B interoperability gap is an
integration problem, and agentic reconciliation across non-interoperable rails is
a concrete, unglamorous, fundable build.

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
| EMEA | Yes — EU AI Act Annex III + DORA + CCD | **2 Aug 2026**; CCD 20 Nov 2026 | Strictest; deadline-driven demand |
| APAC | Yes — MAS Guidelines + SAFR | 7 Oct 2026 (issued) | Most mature on *agentic* specifically |
| North America | Voluntary federally; binding at state level | Colorado 30 Jun 2026 | Permissive, fragmented, examiner-driven |
| LATAM | Mostly no; Peru and Brazil Open Finance excepted | Peru 22 Jan 2026 (in force) | Rails-led, not rules-led |

**No region returned nothing.** Every one of the four produced at least one
dated, binding or near-binding instrument. The genuine research gaps found this
pass, recorded rather than papered over:

- **EMEA:** the search returned no named-bank AI deployments at all — regulation
  is well covered, adoption by specific institutions is not. A follow-up pass
  should target named European banks' AI programmes.
- **APAC:** no named UPI-ecosystem players (banks, fintechs, payment apps) with
  AI-specific payment products were found.
- **LATAM:** little primary regulatory text surfaced; most LATAM sources were
  vendor and marketing material. Mexico's status is actively contradictory
  between sources.
- **North America:** Canada produced almost nothing despite being in scope for
  the region; the material is overwhelmingly US-federal and US-state.

---
*Researched 2026-11-09. Adoption percentages outside the CCAF report are
self-reported vendor or bank figures and should be treated as directional.*
