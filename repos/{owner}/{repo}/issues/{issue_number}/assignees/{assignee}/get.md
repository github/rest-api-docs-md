# Check if a user can be assigned to a issue

Checks if a user has permission to be assigned to a specific issue.

If the `assignee` can be assigned to this issue, a `204` status code with no content is returned.

Otherwise a `404` status code is returned.

## Operation Object

```json
{
    "summary": "Check if a user can be assigned to a issue",
    "description": "Checks if a user has permission to be assigned to a specific issue.\n\nIf the `assignee` can be assigned to this issue, a `204` status code with no content is returned.\n\nOtherwise a `404` status code is returned.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/check-user-can-be-assigned-to-issue",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/assignees#check-if-a-user-can-be-assigned-to-a-issue"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/issue-number"
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
            "description": "Response if `assignee` can be assigned to `issue_number`"
        },
        "404": {
            "description": "Response if `assignee` can not be assigned to `issue_number`",
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

### `#/components/parameters/issue-number`

```json
{
    "name": "issue_number",
    "description": "The number that identifies the issue.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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