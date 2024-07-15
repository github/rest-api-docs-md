# Get a gist comment

`GET /gists/{gist_id}/comments/{comment_id}`

[API method documentation](https://docs.github.com/rest/gists/comments#get-a-gist-comment)

## All Parameters for "Get a gist comment"

### Path Parameters

- `gist_id` (string, required): The unique identifier of the gist.
- `comment_id` (integer, required): The unique identifier of the comment.

## Operation Description

Gets a comment on a gist.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.
- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.
