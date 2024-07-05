# Get GitHub meta information

`get /meta`

Returns meta information about GitHub, including a list of GitHub's IP addresses. For more information, see "[About GitHub's IP addresses](https://docs.github.com/articles/about-github-s-ip-addresses/)."

The API's response also includes a list of GitHub's domain names.

The values shown in the documentation's response are example values. You must always query the API directly to get the latest values.

**Note:** This endpoint returns both IPv4 and IPv6 addresses. However, not all features support IPv6. You should refer to the specific documentation for each feature to determine if IPv6 is supported.

## Operation Object

```json
{
    "summary": "Get GitHub meta information",
    "description": "Returns meta information about GitHub, including a list of GitHub's IP addresses. For more information, see \"[About GitHub's IP addresses](https://docs.github.com/articles/about-github-s-ip-addresses/).\"\n\nThe API's response also includes a list of GitHub's domain names.\n\nThe values shown in the documentation's response are example values. You must always query the API directly to get the latest values.\n\n**Note:** This endpoint returns both IPv4 and IPv6 addresses. However, not all features support IPv6. You should refer to the specific documentation for each feature to determine if IPv6 is supported.",
    "tags": [
        "meta"
    ],
    "operationId": "meta/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/meta/meta#get-apiname-meta-information"
    },
    "parameters": [],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/api-overview"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/api-overview"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "meta",
        "subcategory": "meta"
    }
}
```

## References

### `#/components/schemas/api-overview`

```json
{
    "title": "Api Overview",
    "description": "Api Overview",
    "type": "object",
    "properties": {
        "verifiable_password_authentication": {
            "type": "boolean",
            "example": true
        },
        "ssh_key_fingerprints": {
            "type": "object",
            "properties": {
                "SHA256_RSA": {
                    "type": "string"
                },
                "SHA256_DSA": {
                    "type": "string"
                },
                "SHA256_ECDSA": {
                    "type": "string"
                },
                "SHA256_ED25519": {
                    "type": "string"
                }
            }
        },
        "ssh_keys": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "ssh-ed25519 ABCDEFGHIJKLMNOPQRSTUVWXYZ"
            ]
        },
        "hooks": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "github_enterprise_importer": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "web": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "api": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "git": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "packages": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "pages": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "importer": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "actions": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "actions_macos": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "dependabot": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "192.0.2.1"
            ]
        },
        "domains": {
            "type": "object",
            "properties": {
                "website": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": [
                            "example.com"
                        ]
                    }
                },
                "codespaces": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": [
                            "example.com"
                        ]
                    }
                },
                "copilot": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": [
                            "example.com"
                        ]
                    }
                },
                "packages": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": [
                            "example.com"
                        ]
                    }
                },
                "actions": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": [
                            "example.com"
                        ]
                    }
                }
            }
        }
    },
    "required": [
        "verifiable_password_authentication"
    ]
}
```

### `#/components/examples/api-overview`

```json
{
    "value": {
        "verifiable_password_authentication": true,
        "ssh_key_fingerprints": {
            "SHA256_RSA": 1234567890,
            "SHA256_DSA": 1234567890,
            "SHA256_ECDSA": 1234567890,
            "SHA256_ED25519": 1234567890
        },
        "ssh_keys": [
            "ssh-ed25519 ABCDEFGHIJKLMNOPQRSTUVWXYZ",
            "ecdsa-sha2-nistp256 ABCDEFGHIJKLMNOPQRSTUVWXYZ",
            "ssh-rsa ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        ],
        "hooks": [
            "192.0.2.1"
        ],
        "github_enterprise_importer": [
            "192.0.2.1"
        ],
        "web": [
            "192.0.2.1"
        ],
        "api": [
            "192.0.2.1"
        ],
        "git": [
            "192.0.2.1"
        ],
        "packages": [
            "192.0.2.1"
        ],
        "pages": [
            "192.0.2.1"
        ],
        "importer": [
            "192.0.2.1"
        ],
        "actions": [
            "192.0.2.1"
        ],
        "actions_macos": [
            "192.0.2.1"
        ],
        "dependabot": [
            "192.0.2.1"
        ],
        "domains": {
            "website": [
                "*.example.com"
            ],
            "codespaces": [
                "*.example.com"
            ],
            "copilot": [
                "*.example.com"
            ],
            "packages": [
                "*.example.com"
            ]
        }
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```