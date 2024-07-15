# List GPG keys for the authenticated user

`GET /user/gpg_keys`

[API method documentation](https://docs.github.com/rest/users/gpg-keys#list-gpg-keys-for-the-authenticated-user)

## All Parameters for "List GPG keys for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the current user's GPG keys.

OAuth app tokens and personal access tokens (classic) need the `read:gpg_key` scope to use this endpoint.
