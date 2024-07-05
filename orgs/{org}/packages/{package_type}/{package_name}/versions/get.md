# List package versions for a package owned by an organization

Lists package versions for a package owned by an organization.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint if the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "List package versions for a package owned by an organization",
    "description": "Lists package versions for a package owned by an organization.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint if the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/get-all-package-versions-for-package-owned-by-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#list-package-versions-for-a-package-owned-by-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/package-type"
        },
        {
            "$ref": "#/components/parameters/package-name"
        },
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "name": "state",
            "in": "query",
            "required": false,
            "description": "The state of the package, either active or deleted.",
            "schema": {
                "type": "string",
                "enum": [
                    "active",
                    "deleted"
                ],
                "default": "active"
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
                            "$ref": "#/components/schemas/package-version"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/package-versions-for-org"
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
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "packages",
        "subcategory": "packages"
    }
}
```

## References

### `#/components/parameters/package-type`

```json
{
    "name": "package_type",
    "description": "The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string",
        "enum": [
            "npm",
            "maven",
            "rubygems",
            "docker",
            "nuget",
            "container"
        ]
    }
}
```

### `#/components/parameters/package-name`

```json
{
    "name": "package_name",
    "description": "The name of the package.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

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

### `#/components/schemas/package-version`

```json
{
    "title": "Package Version",
    "description": "A version of a software package",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the package version.",
            "type": "integer",
            "example": 1
        },
        "name": {
            "description": "The name of the package version.",
            "type": "string",
            "example": "latest"
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/packages/container/super-linter/versions/786068"
        },
        "package_html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/package/super-linter"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/super-linter/786068"
        },
        "license": {
            "type": "string",
            "example": "MIT"
        },
        "description": {
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-10T20:09:31Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2014-03-03T18:58:10Z"
        },
        "deleted_at": {
            "type": "string",
            "format": "date-time",
            "example": "2014-03-03T18:58:10Z"
        },
        "metadata": {
            "type": "object",
            "title": "Package Version Metadata",
            "properties": {
                "package_type": {
                    "type": "string",
                    "example": "docker",
                    "enum": [
                        "npm",
                        "maven",
                        "rubygems",
                        "docker",
                        "nuget",
                        "container"
                    ]
                },
                "container": {
                    "type": "object",
                    "title": "Container Metadata",
                    "properties": {
                        "tags": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        }
                    },
                    "required": [
                        "tags"
                    ]
                },
                "docker": {
                    "type": "object",
                    "title": "Docker Metadata",
                    "properties": {
                        "tag": {
                            "type": "array",
                            "items": {
                                "type": "string"
                            }
                        }
                    },
                    "required": [
                        "tags"
                    ]
                }
            },
            "required": [
                "package_type"
            ]
        }
    },
    "required": [
        "id",
        "name",
        "url",
        "package_html_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/package-versions-for-org`

```json
{
    "value": [
        {
            "id": 245301,
            "name": "1.0.4",
            "url": "https://api.github.com/orgs/octo-org/packages/npm/hello-world-npm/versions/245301",
            "package_html_url": "https://github.com/octo-org/hello-world-npm/packages/43752",
            "created_at": "2019-11-05T22:49:04Z",
            "updated_at": "2019-11-05T22:49:04Z",
            "html_url": "https://github.com/octo-org/hello-world-npm/packages/43752?version=1.0.4",
            "metadata": {
                "package_type": "npm"
            }
        },
        {
            "id": 209672,
            "name": "1.0.3",
            "url": "https://api.github.com/orgs/octo-org/packages/npm/hello-world-npm/versions/209672",
            "package_html_url": "https://github.com/octo-org/hello-world-npm/packages/43752",
            "created_at": "2019-10-29T15:42:11Z",
            "updated_at": "2019-10-29T15:42:12Z",
            "html_url": "https://github.com/octo-org/hello-world-npm/packages/43752?version=1.0.3",
            "metadata": {
                "package_type": "npm"
            }
        }
    ]
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

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```