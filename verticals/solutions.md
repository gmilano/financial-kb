---
industry: financial
region: Global
updated: 2026-11-25
---

# Vertical Platforms — Financial Services

> Working systems to start from and put an agentic layer on top of — the
> Fineract-for-banking equivalent of Odoo for ERP or OpenMRS for health.
> Verification method is in `agents/top.md`.

## Permissive — safe to fork and build on

| Platform | Repo | License | Stars | Stack | Use case |
|---|---|---|---|---|---|
| Krayin CRM | https://github.com/krayin/laravel-crm | MIT | 24,188 | Laravel / PHP | **The permissive CRM.** Fully MIT, actively pushed 2026-11-17. Leads, contacts, deals, quotes, activity timeline. For a relationship-management front end to a lending or wealth build this is the clean-license starting point |
| Aureus ERP | https://github.com/aureuserp/aureuserp | MIT | 12,265 | Laravel 12 / FilamentPHP | **The permissive ERP with real accounting.** MIT and pushed 2026-11-20. Plugin architecture. This is the answer to "we need ERPNext but cannot take GPL" — fewer third-party extensions is the trade. Note the slug: `aureus-erp/aureus-erp` does **not** exist |
| Apache Fineract | https://github.com/apache/fineract | Apache-2.0 | 2,638 | Java / Spring, REST, multi-tenant | **The core banking platform of record for open source.** Clients, loans, savings accounts and accounting entries behind a REST API. Donated to the ASF by the Mifos Initiative; built for microfinance and lending. Pushed 2026-11-20 |
| Hyperledger Fabric | https://github.com/hyperledger/fabric | Apache-2.0 | 16,800 | Go, modular consensus | Enterprise permissioned distributed ledger. Relevant for trade finance, settlement and multi-party reconciliation where participants are known and privacy matters |
| FinAegis | https://github.com/FinAegis/finaegis | Apache-2.0 | 212 | PHP 8.4 / Laravel 12, event sourcing, CQRS, GraphQL | **MCP-native core banking — new this pass.** 61 domain modules (Account, Lending, Compliance, Treasury, Wallet, Card Issuance, RegTech, Multi-Tenancy, Key Management, Privacy) plus an explicit **AI Framework** domain shipping an MCP server with 20+ banking tools, and an Agent Protocol domain for A2A messaging and escrow. Apache-2.0 verified at 11,242 B. **212 stars — early, and the architecture is opinionated** |
| Apache OFBiz | https://github.com/apache/ofbiz-framework | Apache-2.0 | 1,151 | Java | Full ERP framework with accounting, suited to a Java-bound engagement. Pushed 2026-11-20 |
| Mifos X Web App | https://github.com/openMF/web-app | MPL-2.0 | 402 | Angular | The ready-made front end for Fineract. MPL-2.0 is file-level copyleft — weaker than GPL, generally workable for a client deployment, but have legal confirm before shipping modified files |

### Fineract vs FinAegis — they are not substitutes

Fineract is the safe institutional choice: ASF governance, a decade of
production deployments, and the integration surface a bank's architects already
recognise. FinAegis is the interesting one: it was designed after agents
existed, so the MCP server and the tool definitions are first-class rather than
bolted on, and event sourcing gives you the per-decision audit trail that EU
deployments need **by construction** instead of by discipline.

Recommendation: **Fineract as the system of record, FinAegis as the reference
design for the agent layer.** Read how FinAegis models banking operations as
tools, and implement that shape against Fineract's REST API. At 212 stars,
putting FinAegis itself under a client's ledger is a decision to make with eyes
open, not a default.

## Financial crime and payment switching — new 2026-11-22

Two Apache-2.0 platforms that between them cover the two things a central bank,
a national switch or a digital-payments client actually asks for: **move the
payment**, and **stop the bad one in real time**. Neither was in this KB before
today. Both are low-star and institutionally backed, which is an unusual
combination and has to be read carefully.

| Platform | Repo / org | License | Stars | Stack | Use case |
|---|---|---|---|---|---|
| Tazama | https://github.com/tazama-lf | Apache-2.0 | 57 (docs), 26 (stack), 12 (case management) | TypeScript microservices, NATS, ArangoDB, Docker/Helm | **Real-time financial crime risk management.** Open source transaction monitoring at payment-switch scale: rules, typologies, case management, rule authoring UI. A Linux Foundation project |
| Mojaloop | https://github.com/mojaloop | Apache-2.0, by reference | 328 (hub), 60 (central-ledger) | Node.js microservices, ISO 20022 alignment, Kubernetes | **Interoperable instant-payment switch.** The open source reference implementation behind several national real-time payment schemes, aimed at interoperability between banks, mobile money and fintechs |
| openIMIS | https://github.com/openimis | **AGPL-3.0 + Swiss-law rider** | 19 (docker dist), 13 (backend) | Python/Django backend, React frontend, modular | Health insurance and social-protection scheme administration: enrolment, policies, claims. Deployed in national schemes; the only maintained open source *insurance* core found |

### Tazama — the gap this KB named as its biggest, measured closed

`repos/foundations.md` carried this as "the single biggest build-vs-buy opening
in the financial KB": no permissive, maintained AML/transaction-monitoring
platform exists. **It exists.** The reason three passes missed it is worth more
than the finding: the searches said *AML* and *transaction monitoring*, and the
project calls itself **FRMS — financial crime risk management**. The vocabulary
chose the result.

What is actually in the org, all pushed within the last week unless noted:

| Component | Repo | What it does |
|---|---|---|
| Transaction monitoring service | `tazama-lf/tms-service` | The ingress: accepts ISO 20022-shaped transaction messages and starts evaluation |
| Event director | `tazama-lf/event-director` | Routes a transaction to the rules that the active network map says apply to it |
| Rule processors | `tazama-lf/rule-901`, `tazama-lf/rule-902`, … | **One rule per repository** — e.g. 901 "amount of transactions debtor made", 902 "number of transactions creditor received". Rules are deployable units, not rows in a table |
| Typology processor | `tazama-lf/typology-processor` | Combines rule outcomes into a typology score — the "is this a known fraud shape" layer |
| Case management | `tazama-lf/case-management-system` | Investigation queue and case workflow for the humans downstream |
| Rule Studio | `tazama-lf/rule-studio`, `tazama-lf/simulation-service` | Authoring and **simulation** of rules before they go live |
| Configuration / connection studios | `tazama-lf/configuration-studio`, `tazama-lf/connection-studio` | Web UIs for platform and integration configuration |
| BI and analytics | `tazama-lf/biar` | Reporting layer |
| Payment platform adapter | `tazama-lf/payment-platform-adapter` | **Adapter for Mojaloop** — the two platforms in this section are designed to meet |
| Deployment | `tazama-lf/tazama-stack`, `tazama-lf/tazama-helm` | Docker Compose and Helm for the whole platform |

