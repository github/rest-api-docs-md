# Get a blob

`GET /repos/{owner}/{repo}/git/blobs/{file_sha}`

[API method documentation](https://docs.github.com/rest/git/blobs#get-a-blob)

## All Parameters for "Get a blob"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `file_sha` (string, required)

## Operation Description

The `content` in the response will always be Base64 encoded.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw blob data.
- **`application/vnd.github+json`**: Returns a JSON representation of the blob with `content` as a base64 encoded string. This is the default if no media type is specified.

**Note** This endpoint supports blobs up to 100 megabytes in size.
