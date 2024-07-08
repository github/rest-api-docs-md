# Get a milestone

`GET /repos/{owner}/{repo}/milestones/{milestone_number}`

Gets a milestone using the given milestone number.

[API method documentation](https://docs.github.com/rest/issues/milestones#get-a-milestone)

## All Parameters for "Get a milestone"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `milestone_number` (integer, required): The number that identifies the milestone.