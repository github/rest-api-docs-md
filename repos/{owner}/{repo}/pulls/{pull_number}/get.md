# Get a pull request

Draft pull requests are available in public repositories with GitHub Free and GitHub Free for organizations, GitHub Pro, and legacy per-repository billing plans, and in public and private repositories with GitHub Team and GitHub Enterprise Cloud. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

Lists details of a pull request by providing its number.

When you get, [create](https://docs.github.com/rest/pulls/pulls/#create-a-pull-request), or [edit](https://docs.github.com/rest/pulls/pulls#update-a-pull-request) a pull request, GitHub creates a merge commit to test whether the pull request can be automatically merged into the base branch. This test commit is not added to the base branch or the head branch. You can review the status of the test commit using the `mergeable` key. For more information, see "[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)".

The value of the `mergeable` attribute can be `true`, `false`, or `null`. If the value is `null`, then GitHub has started a background job to compute the mergeability. After giving the job time to complete, resubmit the request. When the job finishes, you will see a non-`null` value for the `mergeable` attribute in the response. If `mergeable` is `true`, then `merge_commit_sha` will be the SHA of the _test_ merge commit.

The value of the `merge_commit_sha` attribute changes depending on the state of the pull request. Before merging a pull request, the `merge_commit_sha` attribute holds the SHA of the _test_ merge commit. After merging a pull request, the `merge_commit_sha` attribute changes depending on how you merged the pull request:

*   If merged as a [merge commit](https://docs.github.com/articles/about-merge-methods-on-github/), `merge_commit_sha` represents the SHA of the merge commit.
*   If merged via a [squash](https://docs.github.com/articles/about-merge-methods-on-github/#squashing-your-merge-commits), `merge_commit_sha` represents the SHA of the squashed commit on the base branch.
*   If [rebased](https://docs.github.com/articles/about-merge-methods-on-github/#rebasing-and-merging-your-commits), `merge_commit_sha` represents the commit that the base branch was updated to.

Pass the appropriate [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types) to fetch diff and patch formats.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.
- **`application/vnd.github.diff`**: For more information, see "[git-diff](https://git-scm.com/docs/git-diff)" in the Git documentation. If a diff is corrupt, contact us through the [GitHub Support portal](https://support.github.com/). Include the repository name and pull request ID in your message.

## Operation Object

```json
{
    "summary": "Get a pull request",
    "description": "Draft pull requests are available in public repositories with GitHub Free and GitHub Free for organizations, GitHub Pro, and legacy per-repository billing plans, and in public and private repositories with GitHub Team and GitHub Enterprise Cloud. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.\n\nLists details of a pull request by providing its number.\n\nWhen you get, [create](https://docs.github.com/rest/pulls/pulls/#create-a-pull-request), or [edit](https://docs.github.com/rest/pulls/pulls#update-a-pull-request) a pull request, GitHub creates a merge commit to test whether the pull request can be automatically merged into the base branch. This test commit is not added to the base branch or the head branch. You can review the status of the test commit using the `mergeable` key. For more information, see \"[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)\".\n\nThe value of the `mergeable` attribute can be `true`, `false`, or `null`. If the value is `null`, then GitHub has started a background job to compute the mergeability. After giving the job time to complete, resubmit the request. When the job finishes, you will see a non-`null` value for the `mergeable` attribute in the response. If `mergeable` is `true`, then `merge_commit_sha` will be the SHA of the _test_ merge commit.\n\nThe value of the `merge_commit_sha` attribute changes depending on the state of the pull request. Before merging a pull request, the `merge_commit_sha` attribute holds the SHA of the _test_ merge commit. After merging a pull request, the `merge_commit_sha` attribute changes depending on how you merged the pull request:\n\n*   If merged as a [merge commit](https://docs.github.com/articles/about-merge-methods-on-github/), `merge_commit_sha` represents the SHA of the merge commit.\n*   If merged via a [squash](https://docs.github.com/articles/about-merge-methods-on-github/#squashing-your-merge-commits), `merge_commit_sha` represents the SHA of the squashed commit on the base branch.\n*   If [rebased](https://docs.github.com/articles/about-merge-methods-on-github/#rebasing-and-merging-your-commits), `merge_commit_sha` represents the commit that the base branch was updated to.\n\nPass the appropriate [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types) to fetch diff and patch formats.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.\n- **`application/vnd.github.diff`**: For more information, see \"[git-diff](https://git-scm.com/docs/git-diff)\" in the Git documentation. If a diff is corrupt, contact us through the [GitHub Support portal](https://support.github.com/). Include the repository name and pull request ID in your message.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/pulls#get-a-pull-request"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/pull-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Pass the appropriate [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types) to fetch diff and patch formats.",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/pull-request"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pull-request"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "406": {
            "$ref": "#/components/responses/unacceptable"
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "pulls"
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

### `#/components/parameters/pull-number`

```json
{
    "name": "pull_number",
    "description": "The number that identifies the pull request.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/pull-request`

```json
{
    "type": "object",
    "title": "Pull Request",
    "description": "Pull requests let you tell others about changes you've pushed to a repository on GitHub. Once a pull request is sent, interested parties can review the set of changes, discuss potential modifications, and even push follow-up commits if necessary.",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347"
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDExOlB1bGxSZXF1ZXN0MQ=="
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347"
        },
        "diff_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347.diff"
        },
        "patch_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347.patch"
        },
        "issue_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
        },
        "commits_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits"
        },
        "review_comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments"
        },
        "review_comment_url": {
            "type": "string",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}"
        },
        "comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments"
        },
        "statuses_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "number": {
            "description": "Number uniquely identifying the pull request within its repository.",
            "example": 42,
            "type": "integer"
        },
        "state": {
            "description": "State of this Pull Request. Either `open` or `closed`.",
            "enum": [
                "open",
                "closed"
            ],
            "example": "open",
            "type": "string"
        },
        "locked": {
            "type": "boolean",
            "example": true
        },
        "title": {
            "description": "The title of the pull request.",
            "example": "Amazing new feature",
            "type": "string"
        },
        "user": {
            "$ref": "#/components/schemas/simple-user"
        },
        "body": {
            "type": "string",
            "example": "Please pull these awesome changes",
            "nullable": true
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
                    "description": {
                        "type": "string",
                        "nullable": true
                    },
                    "color": {
                        "type": "string"
                    },
                    "default": {
                        "type": "boolean"
                    }
                },
                "required": [
                    "id",
                    "node_id",
                    "url",
                    "name",
                    "description",
                    "color",
                    "default"
                ]
            }
        },
        "milestone": {
            "$ref": "#/components/schemas/nullable-milestone"
        },
        "active_lock_reason": {
            "type": "string",
            "example": "too heated",
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
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z",
            "nullable": true
        },
        "merged_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z",
            "nullable": true
        },
        "merge_commit_sha": {
            "type": "string",
            "example": "e5bd3914e2e596debea16f433f57875b5b90bcd6",
            "nullable": true
        },
        "assignee": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "assignees": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            },
            "nullable": true
        },
        "requested_reviewers": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            },
            "nullable": true
        },
        "requested_teams": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/team-simple"
            },
            "nullable": true
        },
        "head": {
            "type": "object",
            "properties": {
                "label": {
                    "type": "string"
                },
                "ref": {
                    "type": "string"
                },
                "repo": {
                    "type": "object",
                    "nullable": true,
                    "properties": {
                        "archive_url": {
                            "type": "string"
                        },
                        "assignees_url": {
                            "type": "string"
                        },
                        "blobs_url": {
                            "type": "string"
                        },
                        "branches_url": {
                            "type": "string"
                        },
                        "collaborators_url": {
                            "type": "string"
                        },
                        "comments_url": {
                            "type": "string"
                        },
                        "commits_url": {
                            "type": "string"
                        },
                        "compare_url": {
                            "type": "string"
                        },
                        "contents_url": {
                            "type": "string"
                        },
                        "contributors_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "deployments_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "description": {
                            "type": "string",
                            "nullable": true
                        },
                        "downloads_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "events_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "fork": {
                            "type": "boolean"
                        },
                        "forks_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "full_name": {
                            "type": "string"
                        },
                        "git_commits_url": {
                            "type": "string"
                        },
                        "git_refs_url": {
                            "type": "string"
                        },
                        "git_tags_url": {
                            "type": "string"
                        },
                        "hooks_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "html_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "id": {
                            "type": "integer"
                        },
                        "node_id": {
                            "type": "string"
                        },
                        "issue_comment_url": {
                            "type": "string"
                        },
                        "issue_events_url": {
                            "type": "string"
                        },
                        "issues_url": {
                            "type": "string"
                        },
                        "keys_url": {
                            "type": "string"
                        },
                        "labels_url": {
                            "type": "string"
                        },
                        "languages_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "merges_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "milestones_url": {
                            "type": "string"
                        },
                        "name": {
                            "type": "string"
                        },
                        "notifications_url": {
                            "type": "string"
                        },
                        "owner": {
                            "type": "object",
                            "properties": {
                                "avatar_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "events_url": {
                                    "type": "string"
                                },
                                "followers_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "following_url": {
                                    "type": "string"
                                },
                                "gists_url": {
                                    "type": "string"
                                },
                                "gravatar_id": {
                                    "type": "string",
                                    "nullable": true
                                },
                                "html_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "id": {
                                    "type": "integer"
                                },
                                "node_id": {
                                    "type": "string"
                                },
                                "login": {
                                    "type": "string"
                                },
                                "organizations_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "received_events_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "repos_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "site_admin": {
                                    "type": "boolean"
                                },
                                "starred_url": {
                                    "type": "string"
                                },
                                "subscriptions_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "type": {
                                    "type": "string"
                                },
                                "url": {
                                    "type": "string",
                                    "format": "uri"
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
                                "url"
                            ]
                        },
                        "private": {
                            "type": "boolean"
                        },
                        "pulls_url": {
                            "type": "string"
                        },
                        "releases_url": {
                            "type": "string"
                        },
                        "stargazers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "statuses_url": {
                            "type": "string"
                        },
                        "subscribers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "subscription_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "tags_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "teams_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "trees_url": {
                            "type": "string"
                        },
                        "url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "clone_url": {
                            "type": "string"
                        },
                        "default_branch": {
                            "type": "string"
                        },
                        "forks": {
                            "type": "integer"
                        },
                        "forks_count": {
                            "type": "integer"
                        },
                        "git_url": {
                            "type": "string"
                        },
                        "has_downloads": {
                            "type": "boolean"
                        },
                        "has_issues": {
                            "type": "boolean"
                        },
                        "has_projects": {
                            "type": "boolean"
                        },
                        "has_wiki": {
                            "type": "boolean"
                        },
                        "has_pages": {
                            "type": "boolean"
                        },
                        "has_discussions": {
                            "type": "boolean"
                        },
                        "homepage": {
                            "type": "string",
                            "format": "uri",
                            "nullable": true
                        },
                        "language": {
                            "type": "string",
                            "nullable": true
                        },
                        "master_branch": {
                            "type": "string"
                        },
                        "archived": {
                            "type": "boolean"
                        },
                        "disabled": {
                            "type": "boolean"
                        },
                        "visibility": {
                            "description": "The repository visibility: public, private, or internal.",
                            "type": "string"
                        },
                        "mirror_url": {
                            "type": "string",
                            "format": "uri",
                            "nullable": true
                        },
                        "open_issues": {
                            "type": "integer"
                        },
                        "open_issues_count": {
                            "type": "integer"
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
                        "license": {
                            "type": "object",
                            "properties": {
                                "key": {
                                    "type": "string"
                                },
                                "name": {
                                    "type": "string"
                                },
                                "url": {
                                    "type": "string",
                                    "format": "uri",
                                    "nullable": true
                                },
                                "spdx_id": {
                                    "type": "string",
                                    "nullable": true
                                },
                                "node_id": {
                                    "type": "string"
                                }
                            },
                            "required": [
                                "key",
                                "name",
                                "url",
                                "spdx_id",
                                "node_id"
                            ],
                            "nullable": true
                        },
                        "pushed_at": {
                            "type": "string",
                            "format": "date-time"
                        },
                        "size": {
                            "type": "integer"
                        },
                        "ssh_url": {
                            "type": "string"
                        },
                        "stargazers_count": {
                            "type": "integer"
                        },
                        "svn_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "topics": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        },
                        "watchers": {
                            "type": "integer"
                        },
                        "watchers_count": {
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
                        "allow_forking": {
                            "type": "boolean"
                        },
                        "is_template": {
                            "type": "boolean"
                        },
                        "web_commit_signoff_required": {
                            "type": "boolean"
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
                        "has_discussions",
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
                        "updated_at"
                    ]
                },
                "sha": {
                    "type": "string"
                },
                "user": {
                    "type": "object",
                    "properties": {
                        "avatar_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "events_url": {
                            "type": "string"
                        },
                        "followers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "following_url": {
                            "type": "string"
                        },
                        "gists_url": {
                            "type": "string"
                        },
                        "gravatar_id": {
                            "type": "string",
                            "nullable": true
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
                        "login": {
                            "type": "string"
                        },
                        "organizations_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "received_events_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "repos_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "site_admin": {
                            "type": "boolean"
                        },
                        "starred_url": {
                            "type": "string"
                        },
                        "subscriptions_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "type": {
                            "type": "string"
                        },
                        "url": {
                            "type": "string",
                            "format": "uri"
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
                        "url"
                    ]
                }
            },
            "required": [
                "label",
                "ref",
                "repo",
                "sha",
                "user"
            ]
        },
        "base": {
            "type": "object",
            "properties": {
                "label": {
                    "type": "string"
                },
                "ref": {
                    "type": "string"
                },
                "repo": {
                    "type": "object",
                    "properties": {
                        "archive_url": {
                            "type": "string"
                        },
                        "assignees_url": {
                            "type": "string"
                        },
                        "blobs_url": {
                            "type": "string"
                        },
                        "branches_url": {
                            "type": "string"
                        },
                        "collaborators_url": {
                            "type": "string"
                        },
                        "comments_url": {
                            "type": "string"
                        },
                        "commits_url": {
                            "type": "string"
                        },
                        "compare_url": {
                            "type": "string"
                        },
                        "contents_url": {
                            "type": "string"
                        },
                        "contributors_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "deployments_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "description": {
                            "type": "string",
                            "nullable": true
                        },
                        "downloads_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "events_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "fork": {
                            "type": "boolean"
                        },
                        "forks_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "full_name": {
                            "type": "string"
                        },
                        "git_commits_url": {
                            "type": "string"
                        },
                        "git_refs_url": {
                            "type": "string"
                        },
                        "git_tags_url": {
                            "type": "string"
                        },
                        "hooks_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "html_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "id": {
                            "type": "integer"
                        },
                        "is_template": {
                            "type": "boolean"
                        },
                        "node_id": {
                            "type": "string"
                        },
                        "issue_comment_url": {
                            "type": "string"
                        },
                        "issue_events_url": {
                            "type": "string"
                        },
                        "issues_url": {
                            "type": "string"
                        },
                        "keys_url": {
                            "type": "string"
                        },
                        "labels_url": {
                            "type": "string"
                        },
                        "languages_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "merges_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "milestones_url": {
                            "type": "string"
                        },
                        "name": {
                            "type": "string"
                        },
                        "notifications_url": {
                            "type": "string"
                        },
                        "owner": {
                            "type": "object",
                            "properties": {
                                "avatar_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "events_url": {
                                    "type": "string"
                                },
                                "followers_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "following_url": {
                                    "type": "string"
                                },
                                "gists_url": {
                                    "type": "string"
                                },
                                "gravatar_id": {
                                    "type": "string",
                                    "nullable": true
                                },
                                "html_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "id": {
                                    "type": "integer"
                                },
                                "node_id": {
                                    "type": "string"
                                },
                                "login": {
                                    "type": "string"
                                },
                                "organizations_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "received_events_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "repos_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "site_admin": {
                                    "type": "boolean"
                                },
                                "starred_url": {
                                    "type": "string"
                                },
                                "subscriptions_url": {
                                    "type": "string",
                                    "format": "uri"
                                },
                                "type": {
                                    "type": "string"
                                },
                                "url": {
                                    "type": "string",
                                    "format": "uri"
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
                                "url"
                            ]
                        },
                        "private": {
                            "type": "boolean"
                        },
                        "pulls_url": {
                            "type": "string"
                        },
                        "releases_url": {
                            "type": "string"
                        },
                        "stargazers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "statuses_url": {
                            "type": "string"
                        },
                        "subscribers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "subscription_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "tags_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "teams_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "trees_url": {
                            "type": "string"
                        },
                        "url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "clone_url": {
                            "type": "string"
                        },
                        "default_branch": {
                            "type": "string"
                        },
                        "forks": {
                            "type": "integer"
                        },
                        "forks_count": {
                            "type": "integer"
                        },
                        "git_url": {
                            "type": "string"
                        },
                        "has_downloads": {
                            "type": "boolean"
                        },
                        "has_issues": {
                            "type": "boolean"
                        },
                        "has_projects": {
                            "type": "boolean"
                        },
                        "has_wiki": {
                            "type": "boolean"
                        },
                        "has_pages": {
                            "type": "boolean"
                        },
                        "has_discussions": {
                            "type": "boolean"
                        },
                        "homepage": {
                            "type": "string",
                            "format": "uri",
                            "nullable": true
                        },
                        "language": {
                            "type": "string",
                            "nullable": true
                        },
                        "master_branch": {
                            "type": "string"
                        },
                        "archived": {
                            "type": "boolean"
                        },
                        "disabled": {
                            "type": "boolean"
                        },
                        "visibility": {
                            "description": "The repository visibility: public, private, or internal.",
                            "type": "string"
                        },
                        "mirror_url": {
                            "type": "string",
                            "format": "uri",
                            "nullable": true
                        },
                        "open_issues": {
                            "type": "integer"
                        },
                        "open_issues_count": {
                            "type": "integer"
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
                        "license": {
                            "$ref": "#/components/schemas/nullable-license-simple"
                        },
                        "pushed_at": {
                            "type": "string",
                            "format": "date-time"
                        },
                        "size": {
                            "type": "integer"
                        },
                        "ssh_url": {
                            "type": "string"
                        },
                        "stargazers_count": {
                            "type": "integer"
                        },
                        "svn_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "topics": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        },
                        "watchers": {
                            "type": "integer"
                        },
                        "watchers_count": {
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
                        "allow_forking": {
                            "type": "boolean"
                        },
                        "web_commit_signoff_required": {
                            "type": "boolean"
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
                        "has_discussions",
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
                        "updated_at"
                    ]
                },
                "sha": {
                    "type": "string"
                },
                "user": {
                    "type": "object",
                    "properties": {
                        "avatar_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "events_url": {
                            "type": "string"
                        },
                        "followers_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "following_url": {
                            "type": "string"
                        },
                        "gists_url": {
                            "type": "string"
                        },
                        "gravatar_id": {
                            "type": "string",
                            "nullable": true
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
                        "login": {
                            "type": "string"
                        },
                        "organizations_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "received_events_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "repos_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "site_admin": {
                            "type": "boolean"
                        },
                        "starred_url": {
                            "type": "string"
                        },
                        "subscriptions_url": {
                            "type": "string",
                            "format": "uri"
                        },
                        "type": {
                            "type": "string"
                        },
                        "url": {
                            "type": "string",
                            "format": "uri"
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
                        "url"
                    ]
                }
            },
            "required": [
                "label",
                "ref",
                "repo",
                "sha",
                "user"
            ]
        },
        "_links": {
            "type": "object",
            "properties": {
                "comments": {
                    "$ref": "#/components/schemas/link"
                },
                "commits": {
                    "$ref": "#/components/schemas/link"
                },
                "statuses": {
                    "$ref": "#/components/schemas/link"
                },
                "html": {
                    "$ref": "#/components/schemas/link"
                },
                "issue": {
                    "$ref": "#/components/schemas/link"
                },
                "review_comments": {
                    "$ref": "#/components/schemas/link"
                },
                "review_comment": {
                    "$ref": "#/components/schemas/link"
                },
                "self": {
                    "$ref": "#/components/schemas/link"
                }
            },
            "required": [
                "comments",
                "commits",
                "statuses",
                "html",
                "issue",
                "review_comments",
                "review_comment",
                "self"
            ]
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "auto_merge": {
            "$ref": "#/components/schemas/auto-merge"
        },
        "draft": {
            "description": "Indicates whether or not the pull request is a draft.",
            "example": false,
            "type": "boolean"
        },
        "merged": {
            "type": "boolean"
        },
        "mergeable": {
            "type": "boolean",
            "example": true,
            "nullable": true
        },
        "rebaseable": {
            "type": "boolean",
            "example": true,
            "nullable": true
        },
        "mergeable_state": {
            "type": "string",
            "example": "clean"
        },
        "merged_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "comments": {
            "type": "integer",
            "example": 10
        },
        "review_comments": {
            "type": "integer",
            "example": 0
        },
        "maintainer_can_modify": {
            "description": "Indicates whether maintainers can modify the pull request.",
            "example": true,
            "type": "boolean"
        },
        "commits": {
            "type": "integer",
            "example": 3
        },
        "additions": {
            "type": "integer",
            "example": 100
        },
        "deletions": {
            "type": "integer",
            "example": 3
        },
        "changed_files": {
            "type": "integer",
            "example": 5
        }
    },
    "required": [
        "_links",
        "assignee",
        "labels",
        "base",
        "body",
        "closed_at",
        "comments_url",
        "commits_url",
        "created_at",
        "diff_url",
        "head",
        "html_url",
        "id",
        "node_id",
        "issue_url",
        "merge_commit_sha",
        "merged_at",
        "milestone",
        "number",
        "patch_url",
        "review_comment_url",
        "review_comments_url",
        "statuses_url",
        "state",
        "locked",
        "title",
        "updated_at",
        "url",
        "user",
        "author_association",
        "auto_merge",
        "additions",
        "changed_files",
        "comments",
        "commits",
        "deletions",
        "mergeable",
        "mergeable_state",
        "merged",
        "maintainer_can_modify",
        "merged_by",
        "review_comments"
    ]
}
```

### `#/components/examples/pull-request`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347",
        "id": 1,
        "node_id": "MDExOlB1bGxSZXF1ZXN0MQ==",
        "html_url": "https://github.com/octocat/Hello-World/pull/1347",
        "diff_url": "https://github.com/octocat/Hello-World/pull/1347.diff",
        "patch_url": "https://github.com/octocat/Hello-World/pull/1347.patch",
        "issue_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347",
        "commits_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits",
        "review_comments_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments",
        "review_comment_url": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}",
        "comments_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments",
        "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "number": 1347,
        "state": "open",
        "locked": true,
        "title": "Amazing new feature",
        "user": {
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
        "body": "Please pull these awesome changes in!",
        "labels": [
            {
                "id": 208045946,
                "node_id": "MDU6TGFiZWwyMDgwNDU5NDY=",
                "url": "https://api.github.com/repos/octocat/Hello-World/labels/bug",
                "name": "bug",
                "description": "Something isn't working",
                "color": "f29513",
                "default": true
            }
        ],
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
        "active_lock_reason": "too heated",
        "created_at": "2011-01-26T19:01:12Z",
        "updated_at": "2011-01-26T19:01:12Z",
        "closed_at": "2011-01-26T19:01:12Z",
        "merged_at": "2011-01-26T19:01:12Z",
        "merge_commit_sha": "e5bd3914e2e596debea16f433f57875b5b90bcd6",
        "assignee": {
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
        "assignees": [
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
                "site_admin": false
            },
            {
                "login": "hubot",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/hubot_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/hubot",
                "html_url": "https://github.com/hubot",
                "followers_url": "https://api.github.com/users/hubot/followers",
                "following_url": "https://api.github.com/users/hubot/following{/other_user}",
                "gists_url": "https://api.github.com/users/hubot/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/hubot/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/hubot/subscriptions",
                "organizations_url": "https://api.github.com/users/hubot/orgs",
                "repos_url": "https://api.github.com/users/hubot/repos",
                "events_url": "https://api.github.com/users/hubot/events{/privacy}",
                "received_events_url": "https://api.github.com/users/hubot/received_events",
                "type": "User",
                "site_admin": true
            }
        ],
        "requested_reviewers": [
            {
                "login": "other_user",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/other_user_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/other_user",
                "html_url": "https://github.com/other_user",
                "followers_url": "https://api.github.com/users/other_user/followers",
                "following_url": "https://api.github.com/users/other_user/following{/other_user}",
                "gists_url": "https://api.github.com/users/other_user/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/other_user/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/other_user/subscriptions",
                "organizations_url": "https://api.github.com/users/other_user/orgs",
                "repos_url": "https://api.github.com/users/other_user/repos",
                "events_url": "https://api.github.com/users/other_user/events{/privacy}",
                "received_events_url": "https://api.github.com/users/other_user/received_events",
                "type": "User",
                "site_admin": false
            }
        ],
        "requested_teams": [
            {
                "id": 1,
                "node_id": "MDQ6VGVhbTE=",
                "url": "https://api.github.com/teams/1",
                "html_url": "https://github.com/orgs/github/teams/justice-league",
                "name": "Justice League",
                "slug": "justice-league",
                "description": "A great team.",
                "privacy": "closed",
                "notification_setting": "notifications_enabled",
                "permission": "admin",
                "members_url": "https://api.github.com/teams/1/members{/member}",
                "repositories_url": "https://api.github.com/teams/1/repos"
            }
        ],
        "head": {
            "label": "octocat:new-topic",
            "ref": "new-topic",
            "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "user": {
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
            "repo": {
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
                "has_discussions": false,
                "archived": false,
                "disabled": false,
                "pushed_at": "2011-01-26T19:06:43Z",
                "created_at": "2011-01-26T19:01:12Z",
                "updated_at": "2011-01-26T19:14:43Z",
                "permissions": {
                    "admin": false,
                    "push": false,
                    "pull": true
                },
                "allow_rebase_merge": true,
                "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                "allow_squash_merge": true,
                "allow_merge_commit": true,
                "allow_forking": true,
                "forks": 123,
                "open_issues": 123,
                "license": {
                    "key": "mit",
                    "name": "MIT License",
                    "url": "https://api.github.com/licenses/mit",
                    "spdx_id": "MIT",
                    "node_id": "MDc6TGljZW5zZW1pdA=="
                },
                "watchers": 123
            }
        },
        "base": {
            "label": "octocat:master",
            "ref": "master",
            "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "user": {
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
            "repo": {
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
                "has_discussions": false,
                "archived": false,
                "disabled": false,
                "pushed_at": "2011-01-26T19:06:43Z",
                "created_at": "2011-01-26T19:01:12Z",
                "updated_at": "2011-01-26T19:14:43Z",
                "permissions": {
                    "admin": false,
                    "push": false,
                    "pull": true
                },
                "allow_rebase_merge": true,
                "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                "allow_squash_merge": true,
                "allow_merge_commit": true,
                "forks": 123,
                "open_issues": 123,
                "license": {
                    "key": "mit",
                    "name": "MIT License",
                    "url": "https://api.github.com/licenses/mit",
                    "spdx_id": "MIT",
                    "node_id": "MDc6TGljZW5zZW1pdA=="
                },
                "watchers": 123
            }
        },
        "_links": {
            "self": {
                "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347"
            },
            "html": {
                "href": "https://github.com/octocat/Hello-World/pull/1347"
            },
            "issue": {
                "href": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
            },
            "comments": {
                "href": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments"
            },
            "review_comments": {
                "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments"
            },
            "review_comment": {
                "href": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}"
            },
            "commits": {
                "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits"
            },
            "statuses": {
                "href": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e"
            }
        },
        "author_association": "OWNER",
        "auto_merge": null,
        "draft": false,
        "merged": false,
        "mergeable": true,
        "rebaseable": true,
        "mergeable_state": "clean",
        "merged_by": {
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
        "comments": 10,
        "review_comments": 0,
        "maintainer_can_modify": true,
        "commits": 3,
        "additions": 100,
        "deletions": 3,
        "changed_files": 5
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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

### `#/components/responses/unacceptable`

```json
{
    "description": "Unacceptable",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
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