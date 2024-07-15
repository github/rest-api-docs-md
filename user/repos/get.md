# List repositories for the authenticated user

`GET /user/repos`

[API method documentation](https://docs.github.com/rest/repos/repos#list-repositories-for-the-authenticated-user)

## All Parameters for "List repositories for the authenticated user"

### Query Parameters

- `visibility` (string): Limit results to repositories with the specified visibility.
- `affiliation` (string): Comma-separated list of values. Can include:  
 * `owner`: Repositories that are owned by the authenticated user.  
 * `collaborator`: Repositories that the user has been added to as a collaborator.  
 * `organization_member`: Repositories that the user has access to through being a member of an organization. This includes every repository on every team that the user is on.
- `type` (string): Limit results to repositories of the specified type. Will cause a `422` error if used in the same request as **visibility** or **affiliation**.
- `sort` (string): The property to sort the results by.
- `direction` (string): The order to sort by. Default: `asc` when using `full_name`, otherwise `desc`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `since` (string): Only show repositories updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.
- `before` (string): Only show repositories updated before the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.

## Operation Description

Lists repositories that the authenticated user has explicit permission (`:read`, `:write`, or `:admin`) to access.

The authenticated user has explicit permission to access repositories they own, repositories where they are a collaborator, and repositories that they can access through an organization membership.
