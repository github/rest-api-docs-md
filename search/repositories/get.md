# Search repositories

Find repositories via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for repositories, you can get text match metadata for the **name** and **description** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to search for popular Tetris repositories written in assembly code, your query might look like this:

`q=tetris+language:assembly&sort=stars&order=desc`

This query searches for repositories with the word `tetris` in the name, the description, or the README. The results are limited to repositories where the primary language is assembly. The results are sorted by stars in descending order, so that the most popular repositories appear first in the search results.

## Operation Object

```json
{
    "summary": "Search repositories",
    "description": "Find repositories via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).\n\nWhen searching for repositories, you can get text match metadata for the **name** and **description** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).\n\nFor example, if you want to search for popular Tetris repositories written in assembly code, your query might look like this:\n\n`q=tetris+language:assembly&sort=stars&order=desc`\n\nThis query searches for repositories with the word `tetris` in the name, the description, or the README. The results are limited to repositories where the primary language is assembly. The results are sorted by stars in descending order, so that the most popular repositories appear first in the search results.",
    "tags": [
        "search"
    ],
    "operationId": "search/repos",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/search/search#search-repositories"
    },
    "parameters": [
        {
            "name": "q",
            "description": "The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See \"[Searching for repositories](https://docs.github.com/articles/searching-for-repositories/)\" for a detailed list of qualifiers.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "sort",
            "description": "Sorts the results of your query by number of `stars`, `forks`, or `help-wanted-issues` or how recently the items were `updated`. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "stars",
                    "forks",
                    "help-wanted-issues",
                    "updated"
                ]
            }
        },
        {
            "$ref": "#/components/parameters/order"
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
                            "incomplete_results",
                            "items"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "incomplete_results": {
                                "type": "boolean"
                            },
                            "items": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/repo-search-result-item"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repo-search-result-item-paginated"
                        }
                    }
                }
            }
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "search",
        "subcategory": "search"
    }
}
```

## References

### `#/components/parameters/order`

```json
{
    "name": "order",
    "description": "Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "desc",
            "asc"
        ],
        "default": "desc"
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

### `#/components/schemas/repo-search-result-item`

