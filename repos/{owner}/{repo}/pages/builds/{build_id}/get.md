# Get GitHub Pages build

`GET /repos/{owner}/{repo}/pages/builds/{build_id}`

Gets information about a GitHub Pages build.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/pages/pages#get-apiname-pages-build)

## All Parameters for "Get GitHub Pages build"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `build_id` (integer, required)