**Why the architecture matters for an AI engagement.** Rules are repositories
and typologies are composed from rule outcomes, which means a rule is a
versioned, reviewable, independently deployable artefact with its own history.
That is exactly the audit surface a supervisor asks for when a model influences
an outcome — and it is the shape an agent can safely *propose into*: an agent
drafts a rule, Rule Studio simulates it against historical traffic, a human
approves the merge. The agent never touches the live decision path. Compare the
contortions needed to get the same evidence out of a monolithic rules engine.

**The licence defect, measured in both directions.** The periphery is cleanly
licensed — `docs`, `rule-studio`, `admin-service`, `case-management-system`,
`biar`, `frms-coe-lib` and the rule repos all carry Apache-2.0 and GitHub
classifies them correctly. **Three runtime repos — `tms-service`,
`typology-processor`, `event-director` — plus `tazama-stack` have no LICENSE
file at all.** Six filename and case variants were probed on each; all 404
while control files in the same repos returned 200, so the absence is measured,
not assumed.

They are **not** unlicensed. Both machine-readable channels agree:

- `package.json` carries `"license": "Apache-2.0"` in all three service repos.
- Source files open with `// SPDX-License-Identifier: Apache-2.0`, verified in
  `tms-service/src/index.ts` and `event-director/src/index.ts`; the READMEs
  carry the same tag as an HTML comment.

A per-file SPDX identifier plus a package manifest is the form the SPDX and
REUSE specifications actually prescribe, so this is **stronger** evidence than
the README-prose case (`virattt/dexter`) this KB already separates out, and much
stronger than a shields.io badge (`bacen/pix-api`). **Globant verdict:
Apache-2.0, usable.** Two process notes: tell the client's counsel where the
grant is before they go looking for a file that is not there, and raise the
upstream issue — for a Linux Foundation project this is a defect its own
governance would want fixed, and it is a cheap, visible contribution.

### Mojaloop — and the same grant-by-reference pattern

Every `mojaloop/*` repo reports SPDX `NOASSERTION` because `LICENSE.md` is
**756 bytes**: a copyright line for the Mojaloop Foundation and the standard
"made available … under the Apache License, Version 2.0 … you may obtain a copy
of the License at" paragraph. Apache-2.0 by reference, the same shape as
`coinbase/agentkit` (`agents/top.md`). Not a concern; just not something a
classifier can see.

`mojaloop/central-ledger` was pushed 2026-11-20 and the org is active. The
combination that is interesting for a LATAM or African engagement is
**Mojaloop as the switch, Tazama as the real-time fraud layer** — the adapter
between them is maintained by the Tazama side, so the integration is not
speculative.

### openIMIS — read the rider, not just the badge

`openimis/openimis-be_py` and `openimis-fe_js` both report `NOASSERTION`. The
file is 1,852 bytes and is **AGPL-3.0 by reference** — plus a disclaimer of
warranty, a limitation of liability, **and a clause the AGPL does not contain**:
"In case of dispute arising out or in relation to the use of the program, it is
subject to the public law of Switzerland. The place of jurisdiction is Berne."

So it is not plain AGPL-3.0; it is AGPL-3.0 with a governing-law and forum
rider. For an engagement that means two separate questions for counsel — the
AGPL network-copyleft question this KB already flags on Firefly III and
Ghostfolio, and a jurisdiction question that is unusual enough that nobody will
have a template answer. Both repos were pushed 2026-11-21, so the project is
alive.

### Insurance — a measured gap, not an unsearched one

Searching GitHub for insurance core platforms (policy, claims, underwriting,
actuarial) sorted by stars returns, below openIMIS, **nothing but portfolio
demos**: the top results were 0–2 stars, several of them the same ASP.NET or
Django coursework project under different owners. There is no permissive
insurance equivalent of Fineract.

Stated precisely so a future pass does not re-walk it: **openIMIS is the only
maintained open source insurance core found, it is AGPL-3.0 with a Swiss-law
rider, and it is scoped to health and social protection — not P&C, not life,
not commercial lines.** For a P&C or life insurer engagement there is no open
starting point; the composition is a general ERP or CRM (Aureus, Krayin — both
MIT, above) plus a custom domain model. That is a build, and it should be
priced as one.

## Corrections to the previous revision

| Platform | Claim being corrected | Measured 2026-11-21 |
|---|---|---|
| Apache OFBiz | Third-party listicles recommend `apache/ofbiz` | **`apache/ofbiz` is ARCHIVED**, last pushed 2020-04-27, 804 stars; its description says main development moved. The live repo is `apache/ofbiz-framework` (Apache-2.0, 1,151 stars, pushed 2026-11-20). A naive "search and take the top hit" lands on a repo frozen for six years |
| iDURAR ERP/CRM | Listicles cite it as MIT | **AGPL-3.0**, 8,963 stars, pushed 2026-08-14. Not permissive. Listed license claims in ERP roundups were wrong on this row and on Aureus's slug in the same article |

## Copyleft or restricted — usable, but a licensing decision first