```json
{
    "title": "Repo Search Result Item",
    "description": "Repo Search Result Item",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "name": {
            "type": "string"
        },
        "full_name": {
            "type": "string"
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "private": {
            "type": "boolean"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "fork": {
            "type": "boolean"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "pushed_at": {
            "type": "string",
            "format": "date-time"
        },
        "homepage": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "size": {
            "type": "integer"
        },
        "stargazers_count": {
            "type": "integer"
        },
        "watchers_count": {
            "type": "integer"
        },
        "language": {
            "type": "string",
            "nullable": true
        },
        "forks_count": {
            "type": "integer"
        },
        "open_issues_count": {
            "type": "integer"
        },
        "master_branch": {
            "type": "string"
        },
        "default_branch": {
            "type": "string"
        },
        "score": {
            "type": "number"
        },
        "forks_url": {
            "type": "string",
            "format": "uri"
        },
        "keys_url": {
            "type": "string"
        },
        "collaborators_url": {
            "type": "string"
        },
        "teams_url": {
            "type": "string",
            "format": "uri"
        },
        "hooks_url": {
            "type": "string",
            "format": "uri"
        },
        "issue_events_url": {
            "type": "string"
        },
        "events_url": {
            "type": "string",
            "format": "uri"
        },
        "assignees_url": {
            "type": "string"
        },
        "branches_url": {
            "type": "string"
        },
        "tags_url": {
            "type": "string",
            "format": "uri"
        },
        "blobs_url": {
            "type": "string"
        },
        "git_tags_url": {
            "type": "string"
        },
        "git_refs_url": {
            "type": "string"
        },
        "trees_url": {
            "type": "string"
        },
        "statuses_url": {
            "type": "string"
        },
        "languages_url": {
            "type": "string",
            "format": "uri"
        },
        "stargazers_url": {
            "type": "string",
            "format": "uri"
        },
        "contributors_url": {
            "type": "string",
            "format": "uri"
        },
        "subscribers_url": {
            "type": "string",
            "format": "uri"
        },
        "subscription_url": {
            "type": "string",
            "format": "uri"
        },
        "commits_url": {
            "type": "string"
        },
        "git_commits_url": {
            "type": "string"
        },
        "comments_url": {
            "type": "string"
        },
        "issue_comment_url": {
            "type": "string"
        },
        "contents_url": {
            "type": "string"
        },
        "compare_url": {
            "type": "string"
        },
        "merges_url": {
            "type": "string",
            "format": "uri"
        },
        "archive_url": {
            "type": "string"
        },
        "downloads_url": {
            "type": "string",
            "format": "uri"
        },
        "issues_url": {
            "type": "string"
        },
        "pulls_url": {
            "type": "string"
        },
        "milestones_url": {
            "type": "string"
        },
        "notifications_url": {
            "type": "string"
        },
        "labels_url": {
            "type": "string"
        },
        "releases_url": {
            "type": "string"
        },
        "deployments_url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string"
        },
        "ssh_url": {
            "type": "string"
        },
        "clone_url": {
            "type": "string"
        },
        "svn_url": {
            "type": "string",
            "format": "uri"
        },
        "forks": {
            "type": "integer"
        },
        "open_issues": {
            "type": "integer"
        },
        "watchers": {
            "type": "integer"
        },
        "topics": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "mirror_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "has_issues": {
            "type": "boolean"
        },
        "has_projects": {
            "type": "boolean"
        },
        "has_pages": {
            "type": "boolean"
        },
        "has_wiki": {
            "type": "boolean"
        },
        "has_downloads": {
            "type": "boolean"
        },
        "has_discussions": {
            "type": "boolean"
        },
        "archived": {
            "type": "boolean"
        },
        "disabled": {
            "type": "boolean",
            "description": "Returns whether or not this repository disabled."
        },
        "visibility": {
            "description": "The repository visibility: public, private, or internal.",
            "type": "string"
        },
        "license": {
            "$ref": "#/components/schemas/nullable-license-simple"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "admin": {
                    "type": "boolean"
                },
                "maintain": {
                    "type": "boolean"
                },
                "push": {
                    "type": "boolean"
                },
                "triage": {
                    "type": "boolean"
                },
                "pull": {
                    "type": "boolean"
                }
            },
            "required": [
                "admin",
                "pull",
                "push"
            ]
        },
        "text_matches": {
            "$ref": "#/components/schemas/search-result-text-matches"
        },
        "temp_clone_token": {
            "type": "string"
        },
        "allow_merge_commit": {
            "type": "boolean"
        },
        "allow_squash_merge": {
            "type": "boolean"
        },
        "allow_rebase_merge": {
            "type": "boolean"
        },
        "allow_auto_merge": {
            "type": "boolean"
        },
        "delete_branch_on_merge": {
            "type": "boolean"
        },
        "allow_forking": {
            "type": "boolean"
        },
        "is_template": {
            "type": "boolean"
        },
        "web_commit_signoff_required": {
            "type": "boolean",
            "example": false
        }
    },
    "required": [
        "archive_url",
        "assignees_url",
        "blobs_url",
        "branches_url",
        "collaborators_url",
        "comments_url",
        "commits_url",
        "compare_url",
        "contents_url",
        "contributors_url",
        "deployments_url",
        "description",
        "downloads_url",
        "events_url",
        "fork",
        "forks_url",
        "full_name",
        "git_commits_url",
        "git_refs_url",
        "git_tags_url",
        "hooks_url",
        "html_url",
        "id",
        "node_id",
        "issue_comment_url",
        "issue_events_url",
        "issues_url",
        "keys_url",
        "labels_url",
        "languages_url",
        "merges_url",
        "milestones_url",
        "name",
        "notifications_url",
        "owner",
        "private",
        "pulls_url",
        "releases_url",
        "stargazers_url",
        "statuses_url",
        "subscribers_url",
        "subscription_url",
        "tags_url",
        "teams_url",
        "trees_url",
        "url",
        "clone_url",
        "default_branch",
        "forks",
        "forks_count",
        "git_url",
        "has_downloads",
        "has_issues",
        "has_projects",
        "has_wiki",
        "has_pages",
        "homepage",
        "language",
        "archived",
        "disabled",
        "mirror_url",
        "open_issues",
        "open_issues_count",
        "license",
        "pushed_at",
        "size",
        "ssh_url",
        "stargazers_count",
        "svn_url",
        "watchers",
        "watchers_count",
        "created_at",
        "updated_at",
        "score"
    ]
}
```

### `#/components/examples/repo-search-result-item-paginated`

