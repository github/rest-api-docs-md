# Get default workflow permissions for a repository

`get /repos/{owner}/{repo}/actions/permissions/workflow`

Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in a repository,
as well as if GitHub Actions can submit approving pull request reviews.
For more information, see "[Setting the permissions of the GITHUB_TOKEN for your repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#setting-the-permissions-of-the-github_token-for-your-repository)."

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get default workflow permissions for a repository",
    "description": "Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in a repository,\nas well as if GitHub Actions can submit approving pull request reviews.\nFor more information, see \"[Setting the permissions of the GITHUB_TOKEN for your repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#setting-the-permissions-of-the-github_token-for-your-repository).\"\n\nOAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-github-actions-default-workflow-permissions-repository",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-default-workflow-permissions-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-get-default-workflow-permissions"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-default-workflow-permissions"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "permissions"
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

### `#/components/schemas/actions-get-default-workflow-permissions`

```json
{
    "type": "object",
    "properties": {
        "default_workflow_permissions": {
            "$ref": "#/components/schemas/actions-default-workflow-permissions"
        },
        "can_approve_pull_request_reviews": {
            "$ref": "#/components/schemas/actions-can-approve-pull-request-reviews"
        }
    },
    "required": [
        "default_workflow_permissions",
        "can_approve_pull_request_reviews"
    ]
}
```

### `#/components/examples/actions-default-workflow-permissions`

```json
{
    "summary": "Give read-only permission, and allow approving PRs.",
    "value": {
        "default_workflow_permissions": "read",
        "can_approve_pull_request_reviews": true
    }
}
```