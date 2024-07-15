# List deployment statuses

`GET /repos/{owner}/{repo}/deployments/{deployment_id}/statuses`

[API method documentation](https://docs.github.com/rest/deployments/statuses#list-deployment-statuses)

## All Parameters for "List deployment statuses"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `deployment_id` (integer, required): deployment_id parameter
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Users with pull access can view deployment statuses for a deployment:
