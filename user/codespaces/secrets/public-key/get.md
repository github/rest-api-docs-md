# Get public key for the authenticated user

`GET /user/codespaces/secrets/public-key`

[API method documentation](https://docs.github.com/rest/codespaces/secrets#get-public-key-for-the-authenticated-user)


## Operation Description

Gets your public key, which you need to encrypt secrets. You need to encrypt a secret before you can create or update secrets.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.
