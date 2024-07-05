# Download workflow run logs

Gets a redirect URL to download an archive of log files for a workflow run. This link expires after 1 minute. Look for
`Location:` in the response header to find the URL for the download.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Download workflow run logs",
    "description": "Gets a redirect URL to download an archive of log files for a workflow run. This link expires after 1 minute. Look for\n`Location:` in the response header to find the URL for the download.\n\nAnyone with read access to the repository can use this endpoint.\n\nIf the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/download-workflow-run-logs",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-runs#download-workflow-run-logs"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/run-id"
        }
    ],
    "responses": {
        "302": {
            "description": "Response",
            "headers": {
                "Location": {
                    "example": "https://pipelines.actions.githubusercontent.com/ab1f3cCFPB34Nd6imvFxpGZH5hNlDp2wijMwl2gDoO0bcrrlJj/_apis/pipelines/1/runs/19/signedlogcontent?urlExpires=2020-01-22T22%3A44%3A54.1389777Z&urlSigningMethod=HMACV1&urlSignature=2TUDfIg4fm36OJmfPy6km5QD5DLCOkBVzvhWZM8B%2BUY%3D",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "workflow-runs"
    }
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/run-id`

```json
{
    "name": "run_id",
    "description": "The unique identifier of the workflow run.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```