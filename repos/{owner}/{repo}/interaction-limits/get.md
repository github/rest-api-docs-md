# Get interaction restrictions for a repository

`GET /repos/{owner}/{repo}/interaction-limits`

Shows which type of GitHub user can interact with this repository and when the restriction expires. If there are no restrictions, you will see an empty response.

[API method documentation](https://docs.github.com/rest/interactions/repos#get-interaction-restrictions-for-a-repository)

## All Parameters for "Get interaction restrictions for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.