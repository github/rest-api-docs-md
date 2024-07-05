# Get all autolinks of a repository

Gets all autolinks that are configured for a repository.

Information about autolinks are only available to repository administrators.

## Operation Object

```json
{
    "summary": "Get all autolinks of a repository",
    "description": "Gets all autolinks that are configured for a repository.\n\nInformation about autolinks are only available to repository administrators.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-autolinks",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/autolinks#get-all-autolinks-of-a-repository"
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
                            "$ref": "#/components/schemas/autolink"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/autolink-items"
                        }
                    }
                }
            }
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

### `#/components/examples/autolink-items`

```json
{
    "value": [
        {
            "id": 1,
            "key_prefix": "TICKET-",
            "url_template": "https://example.com/TICKET?query=<num>",
            "is_alphanumeric": true
        }
    ]
}
```