# List pull requests

`GET /repos/{owner}/{repo}/pulls`

Lists pull requests in a specified repository.

Draft pull requests are available in public repositories with GitHub
Free and GitHub Free for organizations, GitHub Pro, and legacy per-repository billing
plans, and in public and private repositories with GitHub Team and GitHub Enterprise
Cloud. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products)
in the GitHub Help documentation.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

[API method documentation](https://docs.github.com/rest/pulls/pulls#list-pull-requests)

## All Parameters for "List pull requests"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `state` (string): Either `open`, `closed`, or `all` to filter by state.
- `head` (string): Filter pulls by head user or head organization and branch name in the format of `user:ref-name` or `organization:ref-name`. For example: `github:new-script-format` or `octocat:test-branch`.
- `base` (string): Filter pulls by base branch name. Example: `gh-pages`.
- `sort` (string): What to sort results by. `popularity` will sort by the number of comments. `long-running` will sort by date created and will limit the results to pull requests that have been open for more than a month and have had activity within the past month.
- `direction` (string): The direction of the sort. Default: `desc` when sort is `created` or sort is not specified, otherwise `asc`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."