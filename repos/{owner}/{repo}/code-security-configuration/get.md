# Get the code security configuration associated with a repository

`GET /repos/{owner}/{repo}/code-security-configuration`

[API method documentation](https://docs.github.com/rest/code-security/configurations#get-the-code-security-configuration-associated-with-a-repository)

## All Parameters for "Get the code security configuration associated with a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Get the code security configuration that manages a repository's code security settings.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
