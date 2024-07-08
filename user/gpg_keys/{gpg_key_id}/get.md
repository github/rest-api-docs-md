# Get a GPG key for the authenticated user

`GET /user/gpg_keys/{gpg_key_id}`

View extended details for a single GPG key.

OAuth app tokens and personal access tokens (classic) need the `read:gpg_key` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/users/gpg-keys#get-a-gpg-key-for-the-authenticated-user)

## All Parameters for "Get a GPG key for the authenticated user"

### Path Parameters

- `gpg_key_id` (integer, required): The unique identifier of the GPG key.