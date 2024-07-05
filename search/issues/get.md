# Search issues and pull requests

`get /search/issues`

Find issues by state and keyword. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for issues, you can get text match metadata for the issue **title**, issue **body**, and issue **comment body** fields when you pass the `text-match` media type. For more details about how to receive highlighted
search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to find the oldest unresolved Python bugs on Windows. Your query might look something like this.

`q=windows+label:bug+language:python+state:open&sort=created&order=asc`

This query searches for the keyword `windows`, within any open issue that is labeled as `bug`. The search runs across repositories whose primary language is Python. The results are sorted by creation date in ascending order, which means the oldest issues appear first in the search results.

**Note:** For requests made by GitHub Apps with a user access token, you can't retrieve a combination of issues and pull requests in a single query. Requests that don't include the `is:issue` or `is:pull-request` qualifier will receive an HTTP `422 Unprocessable Entity` response. To get results for both issues and pull requests, you must send separate queries for issues and pull requests. For more information about the `is` qualifier, see "[Searching only issues or pull requests](https://docs.github.com/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-only-issues-or-pull-requests)."

## Operation Object

```json
{
    "summary": "Search issues and pull requests",
    "description": "Find issues by state and keyword. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).\n\nWhen searching for issues, you can get text match metadata for the issue **title**, issue **body**, and issue **comment body** fields when you pass the `text-match` media type. For more details about how to receive highlighted\nsearch results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).\n\nFor example, if you want to find the oldest unresolved Python bugs on Windows. Your query might look something like this.\n\n`q=windows+label:bug+language:python+state:open&sort=created&order=asc`\n\nThis query searches for the keyword `windows`, within any open issue that is labeled as `bug`. The search runs across repositories whose primary language is Python. The results are sorted by creation date in ascending order, which means the oldest issues appear first in the search results.\n\n**Note:** For requests made by GitHub Apps with a user access token, you can't retrieve a combination of issues and pull requests in a single query. Requests that don't include the `is:issue` or `is:pull-request` qualifier will receive an HTTP `422 Unprocessable Entity` response. To get results for both issues and pull requests, you must send separate queries for issues and pull requests. For more information about the `is` qualifier, see \"[Searching only issues or pull requests](https://docs.github.com/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-only-issues-or-pull-requests).\"",
    "tags": [
        "search"
    ],
    "operationId": "search/issues-and-pull-requests",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/search/search#search-issues-and-pull-requests"
    },
    "parameters": [
        {
            "name": "q",
            "description": "The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See \"[Searching issues and pull requests](https://docs.github.com/search-github/searching-on-github/searching-issues-and-pull-requests)\" for a detailed list of qualifiers.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "sort",
            "description": "Sorts the results of your query by the number of `comments`, `reactions`, `reactions-+1`, `reactions--1`, `reactions-smile`, `reactions-thinking_face`, `reactions-heart`, `reactions-tada`, or `interactions`. You can also sort results by how recently the items were `created` or `updated`, Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "comments",
                    "reactions",
                    "reactions-+1",
                    "reactions--1",
                    "reactions-smile",
                    "reactions-thinking_face",
                    "reactions-heart",
                    "reactions-tada",
                    "interactions",
                    "created",
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
                                    "$ref": "#/components/schemas/issue-search-result-item"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue-search-result-item-paginated"
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
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
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

### `#/components/schemas/issue-search-result-item`

