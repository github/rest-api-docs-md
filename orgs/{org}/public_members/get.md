# List public organization members

`GET /orgs/{org}/public_members`

Members of an organization can choose to have their membership publicized or not.

[API method documentation](https://docs.github.com/rest/orgs/members#list-public-organization-members)

## All Parameters for "List public organization members"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."