# Check if a user is a repository collaborator

`GET /repos/{owner}/{repo}/collaborators/{username}`

For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.

Team members will include the members of child teams.

The authenticated user must have push access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.

[API method documentation](https://docs.github.com/rest/collaborators/collaborators#check-if-a-user-is-a-repository-collaborator)

## All Parameters for "Check if a user is a repository collaborator"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.