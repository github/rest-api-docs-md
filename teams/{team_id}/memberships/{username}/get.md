# Get team membership for a user (Legacy)

`GET /teams/{team_id}/memberships/{username}`

[API method documentation](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user-legacy)

## All Parameters for "Get team membership for a user (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `username` (string, required): The handle for the GitHub user account.

## Operation Description

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get team membership for a user](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user) endpoint.

Team members will include the members of child teams.

To get a user's membership with a team, the team must be visible to the authenticated user.

**Note:**
The response contains the `state` of the membership and the member's `role`.

The `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).
