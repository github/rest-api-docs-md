# Get an organization installation for the authenticated app

Enables an authenticated GitHub App to find the organization's installation information.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization installation for the authenticated app",
    "description": "Enables an authenticated GitHub App to find the organization's installation information.\n\nYou must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/get-org-installation",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/apps#get-an-organization-installation-for-the-authenticated-app"
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
                        "$ref": "#/components/schemas/installation"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/installation"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "apps",
        "subcategory": "apps"
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

### `#/components/schemas/installation`

```json
{
    "title": "Installation",
    "description": "Installation",
    "type": "object",
    "properties": {
        "id": {
            "description": "The ID of the installation.",
            "type": "integer",
            "example": 1
        },
        "account": {
            "nullable": true,
            "anyOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                },
                {
                    "$ref": "#/components/schemas/enterprise"
                }
            ]
        },
        "repository_selection": {
            "description": "Describe whether all repositories have been selected or there's a selection involved",
            "type": "string",
            "enum": [
                "all",
                "selected"
            ]
        },
        "access_tokens_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/app/installations/1/access_tokens"
        },
        "repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/installation/repositories"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/organizations/github/settings/installations/1"
        },
        "app_id": {
            "type": "integer",
            "example": 1
        },
        "target_id": {
            "description": "The ID of the user or organization this token is being scoped to.",
            "type": "integer"
        },
        "target_type": {
            "type": "string",
            "example": "Organization"
        },
        "permissions": {
            "$ref": "#/components/schemas/app-permissions"
        },
        "events": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "single_file_name": {
            "type": "string",
            "example": "config.yaml",
            "nullable": true
        },
        "has_multiple_single_files": {
            "type": "boolean",
            "example": true
        },
        "single_file_paths": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "config.yml",
                ".github/issue_TEMPLATE.md"
            ]
        },
        "app_slug": {
            "type": "string",
            "example": "github-actions"
        },
        "suspended_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "suspended_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "contact_email": {
            "type": "string",
            "example": "\"test_13f1e99741e3e004@d7e1eb0bc0a1ba12.com\"",
            "nullable": true
        }
    },
    "required": [
        "id",
        "app_id",
        "app_slug",
        "target_id",
        "target_type",
        "single_file_name",
        "repository_selection",
        "access_tokens_url",
        "html_url",
        "repositories_url",
        "events",
        "account",
        "permissions",
        "created_at",
        "updated_at",
        "suspended_by",
        "suspended_at"
    ]
}
```

### `#/components/examples/installation`

```json
{
    "value": {
        "id": 1,
        "account": {
            "login": "github",
            "id": 1,
            "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
            "avatar_url": "https://github.com/images/error/hubot_happy.gif",
            "gravatar_id": "",
            "url": "https://api.github.com/orgs/github",
            "html_url": "https://github.com/github",
            "followers_url": "https://api.github.com/users/github/followers",
            "following_url": "https://api.github.com/users/github/following{/other_user}",
            "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/github/subscriptions",
            "organizations_url": "https://api.github.com/users/github/orgs",
            "repos_url": "https://api.github.com/orgs/github/repos",
            "events_url": "https://api.github.com/orgs/github/events",
            "received_events_url": "https://api.github.com/users/github/received_events",
            "type": "Organization",
            "site_admin": false
        },
        "repository_selection": "all",
        "access_tokens_url": "https://api.github.com/app/installations/1/access_tokens",
        "repositories_url": "https://api.github.com/installation/repositories",
        "html_url": "https://github.com/organizations/github/settings/installations/1",
        "app_id": 1,
        "target_id": 1,
        "target_type": "Organization",
        "permissions": {
            "checks": "write",
            "metadata": "read",
            "contents": "read"
        },
        "events": [
            "push",
            "pull_request"
        ],
        "created_at": "2018-02-09T20:51:14Z",
        "updated_at": "2018-02-09T20:51:14Z",
        "single_file_name": "config.yml",
        "has_multiple_single_files": true,
        "single_file_paths": [
            "config.yml",
            ".github/issue_TEMPLATE.md"
        ],
        "app_slug": "github-actions",
        "suspended_at": null,
        "suspended_by": null
    }
}
```