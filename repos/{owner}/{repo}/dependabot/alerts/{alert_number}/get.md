# Get a Dependabot alert

`GET /repos/{owner}/{repo}/dependabot/alerts/{alert_number}`

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

[API method documentation](https://docs.github.com/rest/dependabot/alerts#get-a-dependabot-alert)

## All Parameters for "Get a Dependabot alert"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `alert_number` (, required): The number that identifies a Dependabot alert in its repository.
You can find this at the end of the URL for a Dependabot alert within GitHub,
or in `number` fields in the response from the
`GET /repos/{owner}/{repo}/dependabot/alerts` operation.