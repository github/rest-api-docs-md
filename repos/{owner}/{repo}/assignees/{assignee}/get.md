# Check if a user can be assigned

Checks if a user has permission to be assigned to an issue in this repository.

If the `assignee` can be assigned to issues in the repository, a `204` header with no content is returned.

Otherwise a `404` status code is returned.

## Operation Object

```json
{
    "summary": "Check if a user can be assigned",
    "description": "Checks if a user has permission to be assigned to an issue in this repository.\n\nIf the `assignee` can be assigned to issues in the repository, a `204` header with no content is returned.\n\nOtherwise a `404` status code is returned.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/check-user-can-be-assigned",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/assignees#check-if-a-user-can-be-assigned"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "assignee",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "204": {
            "description": "If the `assignee` can be assigned to issues in the repository, a `204` header with no content is returned."
        },
        "404": {
            "description": "Otherwise a `404` status code is returned.",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/basic-error"
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "issues",
        "subcategory": "assignees"
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

### `#/components/schemas/basic-error`

```json
{
    "title": "Basic Error",
    "description": "Basic Error",
    "type": "object",
    "properties": {
        "message": {
            "type": "string"
        },
        "documentation_url": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "status": {
            "type": "string"
        }
    }
}
```