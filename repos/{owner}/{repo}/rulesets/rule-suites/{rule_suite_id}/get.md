# Get a repository rule suite

Gets information about a suite of rule evaluations from within a repository.
For more information, see "[Managing rulesets for a repository](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-insights-for-rulesets)."

## Operation Object

```json
{
    "summary": "Get a repository rule suite",
    "description": "Gets information about a suite of rule evaluations from within a repository.\nFor more information, see \"[Managing rulesets for a repository](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-insights-for-rulesets).\"",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-repo-rule-suite",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/rule-suites#get-a-repository-rule-suite"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/rule-suite-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/rule-suite"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/rule-suite"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "rule-suites"
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

### `#/components/parameters/rule-suite-id`

```json
{
    "name": "rule_suite_id",
    "description": "The unique identifier of the rule suite result.\nTo get this ID, you can use [GET /repos/{owner}/{repo}/rulesets/rule-suites](https://docs.github.com/rest/repos/rule-suites#list-repository-rule-suites)\nfor repositories and [GET /orgs/{org}/rulesets/rule-suites](https://docs.github.com/rest/orgs/rule-suites#list-organization-rule-suites)\nfor organizations.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/rule-suite`

```json
{
    "title": "Rule Suite",
    "description": "Response",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "description": "The unique identifier of the rule insight."
        },
        "actor_id": {
            "type": "integer",
            "description": "The number that identifies the user.",
            "nullable": true
        },
        "actor_name": {
            "type": "string",
            "description": "The handle for the GitHub user account.",
            "nullable": true
        },
        "before_sha": {
            "type": "string",
            "description": "The first commit sha before the push evaluation."
        },
        "after_sha": {
            "type": "string",
            "description": "The last commit sha in the push evaluation."
        },
        "ref": {
            "type": "string",
            "description": "The ref name that the evaluation ran on."
        },
        "repository_id": {
            "type": "integer",
            "description": "The ID of the repository associated with the rule evaluation."
        },
        "repository_name": {
            "type": "string",
            "description": "The name of the repository without the `.git` extension."
        },
        "pushed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:06:43Z"
        },
        "result": {
            "type": "string",
            "enum": [
                "pass",
                "fail",
                "bypass"
            ],
            "description": "The result of the rule evaluations for rules with the `active` enforcement status."
        },
        "evaluation_result": {
            "type": "string",
            "enum": [
                "pass",
                "fail"
            ],
            "description": "The result of the rule evaluations for rules with the `active` and `evaluate` enforcement statuses, demonstrating whether rules would pass or fail if all rules in the rule suite were `active`."
        },
        "rule_evaluations": {
            "type": "array",
            "description": "Details on the evaluated rules.",
            "items": {
                "type": "object",
                "properties": {
                    "rule_source": {
                        "type": "object",
                        "properties": {
                            "type": {
                                "type": "string",
                                "description": "The type of rule source."
                            },
                            "id": {
                                "type": "integer",
                                "nullable": true,
                                "description": "The ID of the rule source."
                            },
                            "name": {
                                "type": "string",
                                "nullable": true,
                                "description": "The name of the rule source."
                            }
                        }
                    },
                    "enforcement": {
                        "type": "string",
                        "enum": [
                            "active",
                            "evaluate",
                            "deleted ruleset"
                        ],
                        "description": "The enforcement level of this rule source."
                    },
                    "result": {
                        "type": "string",
                        "enum": [
                            "pass",
                            "fail"
                        ],
                        "description": "The result of the evaluation of the individual rule."
                    },
                    "rule_type": {
                        "type": "string",
                        "description": "The type of rule."
                    },
                    "details": {
                        "type": "string",
                        "description": "Any associated details with the rule evaluation."
                    }
                }
            }
        }
    }
}
```

### `#/components/examples/rule-suite`

```json
{
    "value": {
        "id": 21,
        "actor_id": 12,
        "username": "octocat",
        "before_sha": "893f768e172fb1bc9c5d6f3dd48557e45f14e01d",
        "after_sha": "dedd88641a362b6b4ea872da4847d6131a164d01",
        "ref": "refs/heads/i-see-everything",
        "repository_id": 404,
        "repository_name": "octo-repo",
        "pushed_at": "2023-07-06T08:43:03Z",
        "result": "bypass",
        "evaluation_result": "fail",
        "rule_evaluations": [
            {
                "rule_source": {
                    "type": "ruleset",
                    "id": 2,
                    "name": "Author email must be a GitHub email address"
                },
                "enforcement": "active",
                "result": "pass",
                "rule_type": "commit_author_email_pattern"
            },
            {
                "rule_source": {
                    "type": "protected_branch"
                },
                "enforcement": "active",
                "result": "fail",
                "rule_type": "pull_request",
                "details": "Changes must be made through a pull request."
            },
            {
                "rule_source": {
                    "type": "ruleset",
                    "id": 3,
                    "name": "Evaluate commit message pattern"
                },
                "enforcement": "evaluate",
                "result": "fail",
                "rule_type": "commit_message_pattern"
            }
        ]
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