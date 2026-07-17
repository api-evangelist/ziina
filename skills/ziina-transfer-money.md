---
name: Transfer money between Ziina accounts
description: Send money to one or more Ziina users by account id or ziiname, retry-safe via operation_id.
api: openapi/ziina-openapi.yml
operations:
- TransferController_initiateTransfer
- TransferController_getTransfer
---

# Transfer money between Ziina accounts

Move funds to other Ziina users (payouts, disbursements, P2P). This moves real
money — always confirm recipient(s) and amount with the user first.

## Auth
- `Authorization: Bearer <JWT>`. Required scope: `write_transfers`.

## Steps
1. **Initiate the transfer** — `POST /transfer` (`TransferController_initiateTransfer`).
   - `operation_id`: **required** client-generated UUID (idempotency key).
   - Recipients: supply **either** `to_account_ids` **or** `to_ziinames` (Ziina usernames), not both.
   - `amount` in minor units; `currency_code` ISO-4217. Optional `message`.
2. **Confirm** — `GET /transfer/{id}` (`TransferController_getTransfer`); the
   caller must be the payer or receiver. Poll until `status` is `completed`,
   `failed`, or `canceled`.

## Idempotency & errors
- Re-send with the same `operation_id` on retry to avoid a duplicate transfer.
- See errors/ziina-problem-types.yml and agentic-access/ziina-agentic-access.yml
  (transfers are a physical-consequence, human-in-the-loop operation).
