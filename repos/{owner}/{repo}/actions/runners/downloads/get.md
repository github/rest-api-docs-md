# List runner applications for a repository

`get /repos/{owner}/{repo}/actions/runners/downloads`

Lists binaries for the runner application that you can download and run.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List runner applications for a repository",
    "description": "Lists binaries for the runner application that you can download and run.\n\nAuthenticated users must have admin access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-runner-applications-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#list-runner-applications-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/runner-application"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/runner-application-items"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "self-hosted-runners"
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

### `#/components/schemas/runner-application`

```json
{
    "title": "Runner Application",
    "description": "Runner Application",
    "type": "object",
    "properties": {
        "os": {
            "type": "string"
        },
        "architecture": {
            "type": "string"
        },
        "download_url": {
            "type": "string"
        },
        "filename": {
            "type": "string"
        },
        "temp_download_token": {
            "description": "A short lived bearer token used to download the runner, if needed.",
            "type": "string"
        },
        "sha256_checksum": {
            "type": "string"
        }
    },
    "required": [
        "os",
        "architecture",
        "download_url",
        "filename"
    ]
}
```

### `#/components/examples/runner-application-items`

```json
{
    "value": [
        {
            "os": "osx",
            "architecture": "x64",
            "download_url": "https://github.com/actions/runner/releases/download/v2.164.0/actions-runner-osx-x64-2.164.0.tar.gz",
            "filename": "actions-runner-osx-x64-2.164.0.tar.gz"
        },
        {
            "os": "linux",
            "architecture": "x64",
            "download_url": "https://github.com/actions/runner/releases/download/v2.164.0/actions-runner-linux-x64-2.164.0.tar.gz",
            "filename": "actions-runner-linux-x64-2.164.0.tar.gz"
        },
        {
            "os": "linux",
            "architecture": "arm",
            "download_url": "https://github.com/actions/runner/releases/download/v2.164.0/actions-runner-linux-arm-2.164.0.tar.gz",
            "filename": "actions-runner-linux-arm-2.164.0.tar.gz"
        },
        {
            "os": "win",
            "architecture": "x64",
            "download_url": "https://github.com/actions/runner/releases/download/v2.164.0/actions-runner-win-x64-2.164.0.zip",
            "filename": "actions-runner-win-x64-2.164.0.zip"
        },
        {
            "os": "linux",
            "architecture": "arm64",
            "download_url": "https://github.com/actions/runner/releases/download/v2.164.0/actions-runner-linux-arm64-2.164.0.tar.gz",
            "filename": "actions-runner-linux-arm64-2.164.0.tar.gz"
        }
    ]
}
```