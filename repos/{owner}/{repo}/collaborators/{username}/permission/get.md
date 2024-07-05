# Get repository permissions for a user

Checks the repository permission of a collaborator. The possible repository
permissions are `admin`, `write`, `read`, and `none`.

*Note*: The `permission` attribute provides the legacy base roles of `admin`, `write`, `read`, and `none`, where the
`maintain` role is mapped to `write` and the `triage` role is mapped to `read`. To determine the role assigned to the
collaborator, see the `role_name` attribute, which will provide the full role name, including custom roles. The
`permissions` hash can also be used to determine which base level of access the collaborator has to the repository.

## Operation Object

```json
{
    "summary": "Get repository permissions for a user",
    "description": "Checks the repository permission of a collaborator. The possible repository\npermissions are `admin`, `write`, `read`, and `none`.\n\n*Note*: The `permission` attribute provides the legacy base roles of `admin`, `write`, `read`, and `none`, where the\n`maintain` role is mapped to `write` and the `triage` role is mapped to `read`. To determine the role assigned to the\ncollaborator, see the `role_name` attribute, which will provide the full role name, including custom roles. The\n`permissions` hash can also be used to determine which base level of access the collaborator has to the repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-collaborator-permission-level",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/collaborators/collaborators#get-repository-permissions-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "if user has admin permissions",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/repository-collaborator-permission"
                    },
                    "examples": {
                        "response-if-user-has-admin-permissions": {
                            "$ref": "#/components/examples/repository-collaborator-permission-response-if-user-has-admin-permissions"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "collaborators",
        "subcategory": "collaborators"
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

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/repository-collaborator-permission`

```json
{
    "title": "Repository Collaborator Permission",
    "description": "Repository Collaborator Permission",
    "type": "object",
    "properties": {
        "permission": {
            "type": "string"
        },
        "role_name": {
            "type": "string",
            "example": "admin"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-collaborator"
        }
    },
    "required": [
        "permission",
        "role_name",
        "user"
    ]
}
```

### `#/components/examples/repository-collaborator-permission-response-if-user-has-admin-permissions`

```json
{
    "value": {
        "permission": "admin",
        "role_name": "admin",
        "user": {
            "login": "octocat",
            "id": 1,
            "node_id": "MDQ6VXNlcjE=",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "gravatar_id": "",
            "url": "https://api.github.com/users/octocat",
            "html_url": "https://github.com/octocat",
            "followers_url": "https://api.github.com/users/octocat/followers",
            "following_url": "https://api.github.com/users/octocat/following{/other_user}",
            "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
            "organizations_url": "https://api.github.com/users/octocat/orgs",
            "repos_url": "https://api.github.com/users/octocat/repos",
            "events_url": "https://api.github.com/users/octocat/events{/privacy}",
            "received_events_url": "https://api.github.com/users/octocat/received_events",
            "type": "User",
            "site_admin": false
        }
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```