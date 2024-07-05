# Get a CodeQL database for a repository

Gets a CodeQL database for a language in a repository.

By default this endpoint returns JSON metadata about the CodeQL database. To
download the CodeQL database binary content, set the `Accept` header of the request
to [`application/zip`](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types), and make sure
your HTTP client is configured to follow redirects or use the `Location` header
to make a second request to get the redirect URL.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get a CodeQL database for a repository",
    "description": "Gets a CodeQL database for a language in a repository.\n\nBy default this endpoint returns JSON metadata about the CodeQL database. To\ndownload the CodeQL database binary content, set the `Accept` header of the request\nto [`application/zip`](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types), and make sure\nyour HTTP client is configured to follow redirects or use the `Location` header\nto make a second request to get the redirect URL.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/get-codeql-database",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-a-codeql-database-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "language",
            "in": "path",
            "description": "The language of the CodeQL database.",
            "schema": {
                "type": "string"
            },
            "required": true
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-codeql-database"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-codeql-database"
                        }
                    }
                }
            }
        },
        "302": {
            "$ref": "#/components/responses/found"
        },
        "403": {
            "$ref": "#/components/responses/code_scanning_forbidden_read"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "code-scanning",
        "subcategory": "code-scanning"
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

### `#/components/schemas/code-scanning-codeql-database`

```json
{
    "title": "CodeQL Database",
    "description": "A CodeQL database.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "description": "The ID of the CodeQL database."
        },
        "name": {
            "type": "string",
            "description": "The name of the CodeQL database."
        },
        "language": {
            "type": "string",
            "description": "The language of the CodeQL database."
        },
        "uploader": {
            "$ref": "#/components/schemas/simple-user"
        },
        "content_type": {
            "type": "string",
            "description": "The MIME type of the CodeQL database file."
        },
        "size": {
            "type": "integer",
            "description": "The size of the CodeQL database file in bytes."
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time at which the CodeQL database was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ."
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time at which the CodeQL database was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ."
        },
        "url": {
            "type": "string",
            "format": "uri",
            "description": "The URL at which to download the CodeQL database. The `Accept` header must be set to the value of the `content_type` property."
        },
        "commit_oid": {
            "type": "string",
            "description": "The commit SHA of the repository at the time the CodeQL database was created.",
            "nullable": true
        }
    },
    "required": [
        "id",
        "name",
        "language",
        "uploader",
        "content_type",
        "size",
        "created_at",
        "updated_at",
        "url"
    ]
}
```

### `#/components/examples/code-scanning-codeql-database`

```json
{
    "value": {
        "id": 1,
        "name": "database.zip",
        "language": "java",
        "uploader": {
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
        "content_type": "application/zip",
        "size": 1024,
        "created_at": "2022-09-12T12:14:32Z",
        "updated_at": "2022-09-12T12:14:32Z",
        "url": "https://api.github.com/repos/octocat/Hello-World/code-scanning/codeql/databases/java",
        "commit_oid": "1927de39fefa25a9d0e64e3f540ff824a72f538c"
    }
}
```

### `#/components/responses/found`

```json
{
    "description": "Found"
}
```

### `#/components/responses/code_scanning_forbidden_read`

```json
{
    "description": "Response if GitHub Advanced Security is not enabled for this repository",
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