# Get all organization repository rulesets

`get /orgs/{org}/rulesets`

Get all the repository rulesets for an organization.

## Operation Object

```json
{
    "summary": "Get all organization repository rulesets",
    "description": "Get all the repository rulesets for an organization.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-org-rulesets",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/rules#get-all-organization-repository-rulesets"
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "rules"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                            "$ref": "#/components/schemas/repository-ruleset"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-ruleset-items"
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

### `#/components/schemas/repository-ruleset`

```json
{
    "title": "Repository ruleset",
    "type": "object",
    "description": "A set of rules to apply when specified conditions are met.",
    "required": [
        "id",
        "name",
        "source",
        "enforcement"
    ],
    "properties": {
        "id": {
            "type": "integer",
            "description": "The ID of the ruleset"
        },
        "name": {
            "type": "string",
            "description": "The name of the ruleset"
        },
        "target": {
            "type": "string",
            "description": "The target of the ruleset\n\n**Note**: The `push` target is in beta and is subject to change.",
            "enum": [
                "branch",
                "tag",
                "push"
            ]
        },
        "source_type": {
            "type": "string",
            "description": "The type of the source of the ruleset",
            "enum": [
                "Repository",
                "Organization"
            ]
        },
        "source": {
            "type": "string",
            "description": "The name of the source"
        },
        "enforcement": {
            "$ref": "#/components/schemas/repository-rule-enforcement"
        },
        "bypass_actors": {
            "type": "array",
            "description": "The actors that can bypass the rules in this ruleset",
            "items": {
                "$ref": "#/components/schemas/repository-ruleset-bypass-actor"
            }
        },
        "current_user_can_bypass": {
            "type": "string",
            "description": "The bypass type of the user making the API request for this ruleset. This field is only returned when\nquerying the repository-level endpoint.",
            "enum": [
                "always",
                "pull_requests_only",
                "never"
            ]
        },
        "node_id": {
            "type": "string"
        },
        "_links": {
            "type": "object",
            "properties": {
                "self": {
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string",
                            "description": "The URL of the ruleset"
                        }
                    }
                },
                "html": {
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string",
                            "description": "The html URL of the ruleset"
                        }
                    }
                }
            }
        },
        "conditions": {
            "nullable": true,
            "anyOf": [
                {
                    "$ref": "#/components/schemas/repository-ruleset-conditions"
                },
                {
                    "$ref": "#/components/schemas/org-ruleset-conditions"
                }
            ]
        },
        "rules": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/repository-rule"
            }
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    }
}
```

### `#/components/examples/org-ruleset-items`

```json
{
    "value": [
        {
            "id": 21,
            "name": "super cool ruleset",
            "source_type": "Organization",
            "source": "my-org",
            "enforcement": "enabled",
            "node_id": "RRS_lACkVXNlcgQB",
            "_links": {
                "self": {
                    "href": "https://api.github.com/orgs/my-org/rulesets/21"
                },
                "html": {
                    "href": "https://github.com/organizations/my-org/settings/rules/21"
                }
            },
            "created_at": "2023-07-15T08:43:03Z",
            "updated_at": "2023-08-23T16:29:47Z"
        },
        {
            "id": 432,
            "name": "Another ruleset",
            "source_type": "Organization",
            "source": "my-org",
            "enforcement": "enabled",
            "node_id": "RRS_lACkVXNlcgQQ",
            "_links": {
                "self": {
                    "href": "https://api.github.com/orgs/my-org/rulesets/432"
                },
                "html": {
                    "href": "https://github.com/organizations/my-org/settings/rules/432"
                }
            },
            "created_at": "2023-08-15T08:43:03Z",
            "updated_at": "2023-09-23T16:29:47Z"
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