# Get repository clones

`GET /repos/{owner}/{repo}/traffic/clones`

Get the total number of clones and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.

[API method documentation](https://docs.github.com/rest/metrics/traffic#get-repository-clones)

## All Parameters for "Get repository clones"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per` (string): The time frame to display results for.