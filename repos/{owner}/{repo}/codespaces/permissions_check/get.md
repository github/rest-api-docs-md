# Check if permissions defined by a devcontainer have been accepted by the authenticated user

`GET /repos/{owner}/{repo}/codespaces/permissions_check`

Checks whether the permissions defined by a given devcontainer configuration have been accepted by the authenticated user.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#check-if-permissions-defined-by-a-devcontainer-have-been-accepted-by-the-authenticated-user)

## All Parameters for "Check if permissions defined by a devcontainer have been accepted by the authenticated user"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `ref` (string, required): The git reference that points to the location of the devcontainer configuration to use for the permission check. The value of `ref` will typically be a branch name (`heads/BRANCH_NAME`). For more information, see "[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)" in the Git documentation.
- `devcontainer_path` (string, required): Path to the devcontainer.json configuration to use for the permission check.