# Check team permissions for a repository (Legacy)

`GET /teams/{team_id}/repos/{owner}/{repo}`

**Note**: Repositories inherited through a parent team will also be checked.

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Check team permissions for a repository](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-repository) endpoint.

You can also get information about the specified repository, including what permissions the team grants on it, by passing the following custom [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types/) via the `Accept` header:

[API method documentation](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-repository-legacy)

## All Parameters for "Check team permissions for a repository (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.