# Get the summary of a CodeQL variant analysis

`GET /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses/{codeql_variant_analysis_id}`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-the-summary-of-a-codeql-variant-analysis)

## All Parameters for "Get the summary of a CodeQL variant analysis"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `codeql_variant_analysis_id` (integer, required): The unique identifier of the variant analysis.

## Operation Description

Gets the summary of a CodeQL variant analysis.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
