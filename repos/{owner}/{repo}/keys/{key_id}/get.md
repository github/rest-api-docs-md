# Get a deploy key



## Operation Object

```json
{
    "summary": "Get a deploy key",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-deploy-key",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deploy-keys/deploy-keys#get-a-deploy-key"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/key-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/deploy-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deploy-key"
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
        "category": "deploy-keys",
        "subcategory": "deploy-keys"
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

### `#/components/parameters/key-id`

```json
{
    "name": "key_id",
    "description": "The unique identifier of the key.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/deploy-key`

```json
{
    "title": "Deploy Key",
    "description": "An SSH key granting access to a single repository.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "key": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "title": {
            "type": "string"
        },
        "verified": {
            "type": "boolean"
        },
        "created_at": {
            "type": "string"
        },
        "read_only": {
            "type": "boolean"
        },
        "added_by": {
            "type": "string",
            "nullable": true
        },
        "last_used": {
            "type": "string",
            "nullable": true
        }
    },
    "required": [
        "id",
        "key",
        "url",
        "title",
        "verified",
        "created_at",
        "read_only"
    ]
}
```

### `#/components/examples/deploy-key`

```json
{
    "value": {
        "id": 1,
        "key": "ssh-rsa AAA...",
        "url": "https://api.github.com/repos/octocat/Hello-World/keys/1",
        "title": "octocat@octomac",
        "verified": true,
        "created_at": "2014-12-10T15:53:42Z",
        "read_only": true,
        "added_by": "octocat",
        "last_used": "2022-01-10T15:53:42Z"
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