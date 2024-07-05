# Get a summary of Copilot usage for organization members

`get /orgs/{org}/copilot/usage`

**Note**: This endpoint is in beta and is subject to change.

You can use this endpoint to see a daily breakdown of aggregated usage metrics for Copilot completions and Copilot Chat in the IDE
across an organization, with a further breakdown of suggestions, acceptances, and number of active users by editor and language for each day.
See the response schema tab for detailed metrics definitions.

The response contains metrics for the prior 28 days. Usage metrics are processed once per day for the previous day,
and the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,
they must have telemetry enabled in their IDE.

Organization owners, and owners and billing managers of the parent enterprise, can view Copilot usage metrics.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot`, `read:org`, or `read:enterprise` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a summary of Copilot usage for organization members",
    "description": "**Note**: This endpoint is in beta and is subject to change.\n\nYou can use this endpoint to see a daily breakdown of aggregated usage metrics for Copilot completions and Copilot Chat in the IDE\nacross an organization, with a further breakdown of suggestions, acceptances, and number of active users by editor and language for each day.\nSee the response schema tab for detailed metrics definitions.\n\nThe response contains metrics for the prior 28 days. Usage metrics are processed once per day for the previous day,\nand the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,\nthey must have telemetry enabled in their IDE.\n\nOrganization owners, and owners and billing managers of the parent enterprise, can view Copilot usage metrics.\n\nOAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot`, `read:org`, or `read:enterprise` scopes to use this endpoint.",
    "tags": [
        "copilot"
    ],
    "operationId": "copilot/usage-metrics-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/copilot/copilot-usage#get-a-summary-of-copilot-usage-for-organization-members"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                            "$ref": "#/components/examples/copilot-usage-metrics-org"
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

### `#/components/examples/copilot-usage-metrics-org`

```json
{
    "value": [
        {
            "day": "2023-10-15",
            "total_suggestions_count": 1000,
            "total_acceptances_count": 800,
            "total_lines_suggested": 1800,
            "total_lines_accepted": 1200,
            "total_active_users": 10,
            "total_chat_acceptances": 32,
            "total_chat_turns": 200,
            "total_active_chat_users": 4,
            "breakdown": [
                {
                    "language": "python",
                    "editor": "vscode",
                    "suggestions_count": 300,
                    "acceptances_count": 250,
                    "lines_suggested": 900,
                    "lines_accepted": 700,
                    "active_users": 5
                },
                {
                    "language": "python",
                    "editor": "jetbrains",
                    "suggestions_count": 300,
                    "acceptances_count": 200,
                    "lines_suggested": 400,
                    "lines_accepted": 300,
                    "active_users": 2
                },
                {
                    "language": "ruby",
                    "editor": "vscode",
                    "suggestions_count": 400,
                    "acceptances_count": 350,
                    "lines_suggested": 500,
                    "lines_accepted": 200,
                    "active_users": 3
                }
            ]
        },
        {
            "day": "2023-10-16",
            "total_suggestions_count": 800,
            "total_acceptances_count": 600,
            "total_lines_suggested": 1100,
            "total_lines_accepted": 700,
            "total_active_users": 12,
            "total_chat_acceptances": 57,
            "total_chat_turns": 426,
            "total_active_chat_users": 8,
            "breakdown": [
                {
                    "language": "python",
                    "editor": "vscode",
                    "suggestions_count": 300,
                    "acceptances_count": 200,
                    "lines_suggested": 600,
                    "lines_accepted": 300,
                    "active_users": 2
                },
                {
                    "language": "python",
                    "editor": "jetbrains",
                    "suggestions_count": 300,
                    "acceptances_count": 150,
                    "lines_suggested": 300,
                    "lines_accepted": 250,
                    "active_users": 6
                },
                {
                    "language": "ruby",
                    "editor": "vscode",
                    "suggestions_count": 200,
                    "acceptances_count": 150,
                    "lines_suggested": 200,
                    "lines_accepted": 150,
                    "active_users": 3
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