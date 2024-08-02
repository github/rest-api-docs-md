# List discussion comments

`GET /orgs/{org}/teams/{team_slug}/discussions/{discussion_number}/comments`

[API method documentation](https://docs.github.com/rest/teams/discussion-comments#list-discussion-comments)

## All Parameters for "List discussion comments"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
- `discussion_number` (integer, required): The number that identifies the discussion.
### Query Parameters

- `direction` (string): The direction to sort the results by.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List all comments on a team discussion.

> [!NOTE]
> You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/discussions/{discussion_number}/comments`.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.
