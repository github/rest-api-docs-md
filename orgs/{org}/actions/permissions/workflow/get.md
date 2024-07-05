# Get default workflow permissions for an organization

`get /orgs/{org}/actions/permissions/workflow`

Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in an organization,
as well as whether GitHub Actions can submit approving pull request reviews. For more information, see
"[Setting the permissions of the GITHUB_TOKEN for your organization](https://docs.github.com/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#setting-the-permissions-of-the-github_token-for-your-organization)."

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get default workflow permissions for an organization",
    "description": "Gets the default workflow permissions granted to the `GITHUB_TOKEN` when running workflows in an organization,\nas well as whether GitHub Actions can submit approving pull request reviews. For more information, see\n\"[Setting the permissions of the GITHUB_TOKEN for your organization](https://docs.github.com/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#setting-the-permissions-of-the-github_token-for-your-organization).\"\n\nOAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-github-actions-default-workflow-permissions-organization",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-default-workflow-permissions-for-an-organization"
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