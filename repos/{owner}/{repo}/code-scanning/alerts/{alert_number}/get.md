# Get a code scanning alert

`GET /repos/{owner}/{repo}/code-scanning/alerts/{alert_number}`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#get-a-code-scanning-alert)

## All Parameters for "Get a code scanning alert"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `alert_number` (, required): The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the `number` field in the response from the `GET /repos/{owner}/{repo}/code-scanning/alerts` operation.

## Operation Description

Gets a single code scanning alert.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
