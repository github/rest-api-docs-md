# Get GitHub Actions cache usage for a repository

`GET /repos/{owner}/{repo}/actions/cache/usage`

Gets GitHub Actions cache usage for a repository.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/cache#get-github-actions-cache-usage-for-a-repository)

## All Parameters for "Get GitHub Actions cache usage for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.