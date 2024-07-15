# Get a repository README

`GET /repos/{owner}/{repo}/readme`

[API method documentation](https://docs.github.com/rest/repos/contents#get-a-repository-readme)

## All Parameters for "Get a repository README"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `ref` (string): The name of the commit/branch/tag. Default: the repository’s default branch.

## Operation Description

Gets the preferred README for a repository.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw file contents. This is the default if you do not specify a media type.
- **`application/vnd.github.html+json`**: Returns the README in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).
