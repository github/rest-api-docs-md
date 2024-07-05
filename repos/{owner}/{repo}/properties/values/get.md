# Get all custom property values for a repository

`get /repos/{owner}/{repo}/properties/values`

Gets all custom property values that are set for a repository.
Users with read access to the repository can use this endpoint.

## Operation Object

```json
{
    "summary": "Get all custom property values for a repository",
    "description": "Gets all custom property values that are set for a repository.\nUsers with read access to the repository can use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-custom-properties-values",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/custom-properties#get-all-custom-property-values-for-a-repository"
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
                            "$ref": "#/components/schemas/custom-property-value"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/custom-property-values"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "custom-properties"
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

### `#/components/schemas/custom-property-value`

```json
{
    "title": "Custom Property Value",
    "description": "Custom property name and associated value",
    "type": "object",
    "properties": {
        "property_name": {
            "type": "string",
            "description": "The name of the property"
        },
        "value": {
            "oneOf": [
                {
                    "type": "string"
                },
                {
                    "type": "array",
                    "items": {
                        "type": "string"
                    }
                }
            ],
            "description": "The value assigned to the property",
            "nullable": true
        }
    },
    "required": [
        "property_name",
        "value"
    ]
}
```

### `#/components/examples/custom-property-values`

```json
{
    "value": [
        {
            "property_name": "environment",
            "value": "production"
        },
        {
            "property_name": "service",
            "value": "web"
        },
        {
            "property_name": "team",
            "value": "octocat"
        }
    ]
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