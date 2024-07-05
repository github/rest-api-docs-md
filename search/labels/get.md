# Search labels

Find labels in a repository with names or descriptions that match search keywords. Returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for labels, you can get text match metadata for the label **name** and **description** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to find labels in the `linguist` repository that match `bug`, `defect`, or `enhancement`. Your query might look like this:

`q=bug+defect+enhancement&repository_id=64778136`

The labels that best match the query appear first in the search results.

## Operation Object

```json
{
    "summary": "Search labels",
    "description": "Find labels in a repository with names or descriptions that match search keywords. Returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).\n\nWhen searching for labels, you can get text match metadata for the label **name** and **description** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).\n\nFor example, if you want to find labels in the `linguist` repository that match `bug`, `defect`, or `enhancement`. Your query might look like this:\n\n`q=bug+defect+enhancement&repository_id=64778136`\n\nThe labels that best match the query appear first in the search results.",
    "tags": [
        "search"
    ],
    "operationId": "search/labels",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/search/search#search-labels"
    },
    "parameters": [
        {
            "name": "repository_id",
            "description": "The id of the repository.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "integer"
            }
        },
        {
            "name": "q",
            "description": "The search keywords. This endpoint does not accept qualifiers in the query. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query).",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "sort",
            "description": "Sorts the results of your query by when the label was `created` or `updated`. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "created",
                    "updated"
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
                                    "$ref": "#/components/schemas/label-search-result-item"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/label-search-result-item-paginated"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
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

### `#/components/schemas/label-search-result-item`

```json
{
    "title": "Label Search Result Item",
    "description": "Label Search Result Item",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "name": {
            "type": "string"
        },
        "color": {
            "type": "string"
        },
        "default": {
            "type": "boolean"
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "score": {
            "type": "number"
        },
        "text_matches": {
            "$ref": "#/components/schemas/search-result-text-matches"
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "name",
        "color",
        "default",
        "description",
        "score"
    ]
}
```

### `#/components/examples/label-search-result-item-paginated`

```json
{
    "value": {
        "total_count": 2,
        "incomplete_results": false,
        "items": [
            {
                "id": 418327088,
                "node_id": "MDU6TGFiZWw0MTgzMjcwODg=",
                "url": "https://api.github.com/repos/octocat/linguist/labels/enhancement",
                "name": "enhancement",
                "color": "84b6eb",
                "default": true,
                "description": "New feature or request.",
                "score": 1
            },
            {
                "id": 418327086,
                "node_id": "MDU6TGFiZWw0MTgzMjcwODY=",
                "url": "https://api.github.com/repos/octocat/linguist/labels/bug",
                "name": "bug",
                "color": "ee0701",
                "default": true,
                "description": "Something isn't working.",
                "score": 1
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