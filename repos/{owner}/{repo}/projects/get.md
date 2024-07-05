# List repository projects

`get /repos/{owner}/{repo}/projects`

Lists the projects in a repository. Returns a `404 Not Found` status if projects are disabled in the repository. If you do not have sufficient privileges to perform this action, a `401 Unauthorized` or `410 Gone` status is returned.

## Operation Object

```json
{
    "summary": "List repository projects",
    "description": "Lists the projects in a repository. Returns a `404 Not Found` status if projects are disabled in the repository. If you do not have sufficient privileges to perform this action, a `401 Unauthorized` or `410 Gone` status is returned.",
    "tags": [
        "projects"
    ],
    "operationId": "projects/list-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/projects/projects#list-repository-projects"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "state",
            "description": "Indicates the state of the projects to return.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "open",
                    "closed",
                    "all"
                ],
                "default": "open"
            }
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/project"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/project-items-2"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "410": {
            "$ref": "#/components/responses/gone"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed_simple"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "projects",
        "subcategory": "projects"
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

### `#/components/schemas/project`

```json
{
    "title": "Project",
    "description": "Projects are a way to organize columns and cards of work.",
    "type": "object",
    "properties": {
        "owner_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/api-playground/projects-test"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/1002604"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/api-playground/projects-test/projects/12"
        },
        "columns_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/1002604/columns"
        },
        "id": {
            "type": "integer",
            "example": 1002604
        },
        "node_id": {
            "type": "string",
            "example": "MDc6UHJvamVjdDEwMDI2MDQ="
        },
        "name": {
            "description": "Name of the project",
            "example": "Week One Sprint",
            "type": "string"
        },
        "body": {
            "description": "Body of the project",
            "example": "This project represents the sprint of the first week in January",
            "type": "string",
            "nullable": true
        },
        "number": {
            "type": "integer",
            "example": 1
        },
        "state": {
            "description": "State of the project; either 'open' or 'closed'",
            "example": "open",
            "type": "string"
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-10T20:09:31Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2014-03-03T18:58:10Z"
        },
        "organization_permission": {
            "description": "The baseline permission that all organization members have on this project. Only present if owner is an organization.",
            "type": "string",
            "enum": [
                "read",
                "write",
                "admin",
                "none"
            ]
        },
        "private": {
            "description": "Whether or not this project can be seen by everyone. Only present if owner is an organization.",
            "type": "boolean"
        }
    },
    "required": [
        "id",
        "node_id",
        "number",
        "name",
        "body",
        "state",
        "url",
        "html_url",
        "owner_url",
        "creator",
        "columns_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/project-items-2`

```json
{
    "value": [
        {
            "owner_url": "https://api.github.com/repos/api-playground/projects-test",
            "url": "https://api.github.com/projects/1002604",
            "html_url": "https://github.com/api-playground/projects-test/projects/1",
            "columns_url": "https://api.github.com/projects/1002604/columns",
            "id": 1002604,
            "node_id": "MDc6UHJvamVjdDEwMDI2MDQ=",
            "name": "Projects Documentation",
            "body": "Developer documentation project for the developer site.",
            "number": 1,
            "state": "open",
            "creator": {
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
            "created_at": "2011-04-10T20:09:31Z",
            "updated_at": "2014-03-03T18:58:10Z"
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

### `#/components/responses/gone`

```json
{
    "description": "Gone",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/validation_failed_simple`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error-simple"
            }
        }
    }
}
```