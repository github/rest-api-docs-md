# Get a codespace for the authenticated user

Gets information about a user's codespace.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a codespace for the authenticated user",
    "description": "Gets information about a user's codespace.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/codespaces#get-a-codespace-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/codespace-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespace"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespace"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "codespaces"
    }
}
```

## References

### `#/components/parameters/codespace-name`

```json
{
    "name": "codespace_name",
    "in": "path",
    "required": true,
    "description": "The name of the codespace.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/codespace`

```json
{
    "type": "object",
    "title": "Codespace",
    "description": "A codespace.",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "name": {
            "description": "Automatically generated name of this codespace.",
            "type": "string",
            "example": "monalisa-octocat-hello-world-g4wpq6h95q"
        },
        "display_name": {
            "description": "Display name for this codespace.",
            "type": "string",
            "example": "bookish space pancake",
            "nullable": true
        },
        "environment_id": {
            "description": "UUID identifying this codespace's environment.",
            "type": "string",
            "example": "26a7c758-7299-4a73-b978-5a92a7ae98a0",
            "nullable": true
        },
        "owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "billable_owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "repository": {
            "$ref": "#/components/schemas/minimal-repository"
        },
        "machine": {
            "$ref": "#/components/schemas/nullable-codespace-machine"
        },
        "devcontainer_path": {
            "description": "Path to devcontainer.json from repo root used to create Codespace.",
            "type": "string",
            "example": ".devcontainer/example/devcontainer.json",
            "nullable": true
        },
        "prebuild": {
            "description": "Whether the codespace was created from a prebuild.",
            "type": "boolean",
            "example": false,
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z"
        },
        "last_used_at": {
            "description": "Last known time this codespace was started.",
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z"
        },
        "state": {
            "description": "State of this codespace.",
            "enum": [
                "Unknown",
                "Created",
                "Queued",
                "Provisioning",
                "Available",
                "Awaiting",
                "Unavailable",
                "Deleted",
                "Moved",
                "Shutdown",
                "Archived",
                "Starting",
                "ShuttingDown",
                "Failed",
                "Exporting",
                "Updating",
                "Rebuilding"
            ],
            "example": "Available",
            "type": "string"
        },
        "url": {
            "description": "API URL for this codespace.",
            "type": "string",
            "format": "uri"
        },
        "git_status": {
            "description": "Details about the codespace's git repository.",
            "type": "object",
            "properties": {
                "ahead": {
                    "description": "The number of commits the local repository is ahead of the remote.",
                    "type": "integer",
                    "example": 0
                },
                "behind": {
                    "description": "The number of commits the local repository is behind the remote.",
                    "type": "integer",
                    "example": 0
                },
                "has_unpushed_changes": {
                    "description": "Whether the local repository has unpushed changes.",
                    "type": "boolean"
                },
                "has_uncommitted_changes": {
                    "description": "Whether the local repository has uncommitted changes.",
                    "type": "boolean"
                },
                "ref": {
                    "description": "The current branch (or SHA if in detached HEAD state) of the local repository.",
                    "type": "string",
                    "example": "main"
                }
            }
        },
        "location": {
            "description": "The initally assigned location of a new codespace.",
            "enum": [
                "EastUs",
                "SouthEastAsia",
                "WestEurope",
                "WestUs2"
            ],
            "example": "WestUs2",
            "type": "string"
        },
        "idle_timeout_minutes": {
            "description": "The number of minutes of inactivity after which this codespace will be automatically stopped.",
            "type": "integer",
            "example": 60,
            "nullable": true
        },
        "web_url": {
            "description": "URL to access this codespace on the web.",
            "type": "string",
            "format": "uri"
        },
        "machines_url": {
            "description": "API URL to access available alternate machine types for this codespace.",
            "type": "string",
            "format": "uri"
        },
        "start_url": {
            "description": "API URL to start this codespace.",
            "type": "string",
            "format": "uri"
        },
        "stop_url": {
            "description": "API URL to stop this codespace.",
            "type": "string",
            "format": "uri"
        },
        "publish_url": {
            "description": "API URL to publish this codespace to a new repository.",
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "pulls_url": {
            "description": "API URL for the Pull Request associated with this codespace, if any.",
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "recent_folders": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "runtime_constraints": {
            "type": "object",
            "properties": {
                "allowed_port_privacy_settings": {
                    "description": "The privacy settings a user can select from when forwarding a port.",
                    "type": "array",
                    "items": {
                        "type": "string"
                    },
                    "nullable": true
                }
            }
        },
        "pending_operation": {
            "description": "Whether or not a codespace has a pending async operation. This would mean that the codespace is temporarily unavailable. The only thing that you can do with a codespace in this state is delete it.",
            "type": "boolean",
            "nullable": true
        },
        "pending_operation_disabled_reason": {
            "description": "Text to show user when codespace is disabled by a pending operation",
            "type": "string",
            "nullable": true
        },
        "idle_timeout_notice": {
            "description": "Text to show user when codespace idle timeout minutes has been overriden by an organization policy",
            "type": "string",
            "nullable": true
        },
        "retention_period_minutes": {
            "description": "Duration in minutes after codespace has gone idle in which it will be deleted. Must be integer minutes between 0 and 43200 (30 days).",
            "type": "integer",
            "example": 60,
            "nullable": true
        },
        "retention_expires_at": {
            "description": "When a codespace will be auto-deleted based on the \"retention_period_minutes\" and \"last_used_at\"",
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T20:01:12Z",
            "nullable": true
        },
        "last_known_stop_notice": {
            "description": "The text to display to a user when a codespace has been stopped for a potentially actionable reason.",
            "type": "string",
            "example": "you've used 100% of your spending limit for Codespaces",
            "nullable": true
        }
    },
    "required": [
        "id",
        "name",
        "environment_id",
        "owner",
        "billable_owner",
        "repository",
        "machine",
        "prebuild",
        "created_at",
        "updated_at",
        "last_used_at",
        "state",
        "url",
        "git_status",
        "location",
        "idle_timeout_minutes",
        "web_url",
        "machines_url",
        "start_url",
        "stop_url",
        "pulls_url",
        "recent_folders"
    ]
}
```

