# List SSH signing keys for a user

`GET /users/{username}/ssh_signing_keys`

[API method documentation](https://docs.github.com/rest/users/ssh-signing-keys#list-ssh-signing-keys-for-a-user)

## All Parameters for "List SSH signing keys for a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the SSH signing keys for a user. This operation is accessible by anyone.