| Platform | Repo | License | Stars | Note |
|---|---|---|---|---|
| ERPNext | https://github.com/frappe/erpnext | GPL-3.0 | 41,100 | Full ERP with a real double-entry accounting module. Fine self-hosted for a client, a problem for a proprietary derivative |
| Firefly III | https://github.com/firefly-iii/firefly-iii | AGPL-3.0 | 25,200 | Personal finance manager. AGPL reaches across the network boundary — offering it as a hosted service triggers source obligations |
| Ghostfolio | https://github.com/ghostfolio/ghostfolio | AGPL-3.0 | 9,700 | Open source wealth management (Angular + NestJS + Prisma). Good bones for a wealth-management demo; same AGPL network caveat |
| iDURAR ERP/CRM | https://github.com/idurar/idurar-erp-crm | AGPL-3.0 | 8,963 | Node/React ERP+CRM with invoicing and accounting. See the correction above |
| open-net-worth | https://github.com/open-net-worth-ai/open-net-worth | AGPL-3.0 | 610 | Self-hosted personal-finance AI assistant, positioned against hosted assistants. Pushed 2026-11-21 — the fastest-moving new asset this pass |
| Jube | https://github.com/jube-home/aml-fraud-transaction-monitoring | AGPL-3.0 | 116 | **Real-time AML and fraud transaction monitoring with ML.** The only maintained open source AML *platform* found (pushed 2026-11-18). AGPL-3.0, so hosting it for a client triggers source obligations — but for an on-premises bank deployment, which is where AML runs anyway, that is far less of an obstacle than it first sounds |
| XS2A Sandbox | https://github.com/adorsys/XS2A-Sandbox | AGPL-3.0 | 81 | PSD2-compatible banking **emulator** following Berlin Group NextGenPSD2. AGPL-3.0 (34,523 B verified), and for a *test rig* that is near-zero risk: you do not ship the sandbox. The cheapest way to develop an EMEA open-banking agent without a bank sponsor |
| Akaunting | https://github.com/akaunting/akaunting | **BSL — not OSI** | 10,300 | Online accounting. Business Source License is *not* an open source license. Do not treat it as one |
| Odoo | https://github.com/odoo/odoo | open-core, LGPL-3 community | 55,700 | ERP/CRM suite, open-core since v9.0: community modules plus proprietary enterprise apps. Confirm per module. For a finance engagement that needs permissive, Aureus ERP above is the cleaner answer |

## FINOS — the governance layer, written by the banks themselves

**Added 2026-11-22 (pass 4).** Four passes of this KB have catalogued what to
*build* with and nothing about what a bank's second line will **accept**. That
artefact exists, it is open, and it is written by the institutions that do the
accepting. FINOS (the Fintech Open Source Foundation, a Linux Foundation
project) runs an AI governance effort whose **Common Controls for AI Services**
work is backed by Citigroup, Morgan Stanley and Bank of America.

| Asset | Repo | License (bytes) | Stars | Forks | Last push | What it is |
|---|---|---|---|---|---|---|
| AI Governance Framework | https://github.com/finos/ai-governance-framework | **CC-BY-4.0** (18,650) | 120 | 82 | 2026-11-18 | Catalogue of AI **risks and mitigations** for financial services, structured for onboarding, development and deployment of AI in a regulated institution. 82 forks |
| AIGF MCP server | https://github.com/finos/aigf-mcp-server | Apache-2.0 (11,336) | 10 | 6 | 2026-11-09 | **The framework as an MCP server** — an agent can query the control catalogue directly while designing or reviewing a system |
| AI reference architecture library | https://github.com/finos/ai-reference-architecture-library | Apache-2.0 (11,357) | 18 | 13 | 2026-11-19 | Reference architectures for AI systems in financial services |
| AI Readiness (SIG) | https://github.com/finos/ai-readiness | CC-BY-4.0 | 66 | — | 2026-08-13 | Cross-member working group on shared AI adoption obstacles |
| Common Domain Model | https://github.com/finos/common-domain-model | **Community Specification License 1.0** (16,142) | 296 | 142 | 2026-11-20 | Standard model for financial products, trades and lifecycle events. A *specification* licence — see the note below |
| Legend | https://github.com/finos/legend | Apache-2.0 | 1,557 | — | 2026-11-22 | Data modelling and governance platform, originally Goldman Sachs. The largest FINOS codebase; pushed today |

### Read the licences before planning the deliverable

**`ai-governance-framework` is CC-BY-4.0 — a *content* licence, not a software
licence.** This is the right choice for a control catalogue and it changes how
you use it: you may redistribute and adapt the material, including commercially,
**with attribution**. You are adopting a document, not importing a dependency,
and a client deliverable that reproduces its controls must credit FINOS.
`common-domain-model` ships the **Community Specification License 1.0**, a
standards instrument with patent and contribution terms — again a specification,
not a code grant. GitHub reports `NOASSERTION` for it.

### Why this belongs in a solutions file at all

Everything else in this KB is a thing you install. This is a thing you **cite**,
and in a regulated engagement the citation is often the harder half. The
commercial logic is the same one the legal KB found in Singapore's MinLaw
guidance: *the short, sector-specific, peer-authored document is what the client
uses as a buying criterion*, and it beats a vendor's assurances precisely
because the client's competitors wrote it.

It also composes with obligations this KB already tracks. The EU AI Act's
Article 9(10) allows AI risk management to fold into existing **DORA** ICT
processes; a control catalogue that is already mapped to financial-services
risks is the natural carrier for that consolidation. And an
`aigf-mcp-server`-shaped control catalogue is queryable **by the agent being
governed**, which is the cheapest available answer to "show me the control that
applies to this component" during a review.

**Caveat, stated rather than hidden:** FINOS publishes a framework, not a
certification. No supervisor has endorsed it. Its value is as a defensible
starting point and a shared vocabulary with the client's risk function — which
is exactly what pass 2 argued is available to whoever writes a credible agent
control framework first, given that US SR 26-2 and OCC Bulletin 2026-13 place
agentic AI **outside** existing model-risk guidance.

## Regional rails — LATAM

| Asset | Repo | License | Stars | Note |
|---|---|---|---|---|
| Pix API (official) | https://github.com/bacen/pix-api | **badge-declared Apache-2.0, no LICENSE file** | 3,010 | The **Banco Central do Brasil's own** OpenAPI 3.0 specification for Pix, latest release 2.11.0-rc1, pushed 2026-10-29, 306 forks. This is the authoritative contract for Brazil's instant-payment rail. Security is explicitly out of scope of the repo and lives in separate BCB manuals |
| OpenFin8:BR | https://github.com/OpenFin8/openfin8-br | Apache-2.0 | 0 | Brazilian Open Finance adapter: consent resources, Pix payment initiation, Pix Automático, on the FAPI-BR security profile. SPDX reads `NOASSERTION` only because three copyright lines precede the Apache text (12,066 B verified). **0 stars, early-stage** |
| pixbr | https://github.com/StrategicProjects/pixbr | MIT | 0 | Python client for the BCB Pix **Open Data** API, pandas-friendly. Useful for market-level Pix analytics rather than transacting |

**How to use the BACEN spec without a licensing problem.** Ground an agent on it
by *consuming* `openapi.yaml` to generate a typed client and tool definitions —
do not vendor the file into a client repository as though it were Apache-licensed
code, because the grant is a badge, not a filed license. The spec content is a
public regulatory artefact; the clean path is to fetch it from BCB's developer
area at build time and keep the generated client as your own work.

