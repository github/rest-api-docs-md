# List user projects

`GET /users/{username}/projects`

[API method documentation](https://docs.github.com/rest/projects/projects#list-user-projects)

## All Parameters for "List user projects"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `state` (string): Indicates the state of the projects to return.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists projects for a user.
