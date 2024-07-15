# Get team membership for a user

`GET /orgs/{org}/teams/{team_slug}/memberships/{username}`

[API method documentation](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user)

## All Parameters for "Get team membership for a user"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Team members will include the members of child teams.

To get a user's membership with a team, the team must be visible to the authenticated user.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/memberships/{username}`.

**Note:**
The response contains the `state` of the membership and the member's `role`.

The `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).
