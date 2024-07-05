# Get allowed actions and reusable workflows for an organization

`get /orgs/{org}/actions/permissions/selected-actions`

Gets the selected actions and reusable workflows that are allowed in an organization. To use this endpoint, the organization permission policy for `allowed_actions` must be configured to `selected`. For more information, see "[Set GitHub Actions permissions for an organization](#set-github-actions-permissions-for-an-organization)."

OAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get allowed actions and reusable workflows for an organization",
    "description": "Gets the selected actions and reusable workflows that are allowed in an organization. To use this endpoint, the organization permission policy for `allowed_actions` must be configured to `selected`. For more information, see \"[Set GitHub Actions permissions for an organization](#set-github-actions-permissions-for-an-organization).\"\n\nOAuth tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "operationId": "actions/get-allowed-actions-organization",
    "tags": [
        "actions"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-allowed-actions-and-reusable-workflows-for-an-organization"
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
                        "$ref": "#/components/schemas/selected-actions"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/selected-actions"
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

### `#/components/schemas/selected-actions`

```json
{
    "type": "object",
    "properties": {
        "github_owned_allowed": {
            "type": "boolean",
            "description": "Whether GitHub-owned actions are allowed. For example, this includes the actions in the `actions` organization."
        },
        "verified_allowed": {
            "type": "boolean",
            "description": "Whether actions from GitHub Marketplace verified creators are allowed. Set to `true` to allow all actions by GitHub Marketplace verified creators."
        },
        "patterns_allowed": {
            "type": "array",
            "description": "Specifies a list of string-matching patterns to allow specific action(s) and reusable workflow(s). Wildcards, tags, and SHAs are allowed. For example, `monalisa/octocat@*`, `monalisa/octocat@v2`, `monalisa/*`.\n\n**Note**: The `patterns_allowed` setting only applies to public repositories.",
            "items": {
                "type": "string"
            }
        }
    }
}
```

### `#/components/examples/selected-actions`

```json
{
    "value": {
        "github_owned_allowed": true,
        "verified_allowed": false,
        "patterns_allowed": [
            "monalisa/octocat@*",
            "docker/*"
        ]
    }
}
```