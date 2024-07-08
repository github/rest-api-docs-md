# List devcontainer configurations in a repository for the authenticated user

`GET /repos/{owner}/{repo}/codespaces/devcontainers`

Lists the devcontainer.json files associated with a specified repository and the authenticated user. These files
specify launchpoint configurations for codespaces created within the repository.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#list-devcontainer-configurations-in-a-repository-for-the-authenticated-user)

## All Parameters for "List devcontainer configurations in a repository for the authenticated user"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."