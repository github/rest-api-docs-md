# List organizations for a user

`GET /users/{username}/orgs`

[API method documentation](https://docs.github.com/rest/orgs/orgs#list-organizations-for-a-user)

## All Parameters for "List organizations for a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List [public organization memberships](https://docs.github.com/articles/publicizing-or-concealing-organization-membership) for the specified user.

This method only lists _public_ memberships, regardless of authentication. If you need to fetch all of the organization memberships (public and private) for the authenticated user, use the [List organizations for the authenticated user](https://docs.github.com/rest/orgs/orgs#list-organizations-for-the-authenticated-user) API instead.
