# List fine-grained personal access tokens with access to organization resources

`get /orgs/{org}/personal-access-tokens`

Lists approved fine-grained personal access tokens owned by organization members that can access organization resources.

Only GitHub Apps can use this endpoint.

## Operation Object

```json
{
    "summary": "List fine-grained personal access tokens with access to organization resources",
    "description": "Lists approved fine-grained personal access tokens owned by organization members that can access organization resources.\n\nOnly GitHub Apps can use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-pat-grants",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/personal-access-tokens#list-fine-grained-personal-access-tokens-with-access-to-organization-resources"
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
        },
        {
            "$ref": "#/components/parameters/personal-access-token-sort"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "$ref": "#/components/parameters/personal-access-token-owner"
        },
        {
            "$ref": "#/components/parameters/personal-access-token-repository"
        },
        {
            "$ref": "#/components/parameters/personal-access-token-permission"
        },
        {
            "$ref": "#/components/parameters/personal-access-token-before"
        },
        {
            "$ref": "#/components/parameters/personal-access-token-after"
        }
    ],
    "responses": {
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/organization-programmatic-access-grant"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-pat-grant-paginated"
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
        "subcategory": "personal-access-tokens"
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

### `#/components/parameters/personal-access-token-sort`

```json
{
    "name": "sort",
    "description": "The property by which to sort the results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "created_at"
        ],
        "default": "created_at"
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

### `#/components/parameters/personal-access-token-owner`

```json
{
    "name": "owner",
    "description": "A list of owner usernames to use to filter the results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "array",
        "maxItems": 10,
        "items": {
            "type": "string"
        },
        "example": "owner[]=octocat1,owner[]=octocat2"
    }
}
```

### `#/components/parameters/personal-access-token-repository`

```json
{
    "name": "repository",
    "description": "The name of the repository to use to filter the results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "example": "Hello-World"
    }
}
```

### `#/components/parameters/personal-access-token-permission`

```json
{
    "name": "permission",
    "description": "The permission to use to filter the results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "example": "issues_read"
    }
}
```

### `#/components/parameters/personal-access-token-before`

```json
{
    "name": "last_used_before",
    "description": "Only show fine-grained personal access tokens used before the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "format": "date-time"
    }
}
```

### `#/components/parameters/personal-access-token-after`

```json
{
    "name": "last_used_after",
    "description": "Only show fine-grained personal access tokens used after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "format": "date-time"
    }
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

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
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

### `#/components/schemas/organization-programmatic-access-grant`

```json
{
    "title": "Organization Programmatic Access Grant",
    "description": "Minimal representation of an organization programmatic access grant for enumerations",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "description": "Unique identifier of the fine-grained personal access token. The `pat_id` used to get details about an approved fine-grained personal access token."
        },
        "owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "repository_selection": {
            "type": "string",
            "enum": [
                "none",
                "all",
                "subset"
            ],
            "description": "Type of repository selection requested."
        },
        "repositories_url": {
            "type": "string",
            "description": "URL to the list of repositories the fine-grained personal access token can access. Only follow when `repository_selection` is `subset`."
        },
        "permissions": {
            "type": "object",
            "description": "Permissions requested, categorized by type of permission.",
            "properties": {
                "organization": {
                    "type": "object",
                    "additionalProperties": {
                        "type": "string"
                    }
                },
                "repository": {
                    "type": "object",
                    "additionalProperties": {
                        "type": "string"
                    }
                },
                "other": {
                    "type": "object",
                    "additionalProperties": {
                        "type": "string"
                    }
                }
            }
        },
        "access_granted_at": {
            "type": "string",
            "description": "Date and time when the fine-grained personal access token was approved to access the organization."
        },
        "token_expired": {
            "type": "boolean",
            "description": "Whether the associated fine-grained personal access token has expired."
        },
        "token_expires_at": {
            "type": "string",
            "nullable": true,
            "description": "Date and time when the associated fine-grained personal access token expires."
        },
        "token_last_used_at": {
            "type": "string",
            "nullable": true,
            "description": "Date and time when the associated fine-grained personal access token was last used for authentication."
        }
    },
    "required": [
        "id",
        "owner",
        "repository_selection",
        "repositories_url",
        "permissions",
        "access_granted_at",
        "token_expired",
        "token_expires_at",
        "token_last_used_at"
    ]
}
```

### `#/components/examples/org-pat-grant-paginated`

```json
{
    "value": [
        {
            "id": 25381,
            "owner": {
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
            "repository_selection": "all",
            "repositories_url": "https://api.github.com/organizations/652551/personal-access-tokens/25381/repositories",
            "permissions": {
                "organization": {
                    "members": "read"
                },
                "repository": {
                    "metadata": "read"
                }
            },
            "access_granted_at": "2023-05-16T08:47:09.000-07:00",
            "token_expired": false,
            "token_expires_at": "2023-11-16T08:47:09.000-07:00",
            "token_last_used_at": null
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