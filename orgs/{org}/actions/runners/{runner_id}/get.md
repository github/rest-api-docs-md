# Get a self-hosted runner for an organization

`GET /orgs/{org}/actions/runners/{runner_id}`

[API method documentation](https://docs.github.com/rest/actions/self-hosted-runners#get-a-self-hosted-runner-for-an-organization)

## All Parameters for "Get a self-hosted runner for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `runner_id` (integer, required): Unique identifier of the self-hosted runner.

## Operation Description

Gets a specific self-hosted runner configured in an organization.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.
