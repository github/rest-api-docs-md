# List secret scanning alerts for a repository

Lists secret scanning alerts for an eligible repository, from newest to oldest.

The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

## Operation Object

```json
{
    "summary": "List secret scanning alerts for a repository",
    "description": "Lists secret scanning alerts for an eligible repository, from newest to oldest.\n\nThe authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.",
    "tags": [
        "secret-scanning"
    ],
    "operationId": "secret-scanning/list-alerts-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/secret-scanning/secret-scanning#list-secret-scanning-alerts-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-alert-state"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-alert-secret-type"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-alert-resolution"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-alert-sort"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-pagination-before-org-repo"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-pagination-after-org-repo"
        },
        {
            "$ref": "#/components/parameters/secret-scanning-alert-validity"
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
                            "$ref": "#/components/schemas/secret-scanning-alert"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/secret-scanning-alert-list"
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Repository is public or secret scanning is disabled for the repository"
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

### `#/components/parameters/secret-scanning-alert-state`

```json
{
    "name": "state",
    "in": "query",
    "description": "Set to `open` or `resolved` to only list secret scanning alerts in a specific state.",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "open",
            "resolved"
        ]
    }
}
```

### `#/components/parameters/secret-scanning-alert-secret-type`

```json
{
    "name": "secret_type",
    "in": "query",
    "description": "A comma-separated list of secret types to return. By default all secret types are returned.\nSee \"[Secret scanning patterns](https://docs.github.com/code-security/secret-scanning/secret-scanning-patterns#supported-secrets-for-advanced-security)\"\nfor a complete list of secret types.",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/secret-scanning-alert-resolution`

```json
{
    "name": "resolution",
    "in": "query",
    "description": "A comma-separated list of resolutions. Only secret scanning alerts with one of these resolutions are listed. Valid resolutions are `false_positive`, `wont_fix`, `revoked`, `pattern_edited`, `pattern_deleted` or `used_in_tests`.",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/secret-scanning-alert-sort`

```json
{
    "name": "sort",
    "description": "The property to sort the results by. `created` means when the alert was created. `updated` means when the alert was updated or resolved.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "created",
            "updated"
        ],
        "default": "created"
    }
}
```

### `#/components/parameters/direction`

```json
{
    "name": "direction",
    "description": "The direction to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "asc",
            "desc"
        ],
        "default": "desc"
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
    }
}
```

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/secret-scanning-pagination-before-org-repo`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for events before this cursor. To receive an initial cursor on your first request, include an empty \"before\" query string.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/secret-scanning-pagination-after-org-repo`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for events after this cursor.  To receive an initial cursor on your first request, include an empty \"after\" query string.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/secret-scanning-alert-validity`

```json
{
    "name": "validity",
    "in": "query",
    "description": "A comma-separated list of validities that, when present, will return alerts that match the validities in this list. Valid options are `active`, `inactive`, and `unknown`.",
    "required": false,
    "schema": {
        "type": "string"
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

### `#/components/examples/secret-scanning-alert-list`

```json
{
    "value": [
        {
            "number": 2,
            "created_at": "2020-11-06T18:48:51Z",
            "url": "https://api.github.com/repos/owner/private-repo/secret-scanning/alerts/2",
            "html_url": "https://github.com/owner/private-repo/security/secret-scanning/2",
            "locations_url": "https://api.github.com/repos/owner/private-repo/secret-scanning/alerts/2/locations",
            "state": "resolved",
            "resolution": "false_positive",
            "resolved_at": "2020-11-07T02:47:13Z",
            "resolved_by": {
                "login": "monalisa",
                "id": 2,
                "node_id": "MDQ6VXNlcjI=",
                "avatar_url": "https://alambic.github.com/avatars/u/2?",
                "gravatar_id": "",
                "url": "https://api.github.com/users/monalisa",
                "html_url": "https://github.com/monalisa",
                "followers_url": "https://api.github.com/users/monalisa/followers",
                "following_url": "https://api.github.com/users/monalisa/following{/other_user}",
                "gists_url": "https://api.github.com/users/monalisa/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/monalisa/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/monalisa/subscriptions",
                "organizations_url": "https://api.github.com/users/monalisa/orgs",
                "repos_url": "https://api.github.com/users/monalisa/repos",
                "events_url": "https://api.github.com/users/monalisa/events{/privacy}",
                "received_events_url": "https://api.github.com/users/monalisa/received_events",
                "type": "User",
                "site_admin": true
            },
            "secret_type": "adafruit_io_key",
            "secret_type_display_name": "Adafruit IO Key",
            "secret": "aio_XXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "push_protection_bypassed_by": {
                "login": "monalisa",
                "id": 2,
                "node_id": "MDQ6VXNlcjI=",
                "avatar_url": "https://alambic.github.com/avatars/u/2?",
                "gravatar_id": "",
                "url": "https://api.github.com/users/monalisa",
                "html_url": "https://github.com/monalisa",
                "followers_url": "https://api.github.com/users/monalisa/followers",
                "following_url": "https://api.github.com/users/monalisa/following{/other_user}",
                "gists_url": "https://api.github.com/users/monalisa/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/monalisa/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/monalisa/subscriptions",
                "organizations_url": "https://api.github.com/users/monalisa/orgs",
                "repos_url": "https://api.github.com/users/monalisa/repos",
                "events_url": "https://api.github.com/users/monalisa/events{/privacy}",
                "received_events_url": "https://api.github.com/users/monalisa/received_events",
                "type": "User",
                "site_admin": true
            },
            "push_protection_bypassed": true,
            "push_protection_bypassed_at": "2020-11-06T21:48:51Z",
            "resolution_comment": "Example comment",
            "validity": "inactive"
        },
        {
            "number": 1,
            "created_at": "2020-11-06T18:18:30Z",
            "url": "https://api.github.com/repos/owner/repo/secret-scanning/alerts/1",
            "html_url": "https://github.com/owner/repo/security/secret-scanning/1",
            "locations_url": "https://api.github.com/repos/owner/private-repo/secret-scanning/alerts/1/locations",
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
    ]
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