### LATAM batch rails — CNAB and boleto, the layer Pix did not replace

**Added 2026-11-22 (pass 4).** The three rows above are all Pix. Pix is the
story, and it is not the whole rail. Brazilian corporate collections and
payables still run on **CNAB 240/400 remessa and retorno files** and on
**boletos**, and that is where a client's accounts-receivable reconciliation
pain actually sits. These are the LATAM counterparts of NACHA (US) and
BAI2/MT940 (EMEA), and unlike those two the ecosystem is large, permissive and
has real traction.

| Asset | Repo | License (bytes) | Stars | Forks | Last push | Note |
|---|---|---|---|---|---|---|
| laravel-boleto | https://github.com/eduardokum/laravel-boleto | MIT (1,123) | 629 | 434 | 2026-11-03 | **The highest-traction LATAM payments asset found in any pass of this KB.** Generates boletos *and* CNAB remessa files, multi-bank. 434 forks is production usage, not curiosity |
| OpenCnabPHP | https://github.com/openboleto/OpenCnabPHP | MIT (1,109) | 214 | 129 | 2026-06-08 | Multi-bank generation **and reading** of CNAB 240 and CNAB 400 remessa/retorno files. The reading half is what a reconciliation agent needs |
| CnabPHP | https://github.com/andersondanilo/CnabPHP | MIT (1,081) | 325 | 192 | 2022-03-10 | Widely forked CNAB library. **Last push 2022-03-10 — stale, listed for its forks and as a format reference, not as a dependency** |
| boleto_bancario | https://github.com/tomas-stefano/boleto_bancario | MIT (1,093) | 69 | — | 2026-02-03 | Boleto issuing in Ruby, for a stack that is not PHP |
| sat-cfdi | https://github.com/Angle/sat-cfdi | MIT (1,059) | 2 | 7 | 2026-10-23 | **Mexico.** Parses and validates **CFDI 4.0** invoices against SAT rules. Low traction, but CFDI is the fiscal artefact every Mexican payable is settled against |

**Why this matters for an engagement, and it is a point the legal KB reached
first.** That KB found that porting a US billing standard (LEDES) into LATAM was
the wrong work, because the region's functional equivalent is **the national
electronic fiscal invoice** — CFDI in Mexico, NF-e/NFS-e in Brazil — not a
sector standard. The same rule holds here in the opposite direction: do not
assume a LATAM reconciliation build needs ISO 20022 tooling. **It needs CNAB and
boleto parsing and CFDI matching**, all of which exist under MIT today, and
`eduardokum/laravel-boleto` has more forks (434) than any ISO 20022 repository
found this pass.

**Caution on the PHP concentration.** Four of the five rows are PHP, which
reflects the Brazilian SMB web stack rather than a bank-grade runtime. For a
tier-1 bank engagement, treat these as **executable format specifications** —
the authoritative answer to "what exactly goes in position 63 of a CNAB 240
segment" — and port the layout, rather than deploying the library.

## How to put AI on top of these

The pattern that works is to leave the system of record alone and wrap it:

1. **Do not fork the ledger.** Fineract's REST API is the integration surface;
   stay out of its schema so upgrades stay possible.
2. **Expose the domain as tools, not as SQL.** Wrap the endpoints (client
   lookup, loan application, repayment schedule, account statement) as typed
   tool definitions an agent can call. FinAegis's AI Framework domain is a
   working reference for exactly this shape.
3. **Keep the agent out of the write path, initially.** Read and advise first;
   put every state-changing call behind an approval step. This is also what the
   regulators in `intel/market.md` expect — MAS's 7 October 2026 Guidelines put
   accountability on the firm including for third-party AI, and the EU AI Act
   lands on human oversight for credit decisions. Both PSD2 MCP servers in
   `agents/top.md` are read-only by design, which is the same lesson from the
   other direction.
4. **Log every agent action against the ledger entry it touched.** DORA has
   applied since 17 January 2025 and supervisors treat AI systems as ICT assets
   with incident-reporting duties. An agent that cannot produce an audit trail
   per decision is not deployable in the EU. Event-sourced cores give you this
   for free; a CRUD core does not.

Concrete wiring, with named repos, is in `compose/patterns.md`.

---
*Re-verified and extended 2026-11-22 (prior passes 2026-11-21, 2026-11-09).
This pass: **Tazama** added and the KB's largest named gap closed with it;
**Mojaloop** added as the switching half of the same build; **openIMIS** added
with its non-standard Swiss-law rider read out of the file; insurance declared a
**measured** gap rather than an open question; the grant-by-reference licence
pattern documented across three unrelated projects.*

---

## Compliance filing and e-invoicing platforms — new 2026-11-22 (pass 5)

Every platform in this file so far is a system a bank *runs*: core banking,
CRM, ERP, financial crime. This section covers the systems a financial
institution — or the corporate client it serves — is **obliged to file into**.
It is the most under-rated engagement surface in the KB because the deadline
is external, the output is machine-checkable, and the client cannot decide to
skip it.

| Platform / library | Repo | License | Stars | Region | What it covers |
|---|---|---|---|---|---|
| einvoicing | https://github.com/josemmo/einvoicing | MIT | 180 | EMEA | **EN 16931** — the European electronic-invoicing semantic standard. Read and create compliant invoices in PHP |
| ubl-invoice | https://github.com/num-num/ubl-invoice | MIT | 143 | EMEA | UBL and **Peppol BIS 3** document construction and validation |
| ixbrl-parse | https://github.com/kanedata/ixbrl-parse | MIT | 72 | EMEA | Inline XBRL extraction — UK statutory accounts as filed to Companies House and HMRC |
| edinet-tools | https://github.com/matthelmer/edinet-tools | MIT | 59 | APAC | Japan EDINET, 42 disclosure document types as typed Python objects |
| SAF-T | https://github.com/SimansoftMZ/SAF-T | MIT | 8 | EMEA | OECD Standard Audit File for Tax generator in .NET |
| metro2 | https://github.com/moov-io/metro2 | Apache-2.0 | 130 | North America | Metro 2 consumer credit-history reporting to the US bureaus |
| metro_2 | https://github.com/teamupstart/metro_2 | MIT | 23 | North America | Ruby Metro 2 file construction. Permissive second implementation — useful as a cross-check oracle |
| fincen | https://github.com/moov-io/fincen | Apache-2.0 | 36 | North America | FinCEN BSA E-Filing forms — SAR and CTR |

