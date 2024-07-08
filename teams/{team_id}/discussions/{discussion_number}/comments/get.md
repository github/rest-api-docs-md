# List discussion comments (Legacy)

`GET /teams/{team_id}/discussions/{discussion_number}/comments`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [List discussion comments](https://docs.github.com/rest/teams/discussion-comments#list-discussion-comments) endpoint.

List all comments on a team discussion.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/teams/discussion-comments#list-discussion-comments-legacy)

## All Parameters for "List discussion comments (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `discussion_number` (integer, required): The number that identifies the discussion.
### Query Parameters

- `direction` (string): The direction to sort the results by.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."