# List codespaces for the authenticated user

`GET /user/codespaces`

Lists the authenticated user's codespaces.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#list-codespaces-for-the-authenticated-user)

## All Parameters for "List codespaces for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `repository_id` (integer): ID of the Repository to filter on