# Get a repository public key

`GET /repos/{owner}/{repo}/codespaces/secrets/public-key`

[API method documentation](https://docs.github.com/rest/codespaces/repository-secrets#get-a-repository-public-key)

## All Parameters for "Get a repository public key"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Gets your public key, which you need to encrypt secrets. You need to
encrypt a secret before you can create or update secrets.

If the repository is private, OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
