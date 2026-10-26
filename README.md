# DoseSpot (dosespot)

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

DoseSpot is a Surescripts- and EPCS-certified electronic prescribing (eRx) platform. Its REST API (v2) lets healthcare and EHR/EMR software embed the full prescription lifecycle - patient and clinician management, medication and drug search, pharmacy selection, e-prescribing, medication history, eligibility, and push notifications - using OAuth2 Bearer tokens scoped by clinic and clinician keys.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dosespot/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dosespot/refs/heads/main/apis.yml)

## Tags

- e-Prescribing
- eRx
- Healthcare
- EHR
- Pharmacy
- EPCS

## Timestamps

- **Created:** 2026-06-21
- **Modified:** 2026-06-21

## APIs

### DoseSpot Patients API

Create, retrieve, update, and search patients, including demographics, self-reported allergies, and self-reported medications used as the subject of a prescription.

- **Human URL:** [https://dosespot.com/full-integration/](https://dosespot.com/full-integration/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Patients
- Demographics
- Healthcare

#### Properties

- [Documentation](https://dosespot.com/full-integration/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### DoseSpot Prescriptions API

Create, send, and track prescriptions for a patient across the prescription lifecycle, retrieve prescription status, and access aggregated medication history and pending renewal/refill requests.

- **Human URL:** [https://dosespot.com/full-integration/](https://dosespot.com/full-integration/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Prescriptions
- eRx
- EPCS

#### Properties

- [Documentation](https://dosespot.com/full-integration/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### DoseSpot Medications API

Search the Medi-Span drug database for medications and supplies, retrieve drug details and strengths, and run drug-drug and drug-allergy interaction checks.

- **Human URL:** [https://dosespot.com/transitioning-to-api-v2-and-the-medi-span-drug-database/](https://dosespot.com/transitioning-to-api-v2-and-the-medi-span-drug-database/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Medications
- Drug Search
- Allergies

#### Properties

- [Documentation](https://dosespot.com/transitioning-to-api-v2-and-the-medi-span-drug-database/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### DoseSpot Pharmacies API

Search the Surescripts pharmacy directory by name, location, and specialty, and manage a patient's preferred pharmacies for prescription routing.

- **Human URL:** [https://dosespot.com/full-integration/](https://dosespot.com/full-integration/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Pharmacies
- Surescripts
- Routing

#### Properties

- [Documentation](https://dosespot.com/full-integration/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### DoseSpot Prescribers API

Create and manage clinicians (prescribers) and supporting staff within a clinic, retrieve clinician records, and configure the prescribing identities used to send eRx and EPCS transactions.

- **Human URL:** [https://dosespot.com/full-integration/](https://dosespot.com/full-integration/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Prescribers
- Clinicians
- Providers

#### Properties

- [Documentation](https://dosespot.com/full-integration/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### DoseSpot Notifications API

Retrieve clinician notification counts and actionable items (transmission errors, refill requests, pharmacy responses), and subscribe to push notifications to avoid polling the API for new events.

- **Human URL:** [https://dosespot.com/full-integration/](https://dosespot.com/full-integration/)
- **Base URL:** `https://my.dosespot.com/webapi/v2`

#### Tags

- Notifications
- Webhooks
- Push

#### Properties

- [Documentation](https://dosespot.com/full-integration/)
- [OpenAPI](openapi/dosespot-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/dosespot.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/dosespot.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/dosespot)
- [Website](https://www.dosespot.com)
- [Documentation](https://dosespot.com/full-integration/)
- [Plans](plans/dosespot-plans-pricing.yml)
- [Rate Limits](rate-limits/dosespot-rate-limits.yml)
- [Fin Ops](finops/dosespot-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
