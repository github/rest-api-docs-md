# List team members

`GET /orgs/{org}/teams/{team_slug}/members`

Team members will include the members of child teams.

To list members in a team, the team must be visible to the authenticated user.

[API method documentation](https://docs.github.com/rest/teams/members#list-team-members)

## All Parameters for "List team members"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
### Query Parameters

- `role` (string): Filters members returned by their role in the team.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."