# List repository invitations for the authenticated user

`GET /user/repository_invitations`

[API method documentation](https://docs.github.com/rest/collaborators/invitations#list-repository-invitations-for-the-authenticated-user)

## All Parameters for "List repository invitations for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

When authenticating as a user, this endpoint will list all currently open repository invitations for that user.
