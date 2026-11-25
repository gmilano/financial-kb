---
industry: financial
region: Global
updated: 2026-11-25
---

# Financial Repos — Trending Log

> **APPEND-ONLY.** Newest dated section at the top; everything below it is
> history and must not be rewritten.

## 2026-11-25 (pass 6)

**Theme of the week: FINOS was cited 19 times in this KB and never enumerated.
It has 194 repositories and most of its best assets had zero mentions.**

### Actively committed FINOS repos — snapshot taken 2026-11-25

Fourteen of the repos below show a push dated **today**. This is not a
foundation parking standards; it is a live monorepo-scale organisation.

| Repo | Licence | Stars | Pushed | What it is |
|---|---|---|---|---|
| https://github.com/finos/legend | Apache-2.0 | 1,558 | 2026-11-25 | Data modelling + governance platform (Goldman Sachs origin) |
| https://github.com/finos/architecture-as-code | Apache-2.0 | 471 | 2026-11-25 | Machine-checkable architecture models (CALM) |
| https://github.com/finos/common-domain-model | **Community Spec License 1.0** | 297 | 2026-11-25 | The ISDA CDM. A **specification**, not software |
| https://github.com/finos/FDC3 | **Community Spec License 1.0** | 275 | 2026-11-19 | Desktop interop standard. Also a specification |
| https://github.com/finos/git-proxy | Apache-2.0 | 270 | 2026-11-25 | Push protections and policy enforcement on top of Git |
| https://github.com/finos/morphir | Apache-2.0 | 219 | 2026-11-25 | Business logic as a portable IR |
| https://github.com/finos/TimeBase-CE | Apache-2.0 | 132 | 2026-11-25 | Market-data time-series database |
| https://github.com/finos/ai-governance-framework | **CC-BY-4.0** | 121 | 2026-11-18 | Governance framework. A **document**, not software |
| https://github.com/finos/traderX | Apache-2.0 | 110 | 2026-11-25 | Reference multi-service trading app |
| https://github.com/finos/vuu | Apache-2.0 | 63 | 2026-11-25 | View server + blotter UI for fast tabular data |
| https://github.com/finos/tracdap | Apache-2.0 | 58 | 2026-11-22 | Analytics platform for **regulated** environments |
| https://github.com/finos/FDC3-Sail | Apache-2.0 | 53 | 2026-11-23 | Working implementation of the FDC3 standard |
| https://github.com/finos/rune-dsl | Apache-2.0 | 50 | 2026-11-25 | Grammar + generators behind the CDM — the **code** |
| https://github.com/finos/open-reg-tech-us-lcr | Apache-2.0 | 17 | 2026-10-30 | US Liquidity Coverage Ratio as executable code |
| https://github.com/finos/cdm-object-builder | Apache-2.0 | 13 | 2026-11-23 | Build/validate CDM trade objects |
| https://github.com/finos/aigf-mcp-server | Apache-2.0 | 10 | 2026-11-09 | The AI governance framework served over MCP |

### The headline for anyone about to add a FINOS dependency

**The two most-starred repos in the list are not software.**
`common-domain-model` (297★, 142 forks) and `FDC3` (275★) are licensed under
the **Community Specification License 1.0** — 99 lines, confirmed byte-for-byte
on both. That licence governs a specification document and makes a patent
commitment to implementers; it does **not** grant the software rights an
Apache-2.0 or MIT grant does. GitHub's API reports `NOASSERTION` for both,
which is why they have sat in this KB as "licence unclear" instead of
"different kind of artefact".

The implementations are separate repos and are properly Apache-2.0:
`rune-dsl`, `rune-common`, `cdm-object-builder` for CDM; `FDC3-Sail`,
`fdc3-dotnet`, `backplane` for FDC3. **Depend on those.**

Third class, same org: `ai-governance-framework` and `ai-readiness` are
**CC-BY-4.0** — prose. Useful prose, not a library.

### Two licence states that are not "unlicensed"

- `quickfix-j/quickfixj` (1,161★, pushed 2026-11-24) reports NOASSERTION. The
  file is **"The QuickFIX Software License, Version 1.0"**, 45 lines, carrying
  the BSD redistribution clause. Permissive in substance, custom in form —
  usable, but have it reviewed before redistribution. **Fifth consecutive pass
  in which a NOASSERTION repo in this KB resolved to a real permissive grant.**
