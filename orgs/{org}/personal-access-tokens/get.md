# List fine-grained personal access tokens with access to organization resources

`GET /orgs/{org}/personal-access-tokens`

Lists approved fine-grained personal access tokens owned by organization members that can access organization resources.

Only GitHub Apps can use this endpoint.

[API method documentation](https://docs.github.com/rest/orgs/personal-access-tokens#list-fine-grained-personal-access-tokens-with-access-to-organization-resources)

## All Parameters for "List fine-grained personal access tokens with access to organization resources"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `sort` (string): The property by which to sort the results.
- `direction` (string): The direction to sort the results by.
- `owner` (array): A list of owner usernames to use to filter the results.
- `repository` (string): The name of the repository to use to filter the results.
- `permission` (string): The permission to use to filter the results.
- `last_used_before` (string): Only show fine-grained personal access tokens used before the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.
- `last_used_after` (string): Only show fine-grained personal access tokens used after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.