# Search users

Find users via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for users, you can get text match metadata for the issue **login**, public **email**, and **name** fields when you pass the `text-match` media type. For more details about highlighting search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata). For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you're looking for a list of popular users, you might try this query:

`q=tom+repos:%3E42+followers:%3E1000`

This query searches for users with the name `tom`. The results are restricted to users with more than 42 repositories and over 1,000 followers.

This endpoint does not accept authentication and will only include publicly visible users. As an alternative, you can use the GraphQL API. The GraphQL API requires authentication and will return private users, including Enterprise Managed Users (EMUs), that you are authorized to view. For more information, see "[GraphQL Queries](https://docs.github.com/graphql/reference/queries#search)."

## Operation Object

```json
{
    "summary": "Search users",
    "description": "Find users via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).\n\nWhen searching for users, you can get text match metadata for the issue **login**, public **email**, and **name** fields when you pass the `text-match` media type. For more details about highlighting search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata). For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).\n\nFor example, if you're looking for a list of popular users, you might try this query:\n\n`q=tom+repos:%3E42+followers:%3E1000`\n\nThis query searches for users with the name `tom`. The results are restricted to users with more than 42 repositories and over 1,000 followers.\n\nThis endpoint does not accept authentication and will only include publicly visible users. As an alternative, you can use the GraphQL API. The GraphQL API requires authentication and will return private users, including Enterprise Managed Users (EMUs), that you are authorized to view. For more information, see \"[GraphQL Queries](https://docs.github.com/graphql/reference/queries#search).\"",
    "tags": [
        "search"
    ],
    "operationId": "search/users",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/search/search#search-users"
    },
    "parameters": [
        {
            "name": "q",
            "description": "The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See \"[Searching users](https://docs.github.com/search-github/searching-on-github/searching-users)\" for a detailed list of qualifiers.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "sort",
            "description": "Sorts the results of your query by number of `followers` or `repositories`, or when the person `joined` GitHub. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "followers",
                    "repositories",
                    "joined"
                ]
            }
        },
        {
            "$ref": "#/components/parameters/order"
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
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "required": [
                            "total_count",
                            "incomplete_results",
                            "items"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "incomplete_results": {
                                "type": "boolean"
                            },
                            "items": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/user-search-result-item"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/user-search-result-item-paginated"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "search",
        "subcategory": "search"
    }
}
```

## References

### `#/components/parameters/order`

```json
{
    "name": "order",
    "description": "Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "desc",
            "asc"
        ],
        "default": "desc"
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

### `#/components/schemas/user-search-result-item`

```json
{
    "title": "User Search Result Item",
    "description": "User Search Result Item",
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
        "received_events_url": {
            "type": "string",
            "format": "uri"
        },
        "type": {
            "type": "string"
        },
        "score": {
            "type": "number"
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
        "events_url": {
            "type": "string"
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
        "name": {
            "type": "string",
            "nullable": true
        },
        "bio": {
            "type": "string",
            "nullable": true
        },
        "email": {
            "type": "string",
            "format": "email",
            "nullable": true
        },
        "location": {
            "type": "string",
            "nullable": true
        },
        "site_admin": {
            "type": "boolean"
        },
        "hireable": {
            "type": "boolean",
            "nullable": true
        },
        "text_matches": {
            "$ref": "#/components/schemas/search-result-text-matches"
        },
        "blog": {
            "type": "string",
            "nullable": true
        },
        "company": {
            "type": "string",
            "nullable": true
        },
        "suspended_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
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
        "score"
    ]
}
```

### `#/components/examples/user-search-result-item-paginated`

```json
{
    "value": {
        "total_count": 12,
        "incomplete_results": false,
        "items": [
            {
                "login": "mojombo",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://secure.gravatar.com/avatar/25c7c18223fb42a4c6ae1c8db6f50f9b?d=https://a248.e.akamai.net/assets.github.com%2Fimages%2Fgravatars%2Fgravatar-user-420.png",
                "gravatar_id": "",
                "url": "https://api.github.com/users/mojombo",
                "html_url": "https://github.com/mojombo",
                "followers_url": "https://api.github.com/users/mojombo/followers",
                "subscriptions_url": "https://api.github.com/users/mojombo/subscriptions",
                "organizations_url": "https://api.github.com/users/mojombo/orgs",
                "repos_url": "https://api.github.com/users/mojombo/repos",
                "received_events_url": "https://api.github.com/users/mojombo/received_events",
                "type": "User",
                "score": 1,
                "following_url": "https://api.github.com/users/mojombo/following{/other_user}",
                "gists_url": "https://api.github.com/users/mojombo/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/mojombo/starred{/owner}{/repo}",
                "events_url": "https://api.github.com/users/mojombo/events{/privacy}",
                "site_admin": true
            }
        ]
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```