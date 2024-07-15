# List repository collaborators

`GET /repos/{owner}/{repo}/collaborators`

[API method documentation](https://docs.github.com/rest/collaborators/collaborators#list-repository-collaborators)

## All Parameters for "List repository collaborators"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `affiliation` (string): Filter collaborators returned by their affiliation. `outside` means all outside collaborators of an organization-owned repository. `direct` means all collaborators with permissions to an organization-owned repository, regardless of organization membership status. `all` means all collaborators the authenticated user can see.
- `permission` (string): Filter collaborators by the permissions they have on the repository. If not specified, all collaborators will be returned.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.
Organization members with write, maintain, or admin privileges on the organization-owned repository can use this endpoint.

Team members will include the members of child teams.

The authenticated user must have push access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.
