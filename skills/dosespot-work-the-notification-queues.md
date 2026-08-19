---
name: Work the DoseSpot notification, refill and RxChange queues
description: Read a clinician's actionable-item counts, pull transmission errors, and approve or deny inbound pharmacy-initiated refill requests and RxChange requests.
api: openapi/_original/dosespot-rest-api-full-epcs-v2-swagger.json
operations:
  - Notifications_GetPrescriberNotificationCountsV2
  - Notifications_GetTransmissionErrorDetailsV2
  - Refills_GetDetailedRefillRequestsV2
  - Refills_ApproveRefillV2
  - Refills_DenyRefillV2
  - Refills_ReplaceRefillV2
  - RxChanges_GetRxChangeQueueDetailedV2
  - RxChanges_ApproveRxChangeV2
  - RxChanges_DenyRxChangeV2
  - RxChanges_ReconcileRxChangeV2
  - HealthCheck_CheckHealthV2
---

# Work the DoseSpot notification, refill and RxChange queues

## Posture
Approving a refill or an RxChange **writes a real prescription to a real pharmacy**. Treat every approve/deny
operation in this skill as requiring a licensed human decision; an agent's job here is to gather, summarise and
stage — not to sign.

## Steps
1. **Triage.** `Notifications_GetPrescriberNotificationCountsV2` (`GET /api/notifications/counts`) returns the
   actionable-item counts for the current clinician. Use it as the cheap poll.
2. **Prefer push over polling.** DoseSpot advertises Push Notifications for these events and explicitly
   recommends them instead of polling — rate limits are enforced and return HTTP 429. See
   `asyncapi/dosespot-webhooks.yml`; the event catalogue is provisioned by your Integration Specialist.
3. **Transmission errors.** `Notifications_GetTransmissionErrorDetailsV2` (`GET /api/notifications/errors`)
   lists prescriptions that failed to reach the pharmacy. These are the `Error` (6) and `EpcsError` (10)
   prescription states.
4. **Refill requests.** `Refills_GetDetailedRefillRequestsV2` (`GET /api/refills/pending/detailed`), then
   `Refills_ApproveRefillV2`, `Refills_DenyRefillV2`, or `Refills_ReplaceRefillV2` (approve with a different
   drug/sig). A denial requires a `DenialReasonType` from the published enumeration — several members are
   marked *Deprecated. Do not use* (3, 10, 11, 12, 13); pick a live one such as `DeniedTooSoon` (7),
   `DeniedPatientNotUnderCare` (5) or `DeniedMedicationDiscontinued` (23).
5. **RxChange requests.** `RxChanges_GetRxChangeQueueDetailedV2` (`GET /api/rxchanges/pending/detailed`), then
   `RxChanges_ApproveRxChangeV2` / `RxChanges_DenyRxChangeV2`. `RxChanges_ReconcileRxChangeV2` binds the change
   to the right patient record.
6. **Mismatched patient?** Both queues expose a `changePatient` PATCH (`Refills_ChangeRefillRequestPatientV2`,
   `RxChanges_ChangeRxChangeRequestPatientV2`) for reattaching an inbound request to the correct chart.
7. **Liveness.** `HealthCheck_CheckHealthV2` (`GET /api/general/check`) before a batch run; the platform status
   feed is https://status.dosespot.com/ ("DoseSpot API V2" is a monitored component).

## Gotchas
- No idempotency key exists. Approving twice because a response was slow can produce two prescriptions —
  re-read the queue instead of retrying the approve.
- Everything returns HTTP 200; the real outcome is `Result.ResultCode`.
