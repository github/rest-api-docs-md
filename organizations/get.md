# List organizations

`GET /organizations`

[API method documentation](https://docs.github.com/rest/orgs/orgs#list-organizations)

## All Parameters for "List organizations"

### Query Parameters

- `since` (integer): An organization ID. Only return organizations with an ID greater than this ID.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all organizations, in the order that they were created.

> [!NOTE]
> Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of organizations.
