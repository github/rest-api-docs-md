# Get default code security configurations

`GET /orgs/{org}/code-security/configurations/defaults`

[API method documentation](https://docs.github.com/rest/code-security/configurations#get-default-code-security-configurations)

## All Parameters for "Get default code security configurations"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Lists the default code security configurations for an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.
