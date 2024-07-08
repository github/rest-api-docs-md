# Get details about a codespace export

`GET /user/codespaces/{codespace_name}/exports/{export_id}`

Gets information about an export of a codespace.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#get-details-about-a-codespace-export)

## All Parameters for "Get details about a codespace export"

### Path Parameters

- `codespace_name` (string, required): The name of the codespace.
- `export_id` (string, required): The ID of the export operation, or `latest`. Currently only `latest` is currently supported.