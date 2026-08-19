---
name: Find and attach a pharmacy in DoseSpot
description: Search the Surescripts pharmacy directory, read the ServiceLevel bitfield to confirm the pharmacy can accept the transaction you intend to send, attach it to the patient, and move an in-flight prescription to a different pharmacy.
api: openapi/_original/dosespot-rest-api-full-epcs-v2-swagger.json
operations:
  - Pharmacies_PharmacySearchV2
  - Pharmacies_GetPharmacyV2
  - Pharmacies_GetPharmacyRestrictionsV2
  - Pharmacies_AddPatientPharmacyV2
  - Pharmacies_GetPatientPharmaciesV2
  - Pharmacies_RemovePatientPharmacyV2
  - Prescriptions_ChangePrescriptionPharmacyV2
---

# Find and attach a pharmacy in DoseSpot

## Steps
1. **Search the directory.** `Pharmacies_PharmacySearchV2` (`GET /api/pharmacies/search`). Results are paged —
   use `pageNumber` / `pageSize` and read `PageResult.HasNext`.
2. **Read `ServiceLevel` as a bitfield, not a number.** It is a bitwise sum:
   NewRx 1, Refill 2, Change 4, RxFill 8, Cancel 16, MedHistory 32, Eligibility 64, ePA 128, Resupply 256,
   Census 512, CCR 1024, Controlled Substance (EPCS) 2048. `ServiceLevel = 2049` means NewRx + EPCS. If you are
   about to send a controlled substance, require bit 2048 — otherwise transmission fails downstream.
3. **Check restrictions** with `Pharmacies_GetPharmacyRestrictionsV2` before committing.
4. **Attach it to the patient.** `Pharmacies_AddPatientPharmacyV2`
   (`POST /api/patients/{patientId}/pharmacies`). Confirm with `Pharmacies_GetPatientPharmaciesV2`.
5. **Redirect an existing prescription** with `Prescriptions_ChangePrescriptionPharmacyV2`
   (`PATCH /api/patients/{patientId}/prescriptions/{prescriptionId}/pharmacy`). This works before transmission;
   after `eRxSent` the correct move is a cancel-and-reissue, not a pharmacy patch.
6. **Detach** with `Pharmacies_RemovePatientPharmacyV2`.

## Gotchas
- `PharmacySpecialtyType` (EPCS 2048, TwentyFourHourPharmacy 64, LongTermCare 32, MailOrder 1, Retail 8,
  Specialty 16) is a *different* bitfield from `PharmacyType` (an ordinal enum, Retail 2, MailOrder 3, …). They
  are not interchangeable; both are in `vocabulary/dosespot-vocabulary.yml`.
- Every response is HTTP 200 — check `Result.ResultCode` for the real outcome.
