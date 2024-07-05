# List app installations for an organization

Lists all GitHub Apps in an organization. The installation count includes
all GitHub Apps installed on repositories in the organization.

The authenticated user must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:read` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List app installations for an organization",
    "description": "Lists all GitHub Apps in an organization. The installation count includes\nall GitHub Apps installed on repositories in the organization.\n\nThe authenticated user must be an organization owner to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:read` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-app-installations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/orgs#list-app-installations-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
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
                            "installations"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "installations": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/installation"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/installation-paginated"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "orgs"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
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

### `#/components/schemas/installation`

```json
{
    "title": "Installation",
    "description": "Installation",
    "type": "object",
    "properties": {
        "id": {
            "description": "The ID of the installation.",
            "type": "integer",
            "example": 1
        },
        "account": {
            "nullable": true,
            "anyOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                },
                {
                    "$ref": "#/components/schemas/enterprise"
                }
            ]
        },
        "repository_selection": {
            "description": "Describe whether all repositories have been selected or there's a selection involved",
            "type": "string",
            "enum": [
                "all",
                "selected"
            ]
        },
        "access_tokens_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/app/installations/1/access_tokens"
        },
        "repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/installation/repositories"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/organizations/github/settings/installations/1"
        },
        "app_id": {
            "type": "integer",
            "example": 1
        },
        "target_id": {
            "description": "The ID of the user or organization this token is being scoped to.",
            "type": "integer"
        },
        "target_type": {
            "type": "string",
            "example": "Organization"
        },
        "permissions": {
            "$ref": "#/components/schemas/app-permissions"
        },
        "events": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "single_file_name": {
            "type": "string",
            "example": "config.yaml",
            "nullable": true
        },
        "has_multiple_single_files": {
            "type": "boolean",
            "example": true
        },
        "single_file_paths": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "config.yml",
                ".github/issue_TEMPLATE.md"
            ]
        },
        "app_slug": {
            "type": "string",
            "example": "github-actions"
        },
        "suspended_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "suspended_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "contact_email": {
            "type": "string",
            "example": "\"test_13f1e99741e3e004@d7e1eb0bc0a1ba12.com\"",
            "nullable": true
        }
    },
    "required": [
        "id",
        "app_id",
        "app_slug",
        "target_id",
        "target_type",
        "single_file_name",
        "repository_selection",
        "access_tokens_url",
        "html_url",
        "repositories_url",
        "events",
        "account",
        "permissions",
        "created_at",
        "updated_at",
        "suspended_by",
        "suspended_at"
    ]
}
```

### `#/components/examples/installation-paginated`

```json
{
    "value": {
        "total_count": 1,
        "installations": [
            {
                "id": 25381,
                "account": {
                    "login": "octo-org",
                    "id": 6811672,
                    "node_id": "MDEyOk9yZ2FuaXphdGlvbjY4MTE2NzI=",
                    "avatar_url": "https://avatars3.githubusercontent.com/u/6811672?v=4",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/octo-org",
                    "html_url": "https://github.com/octo-org",
                    "followers_url": "https://api.github.com/users/octo-org/followers",
                    "following_url": "https://api.github.com/users/octo-org/following{/other_user}",
                    "gists_url": "https://api.github.com/users/octo-org/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/octo-org/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/octo-org/subscriptions",
                    "organizations_url": "https://api.github.com/users/octo-org/orgs",
                    "repos_url": "https://api.github.com/users/octo-org/repos",
                    "events_url": "https://api.github.com/users/octo-org/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/octo-org/received_events",
                    "type": "Organization",
                    "site_admin": false
                },
                "repository_selection": "selected",
                "access_tokens_url": "https://api.github.com/app/installations/25381/access_tokens",
                "repositories_url": "https://api.github.com/installation/repositories",
                "html_url": "https://github.com/organizations/octo-org/settings/installations/25381",
                "app_id": 2218,
                "target_id": 6811672,
                "target_type": "Organization",
                "permissions": {
                    "deployments": "write",
                    "metadata": "read",
                    "pull_requests": "read",
                    "statuses": "read"
                },
                "events": [
                    "deployment",
                    "deployment_status"
                ],
                "created_at": "2017-05-16T08:47:09.000-07:00",
                "updated_at": "2017-06-06T11:23:23.000-07:00",
                "single_file_name": "config.yml",
                "has_multiple_single_files": true,
                "single_file_paths": [
                    "config.yml",
                    ".github/issue_TEMPLATE.md"
                ],
                "app_slug": "github-actions",
                "suspended_at": null,
                "suspended_by": null
            }
        ]
    }
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```