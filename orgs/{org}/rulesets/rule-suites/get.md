# List organization rule suites

`get /orgs/{org}/rulesets/rule-suites`

Lists suites of rule evaluations at the organization level.
For more information, see "[Managing rulesets for repositories in your organization](https://docs.github.com/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#viewing-insights-for-rulesets)."

## Operation Object

```json
{
    "summary": "List organization rule suites",
    "description": "Lists suites of rule evaluations at the organization level.\nFor more information, see \"[Managing rulesets for repositories in your organization](https://docs.github.com/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#viewing-insights-for-rulesets).\"",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-org-rule-suites",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/rule-suites#list-organization-rule-suites"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/repository-name-in-query"
        },
        {
            "$ref": "#/components/parameters/time-period"
        },
        {
            "$ref": "#/components/parameters/actor-name-in-query"
        },
        {
            "$ref": "#/components/parameters/rule-suite-result"
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
                        "$ref": "#/components/schemas/rule-suites"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/rule-suite-items"
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
        "category": "orgs",
        "subcategory": "rule-suites"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repository-name-in-query`

```json
{
    "name": "repository_name",
    "description": "The name of the repository to filter on. When specified, only rule evaluations from this repository will be returned.",
    "in": "query",
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/time-period`

```json
{
    "name": "time_period",
    "description": "The time period to filter by.\n\nFor example, `day` will filter for rule suites that occurred in the past 24 hours, and `week` will filter for insights that occurred in the past 7 days (168 hours).",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "hour",
            "day",
            "week",
            "month"
        ],
        "default": "day"
    }
}
```

### `#/components/parameters/actor-name-in-query`

```json
{
    "name": "actor_name",
    "description": "The handle for the GitHub user account to filter on. When specified, only rule evaluations triggered by this actor will be returned.",
    "in": "query",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/rule-suite-result`

```json
{
    "name": "rule_suite_result",
    "description": "The rule results to filter on. When specified, only suites with this result will be returned.",
    "in": "query",
    "schema": {
        "type": "string",
        "enum": [
            "pass",
            "fail",
            "bypass",
            "all"
        ],
        "default": "all"
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

### `#/components/schemas/rule-suites`

```json
{
    "title": "Rule Suites",
    "description": "Response",
    "type": "array",
    "items": {
        "type": "object",
        "properties": {
            "id": {
                "type": "integer",
                "description": "The unique identifier of the rule insight."
            },
            "actor_id": {
                "type": "integer",
                "description": "The number that identifies the user."
            },
            "actor_name": {
                "type": "string",
                "description": "The handle for the GitHub user account."
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
            }
        }
    }
}
```

### `#/components/examples/rule-suite-items`

```json
{
    "value": [
        {
            "id": 21,
            "actor_id": 12,
            "username": "octocat",
            "before_sha": "893f768e172fb1bc9c5d6f3dd48557e45f14e01d",
            "after_sha": "dedd88641a362b6b4ea872da4847d6131a164d01",
            "ref": "refs/heads/i-see-everything",
            "repository_id": 404,
            "repository_name": "octo-repo",
            "pushed_at": "2023-07-06T08:43:03Z",
            "result": "bypass"
        },
        {
            "id": 25,
            "actor_id": 11,
            "username": "not-octocat",
            "before_sha": "48994e4e01ccc943624c6231f172702b82b233cc",
            "after_sha": "ecfd5a1025fa271a33ca5608d089476a2df3c9a1",
            "ref": "refs/heads/i-am-everything",
            "repository_id": 404,
            "repository_name": "octo-repo",
            "pushed_at": "2023-07-07T08:43:03Z",
            "result": "pass",
            "evaluation_result": "fail"
        }
    ]
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