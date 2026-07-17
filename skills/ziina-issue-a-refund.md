---
name: Issue a refund with Ziina
description: Refund a completed Ziina payment intent in full or part, and confirm the refund status.
api: openapi/ziina-openapi.yml
operations:
- RefundController_initiateRefund
- RefundController_getRefund
---

# Issue a refund with Ziina

Refund a payment that was previously captured. Confirm the payment_intent_id and
amount with the user before issuing a refund.

## Auth
- `Authorization: Bearer <JWT>`. Required scope: `write_refunds`.

## Steps
1. **Create the refund** — `POST /refund` (`RefundController_initiateRefund`).
   - `id`: a client-generated UUID for the refund (idempotency key).
   - `payment_intent_id`: the payment intent to refund.
   - Optional `amount` (minor units) for a partial refund; omit for full. `currency_code` matches the original.
   - `test: true` for a test-mode refund.
2. **Confirm** — poll `GET /refund/{id}` (`RefundController_getRefund`) until
   `status` is `completed` or `failed`. On `failed`, read the `error` object
   ({ message, code }).

## Idempotency & errors
- The refund `id` you supply is the retry key — re-send with the same `id` to avoid a double refund.
- See errors/ziina-problem-types.yml for the error envelope.
