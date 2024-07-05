# List deployment branch policies

Lists the deployment branch policies for an environment.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "List deployment branch policies",
    "description": "Lists the deployment branch policies for an environment.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-deployment-branch-policies",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/branch-policies#list-deployment-branch-policies"
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
                        "type": "object",
                        "properties": {
                            "total_count": {
                                "description": "The number of deployment branch policies for the environment.",
                                "type": "integer",
                                "example": 2
                            },
                            "branch_policies": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/deployment-branch-policy"
                                }
                            }
                        },
                        "required": [
                            "total_count",
                            "branch_policies"
                        ]
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deployment-branch-policies-list"
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
        "subcategory": "branch-policies"
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

### `#/components/schemas/deployment-branch-policy`

```json
{
    "title": "Deployment branch policy",
    "description": "Details of a deployment branch or tag policy.",
    "type": "object",
    "properties": {
        "id": {
            "description": "The unique identifier of the branch or tag policy.",
            "type": "integer",
            "example": 361471
        },
        "node_id": {
            "type": "string",
            "example": "MDE2OkdhdGVCcmFuY2hQb2xpY3kzNjE0NzE="
        },
        "name": {
            "description": "The name pattern that branches or tags must match in order to deploy to the environment.",
            "type": "string",
            "example": "release/*"
        },
        "type": {
            "description": "Whether this rule targets a branch or tag.",
            "type": "string",
            "example": "branch",
            "enum": [
                "branch",
                "tag"
            ]
        }
    }
}
```

### `#/components/examples/deployment-branch-policies-list`

```json
{
    "value": {
        "total_count": 2,
        "branch_policies": [
            {
                "id": 361471,
                "node_id": "MDE2OkdhdGVCcmFuY2hQb2xpY3kzNjE0NzE=",
                "name": "release/*"
            },
            {
                "id": 361472,
                "node_id": "MDE2OkdhdGVCcmFuY2hQb2xpY3kzNjE0NzI=",
                "name": "main"
            }
        ]
    }
}
```