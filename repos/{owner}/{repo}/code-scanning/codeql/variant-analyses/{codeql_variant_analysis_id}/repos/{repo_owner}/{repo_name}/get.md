# Get the analysis status of a repository in a CodeQL variant analysis

`GET /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses/{codeql_variant_analysis_id}/repos/{repo_owner}/{repo_name}`

Gets the analysis status of a repository in a CodeQL variant analysis.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-the-analysis-status-of-a-repository-in-a-codeql-variant-analysis)

## All Parameters for "Get the analysis status of a repository in a CodeQL variant analysis"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the controller repository.
- `codeql_variant_analysis_id` (integer, required): The ID of the variant analysis.
- `repo_owner` (string, required): The account owner of the variant analysis repository. The name is not case sensitive.
- `repo_name` (string, required): The name of the variant analysis repository.