# List custom property values for organization repositories

Lists organization repositories with all of their custom property values.
Organization members can read these properties.

## Operation Object

```json
{
    "summary": "List custom property values for organization repositories",
    "description": "Lists organization repositories with all of their custom property values.\nOrganization members can read these properties.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-custom-properties-values-for-repos",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/custom-properties#list-custom-property-values-for-organization-repositories"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "name": "repository_query",
            "description": "Finds repositories in the organization with a query containing one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See \"[Searching for repositories](https://docs.github.com/articles/searching-for-repositories/)\" for a detailed list of qualifiers.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
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
                            "$ref": "#/components/schemas/org-repo-custom-property-values"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-repo-custom-property-values"
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
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "custom-properties"
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

### `#/components/schemas/org-repo-custom-property-values`

```json
{
    "title": "Organization Repository Custom Property Values",
    "description": "List of custom property values for a repository",
    "type": "object",
    "properties": {
        "repository_id": {
            "type": "integer",
            "example": 1296269
        },
        "repository_name": {
            "type": "string",
            "example": "Hello-World"
        },
        "repository_full_name": {
            "type": "string",
            "example": "octocat/Hello-World"
        },
        "properties": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/custom-property-value"
            },
            "description": "List of custom property names and associated values"
        }
    },
    "required": [
        "repository_id",
        "repository_name",
        "repository_full_name",
        "properties"
    ]
}
```

### `#/components/examples/org-repo-custom-property-values`

```json
{
    "value": [
        {
            "repository_id": 1296269,
            "repository_name": "Hello-World",
            "repository_full_name": "octocat/Hello-World",
            "properties": [
                {
                    "property_name": "environment",
                    "value": "production"
                },
                {
                    "property_name": "service",
                    "value": "web"
                },
                {
                    "property_name": "team",
                    "value": "octocat"
                }
            ]
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