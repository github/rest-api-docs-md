# Get the weekly commit count

`GET /repos/{owner}/{repo}/stats/participation`

Returns the total commit counts for the `owner` and total commit counts in `all`. `all` is everyone combined, including the `owner` in the last 52 weeks. If you'd like to get the commit counts for non-owners, you can subtract `owner` from `all`.

The array order is oldest week (index 0) to most recent week.

The most recent week is seven days ago at UTC midnight to today at UTC midnight.

[API method documentation](https://docs.github.com/rest/metrics/statistics#get-the-weekly-commit-count)

## All Parameters for "Get the weekly commit count"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.