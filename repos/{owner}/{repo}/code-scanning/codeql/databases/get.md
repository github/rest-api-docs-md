# List CodeQL databases for a repository

`GET /repos/{owner}/{repo}/code-scanning/codeql/databases`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#list-codeql-databases-for-a-repository)

## All Parameters for "List CodeQL databases for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Lists the CodeQL databases that are available in a repository.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
