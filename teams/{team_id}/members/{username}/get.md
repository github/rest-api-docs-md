# Get team member (Legacy)

`GET /teams/{team_id}/members/{username}`

The "Get team member" endpoint (described below) is deprecated.

We recommend using the [Get team membership for a user](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user) endpoint instead. It allows you to get both active and pending memberships.

To list members in a team, the team must be visible to the authenticated user.

[API method documentation](https://docs.github.com/rest/teams/members#get-team-member-legacy)

## All Parameters for "Get team member (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `username` (string, required): The handle for the GitHub user account.