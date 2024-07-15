# Download an artifact

`GET /repos/{owner}/{repo}/actions/artifacts/{artifact_id}/{archive_format}`

[API method documentation](https://docs.github.com/rest/actions/artifacts#download-an-artifact)

## All Parameters for "Download an artifact"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `artifact_id` (integer, required): The unique identifier of the artifact.
- `archive_format` (string, required)

## Operation Description

Gets a redirect URL to download an archive for a repository. This URL expires after 1 minute. Look for `Location:` in
the response header to find the URL for the download. The `:archive_format` must be `zip`.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
