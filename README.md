# DoseSpot (dosespot)

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