### Two implementations of one format is a testing asset, not redundancy

`moov-io/metro2` (Go, Apache-2.0) and `teamupstart/metro_2` (Ruby, MIT) build
the same file from the same spec under compatible licences. For a format where
the regulator's validator is not something you can run in CI — and FCRA
accuracy liability attaches to what you file — **generating a batch through
both and diffing the output is a correctness oracle you get for free.** The
same move is available for ISO 20022 (`moov-io/rtp20022` vs
`prowide/prowide-iso20022`, already in this KB) and for EN 16931
(`josemmo/einvoicing` vs `num-num/ubl-invoice`).

This belongs in the engagement as a deliverable, not just a technique: a
differential conformance harness is something a client's second line can read
and a regulator can be shown.

### Where this plugs into the platforms above

`apache/fineract` and `FinAegis/finaegis` are systems of record with no
statutory-filing layer — Fineract keeps the loan, it does not write the Metro 2
file the bureaus need, nor the SAR. `odoo/odoo`, `frappe/erpnext` and
`aureuserp/aureuserp` keep the books but ship country-specific fiscal modules
of wildly uneven quality under mixed licences.

The shape that works is **system of record → format library → filing agent**,
with the format library permissive and separate. It keeps the copyleft and the
country-specific churn out of the core, and it means the filing agent can be
tested against the format library's own fixtures without standing up the
platform.

### Measured: the accounting-filing gap is regional, and it inverts the rails picture

| Region | Payment rails in this KB | Accounting/statutory filing in this KB |
|---|---|---|
| North America | ACH, Fedwire, RTP, ISO 8583 — all Apache-2.0, maintained | Metro 2 ×2, FinCEN BSA — all permissive, maintained |
| EMEA | PSD2/XS2A, SEPA, `pain.001`, `camt.053` | EN 16931, Peppol BIS, iXBRL, SAF-T — all MIT |
| APAC | thin: `fzn0x/idx` (Indonesia), `kingdee/lingee-bench` | EDINET ×2 (Japan only) — MIT and Apache-2.0 |
| LATAM | **strongest in the KB**: `bacen/pix-api` (3,010★), CNAB, boleto, `sat-cfdi` | **effectively nothing** — see `repos/foundations.md` |

LATAM leads the KB on payment rails and is last on accounting filing. Brazil's
SPED/ECD returns six repositories, the best of them LGPL-3.0 with four stars
and no commit since July 2024; Mexico's contabilidad electrónica returns three,
the best GPL-2.0 and last touched in 2015. Both mandates predate Pix.

The reason is structural and worth stating before anyone treats it as an
opportunity: **EN 16931, Peppol and SAF-T are multi-country formats, SPED and
CFDI are single-country ones.** A permissive library for a multi-country format
is written once and used in a dozen jurisdictions; one for a single-country
format serves one market, where commercial fiscal-emitter vendors already own
the ground. For a LATAM engagement the realistic shape is **integrate with the
fiscal emitter the client is already obliged to use** and put the agent layer
above it — not rebuild the emitter.

---

## Pass 6 (2026-11-25) — the capital-markets stack, and a deployable screening service

Earlier passes of this file answered "what is the Fineract of banking" for
retail and payments. This pass answers it for **capital markets**, where the
assembled answer is not one platform but a FINOS stack whose pieces are each
Apache-2.0 and independently adoptable.

### Deployable platforms added this pass

| Platform | Repo | Licence | Stars | Pushed | What you get out of the box |
|---|---|---|---|---|---|
| TracDAP | https://github.com/finos/tracdap | Apache-2.0 | 58 | 2026-11-22 | A data/analytics platform whose premise is regulated use: immutable, versioned models and datasets so every run is reproducible by construction |
| Legend | https://github.com/finos/legend | Apache-2.0 | 1,558 | 2026-11-25 | Model a financial domain once, then generate stores, APIs, transformations and lineage from that model |
| TraderX | https://github.com/finos/traderX | Apache-2.0 | 110 | 2026-11-25 | A full reference trading application across many services — a realistic integration target to put an agent into |
| Vuu | https://github.com/finos/vuu | Apache-2.0 | 63 | 2026-11-25 | View server plus HTML5 grid for large, fast-updating tabular data: the blotter |
| TimeBase CE | https://github.com/finos/TimeBase-CE | Apache-2.0 | 132 | 2026-11-25 | Time-series store built for market data rates |
| yente | https://github.com/opensanctions/yente | MIT (code) | 189 | 2026-11-25 | A self-hostable screening API: entity search and bulk matching against sanctions/PEP data. **Data licensed separately — see the warning below** |
| sieve-aml | https://github.com/AbgarSim/sieve-aml | MIT | 16 | 2026-11-16 | Screening across 35+ official lists with a nightly-refreshed database and a dashboard |
| Fluxnova (BPM) | https://github.com/finos/fluxnova-bpm-platform | Apache-2.0 | 116 | 2026-11-25 | BPMN/DMN process and decision engine under FINOS governance — the deterministic workflow spine an agent should propose into rather than replace |

### Why TracDAP is the one to lead with

This KB spent three passes establishing that the deliverable all regions
converge on is a **control and evidence layer**, and had no permissive platform
to name. TracDAP is built on the assumption that a model run must be
reconstructible from versioned inputs — so the audit trail is a property of the
platform rather than a reporting exercise performed later under deadline.

The practical difference in an engagement: on a general ML platform, "show the
examiner how this decision was reached" is a project. Here it is a query.

Pair with `finos/morphir` (219★, Apache-2.0) so the rule itself is a readable,
portable IR rather than Python a reviewer has to take on trust. Together they
answer the two questions a model-risk function actually asks — *what was the
rule*, and *what exactly ran*.

### Fluxnova, and the architectural point it makes

`finos/fluxnova-bpm-platform` (116★) and `finos/fluxnova-modeler` (32★, MIT)
give a BPMN/DMN engine under foundation governance. This matters for agent
design more than it looks: everything this KB has learned about financial
agents says the **deterministic** parts — clocks, limits, segregation of
duties, approval chains — must live outside the model. A BPMN/DMN engine is
where they live. The agent proposes a transition; the engine decides whether
that transition is permitted; the engine, not the model, holds the state.

That is the same conclusion Patterns 16 and 17 reached from the dispute and
Metro 2 planes, arrived at from the platform side.

### The warning that has to travel with the screening row

