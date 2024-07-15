# List reactions for a commit comment

`GET /repos/{owner}/{repo}/comments/{comment_id}/reactions`

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-commit-comment)

## All Parameters for "List reactions for a commit comment"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `comment_id` (integer, required): The unique identifier of the comment.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to a commit comment.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List the reactions to a [commit comment](https://docs.github.com/rest/commits/comments#get-a-commit-comment).
