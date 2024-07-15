# List repository invitations

`GET /repos/{owner}/{repo}/invitations`

[API method documentation](https://docs.github.com/rest/collaborators/invitations#list-repository-invitations)

## All Parameters for "List repository invitations"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

When authenticating as a user with admin rights to a repository, this endpoint will list all currently open repository invitations.
