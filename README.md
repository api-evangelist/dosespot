# DoseSpot

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

DoseSpot is a Surescripts- and EPCS-certified electronic prescribing (eRx) platform that EHR, EMR, telehealth and digital-health vendors embed to add the full prescription lifecycle to their own software. The REST API v2 covers patients and demographics, allergies and allergen search, Medi-Span medication and supply search, drug-drug and drug-allergy interaction screening, the Surescripts pharmacy directory, prescription creation, signing and transmission including DEA-regulated EPCS for controlled substances, refill and RxChange queues, medication history, eligibility and real-time prescription benefit, electronic prior authorization, PDMP/Narx reports, and clinician, clinic and DEA-number administration. DoseSpot publishes two Swagger 2.0 contracts from its own SwaggerHub organization - Full + EPCS (171 operations) and JumpStart + EPCS (139 operations) - rendered at docs.dosespot.com, which DoseSpot calls the official source for its technical documentation. Access is sales-gated: credentials are issued by an assigned Integration Specialist. DoseSpot is part of Interra Health, alongside its subsidiary pVerify.

**Areas:** e-Prescribing · eRx · Healthcare · Electronic Health Records · Pharmacy · EPCS · Prescriptions · Clinical · Medication · Prior Authorization · Surescripts · Medi-Span

## DoseSpot on APIs.io

