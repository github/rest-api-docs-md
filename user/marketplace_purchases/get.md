# List subscriptions for the authenticated user

Lists the active subscriptions for the authenticated user.

## Operation Object

```json
{
    "summary": "List subscriptions for the authenticated user",
    "description": "Lists the active subscriptions for the authenticated user.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-subscriptions-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/marketplace#list-subscriptions-for-the-authenticated-user"
    },
    "parameters": [
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
                            "$ref": "#/components/schemas/user-marketplace-purchase"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/user-marketplace-purchase-items"
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
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "apps",
        "subcategory": "marketplace"
    }
}
```

## References

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

### `#/components/schemas/user-marketplace-purchase`

```json
{
    "title": "User Marketplace Purchase",
    "description": "User Marketplace Purchase",
    "type": "object",
    "properties": {
        "billing_cycle": {
            "type": "string",
            "example": "monthly"
        },
        "next_billing_date": {
            "type": "string",
            "format": "date-time",
            "example": "2017-11-11T00:00:00Z",
            "nullable": true
        },
        "unit_count": {
            "type": "integer",
            "nullable": true
        },
        "on_free_trial": {
            "type": "boolean",
            "example": true
        },
        "free_trial_ends_on": {
            "type": "string",
            "format": "date-time",
            "example": "2017-11-11T00:00:00Z",
            "nullable": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-11-02T01:12:12Z",
            "nullable": true
        },
        "account": {
            "$ref": "#/components/schemas/marketplace-account"
        },
        "plan": {
            "$ref": "#/components/schemas/marketplace-listing-plan"
        }
    },
    "required": [
        "billing_cycle",
        "next_billing_date",
        "unit_count",
        "updated_at",
        "on_free_trial",
        "free_trial_ends_on",
        "account",
        "plan"
    ]
}
```

### `#/components/examples/user-marketplace-purchase-items`

```json
{
    "value": [
        {
            "billing_cycle": "monthly",
            "next_billing_date": "2017-11-11T00:00:00Z",
            "unit_count": null,
            "on_free_trial": true,
            "free_trial_ends_on": "2017-11-11T00:00:00Z",
            "updated_at": "2017-11-02T01:12:12Z",
            "account": {
                "login": "github",
                "id": 4,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
                "url": "https://api.github.com/orgs/github",
                "email": null,
                "organization_billing_email": "billing@github.com",
                "type": "Organization"
            },
            "plan": {
                "url": "https://api.github.com/marketplace_listing/plans/1313",
                "accounts_url": "https://api.github.com/marketplace_listing/plans/1313/accounts",
                "id": 1313,
                "number": 3,
                "name": "Pro",
                "description": "A professional-grade CI solution",
                "monthly_price_in_cents": 1099,
                "yearly_price_in_cents": 11870,
                "price_model": "FLAT_RATE",
                "has_free_trial": true,
                "unit_name": null,
                "state": "published",
                "bullets": [
                    "Up to 25 private repositories",
                    "11 concurrent builds"
                ]
            }
        }
    ]
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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