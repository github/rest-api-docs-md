# Get default workflow permissions for a repository

`GET /repos/{owner}/{repo}/actions/permissions/workflow`

[API method documentation](https://docs.github.com/rest/actions/permissions#get-default-workflow-permissions-for-a-repository)

## All Parameters for "Get default workflow permissions for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in a repository,
as well as if GitHub Actions can submit approving pull request reviews.
For more information, see "[Setting the permissions of the GITHUB_TOKEN for your repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#setting-the-permissions-of-the-github_token-for-your-repository)."

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
