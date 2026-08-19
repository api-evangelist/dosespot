---
name: Onboard a patient into DoseSpot
description: Create or find a patient, record allergies and self-reported medications, and pull medication history so the clinical decision support checks have something to work with before any prescription is written.
api: openapi/_original/dosespot-rest-api-full-epcs-v2-swagger.json
operations:
  - Patients_SearchPatientsV2
  - Patients_AddPatientV2
  - Patients_GetPatientDemographicDataV2
  - Patients_EditPatientDemographicDataV2
  - Allergies_AddCodedPatientAllergyV2
  - Allergies_AddNoKnownPatientAllergyV2
  - Allergies_GetPatientAllergiesV2
  - Allergens_AllergenSearchV2
  - SelfReportedMedications_AddSelfReportedMedicationCodedV2
  - MedicationHistory_LogPatientMedicationHistoryConsentV2
  - MedicationHistory_GetMedicationHistoryV2
---

# Onboard a patient into DoseSpot

## Before you start
- Send both headers on every request: `Ocp-Apim-Subscription-Key` (your DoseSpot subscription key) and
  `Authorization: Bearer <token>`. Credentials come from your DoseSpot Integration Specialist — there is no
  self-serve signup.
- Base URL: `https://staging.dosespot.com/webapi/v2` for staging, `https://my.dosespot.com/webapi/v2` for
  production. All operation paths below are appended to that base.
- **Read the outcome from the envelope, not the HTTP status.** Every operation returns 200. Success or failure
  is on `Result.ResultCode` (see `errors/dosespot-error-codes.yml`): `1` = Success, `2021` = DuplicatePatient,
  `2029` = ClinicianHasNoAccessToPatient, `3001` = AuthorizationError.

## Steps
1. **Look before you create.** `Patients_SearchPatientsV2` (`GET /api/patients/search`). Creating blind returns
   `ResultCode 2021 DuplicatePatient`; there is no idempotency key on this API, so a retried POST creates a
   second patient.
2. **Create the patient.** `Patients_AddPatientV2` (`POST /api/patients`). Field rules are strict and enforced:
   `State` must be a two-character US abbreviation or the full name, ZIP is 5 or 9 digits (ZIP+4 without the
   hyphen), phone numbers are 10 US digits, no `555` area code, no 7+ repeated digits, extensions after an `x`.
   A length overrun returns HTTP 400.
3. **Record allergies — including the absence of them.** Search coded allergens with
   `Allergens_AllergenSearchV2`, then `Allergies_AddCodedPatientAllergyV2`. If the patient reports none, call
   `Allergies_AddNoKnownPatientAllergyV2` explicitly; leaving allergies empty is not the same statement and
   weakens the interaction screen in the prescribe skill.
4. **Capture self-reported medications** with `SelfReportedMedications_AddSelfReportedMedicationCodedV2` (or
   the `...FreeTextV2` / `...SimpleV2` variants) so drug-drug screening sees the full list.
5. **Pull medication history — consent first.** `MedicationHistory_LogPatientMedicationHistoryConsentV2` must
   be called before `MedicationHistory_GetMedicationHistoryV2`. This is a regulated consent record, not a flag.
6. **Verify** with `Patients_GetPatientDemographicDataV2` and `Allergies_GetPatientAllergiesV2`.

## Gotchas
- SSN is a separate resource: `Patients_AddEditPatientSsnV2` / `Patients_DeletePatientSSNV2`. Do not put it on
  the demographic body.
- `Patients_MergePatientsV2` is destructive and has no undo. Never call it from an unattended agent.
- Paging is `pageNumber` / `pageSize`; read `PageResult.HasNext` rather than guessing at the end of a list.
