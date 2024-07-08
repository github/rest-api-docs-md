# List reactions for an issue comment

`GET /repos/{owner}/{repo}/issues/comments/{comment_id}/reactions`

List the reactions to an [issue comment](https://docs.github.com/rest/issues/comments#get-an-issue-comment).

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-an-issue-comment)

## All Parameters for "List reactions for an issue comment"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `comment_id` (integer, required): The unique identifier of the comment.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to an issue comment.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."