# List repositories a fine-grained personal access token has access to

`GET /orgs/{org}/personal-access-tokens/{pat_id}/repositories`

[API method documentation](https://docs.github.com/rest/orgs/personal-access-tokens#list-repositories-a-fine-grained-personal-access-token-has-access-to)

## All Parameters for "List repositories a fine-grained personal access token has access to"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `pat_id` (integer, required): Unique identifier of the fine-grained personal access token.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the repositories a fine-grained personal access token has access to.

Only GitHub Apps can use this endpoint.
