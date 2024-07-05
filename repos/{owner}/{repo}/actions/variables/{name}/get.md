# Get a repository variable

`get /repos/{owner}/{repo}/actions/variables/{name}`

Gets a specific variable in a repository.

The authenticated user must have collaborator access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a repository variable",
    "description": "Gets a specific variable in a repository.\n\nThe authenticated user must have collaborator access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-repo-variable",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/variables#get-a-repository-variable"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/variable-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-variable"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-variable"
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
        "subcategory": "variables"
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

### `#/components/parameters/variable-name`

```json
{
    "name": "name",
    "description": "The name of the variable.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/actions-variable`

```json
{
    "title": "Actions Variable",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the variable.",
            "example": "USERNAME",
            "type": "string"
        },
        "value": {
            "description": "The value of the variable.",
            "example": "octocat",
            "type": "string"
        },
        "created_at": {
            "description": "The date and time at which the variable was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time",
            "example": "2019-01-24T22:45:36.000Z"
        },
        "updated_at": {
            "description": "The date and time at which the variable was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time",
            "example": "2019-01-24T22:45:36.000Z"
        }
    },
    "required": [
        "name",
        "value",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/actions-variable`

```json
{
    "value": {
        "name": "USERNAME",
        "value": "octocat",
        "created_at": "2021-08-10T14:59:22Z",
        "updated_at": "2022-01-10T14:59:22Z"
    }
}
```