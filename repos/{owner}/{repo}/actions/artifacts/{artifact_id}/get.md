# Get an artifact

`GET /repos/{owner}/{repo}/actions/artifacts/{artifact_id}`

[API method documentation](https://docs.github.com/rest/actions/artifacts#get-an-artifact)

## All Parameters for "Get an artifact"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `artifact_id` (integer, required): The unique identifier of the artifact.

## Operation Description

Gets a specific artifact for a workflow run.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
