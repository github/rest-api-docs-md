# Check if a gist is starred

`get /gists/{gist_id}/star`



## Operation Object

```json
{
    "summary": "Check if a gist is starred",
    "description": "",
    "tags": [
        "gists"
    ],
    "operationId": "gists/check-is-starred",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/gists#check-if-a-gist-is-starred"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/gist-id"
        }
    ],
    "responses": {
        "204": {
            "description": "Response if gist is starred"
        },
        "404": {
            "description": "Not Found if gist is not starred",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {},
                        "additionalProperties": false
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "gists",
        "subcategory": "gists"
    }
}
```

## References

### `#/components/parameters/gist-id`

```json
{
    "name": "gist_id",
    "description": "The unique identifier of the gist.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```