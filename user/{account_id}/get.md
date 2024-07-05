# Get a user using their ID

`get /user/{account_id}`

Provides publicly available information about someone with a GitHub account. This method takes their durable user `ID` instead of their `login`, which can change over time.

The `email` key in the following response is the publicly visible email address from your GitHub [profile page](https://github.com/settings/profile). When setting up your profile, you can select a primary email address to be “public” which provides an email entry for this endpoint. If you do not set a public email address for `email`, then it will have a value of `null`. You only see publicly visible email addresses when authenticated with GitHub. For more information, see [Authentication](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#authentication).

The Emails API enables you to list all of your email addresses, and toggle a primary email to be visible publicly. For more information, see "[Emails API](https://docs.github.com/rest/users/emails)".

## Operation Object

```json
{
    "summary": "Get a user using their ID",
    "description": "Provides publicly available information about someone with a GitHub account. This method takes their durable user `ID` instead of their `login`, which can change over time.\n\nThe `email` key in the following response is the publicly visible email address from your GitHub [profile page](https://github.com/settings/profile). When setting up your profile, you can select a primary email address to be \u201cpublic\u201d which provides an email entry for this endpoint. If you do not set a public email address for `email`, then it will have a value of `null`. You only see publicly visible email addresses when authenticated with GitHub. For more information, see [Authentication](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#authentication).\n\nThe Emails API enables you to list all of your email addresses, and toggle a primary email to be visible publicly. For more information, see \"[Emails API](https://docs.github.com/rest/users/emails)\".",
    "tags": [
        "users"
    ],
    "operationId": "users/get-by-id",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/users#get-a-user-using-their-id"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/account-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "oneOf": [
                            {
                                "$ref": "#/components/schemas/private-user"
                            },
                            {
                                "$ref": "#/components/schemas/public-user"
                            }
                        ]
                    },
                    "examples": {
                        "default-response": {
                            "$ref": "#/components/examples/public-user-default-response"
                        },
                        "response-with-git-hub-plan-information": {
                            "$ref": "#/components/examples/public-user-response-with-git-hub-plan-information"
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
        "category": "users",
        "subcategory": "users"
    }
}
```

## References

### `#/components/parameters/account-id`

```json
{
    "name": "account_id",
    "description": "account_id parameter",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/private-user`

```json
{
    "title": "Private User",
    "description": "Private User",
    "type": "object",
    "properties": {
        "login": {
            "type": "string",
            "example": "octocat"
        },
        "id": {
            "type": "integer",
            "format": "int64",
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
        "name": {
            "type": "string",
            "example": "monalisa octocat",
            "nullable": true
        },
        "company": {
            "type": "string",
            "example": "GitHub",
            "nullable": true
        },
        "blog": {
            "type": "string",
            "example": "https://github.com/blog",
            "nullable": true
        },
        "location": {
            "type": "string",
            "example": "San Francisco",
            "nullable": true
        },
        "email": {
            "type": "string",
            "format": "email",
            "example": "octocat@github.com",
            "nullable": true
        },
        "notification_email": {
            "type": "string",
            "format": "email",
            "example": "octocat@github.com",
            "nullable": true
        },
        "hireable": {
            "type": "boolean",
            "nullable": true
        },
        "bio": {
            "type": "string",
            "example": "There once was...",
            "nullable": true
        },
        "twitter_username": {
            "type": "string",
            "example": "monalisa",
            "nullable": true
        },
        "public_repos": {
            "type": "integer",
            "example": 2
        },
        "public_gists": {
            "type": "integer",
            "example": 1
        },
        "followers": {
            "type": "integer",
            "example": 20
        },
        "following": {
            "type": "integer",
            "example": 0
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2008-01-14T04:33:35Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2008-01-14T04:33:35Z"
        },
        "private_gists": {
            "type": "integer",
            "example": 81
        },
        "total_private_repos": {
            "type": "integer",
            "example": 100
        },
        "owned_private_repos": {
            "type": "integer",
            "example": 100
        },
        "disk_usage": {
            "type": "integer",
            "example": 10000
        },
        "collaborators": {
            "type": "integer",
            "example": 8
        },
        "two_factor_authentication": {
            "type": "boolean",
            "example": true
        },
        "plan": {
            "type": "object",
            "properties": {
                "collaborators": {
                    "type": "integer"
                },
                "name": {
                    "type": "string"
                },
                "space": {
                    "type": "integer"
                },
                "private_repos": {
                    "type": "integer"
                }
            },
            "required": [
                "collaborators",
                "name",
                "space",
                "private_repos"
            ]
        },
        "suspended_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "business_plus": {
            "type": "boolean"
        },
        "ldap_dn": {
            "type": "string"
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
        "url",
        "bio",
        "blog",
        "company",
        "email",
        "followers",
        "following",
        "hireable",
        "location",
        "name",
        "public_gists",
        "public_repos",
        "created_at",
        "updated_at",
        "collaborators",
        "disk_usage",
        "owned_private_repos",
        "private_gists",
        "total_private_repos",
        "two_factor_authentication"
    ]
}
```

### `#/components/schemas/public-user`

```json
{
    "title": "Public User",
    "description": "Public User",
    "type": "object",
    "properties": {
        "login": {
            "type": "string"
        },
        "id": {
            "type": "integer",
            "format": "int64"
        },
        "node_id": {
            "type": "string"
        },
        "avatar_url": {
            "type": "string",
            "format": "uri"
        },
        "gravatar_id": {
            "type": "string",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "followers_url": {
            "type": "string",
            "format": "uri"
        },
        "following_url": {
            "type": "string"
        },
        "gists_url": {
            "type": "string"
        },
        "starred_url": {
            "type": "string"
        },
        "subscriptions_url": {
            "type": "string",
            "format": "uri"
        },
        "organizations_url": {
            "type": "string",
            "format": "uri"
        },
        "repos_url": {
            "type": "string",
            "format": "uri"
        },
        "events_url": {
            "type": "string"
        },
        "received_events_url": {
            "type": "string",
            "format": "uri"
        },
        "type": {
            "type": "string"
        },
        "site_admin": {
            "type": "boolean"
        },
        "name": {
            "type": "string",
            "nullable": true
        },
        "company": {
            "type": "string",
            "nullable": true
        },
        "blog": {
            "type": "string",
            "nullable": true
        },
        "location": {
            "type": "string",
            "nullable": true
        },
        "email": {
            "type": "string",
            "format": "email",
            "nullable": true
        },
        "notification_email": {
            "type": "string",
            "format": "email",
            "nullable": true
        },
        "hireable": {
            "type": "boolean",
            "nullable": true
        },
        "bio": {
            "type": "string",
            "nullable": true
        },
        "twitter_username": {
            "type": "string",
            "nullable": true
        },
        "public_repos": {
            "type": "integer"
        },
        "public_gists": {
            "type": "integer"
        },
        "followers": {
            "type": "integer"
        },
        "following": {
            "type": "integer"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "plan": {
            "type": "object",
            "properties": {
                "collaborators": {
                    "type": "integer"
                },
                "name": {
                    "type": "string"
                },
                "space": {
                    "type": "integer"
                },
                "private_repos": {
                    "type": "integer"
                }
            },
            "required": [
                "collaborators",
                "name",
                "space",
                "private_repos"
            ]
        },
        "suspended_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "private_gists": {
            "type": "integer",
            "example": 1
        },
        "total_private_repos": {
            "type": "integer",
            "example": 2
        },
        "owned_private_repos": {
            "type": "integer",
            "example": 2
        },
        "disk_usage": {
            "type": "integer",
            "example": 1
        },
        "collaborators": {
            "type": "integer",
            "example": 3
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
        "url",
        "bio",
        "blog",
        "company",
        "email",
        "followers",
        "following",
        "hireable",
        "location",
        "name",
        "public_gists",
        "public_repos",
        "created_at",
        "updated_at"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/public-user-default-response`

```json
{
    "summary": "Default response",
    "value": {
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
        "site_admin": false,
        "name": "monalisa octocat",
        "company": "GitHub",
        "blog": "https://github.com/blog",
        "location": "San Francisco",
        "email": "octocat@github.com",
        "hireable": false,
        "bio": "There once was...",
        "twitter_username": "monatheoctocat",
        "public_repos": 2,
        "public_gists": 1,
        "followers": 20,
        "following": 0,
        "created_at": "2008-01-14T04:33:35Z",
        "updated_at": "2008-01-14T04:33:35Z"
    }
}
```

### `#/components/examples/public-user-response-with-git-hub-plan-information`

```json
{
    "summary": "Response with GitHub plan information",
    "value": {
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
        "site_admin": false,
        "name": "monalisa octocat",
        "company": "GitHub",
        "blog": "https://github.com/blog",
        "location": "San Francisco",
        "email": "octocat@github.com",
        "hireable": false,
        "bio": "There once was...",
        "twitter_username": "monatheoctocat",
        "public_repos": 2,
        "public_gists": 1,
        "followers": 20,
        "following": 0,
        "created_at": "2008-01-14T04:33:35Z",
        "updated_at": "2008-01-14T04:33:35Z",
        "plan": {
            "name": "pro",
            "space": 976562499,
            "collaborators": 0,
            "private_repos": 9999
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