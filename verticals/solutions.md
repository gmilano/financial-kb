---
industry: financial
region: Global
updated: 2026-11-21
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
*Re-verified and extended 2026-11-21. Three permissive platforms added
(Krayin MIT, Aureus ERP MIT, FinAegis Apache-2.0), two listicle license claims
corrected, one archived repo caught, LATAM rails section added.*
