# Get large files

`GET /repos/{owner}/{repo}/import/large_files`

[API method documentation](https://docs.github.com/rest/migrations/source-imports#get-large-files)

## All Parameters for "Get large files"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

List files larger than 100MB found during the import

> [!WARNING]
> **Deprecation notice:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).
