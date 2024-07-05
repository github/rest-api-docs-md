# Get a deployment branch policy

`get /repos/{owner}/{repo}/environments/{environment_name}/deployment-branch-policies/{branch_policy_id}`

Gets a deployment branch or tag policy for an environment.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get a deployment branch policy",
    "description": "Gets a deployment branch or tag policy for an environment.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-deployment-branch-policy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/branch-policies#get-a-deployment-branch-policy"
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
            "$ref": "#/components/parameters/branch-policy-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/deployment-branch-policy"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deployment-branch-policy-wildcard"
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

### `#/components/parameters/branch-policy-id`

```json
{
    "name": "branch_policy_id",
    "in": "path",
    "required": true,
    "description": "The unique identifier of the branch policy.",
    "schema": {
        "type": "integer"
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

### `#/components/examples/deployment-branch-policy-wildcard`

```json
{
    "value": {
        "id": 364662,
        "node_id": "MDE2OkdhdGVCcmFuY2hQb2xpY3kzNjQ2NjI=",
        "name": "release/*"
    }
}
```