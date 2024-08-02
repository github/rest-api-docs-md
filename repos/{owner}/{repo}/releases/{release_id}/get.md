# Get a release

`GET /repos/{owner}/{repo}/releases/{release_id}`

[API method documentation](https://docs.github.com/rest/releases/releases#get-a-release)

## All Parameters for "Get a release"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `release_id` (integer, required): The unique identifier of the release.

## Operation Description

Gets a public release with the specified release ID.

> [!NOTE]
> This returns an `upload_url` key corresponding to the endpoint for uploading release assets. This key is a hypermedia resource. For more information, see "[Getting started with the REST API](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#hypermedia)."
