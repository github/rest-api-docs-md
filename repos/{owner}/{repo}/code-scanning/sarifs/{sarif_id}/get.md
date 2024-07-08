# Get information about a SARIF upload

`GET /repos/{owner}/{repo}/code-scanning/sarifs/{sarif_id}`

Gets information about a SARIF upload, including the status and the URL of the analysis that was uploaded so that you can retrieve details of the analysis. For more information, see "[Get a code scanning analysis for a repository](/rest/code-scanning/code-scanning#get-a-code-scanning-analysis-for-a-repository)."
OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-information-about-a-sarif-upload)

## All Parameters for "Get information about a SARIF upload"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `sarif_id` (string, required): The SARIF ID obtained after uploading.