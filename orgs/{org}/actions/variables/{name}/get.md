# Get an organization variable

`get /orgs/{org}/actions/variables/{name}`

Gets a specific variable in an organization.

The authenticated user must have collaborator access to a repository to create, update, or read variables.

OAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization variable",
    "description": "Gets a specific variable in an organization.\n\nThe authenticated user must have collaborator access to a repository to create, update, or read variables.\n\nOAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-org-variable",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/variables#get-an-organization-variable"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                        "$ref": "#/components/schemas/organization-actions-variable"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-actions-variable"
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

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
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

### `#/components/schemas/organization-actions-variable`

```json
{
    "title": "Actions Variable for an Organization",
    "description": "Organization variable for GitHub Actions.",
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
            "example": "2019-01-24T22:45:36.000Z",
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "description": "The date and time at which the variable was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "example": "2019-01-24T22:45:36.000Z",
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "Visibility of a variable",
            "enum": [
                "all",
                "private",
                "selected"
            ],
            "type": "string"
        },
        "selected_repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/org/variables/USERNAME/repositories"
        }
    },
    "required": [
        "name",
        "value",
        "created_at",
        "updated_at",
        "visibility"
    ]
}
```

### `#/components/examples/organization-actions-variable`

```json
{
    "value": {
        "name": "USERNAME",
        "value": "octocat",
        "created_at": "2019-08-10T14:59:22Z",
        "updated_at": "2020-01-10T14:59:22Z",
        "visibility": "selected",
        "selected_repositories_url": "https://api.github.com/orgs/octo-org/actions/variables/USERNAME/repositories"
    }
}
```