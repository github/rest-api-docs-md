# List users

`GET /users`

[API method documentation](https://docs.github.com/rest/users/users#list-users)

## All Parameters for "List users"

### Query Parameters

- `since` (integer): A user ID. Only return users with an ID greater than this ID.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all users, in the order that they signed up on GitHub. This list includes personal user accounts and organization accounts.

Note: Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of users.
