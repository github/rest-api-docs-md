# Get GitHub Actions permissions for an organization

`GET /orgs/{org}/actions/permissions`

[API method documentation](https://docs.github.com/rest/actions/permissions#get-github-actions-permissions-for-an-organization)

## All Parameters for "Get GitHub Actions permissions for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Gets the GitHub Actions permissions policy for repositories and allowed actions and reusable workflows in an organization.

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
