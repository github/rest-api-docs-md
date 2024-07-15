# Get project permission for a user

`GET /projects/{project_id}/collaborators/{username}/permission`

[API method documentation](https://docs.github.com/rest/projects/collaborators#get-project-permission-for-a-user)

## All Parameters for "Get project permission for a user"

### Path Parameters

- `project_id` (integer, required): The unique identifier of the project.
- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Returns the collaborator's permission level for an organization project. Possible values for the `permission` key: `admin`, `write`, `read`, `none`. You must be an organization owner or a project `admin` to review a user's permission level.
