# Get a code scanning default setup configuration

`GET /repos/{owner}/{repo}/code-scanning/default-setup`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-a-code-scanning-default-setup-configuration)

## All Parameters for "Get a code scanning default setup configuration"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Gets a code scanning default setup configuration.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
