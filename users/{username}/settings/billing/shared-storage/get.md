# Get shared storage billing for a user

`GET /users/{username}/settings/billing/shared-storage`

[API method documentation](https://docs.github.com/rest/billing/billing#get-shared-storage-billing-for-a-user)

## All Parameters for "Get shared storage billing for a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Gets the estimated paid and estimated total storage used for GitHub Actions and GitHub Packages.

Paid minutes only apply to packages stored for private repositories. For more information, see "[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages)."

OAuth app tokens and personal access tokens (classic) need the `user` scope to use this endpoint.
