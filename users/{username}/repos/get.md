# List repositories for a user

`GET /users/{username}/repos`

Lists public repositories for the specified user.

[API method documentation](https://docs.github.com/rest/repos/repos#list-repositories-for-a-user)

## All Parameters for "List repositories for a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `type` (string): Limit results to repositories of the specified type.
- `sort` (string): The property to sort the results by.
- `direction` (string): The order to sort by. Default: `asc` when using `full_name`, otherwise `desc`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."