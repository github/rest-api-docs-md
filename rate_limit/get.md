# Get rate limit status for the authenticated user

**Note:** Accessing this endpoint does not count against your REST API rate limit.

Some categories of endpoints have custom rate limits that are separate from the rate limit governing the other REST API endpoints. For this reason, the API response categorizes your rate limit. Under `resources`, you'll see objects relating to different categories:
* The `core` object provides your rate limit status for all non-search-related resources in the REST API.
* The `search` object provides your rate limit status for the REST API for searching (excluding code searches). For more information, see "[Search](https://docs.github.com/rest/search/search)."
* The `code_search` object provides your rate limit status for the REST API for searching code. For more information, see "[Search code](https://docs.github.com/rest/search/search#search-code)."
* The `graphql` object provides your rate limit status for the GraphQL API. For more information, see "[Resource limitations](https://docs.github.com/graphql/overview/resource-limitations#rate-limit)."
* The `integration_manifest` object provides your rate limit status for the `POST /app-manifests/{code}/conversions` operation. For more information, see "[Creating a GitHub App from a manifest](https://docs.github.com/apps/creating-github-apps/setting-up-a-github-app/creating-a-github-app-from-a-manifest#3-you-exchange-the-temporary-code-to-retrieve-the-app-configuration)."
* The `dependency_snapshots` object provides your rate limit status for submitting snapshots to the dependency graph. For more information, see "[Dependency graph](https://docs.github.com/rest/dependency-graph)."
* The `code_scanning_upload` object provides your rate limit status for uploading SARIF results to code scanning. For more information, see "[Uploading a SARIF file to GitHub](https://docs.github.com/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github)."
* The `actions_runner_registration` object provides your rate limit status for registering self-hosted runners in GitHub Actions. For more information, see "[Self-hosted runners](https://docs.github.com/rest/actions/self-hosted-runners)."
* The `source_import` object is no longer in use for any API endpoints, and it will be removed in the next API version. For more information about API versions, see "[API Versions](https://docs.github.com/rest/about-the-rest-api/api-versions)."

**Note:** The `rate` object is deprecated. If you're writing new API client code or updating existing code, you should use the `core` object instead of the `rate` object. The `core` object contains the same information that is present in the `rate` object.

## Operation Object

```json
{
    "summary": "Get rate limit status for the authenticated user",
    "description": "**Note:** Accessing this endpoint does not count against your REST API rate limit.\n\nSome categories of endpoints have custom rate limits that are separate from the rate limit governing the other REST API endpoints. For this reason, the API response categorizes your rate limit. Under `resources`, you'll see objects relating to different categories:\n* The `core` object provides your rate limit status for all non-search-related resources in the REST API.\n* The `search` object provides your rate limit status for the REST API for searching (excluding code searches). For more information, see \"[Search](https://docs.github.com/rest/search/search).\"\n* The `code_search` object provides your rate limit status for the REST API for searching code. For more information, see \"[Search code](https://docs.github.com/rest/search/search#search-code).\"\n* The `graphql` object provides your rate limit status for the GraphQL API. For more information, see \"[Resource limitations](https://docs.github.com/graphql/overview/resource-limitations#rate-limit).\"\n* The `integration_manifest` object provides your rate limit status for the `POST /app-manifests/{code}/conversions` operation. For more information, see \"[Creating a GitHub App from a manifest](https://docs.github.com/apps/creating-github-apps/setting-up-a-github-app/creating-a-github-app-from-a-manifest#3-you-exchange-the-temporary-code-to-retrieve-the-app-configuration).\"\n* The `dependency_snapshots` object provides your rate limit status for submitting snapshots to the dependency graph. For more information, see \"[Dependency graph](https://docs.github.com/rest/dependency-graph).\"\n* The `code_scanning_upload` object provides your rate limit status for uploading SARIF results to code scanning. For more information, see \"[Uploading a SARIF file to GitHub](https://docs.github.com/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github).\"\n* The `actions_runner_registration` object provides your rate limit status for registering self-hosted runners in GitHub Actions. For more information, see \"[Self-hosted runners](https://docs.github.com/rest/actions/self-hosted-runners).\"\n* The `source_import` object is no longer in use for any API endpoints, and it will be removed in the next API version. For more information about API versions, see \"[API Versions](https://docs.github.com/rest/about-the-rest-api/api-versions).\"\n\n**Note:** The `rate` object is deprecated. If you're writing new API client code or updating existing code, you should use the `core` object instead of the `rate` object. The `core` object contains the same information that is present in the `rate` object.",
    "tags": [
        "rate-limit"
    ],
    "operationId": "rate-limit/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/rate-limit/rate-limit#get-rate-limit-status-for-the-authenticated-user"
    },
    "parameters": [],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/rate-limit-overview"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/rate-limit-overview"
                        }
                    }
                }
            },
            "headers": {
                "X-RateLimit-Limit": {
                    "$ref": "#/components/headers/x-rate-limit-limit"
                },
                "X-RateLimit-Remaining": {
                    "$ref": "#/components/headers/x-rate-limit-remaining"
                },
                "X-RateLimit-Reset": {
                    "$ref": "#/components/headers/x-rate-limit-reset"
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "rate-limit",
        "subcategory": "rate-limit"
    }
}
```

