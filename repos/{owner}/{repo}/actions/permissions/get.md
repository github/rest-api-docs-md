# Get GitHub Actions permissions for a repository

`GET /repos/{owner}/{repo}/actions/permissions`

Gets the GitHub Actions permissions policy for a repository, including whether GitHub Actions is enabled and the actions and reusable workflows allowed to run in the repository.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/permissions#get-github-actions-permissions-for-a-repository)

## All Parameters for "Get GitHub Actions permissions for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.