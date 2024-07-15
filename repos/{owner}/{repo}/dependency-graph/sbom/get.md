# Export a software bill of materials (SBOM) for a repository.

`GET /repos/{owner}/{repo}/dependency-graph/sbom`

[API method documentation](https://docs.github.com/rest/dependency-graph/sboms#export-a-software-bill-of-materials-sbom-for-a-repository)

## All Parameters for "Export a software bill of materials (SBOM) for a repository."

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Exports the software bill of materials (SBOM) for a repository in SPDX JSON format.
