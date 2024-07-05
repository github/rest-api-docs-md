# List events received by the authenticated user

`get /users/{username}/received_events`

These are events that you've received by watching repositories and following users. If you are authenticated as the given user, you will see private events. Otherwise, you'll only see public events.

## Operation Object

```json
{
    "summary": "List events received by the authenticated user",
    "description": "These are events that you've received by watching repositories and following users. If you are authenticated as the given user, you will see private events. Otherwise, you'll only see public events.",
    "tags": [
        "activity"
    ],
    "operationId": "activity/list-received-events-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/activity/events#list-events-received-by-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
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
                            "$ref": "#/components/schemas/event"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/user-received-events-items"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "activity",
        "subcategory": "events"
    }
}
```

## References

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
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

### `#/components/schemas/event`

```json
{
    "title": "Event",
    "description": "Event",
    "type": "object",
    "properties": {
        "id": {
            "type": "string"
        },
        "type": {
            "type": "string",
            "nullable": true
        },
        "actor": {
            "$ref": "#/components/schemas/actor"
        },
        "repo": {
            "type": "object",
            "properties": {
                "id": {
                    "type": "integer"
                },
                "name": {
                    "type": "string"
                },
                "url": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "id",
                "name",
                "url"
            ]
        },
        "org": {
            "$ref": "#/components/schemas/actor"
        },
        "payload": {
            "type": "object",
            "properties": {
                "action": {
                    "type": "string"
                },
                "issue": {
                    "$ref": "#/components/schemas/issue"
                },
                "comment": {
                    "$ref": "#/components/schemas/issue-comment"
                },
                "pages": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "page_name": {
                                "type": "string"
                            },
                            "title": {
                                "type": "string"
                            },
                            "summary": {
                                "type": "string",
                                "nullable": true
                            },
                            "action": {
                                "type": "string"
                            },
                            "sha": {
                                "type": "string"
                            },
                            "html_url": {
                                "type": "string"
                            }
                        }
                    }
                }
            }
        },
        "public": {
            "type": "boolean"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        }
    },
    "required": [
        "id",
        "type",
        "actor",
        "repo",
        "payload",
        "public",
        "created_at"
    ]
}
```

### `#/components/examples/user-received-events-items`

```json
{
    "value": [
        {
            "id": "22249084964",
            "type": "PushEvent",
            "actor": {
                "id": 583231,
                "login": "octocat",
                "display_login": "octocat",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "avatar_url": "https://avatars.githubusercontent.com/u/583231?v=4"
            },
            "repo": {
                "id": 1296269,
                "name": "octocat/Hello-World",
                "url": "https://api.github.com/repos/octocat/Hello-World"
            },
            "payload": {
                "push_id": 10115855396,
                "size": 1,
                "distinct_size": 1,
                "ref": "refs/heads/master",
                "head": "7a8f3ac80e2ad2f6842cb86f576d4bfe2c03e300",
                "before": "883efe034920928c47fe18598c01249d1a9fdabd",
                "commits": [
                    {
                        "sha": "7a8f3ac80e2ad2f6842cb86f576d4bfe2c03e300",
                        "author": {
                            "email": "octocat@github.com",
                            "name": "Monalisa Octocat"
                        },
                        "message": "commit",
                        "distinct": true,
                        "url": "https://api.github.com/repos/octocat/Hello-World/commits/7a8f3ac80e2ad2f6842cb86f576d4bfe2c03e300"
                    }
                ]
            },
            "public": true,
            "created_at": "2022-06-09T12:47:28Z"
        },
        {
            "id": "22196946742",
            "type": "CreateEvent",
            "actor": {
                "id": 583231,
                "login": "octocat",
                "display_login": "octocat",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "avatar_url": "https://avatars.githubusercontent.com/u/583231?v=4"
            },
            "repo": {
                "id": 1296269,
                "name": "octocat/Hello-World",
                "url": "https://api.github.com/repos/octocat/Hello-World"
            },
            "payload": {
                "ref": null,
                "ref_type": "repository",
                "master_branch": "master",
                "description": null,
                "pusher_type": "user"
            },
            "public": false,
            "created_at": "2022-06-07T07:50:26Z",
            "org": {
                "id": 9919,
                "login": "github",
                "gravatar_id": "",
                "url": "https://api.github.com/orgs/github",
                "avatar_url": "https://avatars.githubusercontent.com/u/9919?"
            }
        }
    ]
}
```