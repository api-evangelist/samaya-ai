---
name: samaya-ai-audit-org-users
description: >-
  Enumerate every user and team in a Samaya AI organization and produce a per-user access map,
  paginating correctly and flagging inactive accounts.
generated: '2026-08-26'
method: generated
source: openapi/samaya-ai-public-api-openapi.json
api: Samaya Public API
base_url: https://api.samaya.ai
operations:
  - samaya_api_rest_views_teams_list_orgs
  - samaya_api_rest_views_teams_list_users
  - samaya_api_rest_views_teams_list_teams
  - samaya_api_rest_views_teams_list_team_members
---

# Audit Samaya organization access

A read-only pass. Every operation used here is a `GET`, so this skill has no reversibility concerns
and cannot change state.

## Authentication

`Authorization: Bearer <WORKOS_M2M_TOKEN>` — a WorkOS machine-to-machine token, scoped to one
customer.

## Steps

1. **List organizations.**
   `GET /v1/orgs/` — `samaya_api_rest_views_teams_list_orgs`. Returns `{ "orgs": [ { id, name } ] }`.
   Not paginated.

2. **List every user in the organization.**
   `GET /v1/orgs/{org_id}/users` — `samaya_api_rest_views_teams_list_users`.

   Cursor-paginated. Request with `limit`, then follow `next_cursor` while `has_more` is `true`:

   ```
   GET /v1/orgs/42/users?limit=100
   GET /v1/orgs/42/users?limit=100&cursor=<next_cursor>
   ```

   Each `UserOut` carries `email` and `is_active`. `is_active: false` is your deprovisioning
   candidate list.

   To check one specific person instead of the whole org, pass the optional `email` query parameter:
   `GET /v1/orgs/{org_id}/users?email=analyst@bank.example`.

3. **List teams.**
   `GET /v1/orgs/{org_id}/teams` — `samaya_api_rest_views_teams_list_teams`. Not paginated. Note that
   per-user "My Documents" teams are excluded, so team membership here does **not** account for a
   user's private document space.

4. **List members of each team.**
   `GET /v1/orgs/{org_id}/teams/{team_id}/members` —
   `samaya_api_rest_views_teams_list_team_members`. Cursor-paginated exactly as in step 2. Each
   `TeamMemberOut` carries `email`, `role` and `is_active`.

5. **Join on email.**
   Users and team members are both keyed by email address — the spec declares no shared surrogate id
   between `UserOut` and `TeamMemberOut`. Build the access map by matching `email` exactly.

## What to report

- Users with `is_active: false` who still appear in a team's `data[]`.
- Users present in the org listing but on no team (visible only in their excluded "My Documents"
  space).
- Emails on a team that do not appear in the org user listing.
- Teams where `is_customer_modifiable` is `false`, so no remediation write is possible through this
  API.

## Constraints

- Two of the four read operations (`list_orgs`, `list_teams`) return an unpaginated wrapped array.
  Do not build a cursor loop for those; there is no cursor.
- No rate limits are documented and none were observed. Space out the per-team member loops.
- The spec declares only `200` responses. Treat any non-2xx as opaque and stop rather than retry.
