---
industry: financial
region: Global
updated: 2026-11-22
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
