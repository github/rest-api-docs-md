# List deployments

`GET /repos/{owner}/{repo}/deployments`

[API method documentation](https://docs.github.com/rest/deployments/deployments#list-deployments)

## All Parameters for "List deployments"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `sha` (string): The SHA recorded at creation time.
- `ref` (string): The name of the ref. This can be a branch, tag, or SHA.
- `task` (string): The name of the task for the deployment (e.g., `deploy` or `deploy:migrations`).
- `environment` (string): The name of the environment that was deployed to (e.g., `staging` or `production`).
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Simple filtering of deployments is available via query parameters:
