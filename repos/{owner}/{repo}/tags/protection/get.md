# Deprecated - List tag protection states for a repository

`GET /repos/{owner}/{repo}/tags/protection`

**Note**: This operation is deprecated and will be removed after August 30th 2024
Use the "[Repository Rulesets](https://docs.github.com/rest/repos/rules#get-all-repository-rulesets)" endpoint instead.

This returns the tag protection states of a repository.

This information is only available to repository administrators.

[API method documentation](https://docs.github.com/rest/repos/tags#deprecated---list-tag-protection-states-for-a-repository)

## All Parameters for "Deprecated - List tag protection states for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.