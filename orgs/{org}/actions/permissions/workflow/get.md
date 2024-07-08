# Get default workflow permissions for an organization

`GET /orgs/{org}/actions/permissions/workflow`

Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in an organization,
as well as whether GitHub Actions can submit approving pull request reviews. For more information, see
"[Setting the permissions of the GITHUB_TOKEN for your organization](https://docs.github.com/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#setting-the-permissions-of-the-github_token-for-your-organization)."

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/permissions#get-default-workflow-permissions-for-an-organization)

## All Parameters for "Get default workflow permissions for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.