### `#/components/examples/codespace`

```json
{
    "value": {
        "id": 1,
        "name": "monalisa-octocat-hello-world-g4wpq6h95q",
        "environment_id": "26a7c758-7299-4a73-b978-5a92a7ae98a0",
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
        "billable_owner": {
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
        "repository": {
            "id": 1296269,
            "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
            "name": "Hello-World",
            "full_name": "octocat/Hello-World",
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
            "private": false,
            "html_url": "https://github.com/octocat/Hello-World",
            "description": "This your first repo!",
            "fork": false,
            "url": "https://api.github.com/repos/octocat/Hello-World",
            "archive_url": "https://api.github.com/repos/octocat/Hello-World/{archive_format}{/ref}",
            "assignees_url": "https://api.github.com/repos/octocat/Hello-World/assignees{/user}",
            "blobs_url": "https://api.github.com/repos/octocat/Hello-World/git/blobs{/sha}",
            "branches_url": "https://api.github.com/repos/octocat/Hello-World/branches{/branch}",
            "collaborators_url": "https://api.github.com/repos/octocat/Hello-World/collaborators{/collaborator}",
            "comments_url": "https://api.github.com/repos/octocat/Hello-World/comments{/number}",
            "commits_url": "https://api.github.com/repos/octocat/Hello-World/commits{/sha}",
            "compare_url": "https://api.github.com/repos/octocat/Hello-World/compare/{base}...{head}",
            "contents_url": "https://api.github.com/repos/octocat/Hello-World/contents/{+path}",
            "contributors_url": "https://api.github.com/repos/octocat/Hello-World/contributors",
            "deployments_url": "https://api.github.com/repos/octocat/Hello-World/deployments",
            "downloads_url": "https://api.github.com/repos/octocat/Hello-World/downloads",
            "events_url": "https://api.github.com/repos/octocat/Hello-World/events",
            "forks_url": "https://api.github.com/repos/octocat/Hello-World/forks",
            "git_commits_url": "https://api.github.com/repos/octocat/Hello-World/git/commits{/sha}",
            "git_refs_url": "https://api.github.com/repos/octocat/Hello-World/git/refs{/sha}",
            "git_tags_url": "https://api.github.com/repos/octocat/Hello-World/git/tags{/sha}",
            "git_url": "git:github.com/octocat/Hello-World.git",
            "issue_comment_url": "https://api.github.com/repos/octocat/Hello-World/issues/comments{/number}",
            "issue_events_url": "https://api.github.com/repos/octocat/Hello-World/issues/events{/number}",
            "issues_url": "https://api.github.com/repos/octocat/Hello-World/issues{/number}",
            "keys_url": "https://api.github.com/repos/octocat/Hello-World/keys{/key_id}",
            "labels_url": "https://api.github.com/repos/octocat/Hello-World/labels{/name}",
            "languages_url": "https://api.github.com/repos/octocat/Hello-World/languages",
            "merges_url": "https://api.github.com/repos/octocat/Hello-World/merges",
            "milestones_url": "https://api.github.com/repos/octocat/Hello-World/milestones{/number}",
            "notifications_url": "https://api.github.com/repos/octocat/Hello-World/notifications{?since,all,participating}",
            "pulls_url": "https://api.github.com/repos/octocat/Hello-World/pulls{/number}",
            "releases_url": "https://api.github.com/repos/octocat/Hello-World/releases{/id}",
            "ssh_url": "git@github.com:octocat/Hello-World.git",
            "stargazers_url": "https://api.github.com/repos/octocat/Hello-World/stargazers",
            "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/{sha}",
            "subscribers_url": "https://api.github.com/repos/octocat/Hello-World/subscribers",
            "subscription_url": "https://api.github.com/repos/octocat/Hello-World/subscription",
            "tags_url": "https://api.github.com/repos/octocat/Hello-World/tags",
            "teams_url": "https://api.github.com/repos/octocat/Hello-World/teams",
            "trees_url": "https://api.github.com/repos/octocat/Hello-World/git/trees{/sha}",
            "hooks_url": "http://api.github.com/repos/octocat/Hello-World/hooks"
        },
        "machine": {
            "name": "standardLinux",
            "display_name": "4 cores, 16 GB RAM, 64 GB storage",
            "operating_system": "linux",
            "storage_in_bytes": 68719476736,
            "memory_in_bytes": 17179869184,
            "cpus": 4
        },
        "prebuild": false,
        "devcontainer_path": ".devcontainer/devcontainer.json",
        "created_at": "2021-10-14T00:53:30-06:00",
        "updated_at": "2021-10-14T00:53:32-06:00",
        "last_used_at": "2021-10-14T00:53:30-06:00",
        "state": "Available",
        "url": "https://api.github.com/user/codespaces/monalisa-octocat-hello-world-g4wpq6h95q",
        "git_status": {
            "ahead": 0,
            "behind": 0,
            "has_unpushed_changes": false,
            "has_uncommitted_changes": false,
            "ref": "main"
        },
        "location": "WestUs2",
        "idle_timeout_minutes": 60,
        "retention_period_minutes": 43200,
        "retention_expires_at": null,
        "web_url": "https://monalisa-octocat-hello-world-g4wpq6h95q.github.dev",
        "machines_url": "https://api.github.com/user/codespaces/monalisa-octocat-hello-world-g4wpq6h95q/machines",
        "start_url": "https://api.github.com/user/codespaces/monalisa-octocat-hello-world-g4wpq6h95q/start",
        "stop_url": "https://api.github.com/user/codespaces/monalisa-octocat-hello-world-g4wpq6h95q/stop",
        "pulls_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1",
        "recent_folders": [],
        "template": null
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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