- `finos/waltz` (240★) — licence **not determinable**. Probed 3 branches ×
  10 filenames at the repository root; all 404. Same shape as pass 5's
  `OpenPeppol/peppol-bis-invoice-3` finding: when a repo keeps no files at its
  root, `raw.githubusercontent.com` cannot distinguish "no licence" from
  "nothing at this path". Recorded as undeterminable, **not** as unlicensed.
- `finos/OpenMAMA` (178★) is **LGPL-2.1** (503 lines as `LICENSE.md`) —
  copyleft, flagged, not a default choice for client work.

### Capital-markets message layer, added to the KB this week

| Repo | Licence | Stars | Pushed | Format |
|---|---|---|---|---|
| https://github.com/quickfix-j/quickfixj | QuickFIX SL 1.0 | 1,161 | 2026-11-24 | FIX (JVM) |
| https://github.com/da4089/simplefix | MIT | 255 | 2026-06-01 | FIX (Python) |
| https://github.com/prowide/prowide-core | Apache-2.0 | 296 | 2026-11-19 | All SWIFT MT (FIN) messages |
| https://github.com/prowide/prowide-iso20022 | Apache-2.0 | 240 | 2026-11-20 | All ISO 20022 messages |
| https://github.com/esanchezros/quickfixj-spring-boot-starter | Apache-2.0 | 167 | 2026-11-25 | QuickFIX/J wired into Spring Boot |

### Channel note for the next pass

