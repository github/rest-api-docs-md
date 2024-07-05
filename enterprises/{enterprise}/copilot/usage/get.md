# Get a summary of Copilot usage for enterprise members

`get /enterprises/{enterprise}/copilot/usage`

**Note**: This endpoint is in beta and is subject to change.

You can use this endpoint to see a daily breakdown of aggregated usage metrics for Copilot completions and Copilot Chat in the IDE
for all users across organizations with access to Copilot within your enterprise, with a further breakdown of suggestions, acceptances,
and number of active users by editor and language for each day. See the response schema tab for detailed metrics definitions.

The response contains metrics for the prior 28 days. Usage metrics are processed once per day for the previous day,
and the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,
they must have telemetry enabled in their IDE.

Only owners and billing managers can view Copilot usage metrics for the enterprise.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:enterprise` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a summary of Copilot usage for enterprise members",
    "description": "**Note**: This endpoint is in beta and is subject to change.\n\nYou can use this endpoint to see a daily breakdown of aggregated usage metrics for Copilot completions and Copilot Chat in the IDE\nfor all users across organizations with access to Copilot within your enterprise, with a further breakdown of suggestions, acceptances,\nand number of active users by editor and language for each day. See the response schema tab for detailed metrics definitions.\n\nThe response contains metrics for the prior 28 days. Usage metrics are processed once per day for the previous day,\nand the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,\nthey must have telemetry enabled in their IDE.\n\nOnly owners and billing managers can view Copilot usage metrics for the enterprise.\n\nOAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:enterprise` scopes to use this endpoint.",
    "tags": [
        "copilot"
    ],
    "operationId": "copilot/usage-metrics-for-enterprise",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/copilot/copilot-usage#get-a-summary-of-copilot-usage-for-enterprise-members"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/enterprise"
        },
        {
            "name": "since",
            "description": "Show usage metrics since this date. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDTHH:MM:SSZ`). Maximum value is 28 days ago.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "until",
            "description": "Show usage metrics until this date. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDTHH:MM:SSZ`) and should not preceed the `since` date if it is passed.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "name": "per_page",
            "description": "The number of days of metrics to display per page (max 28). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 28
            }
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
                            "$ref": "#/components/schemas/copilot-usage-metrics"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/copilot-usage-metrics-enterprise"
                        }
                    }
                }
            }
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "copilot",
        "subcategory": "copilot-usage"
    }
}
```

## References

### `#/components/parameters/enterprise`

```json
{
    "name": "enterprise",
    "description": "The slug version of the enterprise name. You can also substitute this value with the enterprise id.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
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

### `#/components/schemas/copilot-usage-metrics`

