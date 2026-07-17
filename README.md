# Ziina (ziina)

Ziina is a Dubai-based (UAE) fintech offering an instant money and payments platform for consumers and businesses. Its REST API lets developers create hosted and embedded payment intents, issue refunds, run peer transfers between Ziina accounts, and register webhooks. Amounts are in the currency's minor unit (fils for AED), auth is HTTP bearer (JWT) via OAuth 2.0 scopes, and settlement is in AED with multi-currency acceptance.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ziina/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ziina/refs/heads/main/apis.yml)

## Tags

- Payments
- Fintech
- UAE
- MENA
- Money Transfer
- Wallet

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Ziina Payment Intent API

Create a payment intent (POST /payment_intent) and retrieve it (GET /payment_intent/{id}). Returns a hosted redirect_url and an embedded_url for card, Apple Pay, and Google Pay checkout. Amount is in the currency minor unit (fils for AED, minimum 2 AED); pass test=true for sandbox payments with test cards.

- **Human URL:** [https://docs.ziina.com/api-reference/payment-intent](https://docs.ziina.com/api-reference/payment-intent)
- **Base URL:** `https://api-v2.ziina.com/api`

#### Tags

- Payments
- Checkout
- Payment Intent

#### Properties

- [Documentation](https://docs.ziina.com/api-reference/payment-intent)
- [API Reference](https://docs.ziina.com/api-reference/payment-intent/create)
- [OpenAPI](openapi/ziina-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ziina.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ziina Refund API

Initiate a full or partial refund against a payment intent (POST /refund) and retrieve refund status (GET /refund/{id}). Requires the write_refunds scope.

- **Human URL:** [https://docs.ziina.com/api-reference/refund/create](https://docs.ziina.com/api-reference/refund/create)
- **Base URL:** `https://api-v2.ziina.com/api`

#### Tags

- Payments
- Refunds

#### Properties

- [Documentation](https://docs.ziina.com/api-reference/refund/create)
- [API Reference](https://docs.ziina.com/api-reference/refund/get)
- [OpenAPI](openapi/ziina-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ziina.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ziina Transfer API

Move money between Ziina accounts (POST /transfer) addressed by account ids or ziinames, and retrieve a transfer (GET /transfer/{id}). Requires the write_transfers scope and an idempotent operation_id.

- **Human URL:** [https://docs.ziina.com/api-reference/transfer/create](https://docs.ziina.com/api-reference/transfer/create)
- **Base URL:** `https://api-v2.ziina.com/api`

#### Tags

- Payments
- Transfers
- Payouts

#### Properties

- [Documentation](https://docs.ziina.com/api-reference/transfer/create)
- [API Reference](https://docs.ziina.com/api-reference/transfer/get)
- [OpenAPI](openapi/ziina-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ziina.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ziina Webhooks API

Register (POST /webhook) or delete (DELETE /webhook) a webhook endpoint that receives real-time payment event callbacks, optionally HMAC-signed with a shared secret. HTTP callbacks over HTTPS, not a WebSocket stream.

- **Human URL:** [https://docs.ziina.com/api-reference/webhook](https://docs.ziina.com/api-reference/webhook)
- **Base URL:** `https://api-v2.ziina.com/api`

#### Tags

- Webhooks
- Events

#### Properties

- [Documentation](https://docs.ziina.com/api-reference/webhook)
- [API Reference](https://docs.ziina.com/api-reference/webhook/create)
- [OpenAPI](openapi/ziina-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ziina.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Ziina Account API

Retrieve the authenticated account (GET /account) — account_id, account_type (personal/business), status, ziiname, display_name, and profile picture. Requires the read_account scope.

- **Human URL:** [https://docs.ziina.com/api-reference/account/get](https://docs.ziina.com/api-reference/account/get)
- **Base URL:** `https://api-v2.ziina.com/api`

#### Tags

- Account
- Identity

#### Properties

- [Documentation](https://docs.ziina.com/api-reference/account/get)
- [OpenAPI](openapi/ziina-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ziina.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

## Common Properties

- [Agentic Access](agentic-access/ziina-agentic-access.yml)
- [Trust Center](security/ziina-trust-center.yml)
- [Vulnerability Disclosure](security/ziina-vulnerability-disclosure.yml)
- [Domain Security](security/ziina-domain-security.yml)
- [Authentication](authentication/ziina-authentication.yml)
- [GitHub Organization](https://github.com/ziina-co)
- [LinkedIn](https://www.linkedin.com/company/ziina)
- [Website](https://ziina.com/)
- [Documentation](https://docs.ziina.com)
- [Plans](plans/ziina-plans-pricing.yml)
- [Rate Limits](rate-limits/ziina-rate-limits.yml)
- [Fin Ops](finops/ziina-finops.yml)
- [Blog](https://ziina.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
