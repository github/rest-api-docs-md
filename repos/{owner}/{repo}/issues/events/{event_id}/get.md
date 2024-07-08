# Get an issue event

`GET /repos/{owner}/{repo}/issues/events/{event_id}`

Gets a single event by the event id.

[API method documentation](https://docs.github.com/rest/issues/events#get-an-issue-event)

## All Parameters for "Get an issue event"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `event_id` (integer, required)