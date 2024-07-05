# Get allowed actions and reusable workflows for a repository

`get /repos/{owner}/{repo}/actions/permissions/selected-actions`

Gets the settings for selected actions and reusable workflows that are allowed in a repository. To use this endpoint, the repository policy for `allowed_actions` must be configured to `selected`. For more information, see "[Set GitHub Actions permissions for a repository](#set-github-actions-permissions-for-a-repository)."

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get allowed actions and reusable workflows for a repository",
    "description": "Gets the settings for selected actions and reusable workflows that are allowed in a repository. To use this endpoint, the repository policy for `allowed_actions` must be configured to `selected`. For more information, see \"[Set GitHub Actions permissions for a repository](#set-github-actions-permissions-for-a-repository).\"\n\nOAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "operationId": "actions/get-allowed-actions-repository",
    "tags": [
        "actions"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-allowed-actions-and-reusable-workflows-for-a-repository"
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