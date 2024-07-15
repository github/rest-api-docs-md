# Download a repository archive (zip)

`GET /repos/{owner}/{repo}/zipball/{ref}`

[API method documentation](https://docs.github.com/rest/repos/contents#download-a-repository-archive-zip)

## All Parameters for "Download a repository archive (zip)"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ref` (string, required)

## Operation Description

Gets a redirect URL to download a zip archive for a repository. If you omit `:ref`, the repository’s default branch (usually
`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use
the `Location` header to make a second `GET` request.

**Note**: For private repositories, these links are temporary and expire after five minutes. If the repository is empty, you will receive a 404 when you follow the redirect.