```json
{
    "title": "Copilot Usage Metrics",
    "description": "Summary of Copilot usage.",
    "type": "object",
    "properties": {
        "day": {
            "type": "string",
            "format": "date",
            "description": "The date for which the usage metrics are reported, in `YYYY-MM-DD` format."
        },
        "total_suggestions_count": {
            "type": "integer",
            "description": "The total number of Copilot code completion suggestions shown to users."
        },
        "total_acceptances_count": {
            "type": "integer",
            "description": "The total number of Copilot code completion suggestions accepted by users."
        },
        "total_lines_suggested": {
            "type": "integer",
            "description": "The total number of lines of code completions suggested by Copilot."
        },
        "total_lines_accepted": {
            "type": "integer",
            "description": "The total number of lines of code completions accepted by users."
        },
        "total_active_users": {
            "type": "integer",
            "description": "The total number of users who were shown Copilot code completion suggestions during the day specified."
        },
        "total_chat_acceptances": {
            "type": "integer",
            "description": "The total instances of users who accepted code suggested by Copilot Chat in the IDE (panel and inline)."
        },
        "total_chat_turns": {
            "type": "integer",
            "description": "The total number of chat turns (prompt and response pairs) sent between users and Copilot Chat in the IDE."
        },
        "total_active_chat_users": {
            "type": "integer",
            "description": "The total number of users who interacted with Copilot Chat in the IDE during the day specified."
        },
        "breakdown": {
            "type": "array",
            "description": "Breakdown of Copilot code completions usage by language and editor",
            "nullable": true,
            "items": {
                "type": "object",
                "description": "Breakdown of Copilot usage by editor for this language",
                "additionalProperties": true,
                "properties": {
                    "language": {
                        "type": "string",
                        "description": "The language in which Copilot suggestions were shown to users in the specified editor."
                    },
                    "editor": {
                        "type": "string",
                        "description": "The editor in which Copilot suggestions were shown to users for the specified language."
                    },
                    "suggestions_count": {
                        "type": "integer",
                        "description": "The number of Copilot suggestions shown to users in the editor specified during the day specified."
                    },
                    "acceptances_count": {
                        "type": "integer",
                        "description": "The number of Copilot suggestions accepted by users in the editor specified during the day specified."
                    },
                    "lines_suggested": {
                        "type": "integer",
                        "description": "The number of lines of code suggested by Copilot in the editor specified during the day specified."
                    },
                    "lines_accepted": {
                        "type": "integer",
                        "description": "The number of lines of code accepted by users in the editor specified during the day specified."
                    },
                    "active_users": {
                        "type": "integer",
                        "description": "The number of users who were shown Copilot completion suggestions in the editor specified during the day specified."
                    }
                }
            }
        }
    },
    "required": [
        "day",
        "breakdown"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/copilot-usage-metrics-enterprise`

```json
{
    "value": [
        {
            "day": "2023-10-15",
            "total_suggestions_count": 5000,
            "total_acceptances_count": 3000,
            "total_lines_suggested": 7000,
            "total_lines_accepted": 3500,
            "total_active_users": 15,
            "total_chat_acceptances": 45,
            "total_chat_turns": 350,
            "total_active_chat_users": 8,
            "breakdown": [
                {
                    "language": "python",
                    "editor": "vscode",
                    "suggestions_count": 3000,
                    "acceptances_count": 2000,
                    "lines_suggested": 3000,
                    "lines_accepted": 1500,
                    "active_users": 5
                },
                {
                    "language": "python",
                    "editor": "jetbrains",
                    "suggestions_count": 1000,
                    "acceptances_count": 500,
                    "lines_suggested": 2000,
                    "lines_accepted": 1000,
                    "active_users": 5
                },
                {
                    "language": "javascript",
                    "editor": "vscode",
                    "suggestions_count": 1000,
                    "acceptances_count": 500,
                    "lines_suggested": 2000,
                    "lines_accepted": 1000,
                    "active_users": 5
                }
            ]
        },
        {
            "day": "2023-10-16",
            "total_suggestions_count": 5200,
            "total_acceptances_count": 5100,
            "total_lines_suggested": 5300,
            "total_lines_accepted": 5000,
            "total_active_users": 15,
            "total_chat_acceptances": 57,
            "total_chat_turns": 455,
            "total_active_chat_users": 12,
            "breakdown": [
                {
                    "language": "python",
                    "editor": "vscode",
                    "suggestions_count": 3100,
                    "acceptances_count": 3000,
                    "lines_suggested": 3200,
                    "lines_accepted": 3100,
                    "active_users": 5
                },
                {
                    "language": "python",
                    "editor": "jetbrains",
                    "suggestions_count": 1100,
                    "acceptances_count": 1000,
                    "lines_suggested": 1200,
                    "lines_accepted": 1100,
                    "active_users": 5
                },
                {
                    "language": "javascript",
                    "editor": "vscode",
                    "suggestions_count": 1000,
                    "acceptances_count": 900,
                    "lines_suggested": 1100,
                    "lines_accepted": 1000,
                    "active_users": 5
                }
            ]
        }
    ]
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

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
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