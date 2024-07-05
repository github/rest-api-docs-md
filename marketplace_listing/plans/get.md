# List plans

Lists all plans that are part of your GitHub Marketplace listing.

GitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.

## Operation Object

```json
{
    "summary": "List plans",
    "description": "Lists all plans that are part of your GitHub Marketplace listing.\n\nGitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-plans",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/marketplace#list-plans"
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
                            "$ref": "#/components/schemas/marketplace-listing-plan"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/marketplace-listing-plan-items"
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
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
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

### `#/components/schemas/marketplace-listing-plan`

```json
{
    "title": "Marketplace Listing Plan",
    "description": "Marketplace Listing Plan",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/marketplace_listing/plans/1313"
        },
        "accounts_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/marketplace_listing/plans/1313/accounts"
        },
        "id": {
            "type": "integer",
            "example": 1313
        },
        "number": {
            "type": "integer",
            "example": 3
        },
        "name": {
            "type": "string",
            "example": "Pro"
        },
        "description": {
            "type": "string",
            "example": "A professional-grade CI solution"
        },
        "monthly_price_in_cents": {
            "type": "integer",
            "example": 1099
        },
        "yearly_price_in_cents": {
            "type": "integer",
            "example": 11870
        },
        "price_model": {
            "type": "string",
            "enum": [
                "FREE",
                "FLAT_RATE",
                "PER_UNIT"
            ],
            "example": "FLAT_RATE"
        },
        "has_free_trial": {
            "type": "boolean",
            "example": true
        },
        "unit_name": {
            "type": "string",
            "nullable": true
        },
        "state": {
            "type": "string",
            "example": "published"
        },
        "bullets": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "Up to 25 private repositories",
                "11 concurrent builds"
            ]
        }
    },
    "required": [
        "url",
        "accounts_url",
        "id",
        "number",
        "name",
        "description",
        "has_free_trial",
        "price_model",
        "unit_name",
        "monthly_price_in_cents",
        "state",
        "yearly_price_in_cents",
        "bullets"
    ]
}
```

### `#/components/examples/marketplace-listing-plan-items`

```json
{
    "value": [
        {
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