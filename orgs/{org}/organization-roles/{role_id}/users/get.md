# List users that are assigned to an organization role

`get /orgs/{org}/organization-roles/{role_id}/users`

Lists organization members that are assigned to an organization role. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, you must be an administrator for the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List users that are assigned to an organization role",
    "description": "Lists organization members that are assigned to an organization role. For more information on organization roles, see \"[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).\"\n\nTo use this endpoint, you must be an administrator for the organization.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-org-role-users",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/organization-roles#list-users-that-are-assigned-to-an-organization-role"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/role-id"
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
            "description": "Response - List of assigned users",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "description": "List of users assigned to the organization role",
                        "items": {
                            "$ref": "#/components/schemas/user-role-assignment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/simple-user-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "404": {
            "description": "Response if the organization or role does not exist."
        },
        "422": {
            "description": "Response if the organization roles feature is not enabled or validation failed."
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "organization-roles"
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

### `#/components/parameters/role-id`

```json
{
    "name": "role_id",
    "description": "The unique identifier of the role.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/schemas/user-role-assignment`

```json
{
    "title": "A Role Assignment for a User",
    "description": "The Relationship a User has with a role.",
    "type": "object",
    "properties": {
        "name": {
            "nullable": true,
            "type": "string"
        },
        "email": {
            "nullable": true,
            "type": "string"
        },
        "login": {
            "type": "string",
            "example": "octocat"
        },
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6VXNlcjE="
        },
        "avatar_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "gravatar_id": {
            "type": "string",
            "example": "41d064eb2195891e12d0413f63227ea7",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat"
        },
        "followers_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/followers"
        },
        "following_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/following{/other_user}"
        },
        "gists_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/gists{/gist_id}"
        },
        "starred_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/starred{/owner}{/repo}"
        },
        "subscriptions_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/subscriptions"
        },
        "organizations_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/orgs"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/repos"
        },
        "events_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/events{/privacy}"
        },
        "received_events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/received_events"
        },
        "type": {
            "type": "string",
            "example": "User"
        },
        "site_admin": {
            "type": "boolean"
        },
        "starred_at": {
            "type": "string",
            "example": "\"2020-07-09T00:17:55Z\""
        }
    },
    "required": [
        "avatar_url",
        "events_url",
        "followers_url",
        "following_url",
        "gists_url",
        "gravatar_id",
        "html_url",
        "id",
        "node_id",
        "login",
        "organizations_url",
        "received_events_url",
        "repos_url",
        "site_admin",
        "starred_url",
        "subscriptions_url",
        "type",
        "url"
    ]
}
```

### `#/components/examples/simple-user-items`

```json
{
    "value": [
        {
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
    ]
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```