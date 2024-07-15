# Get a public SSH key for the authenticated user

`GET /user/keys/{key_id}`

[API method documentation](https://docs.github.com/rest/users/keys#get-a-public-ssh-key-for-the-authenticated-user)

## All Parameters for "Get a public SSH key for the authenticated user"

### Path Parameters

- `key_id` (integer, required): The unique identifier of the key.

## Operation Description

View extended details for a single public SSH key.

OAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.
