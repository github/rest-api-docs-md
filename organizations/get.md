# List organizations

`get /organizations`

Lists all organizations, in the order that they were created.

**Note:** Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of organizations.

## Operation Object

```json
{
    "summary": "List organizations",
    "description": "Lists all organizations, in the order that they were created.\n\n**Note:** Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of organizations.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/orgs#list-organizations"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/since-org"
        },
        {
            "$ref": "#/components/parameters/per-page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/organization-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-simple-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "example": "<https://api.github.com/organizations?since=135>; rel=\"next\"",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "orgs"
    }
}
```

## References

### `#/components/parameters/since-org`

```json
{
    "name": "since",
    "description": "An organization ID. Only return organizations with an ID greater than this ID.",
    "in": "query",
    "required": false,
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

### `#/components/schemas/organization-simple`

```json
{
    "title": "Organization Simple",
    "description": "A GitHub organization.",
    "type": "object",
    "properties": {
        "login": {
            "type": "string",
            "example": "github"
        },
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDEyOk9yZ2FuaXphdGlvbjE="
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/repos"
        },
        "events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/events"
        },
        "hooks_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/hooks"
        },
        "issues_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/issues"
        },
        "members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/members{/member}"
        },
        "public_members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/public_members{/member}"
        },
        "avatar_url": {
            "type": "string",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "description": {
            "type": "string",
            "example": "A great organization",
            "nullable": true
        }
    },
    "required": [
        "login",
        "url",
        "id",
        "node_id",
        "repos_url",
        "events_url",
        "hooks_url",
        "issues_url",
        "members_url",
        "public_members_url",
        "avatar_url",
        "description"
    ]
}
```

### `#/components/examples/organization-simple-items`

```json
{
    "value": [
        {
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
        }
    ]
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```