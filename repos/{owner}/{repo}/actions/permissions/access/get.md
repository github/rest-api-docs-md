# Get the level of access for workflows outside of the repository

`get /repos/{owner}/{repo}/actions/permissions/access`

Gets the level of access that workflows outside of the repository have to actions and reusable workflows in the repository.
This endpoint only applies to private repositories.
For more information, see "[Allowing access to components in a private repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-a-private-repository)."

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get the level of access for workflows outside of the repository",
    "description": "Gets the level of access that workflows outside of the repository have to actions and reusable workflows in the repository.\nThis endpoint only applies to private repositories.\nFor more information, see \"[Allowing access to components in a private repository](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-access-to-components-in-a-private-repository).\"\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-workflow-access-to-repository",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-the-level-of-access-for-workflows-outside-of-the-repository"
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
                        "$ref": "#/components/schemas/actions-workflow-access-to-repository"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-workflow-access-to-repository"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
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

### `#/components/schemas/actions-workflow-access-to-repository`

```json
{
    "type": "object",
    "properties": {
        "access_level": {
            "type": "string",
            "description": "Defines the level of access that workflows outside of the repository have to actions and reusable workflows within the\nrepository.\n\n`none` means the access is only possible from workflows in this repository. `user` level access allows sharing across user owned private repositories only. `organization` level access allows sharing across the organization.",
            "enum": [
                "none",
                "user",
                "organization"
            ]
        }
    },
    "required": [
        "access_level"
    ]
}
```

### `#/components/examples/actions-workflow-access-to-repository`

```json
{
    "value": {
        "access_level": "organization"
    }
}
```