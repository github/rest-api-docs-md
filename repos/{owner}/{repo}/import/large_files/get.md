# Get large files

`get /repos/{owner}/{repo}/import/large_files`

List files larger than 100MB found during the import

**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).


## Operation Object

```json
{
    "summary": "Get large files",
    "description": "List files larger than 100MB found during the import\n\n**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).\n",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/get-large-files",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/source-imports#get-large-files"
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
                            "$ref": "#/components/schemas/porter-large-file"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/porter-large-file-items"
                        }
                    }
                }
            }
        },
        "503": {
            "$ref": "#/components/responses/porter_maintenance"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "migrations",
        "subcategory": "source-imports",
        "deprecationDate": "2023-10-12",
        "removalDate": "2024-04-12"
    },
    "deprecated": true
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

### `#/components/schemas/porter-large-file`

```json
{
    "title": "Porter Large File",
    "description": "Porter Large File",
    "type": "object",
    "properties": {
        "ref_name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "oid": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        }
    },
    "required": [
        "oid",
        "path",
        "ref_name",
        "size"
    ]
}
```

### `#/components/examples/porter-large-file-items`

```json
{
    "value": [
        {
            "ref_name": "refs/heads/master",
            "path": "foo/bar/1",
            "oid": "d3d9446802a44259755d38e6d163e820",
            "size": 10485760
        },
        {
            "ref_name": "refs/heads/master",
            "path": "foo/bar/2",
            "oid": "6512bd43d9caa6e02c990b0a82652dca",
            "size": 11534336
        },
        {
            "ref_name": "refs/heads/master",
            "path": "foo/bar/3",
            "oid": "c20ad4d76fe97759aa27a0c99bff6710",
            "size": 12582912
        }
    ]
}
```

### `#/components/responses/porter_maintenance`

```json
{
    "description": "Unavailable due to service under maintenance.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```