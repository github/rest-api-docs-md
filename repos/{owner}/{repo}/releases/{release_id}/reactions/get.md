# List reactions for a release

`GET /repos/{owner}/{repo}/releases/{release_id}/reactions`

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-release)

## All Parameters for "List reactions for a release"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `release_id` (integer, required): The unique identifier of the release.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to a release.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List the reactions to a [release](https://docs.github.com/rest/releases/releases#get-a-release).
