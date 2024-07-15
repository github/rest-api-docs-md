# Get latest Pages build

`GET /repos/{owner}/{repo}/pages/builds/latest`

[API method documentation](https://docs.github.com/rest/pages/pages#get-latest-pages-build)

## All Parameters for "Get latest Pages build"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Gets information about the single most recent build of a GitHub Pages site.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
