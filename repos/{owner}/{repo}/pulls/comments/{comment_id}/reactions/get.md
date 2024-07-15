# List reactions for a pull request review comment

`GET /repos/{owner}/{repo}/pulls/comments/{comment_id}/reactions`

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-pull-request-review-comment)

## All Parameters for "List reactions for a pull request review comment"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `comment_id` (integer, required): The unique identifier of the comment.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to a pull request review comment.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List the reactions to a [pull request review comment](https://docs.github.com/rest/pulls/comments#get-a-review-comment-for-a-pull-request).
