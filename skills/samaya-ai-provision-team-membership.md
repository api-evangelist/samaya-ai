---
name: samaya-ai-provision-team-membership
description: >-
  Add or remove Samaya AI users from a team in bulk by email, handling partial success correctly and
  preserving roles when reversing a change.
generated: '2026-08-26'
method: generated
source: openapi/samaya-ai-public-api-openapi.json
api: Samaya Public API
base_url: https://api.samaya.ai
operations:
  - samaya_api_rest_views_teams_list_orgs
  - samaya_api_rest_views_teams_list_teams
  - samaya_api_rest_views_teams_list_team_members
  - samaya_api_rest_views_teams_add_team_members
  - samaya_api_rest_views_teams_remove_team_members
---

# Provision Samaya team membership

Every operation below is grounded in the operationIds published at
`https://api.samaya.ai/v1/openapi.json`. Nothing here is invented.

## Before you start

Authenticate with a WorkOS machine-to-machine bearer token:

```
Authorization: Bearer <WORKOS_M2M_TOKEN>
```

The token is scoped to one customer. `List Orgs` returns only the organizations under that customer,
so you cannot address another tenant even by guessing an `org_id` (ids are sequential integers, not
opaque).

## Steps

1. **Resolve the organization.**
   `GET /v1/orgs/` — `samaya_api_rest_views_teams_list_orgs`. Returns `{ "orgs": [ { id, name } ] }`.
   Not paginated. Match on `name`; keep the integer `id`.

2. **Resolve the team.**
   `GET /v1/orgs/{org_id}/teams` — `samaya_api_rest_views_teams_list_teams`. Returns
   `{ "teams": [ { id, name, is_customer_modifiable } ] }`. Not paginated. Per-user "My Documents"
   teams are excluded from this listing by the API.

   **Gate on `is_customer_modifiable`.** If it is `false`, stop — do not attempt a membership write
   on that team. The spec declares no error response, so a rejected write has no documented shape and
   you will not be able to interpret the failure.

3. **Snapshot current membership before any change.**
   `GET /v1/orgs/{org_id}/teams/{team_id}/members` —
   `samaya_api_rest_views_teams_list_team_members`. Cursor-paginated: pass `cursor` and `limit`, read
   `data[]`, `next_cursor`, `has_more`. Loop while `has_more` is true.

   Record each member's `email` **and `role`**. This snapshot is your only way to reverse a removal
   faithfully — see step 6.

4. **Add members.**
   `POST /v1/orgs/{org_id}/teams/{team_id}/members` —
   `samaya_api_rest_views_teams_add_team_members`.

   ```json
   { "members": [ { "email": "analyst@bank.example", "role": "MEMBER" } ] }
   ```

   `role` is optional and defaults to `MEMBER`. Set it explicitly whenever you know it.

5. **Treat 200 as partial success, not success.**
   Both write operations return HTTP 200 carrying two arrays:

   - add → `{ "added": [ { email, role } ], "errors": [ { email, detail } ] }`
   - remove → `{ "removed": [ "email" ], "errors": [ { email, detail } ] }`

   **Always read `errors[]`.** A member that failed is reported inside a 200 response, never as a
   non-2xx status. Report `errors[].detail` back verbatim; it is free text and the API publishes no
   error-code registry to map it against.

6. **Remove members.**
   `DELETE /v1/orgs/{org_id}/teams/{team_id}/members` —
   `samaya_api_rest_views_teams_remove_team_members`, with a body of
   `{ "emails": ["analyst@bank.example"] }`. Read `removed[]` and `errors[]` the same way.

## Reversing a change

Add and remove are exact inverses on the same email list, so both writes are reversible. Two caveats
the API does not state for you:

- **Reverse from the response, not the request.** Because of partial success, only `added[]` /
  `removed[]` tell you what actually changed. Reversing the request set will act on members that were
  never touched.
- **Re-adding does not restore role.** `MemberEntry.role` defaults to `MEMBER`, so replaying an add
  after a remove can silently demote someone. Use the roles from your step-3 snapshot.

Samaya publishes **no window** for reversal — nothing states how long a removed member's documents,
history or context survive removal, or whether re-adding restores access to prior work. Do not assume
a removal is fully undoable; confirm with the customer's Samaya contact before removing at scale.

## Constraints

- **No idempotency key.** The API offers no `Idempotency-Key` header. A retried add is convergent
  (the same member ends up on the team), but a retried request after a timeout gives you no way to
  tell whether the first attempt landed. Re-read membership (step 3) instead of blind-retrying.
- **No rate limits published, and no rate-limit headers observed.** Back off conservatively; you have
  no runtime signal. See `rate-limits/samaya-ai-rate-limits.yml`.
- **No error responses in the contract.** All six operations declare only `200`. Handle non-2xx
  defensively — status code only, no guaranteed body shape.
