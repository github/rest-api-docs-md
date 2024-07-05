# List user migrations

`get /user/migrations`

Lists all migrations a user has started.

## Operation Object

```json
{
    "summary": "List user migrations",
    "description": "Lists all migrations a user has started.",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/list-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/users#list-user-migrations"
    },
    "parameters": [
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
                            "$ref": "#/components/schemas/migration"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/migration-items"
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
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "migrations",
        "subcategory": "users"
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

### `#/components/schemas/migration`

```json
{
    "title": "Migration",
    "description": "A migration.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 79
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "guid": {
            "type": "string",
            "example": "0b989ba4-242f-11e5-81e1-c7b6966d2516"
        },
        "state": {
            "type": "string",
            "example": "pending"
        },
        "lock_repositories": {
            "type": "boolean",
            "example": true
        },
        "exclude_metadata": {
            "type": "boolean"
        },
        "exclude_git_data": {
            "type": "boolean"
        },
        "exclude_attachments": {
            "type": "boolean"
        },
        "exclude_releases": {
            "type": "boolean"
        },
        "exclude_owner_projects": {
            "type": "boolean"
        },
        "org_metadata_only": {
            "type": "boolean"
        },
        "repositories": {
            "type": "array",
            "description": "The repositories included in the migration. Only returned for export migrations.",
            "items": {
                "$ref": "#/components/schemas/repository"
            }
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octo-org/migrations/79"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2015-07-06T15:33:38-07:00"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2015-07-06T15:33:38-07:00"
        },
        "node_id": {
            "type": "string"
        },
        "archive_url": {
            "type": "string",
            "format": "uri"
        },
        "exclude": {
            "description": "Exclude related items from being returned in the response in order to improve performance of the request. The array can include any of: `\"repositories\"`.",
            "type": "array",
            "items": {
                "description": "Allowed values that can be passed to the exclude parameter. The array can include any of: `\"repositories\"`.",
                "type": "string"
            }
        }
    },
    "required": [
        "id",
        "node_id",
        "owner",
        "guid",
        "state",
        "lock_repositories",
        "exclude_metadata",
        "exclude_git_data",
        "exclude_attachments",
        "exclude_releases",
        "exclude_owner_projects",
        "org_metadata_only",
        "repositories",
        "url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/migration-items`

```json
{
    "value": [
        {
            "id": 79,
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
            "guid": "0b989ba4-242f-11e5-81e1-c7b6966d2516",
            "state": "pending",
            "lock_repositories": true,
            "exclude_attachments": false,
            "exclude_releases": false,
            "exclude_owner_projects": false,
            "repositories": [
                {
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
                    "clone_url": "https://github.com/octocat/Hello-World.git",
                    "mirror_url": "git:git.example.com/octocat/Hello-World",
                    "hooks_url": "https://api.github.com/repos/octocat/Hello-World/hooks",
                    "svn_url": "https://svn.github.com/octocat/Hello-World",
                    "homepage": "https://github.com",
                    "language": null,
                    "forks_count": 9,
                    "stargazers_count": 80,
                    "watchers_count": 80,
                    "size": 108,
                    "default_branch": "master",
                    "open_issues_count": 0,
                    "is_template": true,
                    "topics": [
                        "octocat",
                        "atom",
                        "electron",
                        "api"
                    ],
                    "has_issues": true,
                    "has_projects": true,
                    "has_wiki": true,
                    "has_pages": false,
                    "has_downloads": true,
                    "archived": false,
                    "disabled": false,
                    "visibility": "public",
                    "pushed_at": "2011-01-26T19:06:43Z",
                    "created_at": "2011-01-26T19:01:12Z",
                    "updated_at": "2011-01-26T19:14:43Z",
                    "permissions": {
                        "admin": false,
                        "push": false,
                        "pull": true
                    },
                    "allow_rebase_merge": true,
                    "template_repository": null,
                    "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                    "allow_squash_merge": true,
                    "allow_auto_merge": false,
                    "delete_branch_on_merge": true,
                    "allow_merge_commit": true,
                    "subscribers_count": 42,
                    "network_count": 0,
                    "license": {
                        "key": "mit",
                        "name": "MIT License",
                        "url": "https://api.github.com/licenses/mit",
                        "spdx_id": "MIT",
                        "node_id": "MDc6TGljZW5zZW1pdA==",
                        "html_url": "https://api.github.com/licenses/mit"
                    },
                    "forks": 1,
                    "open_issues": 1,
                    "watchers": 1
                }
            ],
            "url": "https://api.github.com/orgs/octo-org/migrations/79",
            "created_at": "2015-07-06T15:33:38-07:00",
            "updated_at": "2015-07-06T15:33:38-07:00",
            "node_id": "MDQ6VXNlcjE="
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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