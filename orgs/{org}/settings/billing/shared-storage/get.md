# Get shared storage billing for an organization

`GET /orgs/{org}/settings/billing/shared-storage`

Gets the estimated paid and estimated total storage used for GitHub Actions and GitHub Packages.

Paid minutes only apply to packages stored for private repositories. For more information, see "[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages)."

OAuth app tokens and personal access tokens (classic) need the `repo` or `admin:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/billing/billing#get-shared-storage-billing-for-an-organization)

## All Parameters for "Get shared storage billing for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.