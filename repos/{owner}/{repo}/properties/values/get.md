# Get all custom property values for a repository

`GET /repos/{owner}/{repo}/properties/values`

Gets all custom property values that are set for a repository.
Users with read access to the repository can use this endpoint.

[API method documentation](https://docs.github.com/rest/repos/custom-properties#get-all-custom-property-values-for-a-repository)

## All Parameters for "Get all custom property values for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.