# Get GitHub Actions permissions for an organization

`get /orgs/{org}/actions/permissions`

Gets the GitHub Actions permissions policy for repositories and allowed actions and reusable workflows in an organization.

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Actions permissions for an organization",
    "description": "Gets the GitHub Actions permissions policy for repositories and allowed actions and reusable workflows in an organization.\n\nOAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "operationId": "actions/get-github-actions-permissions-organization",
    "tags": [
        "actions"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-github-actions-permissions-for-an-organization"
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
                        "$ref": "#/components/schemas/actions-organization-permissions"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-organization-permissions"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "githubCloudOnly": false,
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

### `#/components/schemas/actions-organization-permissions`

```json
{
    "type": "object",
    "properties": {
        "enabled_repositories": {
            "$ref": "#/components/schemas/enabled-repositories"
        },
        "selected_repositories_url": {
            "type": "string",
            "description": "The API URL to use to get or set the selected repositories that are allowed to run GitHub Actions, when `enabled_repositories` is set to `selected`."
        },
        "allowed_actions": {
            "$ref": "#/components/schemas/allowed-actions"
        },
        "selected_actions_url": {
            "$ref": "#/components/schemas/selected-actions-url"
        }
    },
    "required": [
        "enabled_repositories"
    ]
}
```

### `#/components/examples/actions-organization-permissions`

```json
{
    "value": {
        "enabled_repositories": "all",
        "allowed_actions": "selected",
        "selected_actions_url": "https://api.github.com/organizations/42/actions/permissions/selected-actions"
    }
}
```