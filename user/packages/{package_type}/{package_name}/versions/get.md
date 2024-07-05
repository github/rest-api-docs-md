# List package versions for a package owned by the authenticated user

Lists package versions for a package owned by the authenticated user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "List package versions for a package owned by the authenticated user",
    "description": "Lists package versions for a package owned by the authenticated user.\n\nOAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/get-all-package-versions-for-package-owned-by-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#list-package-versions-for-a-package-owned-by-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/package-type"
        },
        {
            "$ref": "#/components/parameters/package-name"
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
                            "$ref": "#/components/examples/package-versions-for-authenticated-user"
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

### `#/components/examples/package-versions-for-authenticated-user`

```json
{
    "value": [
        {
            "id": 45763,
            "name": "sha256:08a44bab0bddaddd8837a8b381aebc2e4b933768b981685a9e088360af0d3dd9",
            "url": "https://api.github.com/users/octocat/packages/container/hello_docker/versions/45763",
            "package_html_url": "https://github.com/users/octocat/packages/container/package/hello_docker",
            "created_at": "2020-09-11T21:56:40Z",
            "updated_at": "2021-02-05T21:32:32Z",
            "html_url": "https://github.com/users/octocat/packages/container/hello_docker/45763",
            "metadata": {
                "package_type": "container",
                "container": {
                    "tags": [
                        "latest"
                    ]
                }
            }
        },
        {
            "id": 881,
            "name": "sha256:b3d3e366b55f9a54599220198b3db5da8f53592acbbb7dc7e4e9878762fc5344",
            "url": "https://api.github.com/users/octocat/packages/container/hello_docker/versions/881",
            "package_html_url": "https://github.com/users/octocat/packages/container/package/hello_docker",
            "created_at": "2020-05-21T22:22:20Z",
            "updated_at": "2021-02-05T21:32:32Z",
            "html_url": "https://github.com/users/octocat/packages/container/hello_docker/881",
            "metadata": {
                "package_type": "container",
                "container": {
                    "tags": []
                }
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