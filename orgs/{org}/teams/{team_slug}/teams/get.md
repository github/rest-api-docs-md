# List child teams

`GET /orgs/{org}/teams/{team_slug}/teams`

[API method documentation](https://docs.github.com/rest/teams/teams#list-child-teams)

## All Parameters for "List child teams"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the child teams of the team specified by `{team_slug}`.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/teams`.
