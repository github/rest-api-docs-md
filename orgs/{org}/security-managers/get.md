# List security manager teams

`GET /orgs/{org}/security-managers`

[API method documentation](https://docs.github.com/rest/orgs/security-managers#list-security-manager-teams)

## All Parameters for "List security manager teams"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Lists teams that are security managers for an organization. For more information, see "[Managing security managers in your organization](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization)."

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.
