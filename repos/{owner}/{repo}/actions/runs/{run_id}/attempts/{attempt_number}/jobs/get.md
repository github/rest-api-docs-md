# List jobs for a workflow run attempt

`get /repos/{owner}/{repo}/actions/runs/{run_id}/attempts/{attempt_number}/jobs`

Lists jobs for a specific workflow run attempt. You can use parameters to narrow the list of results. For more information
about using parameters, see [Parameters](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#parameters).

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint  with a private repository.

## Operation Object

```json
{
    "summary": "List jobs for a workflow run attempt",
    "description": "Lists jobs for a specific workflow run attempt. You can use parameters to narrow the list of results. For more information\nabout using parameters, see [Parameters](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#parameters).\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint  with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-jobs-for-workflow-run-attempt",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-jobs#list-jobs-for-a-workflow-run-attempt"
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
            "$ref": "#/components/parameters/attempt-number"
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
                            "jobs"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "jobs": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/job"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/job-paginated"
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
        "category": "actions",
        "subcategory": "workflow-jobs"
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

### `#/components/parameters/attempt-number`

```json
{
    "name": "attempt_number",
    "description": "The attempt number of the workflow run.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/schemas/job`

```json
{
    "title": "Job",
    "description": "Information of a job execution in a workflow run",
    "type": "object",
    "properties": {
        "id": {
            "description": "The id of the job.",
            "example": 21,
            "type": "integer"
        },
        "run_id": {
            "description": "The id of the associated workflow run.",
            "example": 5,
            "type": "integer"
        },
        "run_url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/runs/5"
        },
        "run_attempt": {
            "type": "integer",
            "description": "Attempt number of the associated workflow run, 1 for first attempt and higher if the workflow was re-run.",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDg6Q2hlY2tSdW40"
        },
        "head_sha": {
            "description": "The SHA of the commit that is being run.",
            "example": "009b8a3a9ccbb128af87f9b1c0f4c62e8a304f6d",
            "type": "string"
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/jobs/21"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/github/hello-world/runs/4",
            "nullable": true
        },
        "status": {
            "description": "The phase of the lifecycle that the job is currently in.",
            "example": "queued",
            "type": "string",
            "enum": [
                "queued",
                "in_progress",
                "completed",
                "waiting",
                "requested",
                "pending"
            ]
        },
        "conclusion": {
            "description": "The outcome of the job.",
            "example": "success",
            "type": "string",
            "nullable": true,
            "enum": [
                "success",
                "failure",
                "neutral",
                "cancelled",
                "skipped",
                "timed_out",
                "action_required"
            ]
        },
        "created_at": {
            "description": "The time that the job created, in ISO 8601 format.",
            "example": "2019-08-08T08:00:00-07:00",
            "format": "date-time",
            "type": "string"
        },
        "started_at": {
            "description": "The time that the job started, in ISO 8601 format.",
            "example": "2019-08-08T08:00:00-07:00",
            "format": "date-time",
            "type": "string"
        },
        "completed_at": {
            "description": "The time that the job finished, in ISO 8601 format.",
            "example": "2019-08-08T08:00:00-07:00",
            "format": "date-time",
            "type": "string",
            "nullable": true
        },
        "name": {
            "description": "The name of the job.",
            "example": "test-coverage",
            "type": "string"
        },
        "steps": {
            "description": "Steps in this job.",
            "type": "array",
            "items": {
                "type": "object",
                "required": [
                    "name",
                    "status",
                    "conclusion",
                    "number"
                ],
                "properties": {
                    "status": {
                        "description": "The phase of the lifecycle that the job is currently in.",
                        "example": "queued",
                        "type": "string",
                        "enum": [
                            "queued",
                            "in_progress",
                            "completed"
                        ]
                    },
                    "conclusion": {
                        "description": "The outcome of the job.",
                        "example": "success",
                        "type": "string",
                        "nullable": true
                    },
                    "name": {
                        "description": "The name of the job.",
                        "example": "test-coverage",
                        "type": "string"
                    },
                    "number": {
                        "type": "integer",
                        "example": 1
                    },
                    "started_at": {
                        "description": "The time that the step started, in ISO 8601 format.",
                        "example": "2019-08-08T08:00:00-07:00",
                        "format": "date-time",
                        "type": "string",
                        "nullable": true
                    },
                    "completed_at": {
                        "description": "The time that the job finished, in ISO 8601 format.",
                        "example": "2019-08-08T08:00:00-07:00",
                        "format": "date-time",
                        "type": "string",
                        "nullable": true
                    }
                }
            }
        },
        "check_run_url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/check-runs/4"
        },
        "labels": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "description": "Labels for the workflow job. Specified by the \"runs_on\" attribute in the action's workflow file.",
            "example": [
                "self-hosted",
                "foo",
                "bar"
            ]
        },
        "runner_id": {
            "type": "integer",
            "nullable": true,
            "example": 1,
            "description": "The ID of the runner to which this job has been assigned. (If a runner hasn't yet been assigned, this will be null.)"
        },
        "runner_name": {
            "type": "string",
            "nullable": true,
            "example": "my runner",
            "description": "The name of the runner to which this job has been assigned. (If a runner hasn't yet been assigned, this will be null.)"
        },
        "runner_group_id": {
            "type": "integer",
            "nullable": true,
            "example": 2,
            "description": "The ID of the runner group to which this job has been assigned. (If a runner hasn't yet been assigned, this will be null.)"
        },
        "runner_group_name": {
            "type": "string",
            "nullable": true,
            "example": "my runner group",
            "description": "The name of the runner group to which this job has been assigned. (If a runner hasn't yet been assigned, this will be null.)"
        },
        "workflow_name": {
            "type": "string",
            "description": "The name of the workflow.",
            "nullable": true,
            "example": "Build"
        },
        "head_branch": {
            "type": "string",
            "description": "The name of the current branch.",
            "nullable": true,
            "example": "main"
        }
    },
    "required": [
        "id",
        "node_id",
        "run_id",
        "run_url",
        "head_sha",
        "workflow_name",
        "head_branch",
        "name",
        "url",
        "html_url",
        "status",
        "conclusion",
        "started_at",
        "completed_at",
        "check_run_url",
        "labels",
        "runner_id",
        "runner_name",
        "runner_group_id",
        "runner_group_name",
        "created_at"
    ]
}
```

### `#/components/examples/job-paginated`

```json
{
    "value": {
        "total_count": 1,
        "jobs": [
            {
                "id": 399444496,
                "run_id": 29679449,
                "run_url": "https://api.github.com/repos/octo-org/octo-repo/actions/runs/29679449",
                "node_id": "MDEyOldvcmtmbG93IEpvYjM5OTQ0NDQ5Ng==",
                "head_sha": "f83a356604ae3c5d03e1b46ef4d1ca77d64a90b0",
                "url": "https://api.github.com/repos/octo-org/octo-repo/actions/jobs/399444496",
                "html_url": "https://github.com/octo-org/octo-repo/runs/29679449/jobs/399444496",
                "status": "completed",
                "conclusion": "success",
                "started_at": "2020-01-20T17:42:40Z",
                "completed_at": "2020-01-20T17:44:39Z",
                "name": "build",
                "steps": [
                    {
                        "name": "Set up job",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 1,
                        "started_at": "2020-01-20T09:42:40.000-08:00",
                        "completed_at": "2020-01-20T09:42:41.000-08:00"
                    },
                    {
                        "name": "Run actions/checkout@v2",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 2,
                        "started_at": "2020-01-20T09:42:41.000-08:00",
                        "completed_at": "2020-01-20T09:42:45.000-08:00"
                    },
                    {
                        "name": "Set up Ruby",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 3,
                        "started_at": "2020-01-20T09:42:45.000-08:00",
                        "completed_at": "2020-01-20T09:42:45.000-08:00"
                    },
                    {
                        "name": "Run actions/cache@v3",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 4,
                        "started_at": "2020-01-20T09:42:45.000-08:00",
                        "completed_at": "2020-01-20T09:42:48.000-08:00"
                    },
                    {
                        "name": "Install Bundler",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 5,
                        "started_at": "2020-01-20T09:42:48.000-08:00",
                        "completed_at": "2020-01-20T09:42:52.000-08:00"
                    },
                    {
                        "name": "Install Gems",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 6,
                        "started_at": "2020-01-20T09:42:52.000-08:00",
                        "completed_at": "2020-01-20T09:42:53.000-08:00"
                    },
                    {
                        "name": "Run Tests",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 7,
                        "started_at": "2020-01-20T09:42:53.000-08:00",
                        "completed_at": "2020-01-20T09:42:59.000-08:00"
                    },
                    {
                        "name": "Deploy to Heroku",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 8,
                        "started_at": "2020-01-20T09:42:59.000-08:00",
                        "completed_at": "2020-01-20T09:44:39.000-08:00"
                    },
                    {
                        "name": "Post actions/cache@v3",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 16,
                        "started_at": "2020-01-20T09:44:39.000-08:00",
                        "completed_at": "2020-01-20T09:44:39.000-08:00"
                    },
                    {
                        "name": "Complete job",
                        "status": "completed",
                        "conclusion": "success",
                        "number": 17,
                        "started_at": "2020-01-20T09:44:39.000-08:00",
                        "completed_at": "2020-01-20T09:44:39.000-08:00"
                    }
                ],
                "check_run_url": "https://api.github.com/repos/octo-org/octo-repo/check-runs/399444496",
                "labels": [
                    "self-hosted",
                    "foo",
                    "bar"
                ],
                "runner_id": 1,
                "runner_name": "my runner",
                "runner_group_id": 2,
                "runner_group_name": "my runner group",
                "workflow_name": "CI",
                "head_branch": "main"
            }
        ]
    }
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