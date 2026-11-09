---
industry: financial
region: Global
updated: 2026-11-09
---

# Vertical Platforms — Financial Services

> Working systems to start from and put an agentic layer on top of — the
> Fineract-for-banking equivalent of Odoo for ERP or OpenMRS for health.
> The previous revision of this file contained a single placeholder row
> (`| — | — | — | — | Por completar |`) and no real platform. Verified
> individually on 2026-11-09.

## Permissive — safe to fork and build on

| Platform | Repo | License | Stars | Stack | Use case |
|---|---|---|---|---|---|
| Apache Fineract | https://github.com/apache/fineract | Apache-2.0 | 2.6k | Java / Spring, REST, multi-tenant | **The core banking platform of record for open source.** Holds clients, loans, savings accounts and accounting entries behind a REST API. Donated to the ASF by the Mifos Initiative; built for microfinance and lending |
| Mifos X Web App | https://github.com/openMF/web-app | MPL-2.0 | 397 | Angular | The ready-made front end for Fineract. MPL-2.0 is file-level copyleft — weaker than GPL, generally workable for a client deployment, but have legal confirm before shipping modified files |
| Hyperledger Fabric | https://github.com/hyperledger/fabric | Apache-2.0 | 16.8k | Go, modular consensus | Enterprise-grade permissioned distributed ledger. Relevant for trade finance, settlement and multi-party reconciliation where participants are known and privacy matters |

Also in the Mifos family: **https://github.com/openMF/android-client**, the mobile
field-officer client for Fineract. It exists and resolves, but its license and star
count were not captured this pass, so it is named here in prose rather than given a
data row with empty cells — verify both before using it.

## Copyleft or restricted — usable, but a licensing decision first

| Platform | Repo | License | Stars | Note |
|---|---|---|---|---|
| ERPNext | https://github.com/frappe/erpnext | GPL-3.0 | 41.1k | Full ERP with a real double-entry accounting module. GPL-3.0: fine for a self-hosted client deployment, a problem if Globant wants to ship a proprietary derivative |
| Firefly III | https://github.com/firefly-iii/firefly-iii | AGPL-3.0 | 25.2k | Personal finance manager. AGPL reaches across the network boundary — offering it as a hosted service triggers source obligations |
| Ghostfolio | https://github.com/ghostfolio/ghostfolio | AGPL-3.0 | 9.7k | Open source wealth management (Angular + NestJS + Prisma + TypeScript). Good bones for a wealth-management demo; same AGPL network caveat |
| Akaunting | https://github.com/akaunting/akaunting | **BSL — not OSI** | 10.3k | Online accounting software. Released under the Business Source License, which is *not* an open source license. Do not treat it as one |
| Odoo | https://github.com/odoo/odoo | open-core, **license not shown** | 55.7k | ERP/CRM suite. Open-core since v9.0: community modules plus proprietary enterprise apps and SaaS. The sidebar shows no license name; community edition is generally LGPL-3. Confirm per module |

## Excluded — archived

| Platform | Repo | License | Stars | Why |
|---|---|---|---|---|
| Maybe | https://github.com/maybe-finance/maybe | AGPL-3.0 | 54.2k | **Archived by the owner on 2025-07-27, now read-only.** README: "This repository is no longer actively maintained." Despite 54.2k stars it is a dead end — named here precisely because its star count makes it look like a strong candidate |

## How to put AI on top of these

The pattern that works is to leave the system of record alone and wrap it:

1. **Do not fork the ledger.** Fineract's REST API is the integration surface;
   keep upgrades possible by staying out of its schema.
2. **Expose the domain as tools, not as SQL.** Wrap the Fineract endpoints
   (client lookup, loan application, repayment schedule, account statement) as
   typed tool definitions an agent can call.
3. **Keep the agent out of the write path, initially.** Read and advise first;
   put every state-changing call behind an approval step. This is also what the
   regulators quoted in `intel/market.md` expect — MAS's October 2026 guidelines
   and the EU AI Act both land on human oversight for credit decisions.
4. **Log every agent action against the ledger entry it touched.** DORA treats
   AI systems as ICT assets with incident-reporting duties; an agent that cannot
   produce an audit trail per decision is not deployable in the EU.

Concrete wiring, with named repos, is in `compose/patterns.md`.

---
*Verified and rewritten 2026-11-09.*
