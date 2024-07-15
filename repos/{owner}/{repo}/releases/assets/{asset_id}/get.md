# Get a release asset

`GET /repos/{owner}/{repo}/releases/assets/{asset_id}`

[API method documentation](https://docs.github.com/rest/releases/assets#get-a-release-asset)

## All Parameters for "Get a release asset"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `asset_id` (integer, required): The unique identifier of the asset.

## Operation Description

To download the asset's binary content, set the `Accept` header of the request to [`application/octet-stream`](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types). The API will either redirect the client to the location, or stream it directly if possible. API clients should handle both a `200` or `302` response.
