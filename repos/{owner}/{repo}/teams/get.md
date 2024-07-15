# List repository teams

`GET /repos/{owner}/{repo}/teams`

[API method documentation](https://docs.github.com/rest/repos/repos#list-repository-teams)

## All Parameters for "List repository teams"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the teams that have access to the specified repository and that are also visible to the authenticated user.

For a public repository, a team is listed only if that team added the public repository explicitly.

OAuth app tokens and personal access tokens (classic) need the `public_repo` or `repo` scope to use this endpoint with a public repository, and `repo` scope to use this endpoint with a private repository.
