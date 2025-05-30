# Get access restrictions

`GET /repos/{owner}/{repo}/branches/{branch}/protection/restrictions`

[API method documentation](https://docs.github.com/rest/branches/branch-protection#get-access-restrictions)

## All Parameters for "Get access restrictions"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `branch` (string, required): The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).

## Operation Description

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

Lists who has access to this protected branch.

> [!NOTE]
> Users, apps, and teams `restrictions` are only available for organization-owned repositories.
