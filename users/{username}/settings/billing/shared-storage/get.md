# Get shared storage billing for a user

Gets the estimated paid and estimated total storage used for GitHub Actions and GitHub Packages.

Paid minutes only apply to packages stored for private repositories. For more information, see "[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages)."

OAuth app tokens and personal access tokens (classic) need the `user` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get shared storage billing for a user",
    "description": "Gets the estimated paid and estimated total storage used for GitHub Actions and GitHub Packages.\n\nPaid minutes only apply to packages stored for private repositories. For more information, see \"[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages).\"\n\nOAuth app tokens and personal access tokens (classic) need the `user` scope to use this endpoint.",
    "operationId": "billing/get-shared-storage-billing-user",
    "tags": [
        "billing"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/billing/billing#get-shared-storage-billing-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/combined-billing-usage"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/combined-billing-usage"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "billing",
        "subcategory": "billing"
    }
}
```

## References

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/combined-billing-usage`

```json
{
    "type": "object",
    "properties": {
        "days_left_in_billing_cycle": {
            "type": "integer",
            "description": "Numbers of days left in billing cycle."
        },
        "estimated_paid_storage_for_month": {
            "type": "integer",
            "description": "Estimated storage space (GB) used in billing cycle."
        },
        "estimated_storage_for_month": {
            "type": "integer",
            "description": "Estimated sum of free and paid storage space (GB) used in billing cycle."
        }
    },
    "required": [
        "days_left_in_billing_cycle",
        "estimated_paid_storage_for_month",
        "estimated_storage_for_month"
    ]
}
```

### `#/components/examples/combined-billing-usage`

```json
{
    "value": {
        "days_left_in_billing_cycle": 20,
        "estimated_paid_storage_for_month": 15,
        "estimated_storage_for_month": 40
    }
}
```