Everything profiled for DoseSpot is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/dosespot/](https://apis.io/providers/dosespot/)** — or go straight to one of the APIs or properties below.

### APIs (27)

- [DoseSpot Medications API](https://apis.io/apis/dosespot/dosespot-medications-api/) — Medi-Span drug search and interaction checks.
- [DoseSpot Notifications API](https://apis.io/apis/dosespot/dosespot-notifications-api/) — Clinician notification counts and actionable items.
- [DoseSpot Patients API](https://apis.io/apis/dosespot/dosespot-patients-api/) — Patient demographics, allergies, and self-reported medications.
- [DoseSpot Pharmacies API](https://apis.io/apis/dosespot/dosespot-pharmacies-api/) — Surescripts pharmacy search and patient pharmacy management.
- [DoseSpot Prescribers API](https://apis.io/apis/dosespot/dosespot-prescribers-api/) — Clinician (prescriber) and clinic staff management.
- [DoseSpot Prescriptions API](https://apis.io/apis/dosespot/dosespot-prescriptions-api/) — Prescription creation, transmission, status, and medication history.
- [DoseSpot Allergens API](https://apis.io/apis/dosespot/dosespot-allergens-api/) — The Allergens API from DoseSpot — 3 operation(s) for allergens.
- [DoseSpot Allergies API](https://apis.io/apis/dosespot/dosespot-allergies-api/) — The Allergies API from DoseSpot — 5 operation(s) for allergies.
- [DoseSpot Clinic Favorites API](https://apis.io/apis/dosespot/dosespot-clinicfavorites-api/) — The ClinicFavorites API from DoseSpot — 7 operation(s) for clinicfavorites.
- [DoseSpot Clinic Groups API](https://apis.io/apis/dosespot/dosespot-clinicgroups-api/) — The ClinicGroups API from DoseSpot — 1 operation(s) for clinicgroups.
- [DoseSpot Clinician Favorites API](https://apis.io/apis/dosespot/dosespot-clinicianfavorites-api/) — The ClinicianFavorites API from DoseSpot — 8 operation(s) for clinicianfavorites.
- [DoseSpot Clinician Order Sets API](https://apis.io/apis/dosespot/dosespot-clinicianordersets-api/) — The ClinicianOrderSets API from DoseSpot — 3 operation(s) for clinicianordersets.
- [DoseSpot Clinicians API](https://apis.io/apis/dosespot/dosespot-clinicians-api/) — The Clinicians API from DoseSpot — 26 operation(s) for clinicians.
- [DoseSpot Clinic Order Sets API](https://apis.io/apis/dosespot/dosespot-clinicordersets-api/) — The ClinicOrderSets API from DoseSpot — 1 operation(s) for clinicordersets.
- [DoseSpot Clinics API](https://apis.io/apis/dosespot/dosespot-clinics-api/) — The Clinics API from DoseSpot — 7 operation(s) for clinics.
- [DoseSpot Diagnoses API](https://apis.io/apis/dosespot/dosespot-diagnoses-api/) — The Diagnoses API from DoseSpot — 1 operation(s) for diagnoses.
- [DoseSpot Eligibilities API](https://apis.io/apis/dosespot/dosespot-eligibilities-api/) — The Eligibilities API from DoseSpot — 4 operation(s) for eligibilities.
- [DoseSpot Interactions API](https://apis.io/apis/dosespot/dosespot-interactions-api/) — The Interactions API from DoseSpot — 3 operation(s) for interactions.
- [DoseSpot Medication History API](https://apis.io/apis/dosespot/dosespot-medicationhistory-api/) — The MedicationHistory API from DoseSpot — 2 operation(s) for medicationhistory.
- [DoseSpot Narx API](https://apis.io/apis/dosespot/dosespot-narx-api/) — The Narx API from DoseSpot — 3 operation(s) for narx.
- [DoseSpot Prior Authorizations API](https://apis.io/apis/dosespot/dosespot-priorauthorizations-api/) — The PriorAuthorizations API from DoseSpot — 16 operation(s) for priorauthorizations.
- [DoseSpot Refills API](https://apis.io/apis/dosespot/dosespot-refills-api/) — The Refills API from DoseSpot — 6 operation(s) for refills.
- [DoseSpot Rx Changes API](https://apis.io/apis/dosespot/dosespot-rxchanges-api/) — The RxChanges API from DoseSpot — 6 operation(s) for rxchanges.
- [DoseSpot Self Reported Medications API](https://apis.io/apis/dosespot/dosespot-selfreportedmedications-api/) — The SelfReportedMedications API from DoseSpot — 9 operation(s) for selfreportedmedications.
- [DoseSpot Supplies API](https://apis.io/apis/dosespot/dosespot-supplies-api/) — The Supplies API from DoseSpot — 2 operation(s) for supplies.
- [DoseSpot Transparency API](https://apis.io/apis/dosespot/dosespot-transparency-api/) — The Transparency API from DoseSpot — 1 operation(s) for transparency.
- [DoseSpot Health Check API](https://apis.io/apis/dosespot/dosespot-health-check-api/) — The Health Check API from DoseSpot — 1 operation(s) for health check.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Dosespot Webhooks](https://apis.io/asyncapis/dosespot/dosespot-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [dosespot](https://apis.io/servers/dosespot/dosespot/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Dosespot Agentic Access](https://apis.io/agentic-access/dosespot/dosespot-agentic-access/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [DoseSpot API v2 Enumerations Vocabulary](https://apis.io/vocabularies/dosespot/dosespot-vocabulary/)

#### Collections (7)

Postman and Open Collection request collections.

- [DoseSpot API](https://apis.io/collections/dosespot/open-dosespot/)
- [DoseSpot Medications API](https://apis.io/collections/dosespot/open-dosespot-medications-api/)
- [DoseSpot Medications Notifications API](https://apis.io/collections/dosespot/open-dosespot-notifications-api/)
- [DoseSpot Medications Patients API](https://apis.io/collections/dosespot/open-dosespot-patients-api/)
- [DoseSpot Medications Pharmacies API](https://apis.io/collections/dosespot/open-dosespot-pharmacies-api/)
- [DoseSpot Medications Prescribers API](https://apis.io/collections/dosespot/open-dosespot-prescribers-api/)
- [DoseSpot Medications Prescriptions API](https://apis.io/collections/dosespot/open-dosespot-prescriptions-api/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Dosespot Full Epcs V2 Overlay](https://apis.io/overlays/dosespot/dosespot-full-epcs-v2-overlay/)
- [Dosespot Jumpstart Epcs V2 Overlay](https://apis.io/overlays/dosespot/dosespot-jumpstart-epcs-v2-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Dosespot Authentication](https://apis.io/security/dosespot/dosespot-authentication/)
- [Dosespot Domain Security](https://apis.io/security/dosespot/dosespot-domain-security/)
- [Dosespot Trust Center](https://apis.io/security/dosespot/dosespot-trust-center/)
- [Dosespot Vulnerability Disclosure](https://apis.io/security/dosespot/dosespot-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Dosespot Plans Pricing](https://apis.io/plans/dosespot/dosespot-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Dosespot Rate Limits](https://apis.io/rate-limits/dosespot/dosespot-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Dosespot Finops](https://apis.io/finops/dosespot/dosespot-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.dosespot.com)
- [Documentation](https://dosespot.com/full-integration/)
- [Getting started](https://docs.dosespot.com/staging/docs/getting-started)
- [API reference](https://docs.dosespot.com/staging/docs/dosespot-rest-api-full-epcs-v2-v-full_epcsv2)
- [Sign up](https://dosespot.com/request-a-demo/)
- [Support](https://dosespot.com/request-support/)
- [Blog](https://dosespot.com/blog/)
- [Compliance](https://dosespot.com/security/)
- [Terms of service](https://dosespot.com/dosespot-legal-documentation/)
- [Privacy policy](https://dosespot.com/privacy-policy/)
- [GitHub](https://github.com/DoseSpot)
- [Status](https://status.dosespot.com/)

## API Evangelist rating

**Kin Score 58.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 51.0 |
| Contract governance | 33.3 |
| Operational transparency | 39.5 |
| Developer ergonomics | 67.3 |
| Access clarity | 71.1 |

**Agent readiness 30.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 27.3** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/dosespot/](https://apis.io/providers/dosespot/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for DoseSpot: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/dosespot/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
