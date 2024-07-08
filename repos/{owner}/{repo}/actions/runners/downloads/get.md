# List runner applications for a repository

`GET /repos/{owner}/{repo}/actions/runners/downloads`

Lists binaries for the runner application that you can download and run.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/self-hosted-runners#list-runner-applications-for-a-repository)

## All Parameters for "List runner applications for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.