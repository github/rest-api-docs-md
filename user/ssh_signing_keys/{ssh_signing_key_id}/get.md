# Get an SSH signing key for the authenticated user

`GET /user/ssh_signing_keys/{ssh_signing_key_id}`

[API method documentation](https://docs.github.com/rest/users/ssh-signing-keys#get-an-ssh-signing-key-for-the-authenticated-user)

## All Parameters for "Get an SSH signing key for the authenticated user"

### Path Parameters

- `ssh_signing_key_id` (integer, required): The unique identifier of the SSH signing key.

## Operation Description

Gets extended details for an SSH signing key.

OAuth app tokens and personal access tokens (classic) need the `read:ssh_signing_key` scope to use this endpoint.
