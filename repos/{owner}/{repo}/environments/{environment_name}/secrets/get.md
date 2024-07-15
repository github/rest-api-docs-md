# List environment secrets

`GET /repos/{owner}/{repo}/environments/{environment_name}/secrets`

[API method documentation](https://docs.github.com/rest/actions/secrets#list-environment-secrets)

## All Parameters for "List environment secrets"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all secrets available in an environment without revealing their
encrypted values.

Authenticated users must have collaborator access to a repository to create, update, or read secrets.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
