# Get a discussion (Legacy)

`GET /teams/{team_id}/discussions/{discussion_number}`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion](https://docs.github.com/rest/teams/discussions#get-a-discussion) endpoint.

Get a specific discussion on a team's page.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/teams/discussions#get-a-discussion-legacy)

## All Parameters for "Get a discussion (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `discussion_number` (integer, required): The number that identifies the discussion.