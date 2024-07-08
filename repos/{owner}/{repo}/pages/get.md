# Get a GitHub Pages site

`GET /repos/{owner}/{repo}/pages`

Gets information about a GitHub Pages site.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/pages/pages#get-a-apiname-pages-site)

## All Parameters for "Get a GitHub Pages site"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.