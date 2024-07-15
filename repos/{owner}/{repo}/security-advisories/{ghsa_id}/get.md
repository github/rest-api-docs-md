# Get a repository security advisory

`GET /repos/{owner}/{repo}/security-advisories/{ghsa_id}`

[API method documentation](https://docs.github.com/rest/security-advisories/repository-advisories#get-a-repository-security-advisory)

## All Parameters for "Get a repository security advisory"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ghsa_id` (string, required): The GHSA (GitHub Security Advisory) identifier of the advisory.

## Operation Description

Get a repository security advisory using its GitHub Security Advisory (GHSA) identifier.

Anyone can access any published security advisory on a public repository.

The authenticated user can access an unpublished security advisory from a repository if they are a security manager or administrator of that repository, or if they are a
collaborator on the security advisory.

OAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:read` scope to to get a published security advisory in a private repository, or any unpublished security advisory that the authenticated user has access to.
