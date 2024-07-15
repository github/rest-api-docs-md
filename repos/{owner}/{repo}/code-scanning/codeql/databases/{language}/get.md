# Get a CodeQL database for a repository

`GET /repos/{owner}/{repo}/code-scanning/codeql/databases/{language}`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-a-codeql-database-for-a-repository)

## All Parameters for "Get a CodeQL database for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `language` (string, required): The language of the CodeQL database.

## Operation Description

Gets a CodeQL database for a language in a repository.

By default this endpoint returns JSON metadata about the CodeQL database. To
download the CodeQL database binary content, set the `Accept` header of the request
to [`application/zip`](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types), and make sure
your HTTP client is configured to follow redirects or use the `Location` header
to make a second request to get the redirect URL.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
