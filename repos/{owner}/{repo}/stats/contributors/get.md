# Get all contributor commit activity

`GET /repos/{owner}/{repo}/stats/contributors`


Returns the `total` number of commits authored by the contributor. In addition, the response includes a Weekly Hash (`weeks` array) with the following information:

*   `w` - Start of the week, given as a [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time).
*   `a` - Number of additions
*   `d` - Number of deletions
*   `c` - Number of commits

**Note:** This endpoint will return `0` values for all addition and deletion counts in repositories with 10,000 or more commits.

[API method documentation](https://docs.github.com/rest/metrics/statistics#get-all-contributor-commit-activity)

## All Parameters for "Get all contributor commit activity"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.