```json
{
    "value": {
        "total_count": 40,
        "incomplete_results": false,
        "items": [
            {
                "id": 3081286,
                "node_id": "MDEwOlJlcG9zaXRvcnkzMDgxMjg2",
                "name": "Tetris",
                "full_name": "dtrupenn/Tetris",
                "owner": {
                    "login": "dtrupenn",
                    "id": 872147,
                    "node_id": "MDQ6VXNlcjg3MjE0Nw==",
                    "avatar_url": "https://secure.gravatar.com/avatar/e7956084e75f239de85d3a31bc172ace?d=https://a248.e.akamai.net/assets.github.com%2Fimages%2Fgravatars%2Fgravatar-user-420.png",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/dtrupenn",
                    "received_events_url": "https://api.github.com/users/dtrupenn/received_events",
                    "type": "User",
                    "html_url": "https://github.com/octocat",
                    "followers_url": "https://api.github.com/users/octocat/followers",
                    "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                    "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                    "organizations_url": "https://api.github.com/users/octocat/orgs",
                    "repos_url": "https://api.github.com/users/octocat/repos",
                    "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                    "site_admin": true
                },
                "private": false,
                "html_url": "https://github.com/dtrupenn/Tetris",
                "description": "A C implementation of Tetris using Pennsim through LC4",
                "fork": false,
                "url": "https://api.github.com/repos/dtrupenn/Tetris",
                "created_at": "2012-01-01T00:31:50Z",
                "updated_at": "2013-01-05T17:58:47Z",
                "pushed_at": "2012-01-01T00:37:02Z",
                "homepage": "https://github.com",
                "size": 524,
                "stargazers_count": 1,
                "watchers_count": 1,
                "language": "Assembly",
                "forks_count": 0,
                "open_issues_count": 0,
                "master_branch": "master",
                "default_branch": "master",
                "score": 1,
                "archive_url": "https://api.github.com/repos/dtrupenn/Tetris/{archive_format}{/ref}",
                "assignees_url": "https://api.github.com/repos/dtrupenn/Tetris/assignees{/user}",
                "blobs_url": "https://api.github.com/repos/dtrupenn/Tetris/git/blobs{/sha}",
                "branches_url": "https://api.github.com/repos/dtrupenn/Tetris/branches{/branch}",
                "collaborators_url": "https://api.github.com/repos/dtrupenn/Tetris/collaborators{/collaborator}",
                "comments_url": "https://api.github.com/repos/dtrupenn/Tetris/comments{/number}",
                "commits_url": "https://api.github.com/repos/dtrupenn/Tetris/commits{/sha}",
                "compare_url": "https://api.github.com/repos/dtrupenn/Tetris/compare/{base}...{head}",
                "contents_url": "https://api.github.com/repos/dtrupenn/Tetris/contents/{+path}",
                "contributors_url": "https://api.github.com/repos/dtrupenn/Tetris/contributors",
                "deployments_url": "https://api.github.com/repos/dtrupenn/Tetris/deployments",
                "downloads_url": "https://api.github.com/repos/dtrupenn/Tetris/downloads",
                "events_url": "https://api.github.com/repos/dtrupenn/Tetris/events",
                "forks_url": "https://api.github.com/repos/dtrupenn/Tetris/forks",
                "git_commits_url": "https://api.github.com/repos/dtrupenn/Tetris/git/commits{/sha}",
                "git_refs_url": "https://api.github.com/repos/dtrupenn/Tetris/git/refs{/sha}",
                "git_tags_url": "https://api.github.com/repos/dtrupenn/Tetris/git/tags{/sha}",
                "git_url": "git:github.com/dtrupenn/Tetris.git",
                "issue_comment_url": "https://api.github.com/repos/dtrupenn/Tetris/issues/comments{/number}",
                "issue_events_url": "https://api.github.com/repos/dtrupenn/Tetris/issues/events{/number}",
                "issues_url": "https://api.github.com/repos/dtrupenn/Tetris/issues{/number}",
                "keys_url": "https://api.github.com/repos/dtrupenn/Tetris/keys{/key_id}",
                "labels_url": "https://api.github.com/repos/dtrupenn/Tetris/labels{/name}",
                "languages_url": "https://api.github.com/repos/dtrupenn/Tetris/languages",
                "merges_url": "https://api.github.com/repos/dtrupenn/Tetris/merges",
                "milestones_url": "https://api.github.com/repos/dtrupenn/Tetris/milestones{/number}",
                "notifications_url": "https://api.github.com/repos/dtrupenn/Tetris/notifications{?since,all,participating}",
                "pulls_url": "https://api.github.com/repos/dtrupenn/Tetris/pulls{/number}",
                "releases_url": "https://api.github.com/repos/dtrupenn/Tetris/releases{/id}",
                "ssh_url": "git@github.com:dtrupenn/Tetris.git",
                "stargazers_url": "https://api.github.com/repos/dtrupenn/Tetris/stargazers",
                "statuses_url": "https://api.github.com/repos/dtrupenn/Tetris/statuses/{sha}",
                "subscribers_url": "https://api.github.com/repos/dtrupenn/Tetris/subscribers",
                "subscription_url": "https://api.github.com/repos/dtrupenn/Tetris/subscription",
                "tags_url": "https://api.github.com/repos/dtrupenn/Tetris/tags",
                "teams_url": "https://api.github.com/repos/dtrupenn/Tetris/teams",
                "trees_url": "https://api.github.com/repos/dtrupenn/Tetris/git/trees{/sha}",
                "clone_url": "https://github.com/dtrupenn/Tetris.git",
                "mirror_url": "git:git.example.com/dtrupenn/Tetris",
                "hooks_url": "https://api.github.com/repos/dtrupenn/Tetris/hooks",
                "svn_url": "https://svn.github.com/dtrupenn/Tetris",
                "forks": 1,
                "open_issues": 1,
                "watchers": 1,
                "has_issues": true,
                "has_projects": true,
                "has_pages": true,
                "has_wiki": true,
                "has_downloads": true,
                "archived": true,
                "disabled": true,
                "visibility": "private",
                "license": {
                    "key": "mit",
                    "name": "MIT License",
                    "url": "https://api.github.com/licenses/mit",
                    "spdx_id": "MIT",
                    "node_id": "MDc6TGljZW5zZW1pdA==",
                    "html_url": "https://api.github.com/licenses/mit"
                }
            }
        ]
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```