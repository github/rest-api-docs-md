# Get a repository README for a directory

`GET /repos/{owner}/{repo}/readme/{dir}`

Gets the README from a repository directory.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw file contents. This is the default if you do not specify a media type.
- **`application/vnd.github.html+json`**: Returns the README in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).

[API method documentation](https://docs.github.com/rest/repos/contents#get-a-repository-readme-for-a-directory)

## All Parameters for "Get a repository README for a directory"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `dir` (string, required): The alternate path to look for a README file
### Query Parameters

- `ref` (string): The name of the commit/branch/tag. Default: the repository’s default branch.