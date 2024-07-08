# Get the hourly commit count for each day

`GET /repos/{owner}/{repo}/stats/punch_card`

Each array contains the day number, hour number, and number of commits:

*   `0-6`: Sunday - Saturday
*   `0-23`: Hour of day
*   Number of commits

For example, `[2, 14, 25]` indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.

[API method documentation](https://docs.github.com/rest/metrics/statistics#get-the-hourly-commit-count-for-each-day)

## All Parameters for "Get the hourly commit count for each day"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.