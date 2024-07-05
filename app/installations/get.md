# List installations for the authenticated app

`get /app/installations`

The permissions the installation has are included under the `permissions` key.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

## Operation Object

```json
{
    "summary": "List installations for the authenticated app",
    "description": "The permissions the installation has are included under the `permissions` key.\n\nYou must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-installations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/apps#list-installations-for-the-authenticated-app"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/since"
        },
        {
            "name": "outdated",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "The permissions the installation has are included under the `permissions` key.",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/installation"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/base-installation-items"
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
        "category": "apps",
        "subcategory": "apps"
    }
}
```

## References

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

### `#/components/parameters/since`

```json
{
    "name": "since",
    "description": "Only show results that were last updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "format": "date-time"
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

### `#/components/examples/base-installation-items`

```json
{
    "value": [
        {
            "id": 1,
            "account": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            },
            "access_tokens_url": "https://api.github.com/app/installations/1/access_tokens",
            "repositories_url": "https://api.github.com/installation/repositories",
            "html_url": "https://github.com/organizations/github/settings/installations/1",
            "app_id": 1,
            "target_id": 1,
            "target_type": "Organization",
            "permissions": {
                "checks": "write",
                "metadata": "read",
                "contents": "read"
            },
            "events": [
                "push",
                "pull_request"
            ],
            "single_file_name": "config.yaml",
            "has_multiple_single_files": true,
            "single_file_paths": [
                "config.yml",
                ".github/issue_TEMPLATE.md"
            ],
            "repository_selection": "selected",
            "created_at": "2017-07-08T16:18:44-04:00",
            "updated_at": "2017-07-08T16:18:44-04:00",
            "app_slug": "github-actions",
            "suspended_at": null,
            "suspended_by": null
        }
    ]
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