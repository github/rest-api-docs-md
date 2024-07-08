# Get the level of access for workflows outside of the repository

`GET /repos/{owner}/{repo}/actions/permissions/access`

Gets the level of access that workflows outside of the repository have to actions and reusable workflows in the repository.
This endpoint only applies to private repositories.
For more information, see "[Allowing access to components in a private repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-a-private-repository)."

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/permissions#get-the-level-of-access-for-workflows-outside-of-the-repository)

## All Parameters for "Get the level of access for workflows outside of the repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.