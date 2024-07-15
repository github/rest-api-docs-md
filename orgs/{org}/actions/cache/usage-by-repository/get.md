# List repositories with GitHub Actions cache usage for an organization

`GET /orgs/{org}/actions/cache/usage-by-repository`

[API method documentation](https://docs.github.com/rest/actions/cache#list-repositories-with-github-actions-cache-usage-for-an-organization)

## All Parameters for "List repositories with GitHub Actions cache usage for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists repositories and their GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

OAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.
