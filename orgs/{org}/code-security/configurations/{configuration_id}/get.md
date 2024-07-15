# Get a code security configuration

`GET /orgs/{org}/code-security/configurations/{configuration_id}`

[API method documentation](https://docs.github.com/rest/code-security/configurations#get-a-code-security-configuration)

## All Parameters for "Get a code security configuration"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `configuration_id` (integer, required): The unique identifier of the code security configuration.

## Operation Description

Gets a code security configuration available in an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.
