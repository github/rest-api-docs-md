# List repository collaborators

`get /repos/{owner}/{repo}/collaborators`

For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.
Organization members with write, maintain, or admin privileges on the organization-owned repository can use this endpoint.

Team members will include the members of child teams.

The authenticated user must have push access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "List repository collaborators",
    "description": "For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.\nOrganization members with write, maintain, or admin privileges on the organization-owned repository can use this endpoint.\n\nTeam members will include the members of child teams.\n\nThe authenticated user must have push access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-collaborators",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/collaborators/collaborators#list-repository-collaborators"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "affiliation",
            "description": "Filter collaborators returned by their affiliation. `outside` means all outside collaborators of an organization-owned repository. `direct` means all collaborators with permissions to an organization-owned repository, regardless of organization membership status. `all` means all collaborators the authenticated user can see.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "outside",
                    "direct",
                    "all"
                ],
                "default": "all"
            }
        },
        {
            "name": "permission",
            "description": "Filter collaborators by the permissions they have on the repository. If not specified, all collaborators will be returned.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "pull",
                    "triage",
                    "push",
                    "maintain",
                    "admin"
                ]
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
                            "$ref": "#/components/schemas/collaborator"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/collaborator-items"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "collaborators",
        "subcategory": "collaborators"
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

### `#/components/schemas/collaborator`

```json
{
    "title": "Collaborator",
    "description": "Collaborator",
    "type": "object",
    "properties": {
        "login": {
            "type": "string",
            "example": "octocat"
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "email": {
            "nullable": true,
            "type": "string"
        },
        "name": {
            "nullable": true,
            "type": "string"
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6VXNlcjE="
        },
        "avatar_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "gravatar_id": {
            "type": "string",
            "example": "41d064eb2195891e12d0413f63227ea7",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat"
        },
        "followers_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/followers"
        },
        "following_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/following{/other_user}"
        },
        "gists_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/gists{/gist_id}"
        },
        "starred_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/starred{/owner}{/repo}"
        },
        "subscriptions_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/subscriptions"
        },
        "organizations_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/orgs"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/repos"
        },
        "events_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/events{/privacy}"
        },
        "received_events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/received_events"
        },
        "type": {
            "type": "string",
            "example": "User"
        },
        "site_admin": {
            "type": "boolean"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "pull": {
                    "type": "boolean"
                },
                "triage": {
                    "type": "boolean"
                },
                "push": {
                    "type": "boolean"
                },
                "maintain": {
                    "type": "boolean"
                },
                "admin": {
                    "type": "boolean"
                }
            },
            "required": [
                "pull",
                "push",
                "admin"
            ]
        },
        "role_name": {
            "type": "string",
            "example": "admin"
        }
    },
    "required": [
        "avatar_url",
        "events_url",
        "followers_url",
        "following_url",
        "gists_url",
        "gravatar_id",
        "html_url",
        "id",
        "node_id",
        "login",
        "organizations_url",
        "received_events_url",
        "repos_url",
        "site_admin",
        "starred_url",
        "subscriptions_url",
        "type",
        "url",
        "role_name"
    ]
}
```

### `#/components/examples/collaborator-items`

```json
{
    "value": [
        {
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
            "site_admin": false,
            "permissions": {
                "pull": true,
                "triage": true,
                "push": true,
                "maintain": false,
                "admin": false
            },
            "role_name": "write"
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