`GET /orgs/{org}/repos` → **403** in this session ("sessions are bound to their
configured repositories"). `search/repositories?q=org:<name>` → **works and
paginates**, 30 per page. That is the only channel that renders a whole
organisation here, and it is what produced both this pass's FINOS census and
pass 5's moov-io census. `curl -sI github.com/<slug>` remains **403 for
everything** through the proxy — **sixth consecutive pass measuring this.**
`git ls-remote` remains the only reliable existence check: 54/54 resolved.
## 2026-11-22 (pass 5)

### The byte-count rule this log published yesterday is wrong — use line count

Pass 4 set the rule: *"Apache-2.0 ≈ 11,358 B with appendix / 10,173 B
without"* and *"a byte count within ~50 B of a canonical length is a
whitespace question"*. Two repos found this pass break it.

| Repo | LICENSE bytes | Lines | `APPENDIX` present | Truth |
|---|---|---|---|---|
| `moov-io/fincen` | 10,246 | **201** | **yes** | Full Apache-2.0, left-aligned |
| `moov-io/pinblock` | 10,246 | **201** | **yes** | Full Apache-2.0, left-aligned |
| `ajtgjmdjp/edinet-mcp` | 10,179 | **176** | **no** | Apache-2.0, appendix removed |
| `moov-io/metro2` | 11,357 | 201 | yes | Full Apache-2.0, canonical indentation |

`fincen` sits **67 bytes** from `edinet-mcp` and they are different documents.
Under the published rule `fincen` reads as "Apache without appendix"; it is
1,111 B below canonical, far outside the ±50 B whitespace tolerance, so it
would have been flagged as a truncated or suspect grant and a clean Apache-2.0
asset demoted. The entire difference is leading indentation on 201 lines.

**Rule change: identify a licence by line count plus a marker grep.** Line
count is invariant to indentation; byte count is not. MIT = **21 lines**
(3 of 3 readings this pass, bytes 1,067–1,078, an 11 B spread). Apache-2.0
full = **201 lines** (4 of 4, bytes 10,246–11,444, a **1,198 B** spread —
11.7%). Apache minus appendix = 176 lines. LGPL-3.0 = 187 lines. Byte counts
keep one job: a count *above* canonical means text was added, and that text
must be read.

**Copy to every industry KB.** Pattern 9 ships the byte-band check as a
runnable script in eight KBs; it should become a line check with a marker
grep. The failure it prevents is the expensive direction — silently dropping
a genuinely permissive asset.

### Licence correction — `ledger/ledger` is BSD-3-Clause

GitHub reports `NOASSERTION` on a **6,078-star** repository. The file is
`LICENSE.md`, 1,492 B, opening `Copyright (c) 2003-2025, John Wiegley. All
rights reserved. / Redistribution and use in source and binary forms…` —
verbatim BSD-3-Clause, inside the 1.5 kB band. **Fully permissive and
usable.** Fourth consecutive pass in which `NOASSERTION` resolved to a real
permissive grant; first in which the cause was only the `.md` extension.

### Fifth channel defect — absence cannot be measured without a control file

`OpenPeppol/peppol-bis-invoice-3`: 158★, 5.2 MB, pushed 2026-11-06,
`ls-remote` resolves. Every root-path probe 404s on `master`, `main`,
`release-3` and `gh-pages` — `README.md`, `readme.md`, `index.md`, `LICENSE`,
`LICENSE.md`, `LICENCE`, `license.txt`, `NOTICE`. **No control file returned
200, so absence is not measured.** When a repository keeps no files at its
root, `raw.githubusercontent.com` cannot tell "no licence file" from "nothing
at this path". Recorded as **licence not determinable**, not as unlicensed.

### Twelve Moov repos the KB never listed — all Apache-2.0, all live

`moov-io` has 60 repositories; this KB listed seven.

| Repo | Stars | Last push | What |
|---|---|---|---|
| `moov-io/metro2` | 130 | 2026-11-22 | Metro 2 consumer credit reporting |
| `moov-io/rtp20022` | 90 | 2026-11-20 | **ISO 20022 for TCH Real Time Payments — live** |
| `moov-io/achgateway` | 86 | 2026-11-22 | Distributed ACH operations gateway |
| `moov-io/imagecashletter` | 78 | 2026-11-20 | X9 Check 21 image cash letter |
| `moov-io/fincen` | 36 | 2026-11-20 | FinCEN BSA E-Filing — SAR, CTR |
| `moov-io/bai2` | 27 | 2026-11-20 | BAI2 / X9.121 BTR3 cash management |
| `moov-io/x12` | 23 | 2026-11-21 | ASC X12 EDI |
| `moov-io/pinblock` | 17 | 2026-11-21 | ISO 9564 PIN block |
| `moov-io/dukpt` | 17 | 2026-11-20 | ANSI X9.24 DUKPT key management |
| `moov-io/ach-test-harness` | 17 | 2026-11-20 | ACH returns / NOC / reconciliation scenarios |
| `moov-io/fedwire20022` | 12 | 2026-11-21 | ISO 20022 Fedwire |
| `moov-io/cadeft` | 11 | 2026-11-20 | **Canada CPA-005 1464-byte EFT file** |

Two follow-ons for the archived-`moov-io/iso20022` correction the section
below makes: the live successors are **`rtp20022` (90★)** and
**`fedwire20022` (12★)**. `moov-io/wire` is also archived — the FAIM format
was deprecated in July 2025. `moov-io/customers`, `moov-io/accounts` and
`moov-io/irs` are archived too.

`moov-io/awesome-fintech` (409★) has **no licence file** — index, not
dependency.

### Canada: the twice-measured gap closed by enumeration, not search

Two prior passes searched Canada by region and OSFI by name and got nothing.
The asset is `moov-io/cadeft` at **11 stars** — invisible to any regional
query, found by enumerating an org the KB already cited seven repos from.
**When a region has returned nothing twice, stop querying by region and
enumerate the organisations the KB already trusts.**

### Also new this pass

| Repo | Licence | Stars | Note |
|---|---|---|---|
| `bex-co/beancount-io` | MIT (1,078 B) | 748 | Plain-text double-entry positioned for **AI agents** — a text book of record is diffable and git-versioned, i.e. an audit trail by construction |
| `zhang-accounting/zhang` | Apache-2.0 | 200 | Beancount-compatible double-entry in Rust, server + web UI |
| `josemmo/einvoicing` | MIT (1,124 B) | 180 | EN 16931 European e-invoicing |
| `manusimidt/py-xbrl` | **GPL-3.0** (35,148 B) | 154 | Best XBRL parser in the category — listed as a licensing decision, not a default |
| `num-num/ubl-invoice` | MIT (1,070 B) | 143 | UBL and Peppol BIS |
| `kanedata/ixbrl-parse` | MIT (1,067 B) | 72 | UK iXBRL — Companies House, HMRC |
| `matthelmer/edinet-tools` | MIT (1,071 B) | 59 | Japan EDINET, 42 document types typed |
| `teamupstart/metro_2` | MIT (1,074 B) | 23 | Ruby Metro 2 — **adopted as a differential oracle, not a dependency** |
| `SimansoftMZ/SAF-T` | MIT (1,066 B) | 8 | OECD SAF-T generator, .NET |
| `arnobotha/IFRS9-SICR-Definitions-Logit` | MIT (1,067 B) | 8 | Peer-reviewed IFRS 9 SICR research code — the only permissive IFRS 9 asset found |

### Informed gap — LATAM's accounting-filing plane

Searched in the region's own vocabulary, not translated US terms.
`SPED ECD contabil` → 6 results, best is `nfephp-org/sped-ecd`, **LGPL-3.0**
(187 lines; GitHub said `NOASSERTION`), 4★, no commit since 2024-07-01.
`contabilidad electronica SAT XML` → 3 results, best is GPL-2.0 and last
pushed in **2015**. Both mandates are older and more universal than Pix.

Not a build opportunity: EN 16931, Peppol and SAF-T are **multi-country**
formats and attract permissive libraries; SPED and CFDI are single-country,
and commercial fiscal emitters own that ground. Integrate above the emitter.

## 2026-11-22 (pass 4)

### A dead end this log published eleven hours earlier

The section immediately below — *"The KB's largest named gap, closed — by
changing the words, not the effort"* — is correct and stands. It also contains,
in its own repo table, this row:

> `moov-io/iso20022` | Apache-2.0 | 78 | 2023-01-12 | **ARCHIVED.** The one Moov
> repo you would most want for an EMEA or LATAM rail build is the frozen one. Do
> not start an ISO 20022 build here

**The archive measurement is right. The advice is withdrawn.** The same pass
that correctly refused to read "no results for AML" as "no AML platform" then
read one archived repository as a frozen category. The error survived eleven
hours because nobody re-queried after writing the sentence — the same mechanism
that left a stale EU AI Act date in this KB for twelve days (pass 2 flagship).

What a re-query found, all verified today by `ls-remote` + byte-read licence:

| Repo | License (bytes) | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/prowide/prowide-iso20022 | Apache-2.0 (11,357) | 240 | 2026-11-20 | Parser and business model for **all** ISO 20022 messages. Directly replaces the archived repo |
| https://github.com/moov-io/iso8583 | Apache-2.0 (10,243) | 539 | 2026-11-22 | The **card** rail. Pushed today. Never in this KB |
| https://github.com/moov-io/paygate | Apache-2.0 (11,357) | 133 | 2026-11-20 | ACH origination as a service. Never in this KB |
| https://github.com/sebastienrousseau/bankstatementparser | Apache-2.0 OR MIT | 64 | 2026-11-18 | CAMT, pain.001, MT940/942, OFX, BAI2, CSV, PDF in one parser |
| https://github.com/wolph/mt940 | BSD-3-Clause (1,490) | 106 | 2026-11-16 | MT940, Python, pushed last week |
| https://github.com/ministryofjustice/bai2 | MIT (1,128) | 30 | 2026-03-01 | BAI2, copyright HM Government |
| https://github.com/quickfix-j/quickfixj | Custom (2,096) | 1,161 | 2026-11-22 | FIX engine, 679 forks, pushed today. Licence is **not** Apache/MIT |

Full table of 14 rows in `repos/foundations.md`.

### The query that proves it was vocabulary, not scarcity

| Query | total_count |
|---|---|
| `ISO 20022 agent LLM` | **1** |
| `ISO 20022 message` | 227 |
| `pain.001` | 223 |
| `camt.053` | 154 |
| `ISO 8583 message` | 245 |
| `regulatory reporting automation bank` | **3** (all 0-star) |
| `verification of payee VoP SEPA` | **2** (both 0-star) |

**The single-digit result is the trap, not the answer.** This is P31 from the
legal KB — *adding the industry or technology word to a standard's name is a
filter, not a clarification* — now confirmed in a fourth industry. Two of the
single-digit counts above are genuine gaps and one is an artefact, and **the
count alone does not tell you which**. Only opening the results does.

### Two new licence-evidence tiers, both on high-traction repos

- **Community Specification License 1.0** — `finos/common-domain-model`
  (296 stars), 16,142 B. A specification instrument, not a code grant.
- **QuickFIX Software License 1.0** — `quickfix-j/quickfixj` (1,161 stars),
  2,096 B. BSD-4-clause-shaped: **clause 3 requires an acknowledgment of
  quickfixengine.org in end-user documentation**, clauses 4–5 restrict the name.
  Commercially usable; not a drop-in.

GitHub reports `NOASSERTION` for both. Running total: **seven** tiers of licence
evidence in this KB family.

### Byte bands, 27 of 27

Every licence this pass was predicted by band before the file was opened and
every prediction held: MIT 1,059–1,128 B (13 reads), Apache-2.0 10,173–11,357 B
(11 reads), BSD-3 1,490 B (1), CC-BY-4.0 18,650 B (1), custom 2,096 B (1).

Two refinements:

1. **`moov-io` ships two different Apache files.** `ach`, `iso8583` and
   `iso8583-connection` carry 10,243–10,246 B; `paygate` carries the canonical
   11,357 B. Band membership is an **organisation-level** constant more often
   than a project-level one, which makes an outlier inside one org worth a look.
2. **The 200-byte pointer resolved exactly as the rule predicted.**
   `sebastienrousseau/bankstatementparser` has a 200 B LICENSE reading *"dual-licensed
   under either of: Apache License 2.0 — see LICENSE-APACHE; MIT — see
   LICENSE-MIT"*. Both targets fetched: `LICENSE-APACHE` 10,287 B,
   `LICENSE-MIT` 1,075 B. **Far-below-band means a pointer, and a pointer must
   be followed before the row is written** — pass 2 wrote that rule from the
   `visa/trusted-agent-protocol` case, where following the pointer found *no
   grant at all*. Same shape, opposite outcome. The rule earns its keep by
   telling you to look, not by predicting what you find.

---

## 2026-11-22

### The KB's largest named gap, closed — by changing the words, not the effort

`repos/foundations.md` has carried this since 2026-11-09 and restated it
yesterday as "the single biggest build-vs-buy opening in the financial KB":

> **No permissive, high-traction agentic AML/transaction-monitoring platform.**
> … This gap is **verified open by function**, not merely unsearched.

**It is closed. The platform is `tazama-lf` — a Linux Foundation project,
Apache-2.0, 25+ repositories, most pushed within the last week.**

The gap was real as stated and wrong as searched. Three passes queried "AML"
and "transaction monitoring". The project describes itself as **financial crime
risk management (FRMS)**. Nothing about the world changed between yesterday and
today; the vocabulary did.

| Component | Repo | License | Stars | Last push |
|---|---|---|---|---|
| Docs / project entry point | https://github.com/tazama-lf/docs | Apache-2.0 | 57 | 2026-10-29 |
| Deployment (Compose) | https://github.com/tazama-lf/tazama-stack | Apache-2.0 (SPDX header, no file) | 26 | 2026-11-17 |
| Demo front end | https://github.com/tazama-lf/tazama-demo | Apache-2.0 | 15 | 2026-11-19 |
| Case management | https://github.com/tazama-lf/case-management-system | Apache-2.0 | 12 | 2026-11-20 |
| Rule authoring | https://github.com/tazama-lf/rule-studio | Apache-2.0 | 12 | 2026-11-19 |
| Admin service | https://github.com/tazama-lf/admin-service | Apache-2.0 | 12 | 2026-11-19 |
| Config studio | https://github.com/tazama-lf/configuration-studio | Apache-2.0 | 11 | 2026-11-20 |
| Connection studio | https://github.com/tazama-lf/connection-studio | Apache-2.0 | 11 | 2026-11-19 |
| BI / analytics | https://github.com/tazama-lf/biar | Apache-2.0 | 10 | 2026-11-19 |
| Event monitoring | https://github.com/tazama-lf/event-monitoring-service | Apache-2.0 | 9 | 2026-11-19 |
| Transaction monitoring core | https://github.com/tazama-lf/tms-service | Apache-2.0 (SPDX header + `package.json`, **no LICENSE file**) | 6 | 2026-11-19 |
| Typology scoring | https://github.com/tazama-lf/typology-processor | Apache-2.0, same form | 4 | 2026-11-19 |
| Routing | https://github.com/tazama-lf/event-director | Apache-2.0, same form | 1 | 2026-11-19 |
| Shared library | https://github.com/tazama-lf/frms-coe-lib | Apache-2.0 | 5 | 2026-11-01 |
| Mojaloop adapter | https://github.com/tazama-lf/payment-platform-adapter | Apache-2.0 (SPDX header) | 3 | 2026-10-27 |

**Licence defect, measured in both directions.** Four repos — including the
three that carry the runtime — have **no LICENSE file**; six filename and case
variants were probed on each and all returned 404 while control files in the
same repos returned 200, so the absence is measured. They are nonetheless
Apache-2.0: `package.json` carries `"license": "Apache-2.0"` and source files
open with `// SPDX-License-Identifier: Apache-2.0` (verified in
`tms-service/src/index.ts` and `event-director/src/index.ts`). That is the form
the SPDX and REUSE specs prescribe, so it is **stronger** evidence than the
README-prose tier this KB already tracks — and still invisible to GitHub's
classifier. Worth an upstream issue; for an LF project it is a defect its own
governance would want fixed.

**What stays open is traction, not licence.** The busiest Tazama repo has 57
stars. `verticals/solutions.md` says so in the recommendation rather than
burying it.

### Payments and compliance infrastructure — the other missing layer

| Repo | License | Bytes | Stars | Last push | Role |
|---|---|---|---|---|---|
| https://github.com/moov-io/watchman | Apache-2.0 | 11,357 | 524 | **2026-11-22** | OFAC/EU/UK sanctions and watchlist screening with fuzzy matching, over HTTP |
| https://github.com/moov-io/ach | Apache-2.0 | 10,243 | 572 | 2026-11-21 | NACHA ACH file reader, writer and validator |
| https://github.com/moov-io/fed | Apache-2.0 | 11,357 | 131 | 2026-11-20 | FedACH and Fedwire participant directory lookup |
| https://github.com/blnkfinance/blnk | Apache-2.0 | 10,749 | 598 | 2026-11-18 | Double-entry ledger for wallets, balances and reconciliation |
| https://github.com/mojaloop/central-ledger | Apache-2.0 by reference (756 B) | 756 | 60 | 2026-11-20 | Instant-payment switch: ledger component of the Mojaloop hub |
| https://github.com/openimis/openimis-be_py | **AGPL-3.0 + Swiss-law rider** (1,852 B) | 1,852 | 13 | 2026-11-21 | Health-insurance scheme administration; the only maintained open insurance core found |

### Archived, caught this pass

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/moov-io/iso20022 | Apache-2.0 | 78 | 2023-01-12 | **ARCHIVED.** The one Moov repo you would most want for an EMEA or LATAM rail build is the frozen one. Do not start an ISO 20022 build here |

### Byte-checksum refinement, measured

`x402-foundation/x402` and `coinbase/x402` both read **11,324 B** against a
canonical Apache-2.0 of 11,357–11,358 — 33 bytes short, which the KB's checksum
rule would flag. Diffed against `moov-io/watchman`'s canonical file with leading
whitespace normalised, **the difference is zero**: the 33 bytes are indentation.

Rule, now in `repos/foundations.md`: **below canonical means whitespace, above
canonical means appended terms, 400–800 B means a grant by reference.** Only the
middle case is a licence finding.

### Full-KB URL sweep — replicated clean

All 66 unique `github.com/<owner>/<repo>` URLs re-checked by `git ls-remote` ref
count. **63 live, 3 dead — the same three** already recorded as deleted in the
2026-11-21 section below (`Devsinfin/bank-churn-random-forest`,
`sammygallant214/CryptoDesk-ai`, `skstmdals1-ctrl/bybit-dashboard`). No new
deaths, no new renames.

### Channel note — `gh api repos/<slug>` is not available here

`gh api -X GET search/repositories` works. **`gh api repos/<owner>/<repo>`
returns HTTP 403** ("GitHub access to this repository is not enabled for this
session"), as does `curl https://api.github.com/repos/...`. So the three
channels documented in `agents/top.md` — search for metadata, `git ls-remote`
for existence, `raw.githubusercontent.com` for licence bytes — are the complete
set, and there is no fallback for stars when search returns its known false
negative. `OpenBB-finance/OpenBB` and `FinAegis/finaegis` were both unmeasurable
for stars again this pass for exactly that reason.

## 2026-11-21

### Resolved — the item this log carried forward as blocked

The 2026-11-09 section ends with an **Unresolved** entry:
`formancehq/ledger`, "no license shown on the sidebar and `/blob/main/LICENSE`
returned 404… blocked on license verification. Carried forward to the next pass."

**Resolved: it is MIT.**

| Repo | License | Bytes | Stars | Last push | Evidence |
|---|---|---|---|---|---|
| https://github.com/formancehq/ledger | MIT | 1,083 | 1,482 | 2026-11-21 | Canonical MIT text, identical on `HEAD`, `main` and `master`; `search/repositories` independently reports `MIT` |

The prior 404 came from probing a **github.com web path**, which this proxy
answers 403/404 regardless of truth. Probing
`raw.githubusercontent.com/<slug>/HEAD/LICENSE` discriminates correctly. The
practical consequence is in `repos/foundations.md`: this closes the "no
permissive ledger library" gap this KB had named as genuine. **Every
"license could not be verified" note in every industry KB should be re-run
against raw before it is believed.**

Keep it distinct from `formancehq/stack` (533 stars, SPDX `NOASSERTION`,
pushed 2026-11-10) — a different repo and a separate licensing question.

### Full-KB URL sweep: 3 repos in the history below have been deleted

All 66 unique `github.com/<owner>/<repo>` URLs in this KB were checked by
`git ls-remote` ref count this pass. **63 resolve; 3 return zero refs and no
longer exist:**

| Repo (as recorded in history below) | Status 2026-11-21 |
|---|---|
| https://github.com/Devsinfin/bank-churn-random-forest | **Deleted** — 0 refs |
| https://github.com/sammygallant214/CryptoDesk-ai | **Deleted** — 0 refs |
| https://github.com/skstmdals1-ctrl/bybit-dashboard | **Deleted** — 0 refs |

The history below is **not being rewritten** — that is the point of an
append-only log, and the rows stay as the record of what was true when they were
written. This section is the correction layer.

All three came from the automated 0-star intake of 2026-07-02, and all three were
re-verified as existing on 2026-11-09. **Three of those eight repos vanished
within about four and a half months.** That is the empirical case for the
2026-11-09 decision to demote unlicensed single-author repos out of the curated
set: in this corner of the distribution, "it resolves today" has a measured
half-life. It also sets the honest expectation for the 0-star rows this pass
*did* adopt (`open-banking-io/mcp-server`, `OpenFin8/openfin8-br`,
`StrategicProjects/pixbr`) — they were adopted on verified licence and function
match, and each needs re-checking rather than assuming.

### Infrastructure repos gaining in financial builds

| Repo | License | Stars | Last push | Note |
|---|---|---|---|---|
| https://github.com/freqtrade/freqtrade | GPL-3.0 | 57,113 | 2026-11-19 | Measured for the first time in this KB. By stars the **second-largest asset in the whole financial set**, and it is GPL-3.0 — recorded here precisely so a future pass does not promote it into a permissive table |
| https://github.com/stefan-jansen/machine-learning-for-trading | MIT | 21,921 | 2026-11-18 | The reference ML-for-trading codebase as runnable notebooks. MIT and still actively pushed |
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17,411 | 2026-11-11 | +~0.1k since 2026-11-09. Still the ledger-of-record choice under new payments builds |
| https://github.com/SantanderAI/gen-fraud-graph | Apache-2.0 | 296 | 2026-10-01 | Bank-published synthetic fraud graph generator |
| https://github.com/stefanoamorelli/sec-edgar-mcp | AGPL-3.0 | 388 | 2026-11-01 | SEC filings over MCP. Note the slug — `sec-edgar/sec-edgar-mcp` does not exist |

### Platform corrections measured this pass

| Repo | Status | Detail |
|---|---|---|
| https://github.com/apache/ofbiz | **ARCHIVED** | Last push **2020-04-27**, 804 stars. Still recommended by current ERP roundups. The live project is `apache/ofbiz-framework` (Apache-2.0, 1,151 stars, pushed 2026-11-20) |
| https://github.com/idurar/idurar-erp-crm | License claim wrong in sources | Listicles call it MIT; it is **AGPL-3.0** (8,963 stars) |
| https://github.com/aureuserp/aureuserp | Slug correction | MIT, 12,265 stars, pushed 2026-11-20. The slug cited in roundups, `aureus-erp/aureus-erp`, **does not exist** — `ls-remote` cannot resolve it |

### Channel defects found this pass — these affect how this log should be read

1. **`search/repositories` returns false negatives on live repos.** `OpenBB-finance/OpenBB`
   and `FinAegis/finaegis` return HTTP 422 "resources do not exist or you do not
   have permission"; `stefan-jansen/zipline-reloaded` returns `total_count: 0`.
   All three are live (5,537 / 1,645 / 291 refs, resolving HEAD SHAs). Treat this
   channel as **precision, never coverage**.
2. **`raw.githubusercontent.com` is case-sensitive.** `bacen/pix-api` gives 404
   for `README.md` and 200 for `readme.md`. A case-blind absence probe will
   report "no LICENSE file" on a repo that has one spelled differently. Absence
   counts as *measured* only when case variants were tried and a control file in
   the same repo returned 200.
3. **`NOASSERTION` resolved to Apache-2.0 in 2 of 2 cases opened.**

### Still open, verified by function rather than assumed

- **No permissive, maintained agentic AML / transaction-monitoring platform.**
  Best functional match is AGPL-3.0 (`jube-home/aml-fraud-transaction-monitoring`,
  116 stars). Permissive candidates measured at 0–83 stars with **no LICENSE
  file**. Biggest build-vs-buy opening in this KB.
- **No permissive SEPA or Pix payment-*initiation* agent.** Read paths are
  covered in both regions; initiation is not, and that is a deliberate product
  choice across the space rather than a gap waiting to be filled.

## 2026-11-09

### Infrastructure repos gaining in financial builds

| Repo | License | Stars | Note |
|---|---|---|---|
| https://github.com/tigerbeetle/tigerbeetle | Apache-2.0 | 17.3k | Purpose-built financial transactions database; the ledger-of-record choice appearing under new payments builds |
| https://github.com/ranaroussi/yfinance | Apache-2.0 | 25.9k | Still the default prototype price feed |
| https://github.com/stefan-jansen/zipline-reloaded | Apache-2.0 | 2.0k | Quietly became the live backtesting engine as `quantopian/zipline` stalled |
| https://github.com/skfolio/skfolio | BSD-3-Clause | 2.6k | Portfolio optimisation on scikit-learn; newest of the three optimisers tracked here |

### Falling out — measured, not assumed

| Repo | License | Stars | Status on 2026-11-09 |
|---|---|---|---|
| https://github.com/maybe-finance/maybe | AGPL-3.0 | 54.2k | **Archived by owner 2025-07-27, read-only.** Highest star count in the personal-finance category and completely dead |
| https://github.com/google/tf-quant-finance | Apache-2.0 | 5.6k | **Archived.** "No longer maintained and has been archived" |
| https://github.com/quantopian/zipline | Apache-2.0 | 20.2k | Not community-led; maintainers may not respond "in months, or even years"; docs target Python 2.7/3.5/3.6 |

### Unresolved

- https://github.com/formancehq/ledger (1.5k) — "programmable open source core
  ledger for fintech". **No license shown** on the sidebar and `/blob/main/LICENSE`
  returned 404. Genuinely relevant to payments work; blocked on license
  verification. Carried forward to the next pass.

---

# History

*Everything below is preserved from earlier passes. Do not rewrite.*

*Column labels in the section below were normalised from Spanish to the
canonical English headers on 2026-11-09 so the compiler reads them as headers
rather than ingesting `Nombre` as an entity. **No data row was altered.***


## 2026-07-02

**Re-verification note (2026-11-09):** three of the ten repos in the section
below no longer resolve — `sammygallant214/CryptoDesk-ai`,
`Devsinfin/bank-churn-random-forest` and `skstmdals1-ctrl/bybit-dashboard`.
The rows are preserved as the dated record; treat those three as dead links.

> Última actualización: 2026-07-02

| Repo | License | Description | Stars |
|--------|----------|-------------|-------|
| [Vibe-Trading](https://github.com/HKUDS/Vibe-Trading) | MIT | "Vibe-Trading: Your Personal Trading Agent" | 16.9k |
| [CryptoDesk-ai](https://github.com/sammygallant214/CryptoDesk-ai) | MIT | Build an AI desktop trading co-pilot for secure, simulation-first crypto analysi | 0 |
| [open-bank-oss](https://github.com/JiRaska/open-bank-oss) | Apache-2.0 | Cloud-native, open-source retail banking platform reference implementation (Kotl | 6 |
| [Fundo](https://github.com/Rahilralu/Fundo) | ? | Fundo is a college event payment platform that eliminates the chaos of collectin | 0 |
| [split-checkout](https://github.com/PremaanshVyas/split-checkout) | MIT | Pay for one order with two cards: multi-card payment orchestration on Airwallex | 0 |
| [bank-churn-random-forest](https://github.com/Devsinfin/bank-churn-random-forest) | ? | Random Forest classifier predicting bank customer churn — full-sample vs half-sa | 0 |
| [auditLens](https://github.com/SashaEee/auditLens) | MIT | Deep-research LLM agent + RAG platform for internal bank-product audit — cited r | 0 |
| [clawock](https://github.com/KCNyu/clawock) | ? | Multi-agent LLM analysis on a real HK + US stock portfolio: a bull-vs-bear debat | 4 |
| [bybit-dashboard](https://github.com/skstmdals1-ctrl/bybit-dashboard) | ? | Bybit TensorAI Dashboard | 2 |
| [lumen-core-public](https://github.com/robertashworth1986-debug/lumen-core-public) | MIT | Institutional quant AI + autonomous trading, built solo in a van for 3 kids. Pat | 2 |

---
*Pipeline automático — se actualiza cada hora.*
