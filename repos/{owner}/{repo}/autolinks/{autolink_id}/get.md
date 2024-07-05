# Get an autolink reference of a repository

`get /repos/{owner}/{repo}/autolinks/{autolink_id}`

This returns a single autolink reference by ID that was configured for the given repository.

Information about autolinks are only available to repository administrators.

## Operation Object

```json
{
    "summary": "Get an autolink reference of a repository",
    "description": "This returns a single autolink reference by ID that was configured for the given repository.\n\nInformation about autolinks are only available to repository administrators.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-autolink",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/autolinks#get-an-autolink-reference-of-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/autolink-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/autolink"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/autolink"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "autolinks"
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

### `#/components/parameters/autolink-id`

```json
{
    "name": "autolink_id",
    "description": "The unique identifier of the autolink.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/autolink`

```json
{
    "title": "Autolink reference",
    "description": "An autolink reference.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 3
        },
        "key_prefix": {
            "description": "The prefix of a key that is linkified.",
            "example": "TICKET-",
            "type": "string"
        },
        "url_template": {
            "description": "A template for the target URL that is generated if a key was found.",
            "example": "https://example.com/TICKET?query=<num>",
            "type": "string"
        },
        "is_alphanumeric": {
            "description": "Whether this autolink reference matches alphanumeric characters. If false, this autolink reference only matches numeric characters.",
            "example": true,
            "type": "boolean"
        }
    },
    "required": [
        "id",
        "key_prefix",
        "url_template",
        "is_alphanumeric"
    ]
}
```

### `#/components/examples/autolink`

```json
{
    "value": {
        "id": 1,
        "key_prefix": "TICKET-",
        "url_template": "https://example.com/TICKET?query=<num>",
        "is_alphanumeric": true
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```