`yente` is **MIT code that is not much use without data**, and the data is
**CC BY-NC 4.0** — non-commercial — with some files under `datasets/` being
third-party material OpenSanctions states it "cannot license at all". Its own
README says commercial use "may require a data licence".

For a client engagement this means: **the software is free, the screening is
not.** Price the data licence as a line item at proposal time. A screening
pilot that works beautifully on CC-BY-NC data and then cannot go to production
is the worst possible discovery point, and it is entirely avoidable by reading
two paragraphs of a README.

The same split applies to any reference-data platform: `pygleif` and
`gleif-mcp-server` are MIT, and GLEIF's LEI data is genuinely open — but that
is a fact about GLEIF's terms, **not** an inference from the repo's badge.
Check each one.

### Verification gap, declared

`opensanctions.org/licensing`, which carries the commercial data tiers, **does
not resolve from this session** — the host sits outside the session's allowed
network domains. The licence *split* above is quoted from the repositories'
own READMEs, which state it explicitly. The *pricing* of the commercial tier
is not in this KB and must be obtained before any screening proposal is costed.

### Fluxnova provenance — worth knowing before you propose it

`finos/fluxnova-modeler`'s licence file is MIT and reads
`Copyright (c) 2015-2025 Camunda Services GmbH`, and
`finos/fluxnova-bpm-platform`'s is Apache-2.0 (177 lines, the no-appendix
variant). Fluxnova is the **FINOS-hosted continuation of the Camunda 7
community platform**, built from that codebase under foundation governance.

That is a concrete answer to a question that comes up in a lot of financial
engagements: a client standing on Camunda 7 has a **governed open-source
continuation path** rather than only a commercial migration. Confirm the
project's own current statement of scope and support before committing a client
to it — the provenance here is read from licence headers and org membership,
which establishes lineage, not a roadmap.

## Pass 7 (2026-11-25) — the insurance core: correcting the *reason*, not the conclusion

Pass 6 wrote, under "Insurance — a measured gap, not an unsearched one":

> "Searching GitHub for insurance core platforms (policy, claims, underwriting,
> actuarial) sorted by stars returns, below openIMIS, **nothing but portfolio
> demos** … There is no permissive insurance equivalent of Fineract."

and closed it "so a future pass does not re-walk it". This pass re-walked it
anyway, because the probe used a **multi-word query containing the sector
noun** — the pattern rule **G-L19** already records as an AND that returns
nothing. **The conclusion survives. The supporting claim does not, and the
replacement is more useful to an engagement.**

### What a corrected search finds

| Platform | Repo | Licence (read, title line + lines) | Stars / forks | Last push | Verdict |
|---|---|---|---|---|---|
| **Open Insurance Platform** | https://github.com/aposin/openinsuranceplatform | **Apache-2.0** (202 L, 11,474 B) | 93 / 34 | **2019-11-27** | A **fully permissive core insurance platform** — policy, claims, all lines of business, B2C/B2B/B2B2C — from the **Open Source Insurance Alliance**. Dead seven years |
| **CalculusPrime-PnC** | https://github.com/aposin/CalculusPrime-PnC | **Apache-2.0** (202 L, 11,677 B) | 6 | **2019-11-28** | P&C **rating engine** — tariff calculation. Dead seven years |
| open_insure | https://github.com/daxaxelrod/open_insure | **no licence file** | 53 / 13 | 2024-01-22 | Policy management for self-insurance / group pools. 53 stars and **unlicensed** — unusable regardless of fit |
| ai-insurance-ops | https://github.com/adamblansett/ai-insurance-ops | **MIT** (20 L, 1,069 B) | 0 / 0 | 2026-11-24 | Self-hosted AI insurance ops: policy intake, claims triage, coverage verification, underwriting support. **0 stars, published the day before this pass.** A sighting, not a starting point |
| openIMIS | https://github.com/openimis | **AGPL-3.0 + Swiss-law rider** (see the pass-6 section above) | 19 / 13 | 2026-11-21 | Unchanged, and still the only *maintained* open insurance core. Health and social protection only |

### The corrected statement, written so it can be quoted to a client

**There is no maintained permissive insurance core. There was one. It was
Apache-2.0, it was built by an industry consortium, and it was abandoned in
November 2019.** Five of `aposin`'s eight repositories open their own
description with the word `ARCHIVED:`.

That changes the conversation in a specific way. "Nothing exists" invites a
client to assume nobody tried and that Globant can be first. The measured truth
is that the insurance industry's **collective** attempt at a shared permissive
core was made, published under the most permissive practical licence, attracted
34 forks, and stopped. The risk to price is **not novelty — it is a known
failure mode**, and the engagement should be shaped to avoid repeating it:
build for one carrier's lines of business, not as a would-be industry asset.

### Why the plane is closed — and it is governance, not technology

Two independent measurements converge, and together they are the central
finding of pass 7:

1. **The shared format is behind a membership fee.** ACORD — read by carrier,
   agent, broker and reinsurer — gates its Standards behind membership and paid
   programmes (programme fees; the EHR Digital Standards Programme at **$5,000
   per year**; Forms licensed separately; terms dated **2025-10-27**). GitHub
   has **no** permissive ACORD library above 8 stars, and `AL3 insurance`
   returns **0 results**.
2. **The shared code attempt is dead** (above).

So insurance fails pass 6's law for a reason pass 6 did not anticipate: the
multi-party condition *is* met and the population still does not form, because
**the specification cannot be read without paying to join**. Full statement of
the third clause in `agents/top.md` pass 7.

### What IS alive, and it is the part to compose on

The profession ships code — just not platform code, and not under the sector
noun. **Loss reserving, mortality, life contingencies, economic scenario
generation and experience analysis are all mature, maintained and permissive
or weak-copyleft**, owned by the Casualty Actuarial Society (`casact`, 45
repos), `JuliaActuary` (16 repos, three pushed the day of this pass),
`lifelib-dev` (12 repos) — fully tabulated in `repos/foundations.md` pass 7.

**So the composition for an insurer engagement is not "ERP + custom domain
model" as pass 6 proposed.** It is:

