# Get GitHub Actions billing for an organization

`get /orgs/{org}/settings/billing/actions`

Gets the summary of the free and paid GitHub Actions minutes used.

Paid minutes only apply to workflows in private repositories that use GitHub-hosted runners. Minutes used is listed for each GitHub-hosted runner operating system. Any job re-runs are also included in the usage. The usage returned includes any minute multipliers for macOS and Windows runners, and is rounded up to the nearest whole minute. For more information, see "[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)".

OAuth app tokens and personal access tokens (classic) need the `repo` or `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Actions billing for an organization",
    "description": "Gets the summary of the free and paid GitHub Actions minutes used.\n\nPaid minutes only apply to workflows in private repositories that use GitHub-hosted runners. Minutes used is listed for each GitHub-hosted runner operating system. Any job re-runs are also included in the usage. The usage returned includes any minute multipliers for macOS and Windows runners, and is rounded up to the nearest whole minute. For more information, see \"[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)\".\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `admin:org` scope to use this endpoint.",
    "operationId": "billing/get-github-actions-billing-org",
    "tags": [
        "billing"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/billing/billing#get-github-actions-billing-for-an-organization"
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
                        "$ref": "#/components/schemas/actions-billing-usage"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-billing-usage"
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

### `#/components/schemas/actions-billing-usage`

```json
{
    "type": "object",
    "properties": {
        "total_minutes_used": {
            "type": "integer",
            "description": "The sum of the free and paid GitHub Actions minutes used."
        },
        "total_paid_minutes_used": {
            "type": "integer",
            "description": "The total paid GitHub Actions minutes used."
        },
        "included_minutes": {
            "type": "integer",
            "description": "The amount of free GitHub Actions minutes available."
        },
        "minutes_used_breakdown": {
            "type": "object",
            "properties": {
                "UBUNTU": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu runner machines."
                },
                "MACOS": {
                    "type": "integer",
                    "description": "Total minutes used on macOS runner machines."
                },
                "WINDOWS": {
                    "type": "integer",
                    "description": "Total minutes used on Windows runner machines."
                },
                "ubuntu_4_core": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu 4 core runner machines."
                },
                "ubuntu_8_core": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu 8 core runner machines."
                },
                "ubuntu_16_core": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu 16 core runner machines."
                },
                "ubuntu_32_core": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu 32 core runner machines."
                },
                "ubuntu_64_core": {
                    "type": "integer",
                    "description": "Total minutes used on Ubuntu 64 core runner machines."
                },
                "windows_4_core": {
                    "type": "integer",
                    "description": "Total minutes used on Windows 4 core runner machines."
                },
                "windows_8_core": {
                    "type": "integer",
                    "description": "Total minutes used on Windows 8 core runner machines."
                },
                "windows_16_core": {
                    "type": "integer",
                    "description": "Total minutes used on Windows 16 core runner machines."
                },
                "windows_32_core": {
                    "type": "integer",
                    "description": "Total minutes used on Windows 32 core runner machines."
                },
                "windows_64_core": {
                    "type": "integer",
                    "description": "Total minutes used on Windows 64 core runner machines."
                },
                "macos_12_core": {
                    "type": "integer",
                    "description": "Total minutes used on macOS 12 core runner machines."
                },
                "total": {
                    "type": "integer",
                    "description": "Total minutes used on all runner machines."
                }
            }
        }
    },
    "required": [
        "total_minutes_used",
        "total_paid_minutes_used",
        "included_minutes",
        "minutes_used_breakdown"
    ]
}
```

### `#/components/examples/actions-billing-usage`

```json
{
    "value": {
        "total_minutes_used": 305,
        "total_paid_minutes_used": 0,
        "included_minutes": 3000,
        "minutes_used_breakdown": {
            "UBUNTU": 205,
            "MACOS": 10,
            "WINDOWS": 90
        }
    }
}
```