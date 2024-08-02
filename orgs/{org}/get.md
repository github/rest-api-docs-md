# Get an organization

`GET /orgs/{org}`

[API method documentation](https://docs.github.com/rest/orgs/orgs#get-an-organization)

## All Parameters for "Get an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Gets information about an organization.

When the value of `two_factor_requirement_enabled` is `true`, the organization requires all members, billing managers, and outside collaborators to enable [two-factor authentication](https://docs.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/).

To see the full details about an organization, the authenticated user must be an organization owner.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to see the full details about an organization.

To see information about an organization's GitHub plan, GitHub Apps need the `Organization plan` permission.