| Layer | What to use | Licence posture |
|---|---|---|
| Policy / claims **system of record** | The carrier's existing commercial PAS. **Do not attempt to replace it** — that is what `aposin` tried | n/a |
| Interchange format | **Buy it.** ACORD membership is a line item, not an engineering task | Commercial |
| **Actuarial method layer** | `casact/chainladder-python`, `lifelib`, `JuliaActuary/*` | MPL-2.0 / MIT — **wrap, do not patch** |
| Reserving correctness oracle | `mages/ChainLadder` (R) + `actuarialopensource/benchmarks` | GPL / MIT — oracle only, never shipped |
| Judgment + narrative layer | Built. See `agents/top.md` pass 7 for the seven agentic references | Client-owned |
| Scheme administration *if* health / social protection | openIMIS — **and read the Swiss-law rider** | AGPL-3.0 + rider |

**The inversion worth naming:** everywhere else in this KB the advice is
*adopt the parser, build the decision* (pass 5). On the insurance plane there
is no parser to adopt and none that may lawfully be written, so the advice
inverts to **buy the format, adopt the method, build the judgment** — and the
method layer, unusually, comes with a free correctness oracle. Pass 6 found a
different inversion in capital markets (the client already pays an ARM). Three
planes, three different reasons the default advice fails. That is now a pattern
in its own right: **check who owns the spec before assuming the format layer is
free.**

## Pass 8 (2026-11-25) — a deployable metadata registry, and a platform whose UI is open and whose core is not

Three additions, each a real system that can be stood up and have an agentic
layer put on it, plus one correction to how this file should describe Fineract.

### Fusion Metadata Registry — the deployable SDMX server

**What it is:** a structural metadata registry for SDMX — the component that
holds an institution's data structure definitions, codelists, concept schemes
and dataflows, and serves them over the SDMX REST API. It is the piece that
makes "our statistical data is governed" true rather than aspirational.

| Field | Value |
|---|---|
| Release channel | https://github.com/bis-med-it/FMR-releases |
| Licence | Apache-2.0 (175 lines, verified) |
| Owner | **Bank for International Settlements** |
| ★ / push | 4 / 2026-11-24 |
| Region | Global |

**Why four stars is not a reason to dismiss it.** This is the standing rule for
institutional software restated: the repo is a *release channel* for a server
run by central banks, not a community project competing for attention. The
signal is **owner + push date + archive flag**, and all three are good. The
same BIS org's `SDMX-dashboard-generator` (18★, Apache-2.0) is **archived** —
that is the contrast the flag exists to show.

**The agentic layer that belongs on top:** a registry is a *typed* description
of every series an institution holds. An agent given the registry can resolve
"unemployment, Spain, monthly, seasonally adjusted" to an exact dataflow key
before it fetches a single observation — which is the difference between a
cited figure and a plausible one. Wire it as described in Pattern 25.

### Cyclos — the licence shape this file has not recorded before

**What it is:** a payment platform for communities, complementary-currency
schemes, cooperatives and large organisations — the "member-to-member payments"
system that sits where Fineract sits for lending.

| Component | Repo | Licence (verified) | ★ | Push |
|---|---|---|---|---|
| Official frontend | https://github.com/cyclosproject/cyclos4-ui | **MIT** (20 lines) | 47 | 2026-11-13 |
| Fork of the last open core | https://github.com/mateli/OpenCyclos | `NOASSERTION` — unresolved | 17 | **2021-11-06** |
| Deployment package | https://github.com/jelastic-jps/cyclos | Apache-2.0 | 17 | 2025-11-27 |

**The shape, stated so it can be quoted to a client: the user interface is
open source and the engine is not.** `cyclos4-ui` is a genuine MIT frontend
published by the vendor, for a Cyclos 4 server that is commercially licensed.
`OpenCyclos` is a community fork of **Cyclos 3**, the last open-source core,
and it has not been touched since **2021**.

This is a **fourth licence shape** for this file, alongside pass 7's three. Not
"open core" in the usual sense (free core, paid add-ons) but its mirror: **free
shell, paid core.** The practical consequence is specific — you may freely fork,
rebrand and extend the Cyclos UI for a client, including putting an agentic
layer in it, but the ledger underneath is a commercial dependency and must
appear in the client's licence register and cost model from day one. Do **not**
propose `OpenCyclos` as the engine: a five-year-dormant fork of a superseded
major version is a migration project disguised as a platform.

### Apache Fineract — current state, and the gap the community itself names

This file has cited Fineract since its first revision; this pass measures it
rather than assuming it.

| Field | Value |
|---|---|
| Repo | https://github.com/apache/fineract |
| Licence | **Apache-2.0** |
| ★ / push | 2,661 / **2026-11-25** |
| Current stable | **1.15.0** (1.14.0 end-of-life) |
| Standing | **Recertified as a UN Digital Public Good** by the Digital Public Goods Alliance (announced by the ASF, November 2025) |

**The actionable gap, and it comes from the project's own community.** A May
2026 Fineract community note recorded on the Apache GSoC 2026 page states that
Fineract provides **core banking APIs but has no community-maintained
end-user layer**, the former Self-Service API having been removed, and proposes
a standalone Spring Boot **backend-for-frontend** application as the fix.

That is an unusually clean engagement opening, for three reasons: the gap is
**named by the maintainers** rather than inferred by a vendor; it sits at the
**BFF layer**, which is where an agentic interface naturally lives; and it does
not require touching the core banking engine, so it carries none of the
regulatory risk that core changes carry. A studio proposing a conversational or
agentic member-servicing layer for a credit union, cooperative or neobank on
Fineract is building the component the project says is missing — and
Apache-2.0 end to end.

**One caution to carry:** a commercial distribution exists (BaaSFlow, whose CEO
is a Fineract PMC member) which simplifies deployment. That is not a conflict,
but a client comparing "open source Fineract" against a vendor's packaged
Fineract should be told the vendor is a project insider — it changes the support
conversation, not the licence.

### What this pass could not verify, declared

The Fineract 1.15.0 version, end-of-life status and the UN Digital Public Good
recertification come from the project's own site and the ASF news entry via
search results; the BFF gap comes from the Apache GSoC 2026 wiki page. The
repository figures (stars, licence, push date) were measured directly. No
primary-source confirmation was obtained for the UK and commercial items in
this section, and `www.gov.uk` is **outside this session's permitted network
domains**, so any UK government document referenced in `intel/market.md` this
pass is secondary-sourced and marked as such there.

---

## Pass 9 (2026-11-25) — the analytics platforms you customise rather than replace

Previous passes catalogued the systems of record a financial AI engagement sits
on top of: Apache Fineract (core banking), Tazama (real-time financial crime),
Cyclos, the ledger tier. **This pass adds the analytics tier — platforms that
are not systems of record but are just as much "the thing already installed",
and which an AI layer customises rather than replaces.**

