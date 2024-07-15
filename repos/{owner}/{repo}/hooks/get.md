# List repository webhooks

`GET /repos/{owner}/{repo}/hooks`

[API method documentation](https://docs.github.com/rest/repos/webhooks#list-repository-webhooks)

## All Parameters for "List repository webhooks"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists webhooks for a repository. `last response` may return null if there have not been any deliveries within 30 days.
