# Get allowed actions and reusable workflows for an organization

`GET /orgs/{org}/actions/permissions/selected-actions`

Gets the selected actions and reusable workflows that are allowed in an organization. To use this endpoint, the organization permission policy for `allowed_actions` must be configured to `selected`. For more information, see "[Set GitHub Actions permissions for an organization](#set-github-actions-permissions-for-an-organization)."

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/permissions#get-allowed-actions-and-reusable-workflows-for-an-organization)

## All Parameters for "Get allowed actions and reusable workflows for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.