### QuantLib — the valuation platform

| | |
|---|---|
| Repo | https://github.com/lballabio/QuantLib |
| Licence | BSD-3-Clause (239-line `LICENSE.TXT`; 180-line copyright roster then a verbatim 3-clause grant) |
| Scale | 7,804★, 2,532 refs, latest tag `v1.44`, pushed 2026-11-25 |
| Bindings | `lballabio/QuantLib-SWIG` (405★, pushed 2026-11-25) — Python, Java, C#, R |

**Why it belongs in this file and not only in `repos/foundations.md`:**
QuantLib is to derivatives valuation what Odoo is to ERP — the open platform
that a serious installation extends rather than replaces, with a plugin surface
(instruments, pricing engines, term structures) that is explicitly designed for
extension. The engagement shape is identical to the ERP one: **do not rebuild
the platform, add the layer the client's business actually needs on top of it,
and use the platform's own test suite as the acceptance gate.**

Customisation surface for an AI layer: instrument and payoff definitions,
calibration routines, market-data adapters, scenario generation. The agent
belongs **outside** the pricing call — proposing calibrations, explaining
sensitivities, triaging which trades moved and why — and never inside it,
because the pricing call is the part with an oracle and the part a validator
will reproduce.

### ORE — the risk platform on top of the valuation platform

| | |
|---|---|
| Repo | https://github.com/OpenSourceRisk/Engine |
| Licence | Modified BSD (`license.txt`, 29 lines, 1,627 B) |
| Scale | 831★, 248 refs, 21 release tags, latest `v1.8.9.1`, pushed 2026-09-15 |
| UI/exploration | `OpenSourceRisk/explORE` (Apache-2.0, 1★) |

ORE extends QuantLib with exposure simulation, XVA, sensitivities and capital
analytics, and is configured by XML rather than programmed — which makes it a
**platform** in this file's sense: the client's portfolio, netting sets,
collateral agreements and scenario definitions are configuration, not code.
LSEG's post-trade group publishes about it, so it is not a lone academic
project.

**The scoping fact to put in any ORE proposal:** `ORE-SWIG`, the Python
binding, has not been pushed since **2024-06-14** while the C++ engine is
current to September 2026. **A Python-first ORE engagement includes binding
maintenance as scope.** `QuantLib-SWIG` carries no such debt.

### Strata — the independent second implementation

| | |
|---|---|
| Repo | https://github.com/OpenGamma/Strata |
| Licence | Apache-2.0 (`LICENSE.txt`, 201 lines, 11,357 B — canonical with appendix) |
| Scale | 3,029 refs, latest tag `v2.9.4`. **Star count not measurable** — `search/repositories` returns HTTP 422 for this org |

Java, from OpenGamma, and **not a QuantLib derivative.** That independence is
its value: it is the only permissive library that can serve as a **differential
oracle** against the QuantLib/ORE stack for the instruments both cover. Two
independent implementations under compatible permissive licences is the
precondition for this KB's differential-oracle patterns (16, 22, 26), and this
is the first time the valuation plane has had one.

### Credit scorecard platforms — the judgment tier that is already built

| Platform | Repo | Licence | ★ |
|---|---|---|---|
| scorecardpy | https://github.com/ShichenXie/scorecardpy | MIT | 814 |
| optbinning | https://github.com/guillermo-navas-palencia/optbinning | Apache-2.0 | 538 |
| toad | https://github.com/amphibian-dev/toad | MIT | 529 |
| scorecardpipeline | https://github.com/itlubber/scorecardpipeline | MIT | 266 |

These are end-to-end scorecard **toolchains**, not algorithms: binning,
WOE/IV transformation, feature selection, model fitting, performance reporting,
PMML export, and in `scorecardpipeline`'s case Excel report generation and
hyperparameter search across the whole pipeline. `optbinning` adds batch and
streaming optimal binning plus counterfactual explanations.

**Engagement consequence:** a client asking for "an AI credit scorecard" in
most cases needs the **governance, monitoring and explanation layer** around one
of these, not a new modelling stack. Three of them are independent
implementations of the same binning mathematics, which makes the acceptance
gate cheap to build (Pattern 31).

### EBA supervisory reporting — the filing path

| | |
|---|---|
| Repo | https://github.com/Meaningful-Data/xbridge |
| Licence | Apache-2.0 (200 lines, 11,356 B) |
| Scale | 10★, 129 refs, pushed **2026-11-25 16:34 UTC** |

Converts XBRL-XML to XBRL-CSV for EBA taxonomies — the COREP/FINREP submission
path, sitting on the EBA's own migration between the two encodings. Small,
current, permissive, and squarely on a mandated obligation with a
machine-checkable output. Customise around it; do not write a second one.

### Recorded as reference architecture, explicitly not a platform to build on

- **`mit-dci/opencbdc-tx`** (MIT at `COPYING`, 931★) — Project Hamilton's
  retail CBDC transaction processor, co-copyright *MIT Digital Currency
  Initiative and the Federal Reserve*. **No push in 20 months**; the whole
  organisation is dormant. The best public description of a high-throughput
  two-phase payment core available under a permissive licence, and not
  maintained. Read and cite; do not link.
- **`FinancePy-Org/FinancePy`** (3,239★, **GPL-3.0**) — the most convenient
  Python derivatives-pricing install in the ecosystem, and copyleft. A team
  reaching for `pip install` lands here rather than on BSD-licensed QuantLib.
  **Run the licence probe before the prototype, not after.**
- **`frtb-net/FRTB`** (13★, **AGPL-3.0**) — the only FRTB capital calculator
  found anywhere. Network copyleft, so unusable as a component in a hosted
  client platform. The FRTB plane has no permissive option at all.
- **`Fincept-Corporation/FinceptTerminal`** (34,209★, **AGPL-3.0**) — a
  terminal-style analytics application. Thirty-four thousand stars does not
  make network copyleft safe inside a client product.

### What this pass did not verify, declared

ORE's association with LSEG post-trade, the ORE release-count numbering and
QuantLib's "de facto standard" status come from project pages and vendor posts
reached through search results, which are self-reported. **Every repository
figure in this section — stars, licence text, line and byte counts, push dates,
ref counts — was measured directly** via `search/repositories`,
`raw.githubusercontent.com` and `git ls-remote`, except `Strata`'s star count
and push date, which are recorded as not measurable.
