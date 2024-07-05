# Get workflow run usage

`get /repos/{owner}/{repo}/actions/runs/{run_id}/timing`

Gets the number of billable minutes and total run time for a specific workflow run. Billable minutes only apply to workflows in private repositories that use GitHub-hosted runners. Usage is listed for each GitHub-hosted runner operating system in milliseconds. Any job re-runs are also included in the usage. The usage does not include the multiplier for macOS and Windows runners and is not rounded up to the nearest whole minute. For more information, see "[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)".

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get workflow run usage",
    "description": "Gets the number of billable minutes and total run time for a specific workflow run. Billable minutes only apply to workflows in private repositories that use GitHub-hosted runners. Usage is listed for each GitHub-hosted runner operating system in milliseconds. Any job re-runs are also included in the usage. The usage does not include the multiplier for macOS and Windows runners and is not rounded up to the nearest whole minute. For more information, see \"[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)\".\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-workflow-run-usage",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-runs#get-workflow-run-usage"
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
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/workflow-run-usage"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/workflow-run-usage"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
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

### `#/components/schemas/workflow-run-usage`

```json
{
    "title": "Workflow Run Usage",
    "description": "Workflow Run Usage",
    "type": "object",
    "properties": {
        "billable": {
            "type": "object",
            "properties": {
                "UBUNTU": {
                    "type": "object",
                    "required": [
                        "total_ms",
                        "jobs"
                    ],
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        },
                        "jobs": {
                            "type": "integer"
                        },
                        "job_runs": {
                            "type": "array",
                            "items": {
                                "type": "object",
                                "required": [
                                    "job_id",
                                    "duration_ms"
                                ],
                                "properties": {
                                    "job_id": {
                                        "type": "integer"
                                    },
                                    "duration_ms": {
                                        "type": "integer"
                                    }
                                }
                            }
                        }
                    }
                },
                "MACOS": {
                    "type": "object",
                    "required": [
                        "total_ms",
                        "jobs"
                    ],
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        },
                        "jobs": {
                            "type": "integer"
                        },
                        "job_runs": {
                            "type": "array",
                            "items": {
                                "type": "object",
                                "required": [
                                    "job_id",
                                    "duration_ms"
                                ],
                                "properties": {
                                    "job_id": {
                                        "type": "integer"
                                    },
                                    "duration_ms": {
                                        "type": "integer"
                                    }
                                }
                            }
                        }
                    }
                },
                "WINDOWS": {
                    "type": "object",
                    "required": [
                        "total_ms",
                        "jobs"
                    ],
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        },
                        "jobs": {
                            "type": "integer"
                        },
                        "job_runs": {
                            "type": "array",
                            "items": {
                                "type": "object",
                                "required": [
                                    "job_id",
                                    "duration_ms"
                                ],
                                "properties": {
                                    "job_id": {
                                        "type": "integer"
                                    },
                                    "duration_ms": {
                                        "type": "integer"
                                    }
                                }
                            }
                        }
                    }
                }
            }
        },
        "run_duration_ms": {
            "type": "integer"
        }
    },
    "required": [
        "billable"
    ]
}
```

### `#/components/examples/workflow-run-usage`

```json
{
    "value": {
        "billable": {
            "UBUNTU": {
                "total_ms": 180000,
                "jobs": 1,
                "job_runs": [
                    {
                        "job_id": 1,
                        "duration_ms": 180000
                    }
                ]
            },
            "MACOS": {
                "total_ms": 240000,
                "jobs": 4,
                "job_runs": [
                    {
                        "job_id": 2,
                        "duration_ms": 60000
                    },
                    {
                        "job_id": 3,
                        "duration_ms": 60000
                    },
                    {
                        "job_id": 4,
                        "duration_ms": 60000
                    },
                    {
                        "job_id": 5,
                        "duration_ms": 60000
                    }
                ]
            },
            "WINDOWS": {
                "total_ms": 300000,
                "jobs": 2,
                "job_runs": [
                    {
                        "job_id": 6,
                        "duration_ms": 150000
                    },
                    {
                        "job_id": 7,
                        "duration_ms": 150000
                    }
                ]
            }
        },
        "run_duration_ms": 500000
    }
}
```