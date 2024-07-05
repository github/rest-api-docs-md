# Get all commonly used licenses

`get /licenses`

Lists the most commonly used licenses on GitHub. For more information, see "[Licensing a repository ](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)."

## Operation Object

```json
{
    "summary": "Get all commonly used licenses",
    "description": "Lists the most commonly used licenses on GitHub. For more information, see \"[Licensing a repository ](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository).\"",
    "tags": [
        "licenses"
    ],
    "operationId": "licenses/get-all-commonly-used",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/licenses/licenses#get-all-commonly-used-licenses"
    },
    "parameters": [
        {
            "name": "featured",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/license-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/license-simple-items"
                        }
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
        "category": "licenses",
        "subcategory": "licenses"
    }
}
```

## References

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

### `#/components/schemas/license-simple`

```json
{
    "title": "License Simple",
    "description": "License Simple",
    "type": "object",
    "properties": {
        "key": {
            "type": "string",
            "example": "mit"
        },
        "name": {
            "type": "string",
            "example": "MIT License"
        },
        "url": {
            "type": "string",
            "nullable": true,
            "format": "uri",
            "example": "https://api.github.com/licenses/mit"
        },
        "spdx_id": {
            "type": "string",
            "nullable": true,
            "example": "MIT"
        },
        "node_id": {
            "type": "string",
            "example": "MDc6TGljZW5zZW1pdA=="
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        }
    },
    "required": [
        "key",
        "name",
        "url",
        "spdx_id",
        "node_id"
    ]
}
```

### `#/components/examples/license-simple-items`

```json
{
    "value": [
        {
            "key": "mit",
            "name": "MIT License",
            "spdx_id": "MIT",
            "url": "https://api.github.com/licenses/mit",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "lgpl-3.0",
            "name": "GNU Lesser General Public License v3.0",
            "spdx_id": "LGPL-3.0",
            "url": "https://api.github.com/licenses/lgpl-3.0",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "mpl-2.0",
            "name": "Mozilla Public License 2.0",
            "spdx_id": "MPL-2.0",
            "url": "https://api.github.com/licenses/mpl-2.0",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "agpl-3.0",
            "name": "GNU Affero General Public License v3.0",
            "spdx_id": "AGPL-3.0",
            "url": "https://api.github.com/licenses/agpl-3.0",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "unlicense",
            "name": "The Unlicense",
            "spdx_id": "Unlicense",
            "url": "https://api.github.com/licenses/unlicense",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "apache-2.0",
            "name": "Apache License 2.0",
            "spdx_id": "Apache-2.0",
            "url": "https://api.github.com/licenses/apache-2.0",
            "node_id": "MDc6TGljZW5zZW1pdA=="
        },
        {
            "key": "gpl-3.0",
            "name": "GNU General Public License v3.0",
            "spdx_id": "GPL-3.0",
            "url": "https://api.github.com/licenses/gpl-3.0",
            "node_id": "MDc6TGljZW5zZW1pdA=="
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