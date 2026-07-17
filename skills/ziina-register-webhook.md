---
name: Register a Ziina webhook
description: Register (or remove) a webhook endpoint to receive Ziina payment and refund events, and verify HMAC signatures.
api: openapi/ziina-openapi.yml
operations:
- WebhookController_createWebhook
- WebhookController_deleteWebhook
---

# Register a Ziina webhook

Receive real-time `payment_intent.status.updated` and `refund.status.updated`
events instead of polling.

## Auth
- `Authorization: Bearer <JWT>`. Required scope: `write_webhooks`.

## Steps
1. **Register the endpoint** — `POST /webhook` (`WebhookController_createWebhook`).
   - `url`: your HTTPS endpoint. A new POST overwrites the previous URL (one webhook per account).
   - `secret` (optional but recommended): shared secret used to HMAC-sign deliveries.
2. **Verify deliveries** — Ziina POSTs `{ event, data }` to your URL.
   - If a secret was set, verify the `X-Hmac-Signature` header = hex SHA-256 HMAC of the raw body.
   - Accept deliveries **only** from Ziina source IPs: 3.29.184.186, 3.29.190.95, 20.233.47.127, 13.202.161.181.
   - Return 2xx; non-2xx is retried up to 3 times.
3. **Remove** — `DELETE /webhook` (`WebhookController_deleteWebhook`) to stop deliveries.

## Reference
- Event schemas: asyncapi/ziina-webhooks-asyncapi.yml
- Conventions: conventions/ziina-conventions.yml
