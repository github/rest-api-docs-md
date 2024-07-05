# Get a custom deployment protection rule

Gets an enabled custom deployment protection rule for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see [`GET /apps/{app_slug}`](https://docs.github.com/rest/apps/apps#get-an-app).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get a custom deployment protection rule",
    "description": "Gets an enabled custom deployment protection rule for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see \"[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment).\"\n\nFor more information about the app that is providing this custom deployment rule, see [`GET /apps/{app_slug}`](https://docs.github.com/rest/apps/apps#get-an-app).\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-custom-deployment-protection-rule",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/protection-rules#get-a-custom-deployment-protection-rule"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/environment-name"
        },
        {
            "$ref": "#/components/parameters/protection-rule-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/deployment-protection-rule"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deployment-protection-rule"
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

### `#/components/parameters/protection-rule-id`

```json
{
    "name": "protection_rule_id",
    "description": "The unique identifier of the protection rule.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/examples/deployment-protection-rule`

```json
{
    "value": {
        "id": 3,
        "node_id": "IEH37kRlcGxveW1lbnRTdGF0ddiv",
        "enabled": true,
        "app": {
            "id": 1,
            "node_id": "GHT58kRlcGxveW1lbnRTdTY!bbcy",
            "slug": "a-custom-app",
            "integration_url": "https://api.github.com/apps/a-custom-app"
        }
    }
}
```