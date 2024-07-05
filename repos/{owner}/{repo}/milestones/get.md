# List milestones

Lists milestones for a repository.

## Operation Object

```json
{
    "summary": "List milestones",
    "description": "Lists milestones for a repository.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list-milestones",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/milestones#list-milestones"
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
            "description": "The state of the milestone. Either `open`, `closed`, or `all`.",
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
            "name": "sort",
            "description": "What to sort results by. Either `due_on` or `completeness`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "due_on",
                    "completeness"
                ],
                "default": "due_on"
            }
        },
        {
            "name": "direction",
            "description": "The direction of the sort. Either `asc` or `desc`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "asc",
                    "desc"
                ],
                "default": "asc"
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
                            "$ref": "#/components/schemas/milestone"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/milestone-items"
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
        "category": "issues",
        "subcategory": "milestones"
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

### `#/components/schemas/milestone`

```json
{
    "title": "Milestone",
    "description": "A collection of related issues and pull requests.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/milestones/1"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/milestones/v1.0"
        },
        "labels_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/milestones/1/labels"
        },
        "id": {
            "type": "integer",
            "example": 1002604
        },
        "node_id": {
            "type": "string",
            "example": "MDk6TWlsZXN0b25lMTAwMjYwNA=="
        },
        "number": {
            "description": "The number of the milestone.",
            "type": "integer",
            "example": 42
        },
        "state": {
            "description": "The state of the milestone.",
            "example": "open",
            "type": "string",
            "enum": [
                "open",
                "closed"
            ],
            "default": "open"
        },
        "title": {
            "description": "The title of the milestone.",
            "example": "v1.0",
            "type": "string"
        },
        "description": {
            "type": "string",
            "example": "Tracking milestone for version 1.0",
            "nullable": true
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "open_issues": {
            "type": "integer",
            "example": 4
        },
        "closed_issues": {
            "type": "integer",
            "example": 8
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
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2013-02-12T13:22:01Z",
            "nullable": true
        },
        "due_on": {
            "type": "string",
            "format": "date-time",
            "example": "2012-10-09T23:39:01Z",
            "nullable": true
        }
    },
    "required": [
        "closed_issues",
        "creator",
        "description",
        "due_on",
        "closed_at",
        "id",
        "node_id",
        "labels_url",
        "html_url",
        "number",
        "open_issues",
        "state",
        "title",
        "url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/milestone-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/milestones/1",
            "html_url": "https://github.com/octocat/Hello-World/milestones/v1.0",
            "labels_url": "https://api.github.com/repos/octocat/Hello-World/milestones/1/labels",
            "id": 1002604,
            "node_id": "MDk6TWlsZXN0b25lMTAwMjYwNA==",
            "number": 1,
            "state": "open",
            "title": "v1.0",
            "description": "Tracking milestone for version 1.0",
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
            "open_issues": 4,
            "closed_issues": 8,
            "created_at": "2011-04-10T20:09:31Z",
            "updated_at": "2014-03-03T18:58:10Z",
            "closed_at": "2013-02-12T13:22:01Z",
            "due_on": "2012-10-09T23:39:01Z"
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