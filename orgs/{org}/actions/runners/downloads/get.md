# List runner applications for an organization

`GET /orgs/{org}/actions/runners/downloads`

[API method documentation](https://docs.github.com/rest/actions/self-hosted-runners#list-runner-applications-for-an-organization)

## All Parameters for "List runner applications for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Lists binaries for the runner application that you can download and run.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.  If the repository is private, the `repo` scope is also required.
