# List repositories accessible to the user access token

`GET /user/installations/{installation_id}/repositories`

List repositories that the authenticated user has explicit permission (`:read`, `:write`, or `:admin`) to access for an installation.

The authenticated user has explicit permission to access repositories they own, repositories where they are a collaborator, and repositories that they can access through an organization membership.

The access the user has to each repository is included in the hash under the `permissions` key.

[API method documentation](https://docs.github.com/rest/apps/installations#list-repositories-accessible-to-the-user-access-token)

## All Parameters for "List repositories accessible to the user access token"

### Path Parameters

- `installation_id` (integer, required): The unique identifier of the installation.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."