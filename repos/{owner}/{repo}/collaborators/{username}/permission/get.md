# Get repository permissions for a user

`GET /repos/{owner}/{repo}/collaborators/{username}/permission`

Checks the repository permission of a collaborator. The possible repository
permissions are `admin`, `write`, `read`, and `none`.

*Note*: The `permission` attribute provides the legacy base roles of `admin`, `write`, `read`, and `none`, where the
`maintain` role is mapped to `write` and the `triage` role is mapped to `read`. To determine the role assigned to the
collaborator, see the `role_name` attribute, which will provide the full role name, including custom roles. The
`permissions` hash can also be used to determine which base level of access the collaborator has to the repository.

[API method documentation](https://docs.github.com/rest/collaborators/collaborators#get-repository-permissions-for-a-user)

## All Parameters for "Get repository permissions for a user"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.