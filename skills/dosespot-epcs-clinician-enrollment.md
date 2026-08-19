---
name: Enroll a clinician for EPCS in DoseSpot
description: Create a clinician, register DEA numbers, run DEA-required identity proofing and two-factor activation, and confirm the clinician is eligible to sign controlled-substance prescriptions.
api: openapi/_original/dosespot-rest-api-full-epcs-v2-swagger.json
operations:
  - Clinicians_ClinicianAddV2
  - Clinicians_GetClinicianDetailsByIdV2
  - Clinicians_GetClinicianLegalAgreementsV2
  - Clinicians_AcceptAgreementV2
  - Clinicians_GetIdentityProofingDisclaimerV2
  - Clinicians_AcceptIdentityProofingDisclaimerV2
  - Clinicians_InitializeIDPV2
  - Clinicians_ClinicianIdentityProofingV2
  - Clinicians_ClinicianIdentityProofingAnswersV2
  - Clinicians_ClinicianIdentityProofingOneTimeCodeV2
  - Clinicians_InitializeTfaActivationV2
  - Clinicians_SendMobileTfaV2
  - Clinicians_TfaActivateV2
  - Clinicians_SetPinV2
  - Clinicians_ClinicianCheckRegistrationStatusV2
  - DEANumbers_AddDEANumber
  - DEANumbers_GetDEANumbers
---

# Enroll a clinician for EPCS in DoseSpot

## Posture
EPCS enrollment is a **DEA-regulated identity-proofing ceremony**. An agent may orchestrate the calls and
report status; it must never supply, guess or store the clinician's identity answers, one-time codes or PIN.
Every step here is human-in-the-loop by regulation, not by preference.

## Steps
1. **Create the clinician.** `Clinicians_ClinicianAddV2` (`POST /api/clinicians`). If the clinician already
   exists, `Clinicians_GetClinicianByNpiOrDeaV2` (`GET /api/clinician`) resolves them by NPI or DEA.
   `ResultCode 3025 ClinicianLicenseDuplicate` and `3026 ClinicianNotInitialized` are the common failures.
2. **Set the role.** `ClinicianRoleType`: PrescribingClinician 1, ReportingClinician 2, EpcsCoordinator 3,
   ClinicianAdmin 4, PrescribingAgentClinician 5, ProxyClinician 6.
3. **Register DEA numbers.** `DEANumbers_AddDEANumber`
   (`POST /api/clinicians/{clinicianId}/deanumbers`), verify with `DEANumbers_GetDEANumbers`. A clinician
   without a valid DEA registration cannot be enrolled for controlled substances.
4. **Legal agreements.** `Clinicians_GetClinicianLegalAgreementsV2` then `Clinicians_AcceptAgreementV2`.
5. **Identity proofing (IDP).** `Clinicians_GetIdentityProofingDisclaimerV2` →
   `Clinicians_AcceptIdentityProofingDisclaimerV2` → `Clinicians_InitializeIDPV2` →
   `Clinicians_ClinicianIdentityProofingV2` → `Clinicians_ClinicianIdentityProofingAnswersV2` →
   `Clinicians_ClinicianIdentityProofingOneTimeCodeV2`. Progress shows in `RegistrationStatusType`:
   `IDPInitializeSuccess` 12 → `IDPSuccess` 4, or `IDPError` 5.
6. **Two-factor.** `Clinicians_InitializeTfaActivationV2` → `Clinicians_SendMobileTfaV2` →
   `Clinicians_TfaActivateV2`. `TFAType`: Mobile 2, Token 3. States run
   `TFAActivateInit` 6 → `TFAActivatedSuccess` 7, or `TFAActivatedError` 8.
   `Clinicians_ResyncTokenV2` recovers a drifted hardware token.
7. **Signing PIN.** `Clinicians_SetPinV2`; `Clinicians_ChangePinV2` / `Clinicians_ResetMyPinV2` /
   `Clinicians_ResetClinicianPinV2` for lifecycle.
8. **Confirm.** `Clinicians_ClinicianCheckRegistrationStatusV2`
   (`GET /api/clinicians/{clinicianId}/registrationStatus`) must report `RegistrationSuccess` (2) plus
   `IDPSuccess` and `TFAActivatedSuccess` before `Prescriptions_SendEpcsPrescriptionsV2` will succeed.
9. **Supervision, where required.** `Clinicians_AddSupervisorToClinicianV2` /
   `Clinicians_DeleteSupervisorToClinicianV2`.
10. **PDMP.** `Clinicians_GetClinicianPDMPV2` returns the clinician's PDMP registration; `PDMPRoleType`
    (Physician 1, Dentist 2, NursePractitioner 3, …) is published in the enumeration tables.

## Gotchas
- Full enumeration values for every status above are in `vocabulary/dosespot-vocabulary.yml`.
- `ResultCode 2027 ClinicianHasNoAccessToClinic` and `2033 NotAClinician` mean the clinic/clinician key scoping
  is wrong, not that enrollment failed.
- The EPCS operation set is the difference between the two published plans — JumpStart customers receive a
  subset of the Full contract.
