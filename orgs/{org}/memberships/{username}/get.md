# Get organization membership for a user

`get /orgs/{org}/memberships/{username}`

In order to get a user's membership with an organization, the authenticated user must be an organization member. The `state` parameter in the response can be used to identify the user's membership status.

## Operation Object

```json
{
    "summary": "Get organization membership for a user",
    "description": "In order to get a user's membership with an organization, the authenticated user must be an organization member. The `state` parameter in the response can be used to identify the user's membership status.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get-membership-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/members#get-organization-membership-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/org-membership"
                    },
                    "examples": {
                        "response-if-user-has-an-active-admin-membership-with-organization": {
                            "$ref": "#/components/examples/org-membership-response-if-user-has-an-active-admin-membership-with-organization"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "members"
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

### `#/components/schemas/org-membership`

```json
{
    "title": "Org Membership",
    "description": "Org Membership",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat/memberships/defunkt"
        },
        "state": {
            "type": "string",
            "description": "The state of the member in the organization. The `pending` state indicates the user has not yet accepted an invitation.",
            "example": "active",
            "enum": [
                "active",
                "pending"
            ]
        },
        "role": {
            "type": "string",
            "description": "The user's membership type in the organization.",
            "example": "admin",
            "enum": [
                "admin",
                "member",
                "billing_manager"
            ]
        },
        "organization_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat"
        },
        "organization": {
            "$ref": "#/components/schemas/organization-simple"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "can_create_repository": {
                    "type": "boolean"
                }
            },
            "required": [
                "can_create_repository"
            ]
        }
    },
    "required": [
        "state",
        "role",
        "organization_url",
        "url",
        "organization",
        "user"
    ]
}
```

### `#/components/examples/org-membership-response-if-user-has-an-active-admin-membership-with-organization`

```json
{
    "summary": "Response if user has an active admin membership with organization",
    "value": {
        "url": "https://api.github.com/orgs/octocat/memberships/defunkt",
        "state": "active",
        "role": "admin",
        "organization_url": "https://api.github.com/orgs/octocat",
        "organization": {
            "login": "github",
            "id": 1,
            "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
            "url": "https://api.github.com/orgs/github",
            "repos_url": "https://api.github.com/orgs/github/repos",
            "events_url": "https://api.github.com/orgs/github/events",
            "hooks_url": "https://api.github.com/orgs/github/hooks",
            "issues_url": "https://api.github.com/orgs/github/issues",
            "members_url": "https://api.github.com/orgs/github/members{/member}",
            "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "description": "A great organization"
        },
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

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```