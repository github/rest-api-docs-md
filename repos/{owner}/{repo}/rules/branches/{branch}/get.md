# Get rules for a branch

Returns all active rules that apply to the specified branch. The branch does not need to exist; rules that would apply
to a branch with that name will be returned. All active rules that apply will be returned, regardless of the level
at which they are configured (e.g. repository or organization). Rules in rulesets with "evaluate" or "disabled"
enforcement statuses are not returned.

## Operation Object

```json
{
    "summary": "Get rules for a branch",
    "description": "Returns all active rules that apply to the specified branch. The branch does not need to exist; rules that would apply\nto a branch with that name will be returned. All active rules that apply will be returned, regardless of the level\nat which they are configured (e.g. repository or organization). Rules in rulesets with \"evaluate\" or \"disabled\"\nenforcement statuses are not returned.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-branch-rules",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/rules#get-rules-for-a-branch"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/branch"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/repository-rule-detailed"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repository-rule-items"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "rules"
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

### `#/components/parameters/branch`

```json
{
    "name": "branch",
    "description": "The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
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

### `#/components/schemas/repository-rule-detailed`

```json
{
    "title": "Repository Rule",
    "type": "object",
    "description": "A repository rule with ruleset details.",
    "oneOf": [
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-creation"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-update"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-deletion"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-required-linear-history"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-required-deployments"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-required-signatures"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-pull-request"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-required-status-checks"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-non-fast-forward"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-commit-message-pattern"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-commit-author-email-pattern"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-committer-email-pattern"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-branch-name-pattern"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-tag-name-pattern"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-workflows"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        },
        {
            "allOf": [
                {
                    "$ref": "#/components/schemas/repository-rule-code-scanning"
                },
                {
                    "$ref": "#/components/schemas/repository-rule-ruleset-info"
                }
            ]
        }
    ]
}
```

### `#/components/examples/repository-rule-items`

```json
{
    "value": [
        {
            "type": "commit_message_pattern",
            "ruleset_source_type": "Repository",
            "ruleset_source": "monalisa/my-repo",
            "ruleset_id": 42,
            "parameters": {
                "operator": "starts_with",
                "pattern": "issue"
            }
        },
        {
            "type": "commit_author_email_pattern",
            "ruleset_source_type": "Organization",
            "ruleset_source": "my-org",
            "ruleset_id": 73,
            "parameters": {
                "operator": "contains",
                "pattern": "github"
            }
        }
    ]
}
```