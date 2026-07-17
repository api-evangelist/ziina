---
name: Accept a payment with Ziina
description: Create a Ziina payment intent, present the hosted or embedded checkout, and confirm the outcome.
api: openapi/ziina-openapi.yml
operations:
- PaymentIntentController_createPaymentIntent
- PaymentIntentController_getPaymentIntent
---

# Accept a payment with Ziina

Use this flow to charge a customer. Ziina moves real money — confirm amount and
currency with the user before creating a live (non-test) payment intent.

## Auth
- `Authorization: Bearer <JWT>` on every call. The token is a Ziina OAuth 2.0 /
  OIDC access token (auth.ziina.com/oidc) or a business-connect personal token.
- Required scope: `write_payment_intents`.

## Steps
1. **Create the payment intent** — `POST /payment_intent`
   (`PaymentIntentController_createPaymentIntent`).
   - `amount` is in the currency's **minor unit** (fils for AED): 10 AED = `1000`. Minimum 2 AED.
   - `currency_code` is a 3-letter ISO-4217 code (e.g. `AED`).
   - Optional: `message`, `success_url`, `cancel_url`, `failure_url`, `allow_tips`, `expiry`.
   - For testing pass `test: true` (see sandbox/ziina-sandbox.yml) — no real charge, any test card works.
   - The response includes `redirect_url` (hosted page) and `embedded_url` (iframe widget), plus `operation_id`.
2. **Present checkout** — redirect the buyer to `redirect_url`, or embed
   `embedded_url` in an iframe (append `?version=v1` for the stable widget, `&locale=ar` for Arabic).
3. **Confirm** — either handle the `payment_intent.status.updated` webhook
   (recommended, see asyncapi/ziina-webhooks-asyncapi.yml) or poll
   `GET /payment_intent/{id}` (`PaymentIntentController_getPaymentIntent`) until
   `status` is `completed`, `failed`, or `canceled`.

## Idempotency & errors
- Retries: re-send with the same `operation_id` to avoid a duplicate charge.
- On failure, read `latest_error` ({ message, code }, see errors/ziina-problem-types.yml).
