# Check if automated security fixes are enabled for a repository

`GET /repos/{owner}/{repo}/automated-security-fixes`

[API method documentation](https://docs.github.com/rest/repos/repos#check-if-automated-security-fixes-are-enabled-for-a-repository)

## All Parameters for "Check if automated security fixes are enabled for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Shows whether automated security fixes are enabled, disabled or paused for a repository. The authenticated user must have admin read access to the repository. For more information, see "[Configuring automated security fixes](https://docs.github.com/articles/configuring-automated-security-fixes)".
