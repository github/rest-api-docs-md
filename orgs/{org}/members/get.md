# List organization members

`GET /orgs/{org}/members`

List all users who are members of an organization. If the authenticated user is also a member of this organization then both concealed and public members will be returned.

[API method documentation](https://docs.github.com/rest/orgs/members#list-organization-members)

## All Parameters for "List organization members"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `filter` (string): Filter members returned in the list. `2fa_disabled` means that only members without [two-factor authentication](https://github.com/blog/1614-two-factor-authentication) enabled will be returned. This options is only available for organization owners.
- `role` (string): Filter members returned by their role.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."