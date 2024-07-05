# List custom deployment rule integrations available for an environment

`get /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/apps`

Gets all custom deployment protection rule integrations that are available for an environment. Anyone with read access to the repository can use this endpoint.

For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see "[GET an app](https://docs.github.com/rest/apps/apps#get-an-app)".

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "List custom deployment rule integrations available for an environment",
    "description": "Gets all custom deployment protection rule integrations that are available for an environment. Anyone with read access to the repository can use this endpoint.\n\nFor more information about environments, see \"[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment).\"\n\nFor more information about the app that is providing this custom deployment rule, see \"[GET an app](https://docs.github.com/rest/apps/apps#get-an-app)\".\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-custom-deployment-rule-integrations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/protection-rules#list-custom-deployment-rule-integrations-available-for-an-environment"
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
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        }
    ],
    "responses": {
        "200": {
            "description": "A list of custom deployment rule integrations available for this environment.",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "total_count": {
                                "description": "The total number of custom deployment protection rule integrations available for this environment.",
                                "type": "integer",
                                "example": 35
                            },
                            "available_custom_deployment_protection_rule_integrations": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/custom-deployment-rule-app"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/custom-deployment-protection-rule-apps"
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

### `#/components/schemas/custom-deployment-rule-app`

```json
{
    "title": "Custom deployment protection rule app",
    "description": "A GitHub App that is providing a custom deployment protection rule.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 3515,
            "description": "The unique identifier of the deployment protection rule integration."
        },
        "slug": {
            "type": "string",
            "example": "my-custom-app",
            "description": "The slugified name of the deployment protection rule integration."
        },
        "integration_url": {
            "type": "string",
            "example": "https://api.github.com/apps/custom-app-slug",
            "description": "The URL for the endpoint to get details about the app."
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6R2F0ZTM1MTU=",
            "description": "The node ID for the deployment protection rule integration."
        }
    },
    "required": [
        "id",
        "slug",
        "integration_url",
        "node_id"
    ]
}
```

### `#/components/examples/custom-deployment-protection-rule-apps`

```json
{
    "value": [
        {
            "total_count": 2
        },
        {
            "available_custom_deployment_protection_rule_integrations": [
                {
                    "id": 1,
                    "node_id": "GHT58kRlcGxveW1lbnRTdTY!bbcy",
                    "slug": "a-custom-app",
                    "integration_url": "https://api.github.com/apps/a-custom-app"
                },
                {
                    "id": 2,
                    "node_id": "UHVE67RlcGxveW1lbnRTdTY!jfeuy",
                    "slug": "another-custom-app",
                    "integration_url": "https://api.github.com/apps/another-custom-app"
                }
            ]
        }
    ]
}
```