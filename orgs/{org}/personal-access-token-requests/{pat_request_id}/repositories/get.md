# List repositories requested to be accessed by a fine-grained personal access token

`GET /orgs/{org}/personal-access-token-requests/{pat_request_id}/repositories`

[API method documentation](https://docs.github.com/rest/orgs/personal-access-tokens#list-repositories-requested-to-be-accessed-by-a-fine-grained-personal-access-token)

## All Parameters for "List repositories requested to be accessed by a fine-grained personal access token"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `pat_request_id` (integer, required): Unique identifier of the request for access via fine-grained personal access token.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the repositories a fine-grained personal access token request is requesting access to.

Only GitHub Apps can use this endpoint.