## References

### `#/components/schemas/rate-limit-overview`

```json
{
    "title": "Rate Limit Overview",
    "description": "Rate Limit Overview",
    "type": "object",
    "properties": {
        "resources": {
            "type": "object",
            "properties": {
                "core": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "graphql": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "search": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "code_search": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "source_import": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "integration_manifest": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "code_scanning_upload": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "actions_runner_registration": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "scim": {
                    "$ref": "#/components/schemas/rate-limit"
                },
                "dependency_snapshots": {
                    "$ref": "#/components/schemas/rate-limit"
                }
            },
            "required": [
                "core",
                "search"
            ]
        },
        "rate": {
            "$ref": "#/components/schemas/rate-limit"
        }
    },
    "required": [
        "rate",
        "resources"
    ]
}
```

### `#/components/examples/rate-limit-overview`

```json
{
    "value": {
        "resources": {
            "core": {
                "limit": 5000,
                "used": 1,
                "remaining": 4999,
                "reset": 1691591363
            },
            "search": {
                "limit": 30,
                "used": 12,
                "remaining": 18,
                "reset": 1691591091
            },
            "graphql": {
                "limit": 5000,
                "used": 7,
                "remaining": 4993,
                "reset": 1691593228
            },
            "integration_manifest": {
                "limit": 5000,
                "used": 1,
                "remaining": 4999,
                "reset": 1691594631
            },
            "source_import": {
                "limit": 100,
                "used": 1,
                "remaining": 99,
                "reset": 1691591091
            },
            "code_scanning_upload": {
                "limit": 500,
                "used": 1,
                "remaining": 499,
                "reset": 1691594631
            },
            "actions_runner_registration": {
                "limit": 10000,
                "used": 0,
                "remaining": 10000,
                "reset": 1691594631
            },
            "scim": {
                "limit": 15000,
                "used": 0,
                "remaining": 15000,
                "reset": 1691594631
            },
            "dependency_snapshots": {
                "limit": 100,
                "used": 0,
                "remaining": 100,
                "reset": 1691591091
            },
            "code_search": {
                "limit": 10,
                "used": 0,
                "remaining": 10,
                "reset": 1691591091
            }
        },
        "rate": {
            "limit": 5000,
            "used": 1,
            "remaining": 4999,
            "reset": 1372700873
        }
    }
}
```

### `#/components/headers/x-rate-limit-limit`

```json
{
    "example": 5000,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/headers/x-rate-limit-remaining`

```json
{
    "example": 4999,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/headers/x-rate-limit-reset`

```json
{
    "example": 1590701888,
    "schema": {
        "type": "integer",
        "format": "timestamp"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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