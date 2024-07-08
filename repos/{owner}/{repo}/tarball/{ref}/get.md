# Download a repository archive (tar)

`GET /repos/{owner}/{repo}/tarball/{ref}`

Gets a redirect URL to download a tar archive for a repository. If you omit `:ref`, the repository’s default branch (usually
`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use
the `Location` header to make a second `GET` request.
**Note**: For private repositories, these links are temporary and expire after five minutes.

[API method documentation](https://docs.github.com/rest/repos/contents#download-a-repository-archive-tar)

## All Parameters for "Download a repository archive (tar)"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ref` (string, required)