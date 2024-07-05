# Get a secret scanning alert

Gets a single secret scanning alert detected in an eligible repository.

The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

## Operation Object

```json
{
    "summary": "Get a secret scanning alert",
    "description": "Gets a single secret scanning alert detected in an eligible repository.\n\nThe authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.",
    "tags": [
        "secret-scanning"
    ],
    "operationId": "secret-scanning/get-alert",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/secret-scanning/secret-scanning#get-a-secret-scanning-alert"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/alert-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/secret-scanning-alert"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/secret-scanning-alert-open"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "description": "Repository is public, or secret scanning is disabled for the repository, or the resource is not found"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "secret-scanning",
        "subcategory": "secret-scanning"
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

### `#/components/parameters/alert-number`

```json
{
    "name": "alert_number",
    "in": "path",
    "description": "The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the `number` field in the response from the `GET /repos/{owner}/{repo}/code-scanning/alerts` operation.",
    "required": true,
    "schema": {
        "$ref": "#/components/schemas/alert-number"
    }
}
```

### `#/components/schemas/secret-scanning-alert`

```json
{
    "type": "object",
    "properties": {
        "number": {
            "$ref": "#/components/schemas/alert-number"
        },
        "created_at": {
            "$ref": "#/components/schemas/alert-created-at"
        },
        "updated_at": {
            "$ref": "#/components/schemas/nullable-alert-updated-at"
        },
        "url": {
            "$ref": "#/components/schemas/alert-url"
        },
        "html_url": {
            "$ref": "#/components/schemas/alert-html-url"
        },
        "locations_url": {
            "type": "string",
            "format": "uri",
            "description": "The REST API URL of the code locations for this alert."
        },
        "state": {
            "$ref": "#/components/schemas/secret-scanning-alert-state"
        },
        "resolution": {
            "$ref": "#/components/schemas/secret-scanning-alert-resolution"
        },
        "resolved_at": {
            "type": "string",
            "format": "date-time",
            "description": "The time that the alert was resolved in ISO 8601 format: `YYYY-MM-DDTHH:MM:SSZ`.",
            "nullable": true
        },
        "resolved_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "resolution_comment": {
            "type": "string",
            "description": "An optional comment to resolve an alert.",
            "nullable": true
        },
        "secret_type": {
            "type": "string",
            "description": "The type of secret that secret scanning detected."
        },
        "secret_type_display_name": {
            "type": "string",
            "description": "User-friendly name for the detected secret, matching the `secret_type`.\nFor a list of built-in patterns, see \"[Secret scanning patterns](https://docs.github.com/code-security/secret-scanning/secret-scanning-patterns#supported-secrets-for-advanced-security).\""
        },
        "secret": {
            "type": "string",
            "description": "The secret that was detected."
        },
        "push_protection_bypassed": {
            "type": "boolean",
            "description": "Whether push protection was bypassed for the detected secret.",
            "nullable": true
        },
        "push_protection_bypassed_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "push_protection_bypassed_at": {
            "type": "string",
            "format": "date-time",
            "description": "The time that push protection was bypassed in ISO 8601 format: `YYYY-MM-DDTHH:MM:SSZ`.",
            "nullable": true
        },
        "validity": {
            "type": "string",
            "description": "The token status as of the latest validity check.",
            "enum": [
                "active",
                "inactive",
                "unknown"
            ]
        }
    }
}
```

### `#/components/examples/secret-scanning-alert-open`

```json
{
    "value": {
        "number": 42,
        "created_at": "2020-11-06T18:18:30Z",
        "url": "https://api.github.com/repos/owner/private-repo/secret-scanning/alerts/42",
        "html_url": "https://github.com/owner/private-repo/security/secret-scanning/42",
        "locations_url": "https://api.github.com/repos/owner/private-repo/secret-scanning/alerts/42/locations",
        "state": "open",
        "resolution": null,
        "resolved_at": null,
        "resolved_by": null,
        "secret_type": "mailchimp_api_key",
        "secret_type_display_name": "Mailchimp API Key",
        "secret": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX-us2",
        "push_protection_bypassed_by": null,
        "push_protection_bypassed": false,
        "push_protection_bypassed_at": null,
        "resolution_comment": null,
        "validity": "unknown"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```