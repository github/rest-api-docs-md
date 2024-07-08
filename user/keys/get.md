# List public SSH keys for the authenticated user

`GET /user/keys`

Lists the public SSH keys for the authenticated user's GitHub account.

OAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/users/keys#list-public-ssh-keys-for-the-authenticated-user)

## All Parameters for "List public SSH keys for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."