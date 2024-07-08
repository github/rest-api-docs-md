# List reactions for an issue

`GET /repos/{owner}/{repo}/issues/{issue_number}/reactions`

List the reactions to an [issue](https://docs.github.com/rest/issues/issues#get-an-issue).

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-an-issue)

## All Parameters for "List reactions for an issue"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `issue_number` (integer, required): The number that identifies the issue.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to an issue.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."