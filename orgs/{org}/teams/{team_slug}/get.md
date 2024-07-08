# Get a team by name

`GET /orgs/{org}/teams/{team_slug}`

Gets a team using the team's `slug`. To create the `slug`, GitHub replaces special characters in the `name` string, changes all words to lowercase, and replaces spaces with a `-` separator. For example, `"My TEam Näme"` would become `my-team-name`.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}`.

[API method documentation](https://docs.github.com/rest/teams/teams#get-a-team-by-name)

## All Parameters for "Get a team by name"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.