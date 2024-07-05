# Get all deployment protection rules for an environment

`get /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules`

Gets all custom deployment protection rules that are enabled for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see the [documentation for the `GET /apps/{app_slug}` endpoint](https://docs.github.com/rest/apps/apps#get-an-app).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get all deployment protection rules for an environment",
    "description": "Gets all custom deployment protection rules that are enabled for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see \"[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment).\"\n\nFor more information about the app that is providing this custom deployment rule, see the [documentation for the `GET /apps/{app_slug}` endpoint](https://docs.github.com/rest/apps/apps#get-an-app).\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-all-deployment-protection-rules",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/protection-rules#get-all-deployment-protection-rules-for-an-environment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/environment-name"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/owner"
        }
    ],
    "responses": {
        "200": {
            "description": "List of deployment protection rules",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "total_count": {
                                "description": "The number of enabled custom deployment protection rules for this environment",
                                "type": "integer",
                                "example": 10
                            },
                            "custom_deployment_protection_rules": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/deployment-protection-rule"
                                }
                            }
                        },
                        "example": {
                            "$ref": "#/components/examples/deployment-protection-rules"
                        }
                    },
                    "examples": {
                        "default": {
                            "value": {
                                "total_count": 2,
                                "custom_deployment_protection_rules": [
                                    {
                                        "id": 3,
                                        "node_id": "IEH37kRlcGxveW1lbnRTdGF0ddiv",
                                        "enabled": true,
                                        "app": {
                                            "id": 1,
                                            "node_id": "GHT58kRlcGxveW1lbnRTdTY!bbcy",
                                            "slug": "a-custom-app",
                                            "integration_url": "https://api.github.com/apps/a-custom-app"
                                        }
                                    },
                                    {
                                        "id": 4,
                                        "node_id": "MDE2OkRlcGxveW1lbnRTdHJ41128",
                                        "enabled": true,
                                        "app": {
                                            "id": 1,
                                            "node_id": "UHVE67RlcGxveW1lbnRTdTY!jfeuy",
                                            "slug": "another-custom-app",
                                            "integration_url": "https://api.github.com/apps/another-custom-app"
                                        }
                                    }
                                ]
                            }
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "deployments",
        "subcategory": "protection-rules"
    }
}
```

## References

### `#/components/parameters/environment-name`

```json
{
    "name": "environment_name",
    "in": "path",
    "required": true,
    "description": "The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/deployment-protection-rule`

```json
{
    "title": "Deployment protection rule",
    "description": "Deployment protection rule",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 3515,
            "description": "The unique identifier for the deployment protection rule."
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6R2F0ZTM1MTU=",
            "description": "The node ID for the deployment protection rule."
        },
        "enabled": {
            "type": "boolean",
            "example": true,
            "description": "Whether the deployment protection rule is enabled for the environment."
        },
        "app": {
            "$ref": "#/components/schemas/custom-deployment-rule-app"
        }
    },
    "required": [
        "id",
        "node_id",
        "enabled",
        "app"
    ]
}
```

### `#/components/examples/deployment-protection-rules`

```json
{
    "value": [
        {
            "total_count": 2
        },
        {
            "custom_deployment_protection_rules": [
                {
                    "id": 3,
                    "node_id": "IEH37kRlcGxveW1lbnRTdGF0ddiv",
                    "enabled": true,
                    "app": {
                        "id": 1,
                        "node_id": "GHT58kRlcGxveW1lbnRTdTY!bbcy",
                        "slug": "a-custom-app",
                        "integration_url": "https://api.github.com/apps/a-custom-app"
                    }
                },
                {
                    "id": 4,
                    "node_id": "MDE2OkRlcGxveW1lbnRTdHJ41128",
                    "enabled": true,
                    "app": {
                        "id": 1,
                        "node_id": "UHVE67RlcGxveW1lbnRTdTY!jfeuy",
                        "slug": "another-custom-app",
                        "integration_url": "https://api.github.com/apps/another-custom-app"
                    }
                }
            ]
        }
    ]
}
```