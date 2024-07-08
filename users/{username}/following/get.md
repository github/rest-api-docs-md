# List the people a user follows

`GET /users/{username}/following`

Lists the people who the specified user follows.

[API method documentation](https://docs.github.com/rest/users/followers#list-the-people-a-user-follows)

## All Parameters for "List the people a user follows"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."