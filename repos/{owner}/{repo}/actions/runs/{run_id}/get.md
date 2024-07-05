# Get a workflow run

Gets a specific workflow run.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get a workflow run",
    "description": "Gets a specific workflow run.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-workflow-run",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-runs#get-a-workflow-run"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/run-id"
        },
        {
            "$ref": "#/components/parameters/exclude-pull-requests"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/workflow-run"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/workflow-run"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "workflow-runs"
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

### `#/components/parameters/run-id`

```json
{
    "name": "run_id",
    "description": "The unique identifier of the workflow run.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/exclude-pull-requests`

```json
{
    "name": "exclude_pull_requests",
    "description": "If `true` pull requests are omitted from the response (empty array).",
    "in": "query",
    "required": false,
    "schema": {
        "type": "boolean",
        "default": false
    }
}
```

### `#/components/schemas/workflow-run`

```json
{
    "title": "Workflow Run",
    "description": "An invocation of a workflow",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "description": "The ID of the workflow run.",
            "example": 5
        },
        "name": {
            "type": "string",
            "description": "The name of the workflow run.",
            "nullable": true,
            "example": "Build"
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOkNoZWNrU3VpdGU1"
        },
        "check_suite_id": {
            "type": "integer",
            "description": "The ID of the associated check suite.",
            "example": 42
        },
        "check_suite_node_id": {
            "type": "string",
            "description": "The node ID of the associated check suite.",
            "example": "MDEwOkNoZWNrU3VpdGU0Mg=="
        },
        "head_branch": {
            "type": "string",
            "nullable": true,
            "example": "master"
        },
        "head_sha": {
            "description": "The SHA of the head commit that points to the version of the workflow being run.",
            "example": "009b8a3a9ccbb128af87f9b1c0f4c62e8a304f6d",
            "type": "string"
        },
        "path": {
            "description": "The full path of the workflow",
            "example": "octocat/octo-repo/.github/workflows/ci.yml@main",
            "type": "string"
        },
        "run_number": {
            "type": "integer",
            "description": "The auto incrementing run number for the workflow run.",
            "example": 106
        },
        "run_attempt": {
            "type": "integer",
            "description": "Attempt number of the run, 1 for first attempt and higher if the workflow was re-run.",
            "example": 1
        },
        "referenced_workflows": {
            "type": "array",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/referenced-workflow"
            }
        },
        "event": {
            "type": "string",
            "example": "push"
        },
        "status": {
            "type": "string",
            "nullable": true,
            "example": "completed"
        },
        "conclusion": {
            "type": "string",
            "nullable": true,
            "example": "neutral"
        },
        "workflow_id": {
            "type": "integer",
            "description": "The ID of the parent workflow.",
            "example": 5
        },
        "url": {
            "type": "string",
            "description": "The URL to the workflow run.",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/github/hello-world/suites/4"
        },
        "pull_requests": {
            "description": "Pull requests that are open with a `head_sha` or `head_branch` that matches the workflow run. The returned pull requests do not necessarily indicate pull requests that triggered the run.",
            "type": "array",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/pull-request-minimal"
            }
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "actor": {
            "$ref": "#/components/schemas/simple-user"
        },
        "triggering_actor": {
            "$ref": "#/components/schemas/simple-user"
        },
        "run_started_at": {
            "type": "string",
            "format": "date-time",
            "description": "The start time of the latest run. Resets on re-run."
        },
        "jobs_url": {
            "description": "The URL to the jobs for the workflow run.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/jobs"
        },
        "logs_url": {
            "description": "The URL to download the logs for the workflow run.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/logs"
        },
        "check_suite_url": {
            "description": "The URL to the associated check suite.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/check-suites/12"
        },
        "artifacts_url": {
            "description": "The URL to the artifacts for the workflow run.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/rerun/artifacts"
        },
        "cancel_url": {
            "description": "The URL to cancel the workflow run.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/cancel"
        },
        "rerun_url": {
            "description": "The URL to rerun the workflow run.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/rerun"
        },
        "previous_attempt_url": {
            "nullable": true,
            "description": "The URL to the previous attempted run of this workflow, if one exists.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5/attempts/3"
        },
        "workflow_url": {
            "description": "The URL to the workflow.",
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/workflows/main.yaml"
        },
        "head_commit": {
            "$ref": "#/components/schemas/nullable-simple-commit"
        },
        "repository": {
            "$ref": "#/components/schemas/minimal-repository"
        },
        "head_repository": {
            "$ref": "#/components/schemas/minimal-repository"
        },
        "head_repository_id": {
            "type": "integer",
            "example": 5
        },
        "display_title": {
            "type": "string",
            "example": "Simple Workflow",
            "description": "The event-specific title associated with the run or the run-name if set, or the value of `run-name` if it is set in the workflow."
        }
    },
    "required": [
        "id",
        "node_id",
        "head_branch",
        "run_number",
        "display_title",
        "event",
        "status",
        "conclusion",
        "head_sha",
        "path",
        "workflow_id",
        "url",
        "html_url",
        "created_at",
        "updated_at",
        "head_commit",
        "head_repository",
        "repository",
        "jobs_url",
        "logs_url",
        "check_suite_url",
        "cancel_url",
        "rerun_url",
        "artifacts_url",
        "workflow_url",
        "pull_requests"
    ]
}
```

### `#/components/examples/workflow-run`

```json
{
    "value": {
        "id": 30433642,
        "name": "Build",
        "node_id": "MDEyOldvcmtmbG93IFJ1bjI2OTI4OQ==",
        "check_suite_id": 42,
        "check_suite_node_id": "MDEwOkNoZWNrU3VpdGU0Mg==",
        "head_branch": "main",
        "head_sha": "acb5820ced9479c074f688cc328bf03f341a511d",
        "path": ".github/workflows/build.yml@main",
        "run_number": 562,
        "event": "push",
        "display_title": "Update README.md",
        "status": "queued",
        "conclusion": null,
        "workflow_id": 159038,
        "url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642",
        "html_url": "https://github.com/octo-org/octo-repo/actions/runs/30433642",
        "pull_requests": [],
        "created_at": "2020-01-22T19:33:08Z",
        "updated_at": "2020-01-22T19:33:08Z",
        "actor": {
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
        "run_attempt": 1,
        "referenced_workflows": [
            {
                "path": "octocat/Hello-World/.github/workflows/deploy.yml@main",
                "sha": "86e8bc9ecf7d38b1ed2d2cfb8eb87ba9b35b01db",
                "ref": "refs/heads/main"
            },
            {
                "path": "octo-org/octo-repo/.github/workflows/report.yml@v2",
                "sha": "79e9790903e1c3373b1a3e3a941d57405478a232",
                "ref": "refs/tags/v2"
            },
            {
                "path": "octo-org/octo-repo/.github/workflows/secure.yml@1595d4b6de6a9e9751fb270a41019ce507d4099e",
                "sha": "1595d4b6de6a9e9751fb270a41019ce507d4099e"
            }
        ],
        "run_started_at": "2020-01-22T19:33:08Z",
        "triggering_actor": {
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
        "jobs_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/jobs",
        "logs_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/logs",
        "check_suite_url": "https://api.github.com/repos/octo-org/octo-repo/check-suites/414944374",
        "artifacts_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/artifacts",
        "cancel_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/cancel",
        "rerun_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/rerun",
        "previous_attempt_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/30433642/attempts/1",
        "workflow_url": "https://api.github.com/repos/octo-org/octo-repo/actions/workflows/159038",
        "head_commit": {
            "id": "acb5820ced9479c074f688cc328bf03f341a511d",
            "tree_id": "d23f6eedb1e1b9610bbc754ddb5197bfe7271223",
            "message": "Create linter.yaml",
            "timestamp": "2020-01-22T19:33:05Z",
            "author": {
                "name": "Octo Cat",
                "email": "octocat@github.com"
            },
            "committer": {
                "name": "GitHub",
                "email": "noreply@github.com"
            }
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
        "head_repository": {
            "id": 217723378,
            "node_id": "MDEwOlJlcG9zaXRvcnkyMTc3MjMzNzg=",
            "name": "octo-repo",
            "full_name": "octo-org/octo-repo",
            "private": true,
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
            "html_url": "https://github.com/octo-org/octo-repo",
            "description": null,
            "fork": false,
            "url": "https://api.github.com/repos/octo-org/octo-repo",
            "forks_url": "https://api.github.com/repos/octo-org/octo-repo/forks",
            "keys_url": "https://api.github.com/repos/octo-org/octo-repo/keys{/key_id}",
            "collaborators_url": "https://api.github.com/repos/octo-org/octo-repo/collaborators{/collaborator}",
            "teams_url": "https://api.github.com/repos/octo-org/octo-repo/teams",
            "hooks_url": "https://api.github.com/repos/octo-org/octo-repo/hooks",
            "issue_events_url": "https://api.github.com/repos/octo-org/octo-repo/issues/events{/number}",
            "events_url": "https://api.github.com/repos/octo-org/octo-repo/events",
            "assignees_url": "https://api.github.com/repos/octo-org/octo-repo/assignees{/user}",
            "branches_url": "https://api.github.com/repos/octo-org/octo-repo/branches{/branch}",
            "tags_url": "https://api.github.com/repos/octo-org/octo-repo/tags",
            "blobs_url": "https://api.github.com/repos/octo-org/octo-repo/git/blobs{/sha}",
            "git_tags_url": "https://api.github.com/repos/octo-org/octo-repo/git/tags{/sha}",
            "git_refs_url": "https://api.github.com/repos/octo-org/octo-repo/git/refs{/sha}",
            "trees_url": "https://api.github.com/repos/octo-org/octo-repo/git/trees{/sha}",
            "statuses_url": "https://api.github.com/repos/octo-org/octo-repo/statuses/{sha}",
            "languages_url": "https://api.github.com/repos/octo-org/octo-repo/languages",
            "stargazers_url": "https://api.github.com/repos/octo-org/octo-repo/stargazers",
            "contributors_url": "https://api.github.com/repos/octo-org/octo-repo/contributors",
            "subscribers_url": "https://api.github.com/repos/octo-org/octo-repo/subscribers",
            "subscription_url": "https://api.github.com/repos/octo-org/octo-repo/subscription",
            "commits_url": "https://api.github.com/repos/octo-org/octo-repo/commits{/sha}",
            "git_commits_url": "https://api.github.com/repos/octo-org/octo-repo/git/commits{/sha}",
            "comments_url": "https://api.github.com/repos/octo-org/octo-repo/comments{/number}",
            "issue_comment_url": "https://api.github.com/repos/octo-org/octo-repo/issues/comments{/number}",
            "contents_url": "https://api.github.com/repos/octo-org/octo-repo/contents/{+path}",
            "compare_url": "https://api.github.com/repos/octo-org/octo-repo/compare/{base}...{head}",
            "merges_url": "https://api.github.com/repos/octo-org/octo-repo/merges",
            "archive_url": "https://api.github.com/repos/octo-org/octo-repo/{archive_format}{/ref}",
            "downloads_url": "https://api.github.com/repos/octo-org/octo-repo/downloads",
            "issues_url": "https://api.github.com/repos/octo-org/octo-repo/issues{/number}",
            "pulls_url": "https://api.github.com/repos/octo-org/octo-repo/pulls{/number}",
            "milestones_url": "https://api.github.com/repos/octo-org/octo-repo/milestones{/number}",
            "notifications_url": "https://api.github.com/repos/octo-org/octo-repo/notifications{?since,all,participating}",
            "labels_url": "https://api.github.com/repos/octo-org/octo-repo/labels{/name}",
            "releases_url": "https://api.github.com/repos/octo-org/octo-repo/releases{/id}",
            "deployments_url": "https://api.github.com/repos/octo-org/octo-repo/deployments"
        }
    }
}
```