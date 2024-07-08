# Get GitHub Actions cache usage for an organization

`GET /orgs/{org}/actions/cache/usage`

Gets the total GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

OAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/cache#get-github-actions-cache-usage-for-an-organization)

## All Parameters for "Get GitHub Actions cache usage for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.