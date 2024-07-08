# Get a branch

`GET /repos/{owner}/{repo}/branches/{branch}`



[API method documentation](https://docs.github.com/rest/branches/branches#get-a-branch)

## All Parameters for "Get a branch"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `branch` (string, required): The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).