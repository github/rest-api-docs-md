# List discussions (Legacy)

`GET /teams/{team_id}/discussions`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [`List discussions`](https://docs.github.com/rest/teams/discussions#list-discussions) endpoint.

List all discussions on a team's page.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/teams/discussions#list-discussions-legacy)

## All Parameters for "List discussions (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
### Query Parameters

- `direction` (string): The direction to sort the results by.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."