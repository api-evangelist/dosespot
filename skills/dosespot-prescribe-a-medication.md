---
name: Write and transmit a prescription with DoseSpot
description: Search the Medi-Span drug database, run interaction and allergy screening, attach a pharmacy, then create, sign and transmit a prescription — including the separate EPCS path for controlled substances.
api: openapi/_original/dosespot-rest-api-full-epcs-v2-swagger.json
operations:
  - Medications_MedicationSearchV2
  - Medications_MedicationSelectV2
  - Medications_GetStandardDispenseUnitsV2
  - Interactions_GetPreCheckInteractionsV2
  - Interactions_GetDrugInteractionsV2
  - Interactions_GetAllergyInteractionsV2
  - Prescriptions_AddCodedPrescriptionV2
  - Prescriptions_SetPrescriptionsReadyToSignV2
  - Prescriptions_SendPrescriptionsV2
  - Prescriptions_SendEpcsPrescriptionsV2
  - Prescriptions_GetPatientPrescriptionV2
  - Prescriptions_GetPrescriptionLogDetailsV2
  - Prescriptions_CancelPrescriptionV2
---

# Write and transmit a prescription with DoseSpot

## Before you start
- Headers: `Ocp-Apim-Subscription-Key` + `Authorization: Bearer <token>`. Access is scoped by clinic key and
  clinician key — the acting clinician determines what you may prescribe.
- The patient must already exist with allergies recorded — run the *Onboard a patient* skill first.
- **This is a safety-critical write path.** Transmission is irreversible: once `eRxSent`, the message is with
  Surescripts and the pharmacy. There is no idempotency key on this API, so a blind retry of
  `Prescriptions_SendPrescriptionsV2` can send twice. Confirm state with a GET before retrying anything.

## Steps
1. **Find the drug.** `Medications_MedicationSearchV2` (`GET /api/medications/search`), or
   `Medications_MedicationSearchRxCUIV2` when you hold an RxNorm RxCUI. Then `Medications_MedicationSelectV2`
   to resolve the dispensable drug you will actually prescribe.
2. **Pre-check before you write.** `Interactions_GetPreCheckInteractionsV2`
   (`GET /api/patients/{patientId}/interactions/precheck/{dispensableDrugId}`) screens the candidate drug
   against the patient. Severity comes back as MinorInteraction / ModerateInteraction / MajorInteraction /
   UnknownInteraction (`vocabulary/dosespot-vocabulary.yml`). **Escalate a MajorInteraction to a human.**
3. **Resolve dispense units** with `Medications_GetStandardDispenseUnitsV2` — quantity is meaningless without
   the right `DispenseUnitTypeID` (Tablet 26, Capsule 4, Milliliter 15, Each 32, …).
4. **Attach a pharmacy** — see the *Manage patient pharmacies* skill. Check `ServiceLevel` on the pharmacy: it
   is a bitwise sum, and a controlled-substance script requires the EPCS bit (2048).
5. **Create the prescription.** `Prescriptions_AddCodedPrescriptionV2`
   (`POST /api/patients/{patientId}/prescriptions/coded`). Compounds use
   `Prescriptions_AddCompiledCompoundV2`; supplies use `Prescriptions_AddCodedSupplyV2`. Status is now
   `Entered` (1).
6. **Mark ready to sign.** `Prescriptions_SetPrescriptionsReadyToSignV2` → status `ReadyToSign` (12).
7. **Transmit.**
   - Non-controlled: `Prescriptions_SendPrescriptionsV2` (`POST /api/patients/{patientId}/prescriptions/send`).
   - **Controlled substances: `Prescriptions_SendEpcsPrescriptionsV2`.** This requires a clinician who has
     completed identity proofing and two-factor activation — run the *EPCS clinician enrollment* skill first.
     Failure modes surface as `EpcsError` (10) rather than `EpcsSigned` (11).
   - Print/fax fallbacks: `Prescriptions_SetPrescriptionsPrintedV2`, `Prescriptions_SendToAddressPrescriptionsV2`.
8. **Confirm the outcome.** `Prescriptions_GetPatientPrescriptionV2`, then walk
   `Prescriptions_GetPrescriptionLogDetailsV2`. Statuses: `Sending` (3) → `eRxSent` (4) →
   `PharmacyVerified` (13). `Error` (6) is terminal until handled.
9. **Cancel if needed.** `Prescriptions_CancelPrescriptionV2` sends a CancelRx to the pharmacy — it is a new
   transaction, not a delete. `Prescriptions_DeletePrescriptionsV2` only removes an unsent prescription.

## Gotchas
- `Prescriptions_IgnoreAlertV2` suppresses a clinical alert. **An agent must never call it autonomously** —
  it is the override of a drug-safety warning and belongs to a licensed human.
- Rate limits are enforced and return HTTP 429; DoseSpot's guidance is to consume Push Notifications rather
  than poll prescription status.
