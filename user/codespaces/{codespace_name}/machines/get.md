# List machine types for a codespace

List the machine types a codespace can transition to use.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List machine types for a codespace",
    "description": "List the machine types a codespace can transition to use.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/codespace-machines-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/machines#list-machine-types-for-a-codespace"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/codespace-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "required": [
                            "total_count",
                            "machines"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "machines": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/codespace-machine"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespace-machines-list"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
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
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "machines"
    }
}
```

## References

### `#/components/parameters/codespace-name`

```json
{
    "name": "codespace_name",
    "in": "path",
    "required": true,
    "description": "The name of the codespace.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/codespace-machine`

```json
{
    "type": "object",
    "title": "Codespace machine",
    "description": "A description of the machine powering a codespace.",
    "properties": {
        "name": {
            "type": "string",
            "description": "The name of the machine.",
            "example": "standardLinux"
        },
        "display_name": {
            "type": "string",
            "description": "The display name of the machine includes cores, memory, and storage.",
            "example": "4 cores, 16 GB RAM, 64 GB storage"
        },
        "operating_system": {
            "type": "string",
            "description": "The operating system of the machine.",
            "example": "linux"
        },
        "storage_in_bytes": {
            "type": "integer",
            "description": "How much storage is available to the codespace.",
            "example": 68719476736
        },
        "memory_in_bytes": {
            "type": "integer",
            "description": "How much memory is available to the codespace.",
            "example": 17179869184
        },
        "cpus": {
            "type": "integer",
            "description": "How many cores are available to the codespace.",
            "example": 4
        },
        "prebuild_availability": {
            "type": "string",
            "description": "Whether a prebuild is currently available when creating a codespace for this machine and repository. If a branch was not specified as a ref, the default branch will be assumed. Value will be \"null\" if prebuilds are not supported or prebuild availability could not be determined. Value will be \"none\" if no prebuild is available. Latest values \"ready\" and \"in_progress\" indicate the prebuild availability status.",
            "example": "ready",
            "enum": [
                "none",
                "ready",
                "in_progress"
            ],
            "nullable": true
        }
    },
    "required": [
        "name",
        "display_name",
        "operating_system",
        "storage_in_bytes",
        "memory_in_bytes",
        "cpus",
        "prebuild_availability"
    ]
}
```

### `#/components/examples/codespace-machines-list`

```json
{
    "value": {
        "total_count": 2,
        "machines": [
            {
                "name": "standardLinux",
                "display_name": "4 cores, 16 GB RAM, 64 GB storage",
                "operating_system": "linux",
                "storage_in_bytes": 68719476736,
                "memory_in_bytes": 17179869184,
                "cpus": 4
            },
            {
                "name": "premiumLinux",
                "display_name": "8 cores, 32 GB RAM, 64 GB storage",
                "operating_system": "linux",
                "storage_in_bytes": 68719476736,
                "memory_in_bytes": 34359738368,
                "cpus": 8
            }
        ]
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/internal_error`

```json
{
    "description": "Internal Error",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
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