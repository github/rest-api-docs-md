# List outside collaborators for an organization

`GET /orgs/{org}/outside_collaborators`

[API method documentation](https://docs.github.com/rest/orgs/outside-collaborators#list-outside-collaborators-for-an-organization)

## All Parameters for "List outside collaborators for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `filter` (string): Filter the list of outside collaborators. `2fa_disabled` means that only outside collaborators without [two-factor authentication](https://github.com/blog/1614-two-factor-authentication) enabled will be returned.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List all users who are outside collaborators of an organization.
