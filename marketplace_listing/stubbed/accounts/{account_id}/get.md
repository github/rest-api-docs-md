# Get a subscription plan for an account (stubbed)

`get /marketplace_listing/stubbed/accounts/{account_id}`

Shows whether the user or organization account actively subscribes to a plan listed by the authenticated GitHub App. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.

GitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.

## Operation Object

```json
{
    "summary": "Get a subscription plan for an account (stubbed)",
    "description": "Shows whether the user or organization account actively subscribes to a plan listed by the authenticated GitHub App. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.\n\nGitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/get-subscription-plan-for-account-stubbed",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/marketplace#get-a-subscription-plan-for-an-account-stubbed"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/account-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/marketplace-purchase"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/marketplace-purchase"
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Not Found when the account has not purchased the listing"
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

### `#/components/parameters/account-id`

```json
{
    "name": "account_id",
    "description": "account_id parameter",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/marketplace-purchase`

```json
{
    "title": "Marketplace Purchase",
    "description": "Marketplace Purchase",
    "type": "object",
    "properties": {
        "url": {
            "type": "string"
        },
        "type": {
            "type": "string"
        },
        "id": {
            "type": "integer"
        },
        "login": {
            "type": "string"
        },
        "organization_billing_email": {
            "type": "string"
        },
        "email": {
            "type": "string",
            "nullable": true
        },
        "marketplace_pending_change": {
            "type": "object",
            "properties": {
                "is_installed": {
                    "type": "boolean"
                },
                "effective_date": {
                    "type": "string"
                },
                "unit_count": {
                    "type": "integer",
                    "nullable": true
                },
                "id": {
                    "type": "integer"
                },
                "plan": {
                    "$ref": "#/components/schemas/marketplace-listing-plan"
                }
            },
            "nullable": true
        },
        "marketplace_purchase": {
            "type": "object",
            "properties": {
                "billing_cycle": {
                    "type": "string"
                },
                "next_billing_date": {
                    "type": "string",
                    "nullable": true
                },
                "is_installed": {
                    "type": "boolean"
                },
                "unit_count": {
                    "type": "integer",
                    "nullable": true
                },
                "on_free_trial": {
                    "type": "boolean"
                },
                "free_trial_ends_on": {
                    "type": "string",
                    "nullable": true
                },
                "updated_at": {
                    "type": "string"
                },
                "plan": {
                    "$ref": "#/components/schemas/marketplace-listing-plan"
                }
            }
        }
    },
    "required": [
        "url",
        "id",
        "type",
        "login",
        "marketplace_purchase"
    ]
}
```

### `#/components/examples/marketplace-purchase`

```json
{
    "value": {
        "url": "https://api.github.com/orgs/github",
        "type": "Organization",
        "id": 4,
        "login": "github",
        "organization_billing_email": "billing@github.com",
        "email": "billing@github.com",
        "marketplace_pending_change": {
            "effective_date": "2017-11-11T00:00:00Z",
            "unit_count": null,
            "id": 77,
            "plan": {
                "url": "https://api.github.com/marketplace_listing/plans/1111",
                "accounts_url": "https://api.github.com/marketplace_listing/plans/1111/accounts",
                "id": 1111,
                "number": 2,
                "name": "Startup",
                "description": "A professional-grade CI solution",
                "monthly_price_in_cents": 699,
                "yearly_price_in_cents": 7870,
                "price_model": "FLAT_RATE",
                "has_free_trial": true,
                "state": "published",
                "unit_name": null,
                "bullets": [
                    "Up to 10 private repositories",
                    "3 concurrent builds"
                ]
            }
        },
        "marketplace_purchase": {
            "billing_cycle": "monthly",
            "next_billing_date": "2017-11-11T00:00:00Z",
            "unit_count": null,
            "on_free_trial": true,
            "free_trial_ends_on": "2017-11-11T00:00:00Z",
            "updated_at": "2017-11-02T01:12:12Z",
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