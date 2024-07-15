# Get a diff of the dependencies between commits

`GET /repos/{owner}/{repo}/dependency-graph/compare/{basehead}`

[API method documentation](https://docs.github.com/rest/dependency-graph/dependency-review#get-a-diff-of-the-dependencies-between-commits)

## All Parameters for "Get a diff of the dependencies between commits"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `basehead` (string, required): The base and head Git revisions to compare. The Git revisions will be resolved to commit SHAs. Named revisions will be resolved to their corresponding HEAD commits, and an appropriate merge base will be determined. This parameter expects the format `{base}...{head}`.
### Query Parameters

- `name` (string): The full path, relative to the repository root, of the dependency manifest file.

## Operation Description

Gets the diff of the dependency changes between two commits of a repository, based on the changes to the dependency manifests made in those commits.
