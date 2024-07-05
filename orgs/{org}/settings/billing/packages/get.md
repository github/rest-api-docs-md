# Get GitHub Packages billing for an organization

Gets the free and paid storage used for GitHub Packages in gigabytes.

Paid minutes only apply to packages stored for private repositories. For more information, see "[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages)."

OAuth app tokens and personal access tokens (classic) need the `repo` or `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Packages billing for an organization",
    "description": "Gets the free and paid storage used for GitHub Packages in gigabytes.\n\nPaid minutes only apply to packages stored for private repositories. For more information, see \"[Managing billing for GitHub Packages](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-packages).\"\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `admin:org` scope to use this endpoint.",
    "operationId": "billing/get-github-packages-billing-org",
    "tags": [
        "billing"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/billing/billing#get-github-packages-billing-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/packages-billing-usage"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/packages-billing-usage"
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

### `#/components/schemas/packages-billing-usage`

```json
{
    "type": "object",
    "properties": {
        "total_gigabytes_bandwidth_used": {
            "type": "integer",
            "description": "Sum of the free and paid storage space (GB) for GitHuub Packages."
        },
        "total_paid_gigabytes_bandwidth_used": {
            "type": "integer",
            "description": "Total paid storage space (GB) for GitHuub Packages."
        },
        "included_gigabytes_bandwidth": {
            "type": "integer",
            "description": "Free storage space (GB) for GitHub Packages."
        }
    },
    "required": [
        "total_gigabytes_bandwidth_used",
        "total_paid_gigabytes_bandwidth_used",
        "included_gigabytes_bandwidth"
    ]
}
```

### `#/components/examples/packages-billing-usage`

```json
{
    "value": {
        "total_gigabytes_bandwidth_used": 50,
        "total_paid_gigabytes_bandwidth_used": 40,
        "included_gigabytes_bandwidth": 10
    }
}
```