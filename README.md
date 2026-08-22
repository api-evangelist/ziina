# Ziina (ziina)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
