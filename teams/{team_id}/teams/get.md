# List child teams (Legacy)

`GET /teams/{team_id}/teams`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [`List child teams`](https://docs.github.com/rest/teams/teams#list-child-teams) endpoint.

[API method documentation](https://docs.github.com/rest/teams/teams#list-child-teams-legacy)

## All Parameters for "List child teams (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."