```json
{
    "title": "Issue Search Result Item",
    "description": "Issue Search Result Item",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "repository_url": {
            "type": "string",
            "format": "uri"
        },
        "labels_url": {
            "type": "string"
        },
        "comments_url": {
            "type": "string",
            "format": "uri"
        },
        "events_url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "id": {
            "type": "integer",
            "format": "int64"
        },
        "node_id": {
            "type": "string"
        },
        "number": {
            "type": "integer"
        },
        "title": {
            "type": "string"
        },
        "locked": {
            "type": "boolean"
        },
        "active_lock_reason": {
            "type": "string",
            "nullable": true
        },
        "assignees": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            },
            "nullable": true
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "labels": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer",
                        "format": "int64"
                    },
                    "node_id": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string"
                    },
                    "name": {
                        "type": "string"
                    },
                    "color": {
                        "type": "string"
                    },
                    "default": {
                        "type": "boolean"
                    },
                    "description": {
                        "type": "string",
                        "nullable": true
                    }
                }
            }
        },
        "state": {
            "type": "string"
        },
        "state_reason": {
            "type": "string",
            "nullable": true
        },
        "assignee": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "milestone": {
            "$ref": "#/components/schemas/nullable-milestone"
        },
        "comments": {
            "type": "integer"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "text_matches": {
            "$ref": "#/components/schemas/search-result-text-matches"
        },
        "pull_request": {
            "type": "object",
            "properties": {
                "merged_at": {
                    "type": "string",
                    "format": "date-time",
                    "nullable": true
                },
                "diff_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "patch_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                }
            },
            "required": [
                "diff_url",
                "html_url",
                "patch_url",
                "url"
            ]
        },
        "body": {
            "type": "string"
        },
        "score": {
            "type": "number"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "draft": {
            "type": "boolean"
        },
        "repository": {
            "$ref": "#/components/schemas/repository"
        },
        "body_html": {
            "type": "string"
        },
        "body_text": {
            "type": "string"
        },
        "timeline_url": {
            "type": "string",
            "format": "uri"
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        }
    },
    "required": [
        "assignee",
        "closed_at",
        "comments",
        "comments_url",
        "events_url",
        "html_url",
        "id",
        "node_id",
        "labels",
        "labels_url",
        "milestone",
        "number",
        "repository_url",
        "state",
        "locked",
        "title",
        "url",
        "user",
        "author_association",
        "created_at",
        "updated_at",
        "score"
    ]
}
```

### `#/components/examples/issue-search-result-item-paginated`

```json
{
    "value": {
        "total_count": 280,
        "incomplete_results": false,
        "items": [
            {
                "url": "https://api.github.com/repos/batterseapower/pinyin-toolkit/issues/132",
                "repository_url": "https://api.github.com/repos/batterseapower/pinyin-toolkit",
                "labels_url": "https://api.github.com/repos/batterseapower/pinyin-toolkit/issues/132/labels{/name}",
                "comments_url": "https://api.github.com/repos/batterseapower/pinyin-toolkit/issues/132/comments",
                "events_url": "https://api.github.com/repos/batterseapower/pinyin-toolkit/issues/132/events",
                "html_url": "https://github.com/batterseapower/pinyin-toolkit/issues/132",
                "id": 35802,
                "node_id": "MDU6SXNzdWUzNTgwMg==",
                "number": 132,
                "title": "Line Number Indexes Beyond 20 Not Displayed",
                "user": {
                    "login": "Nick3C",
                    "id": 90254,
                    "node_id": "MDQ6VXNlcjkwMjU0",
                    "avatar_url": "https://secure.gravatar.com/avatar/934442aadfe3b2f4630510de416c5718?d=https://a248.e.akamai.net/assets.github.com%2Fimages%2Fgravatars%2Fgravatar-user-420.png",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/Nick3C",
                    "html_url": "https://github.com/Nick3C",
                    "followers_url": "https://api.github.com/users/Nick3C/followers",
                    "following_url": "https://api.github.com/users/Nick3C/following{/other_user}",
                    "gists_url": "https://api.github.com/users/Nick3C/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/Nick3C/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/Nick3C/subscriptions",
                    "organizations_url": "https://api.github.com/users/Nick3C/orgs",
                    "repos_url": "https://api.github.com/users/Nick3C/repos",
                    "events_url": "https://api.github.com/users/Nick3C/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/Nick3C/received_events",
                    "type": "User",
                    "site_admin": true
                },
                "labels": [
                    {
                        "id": 4,
                        "node_id": "MDU6TGFiZWw0",
                        "url": "https://api.github.com/repos/batterseapower/pinyin-toolkit/labels/bug",
                        "name": "bug",
                        "color": "ff0000"
                    }
                ],
                "state": "open",
                "assignee": null,
                "milestone": {
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
                },
                "comments": 15,
                "created_at": "2009-07-12T20:10:41Z",
                "updated_at": "2009-07-19T09:23:43Z",
                "closed_at": null,
                "pull_request": {
                    "url": "https://api/github.com/repos/octocat/Hello-World/pull/1347",
                    "html_url": "https://github.com/octocat/Hello-World/pull/1347",
                    "diff_url": "https://github.com/octocat/Hello-World/pull/1347.diff",
                    "patch_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347"
                },
                "body": "...",
                "score": 1,
                "locked": true,
                "author_association": "COLLABORATOR",
                "state_reason": "completed"
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