# Get a review for a pull request

`GET /repos/{owner}/{repo}/pulls/{pull_number}/reviews/{review_id}`

[API method documentation](https://docs.github.com/rest/pulls/reviews#get-a-review-for-a-pull-request)

## All Parameters for "Get a review for a pull request"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `pull_number` (integer, required): The number that identifies the pull request.
- `review_id` (integer, required): The unique identifier of the review.

## Operation Description

Retrieves a pull request review by its ID.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.
