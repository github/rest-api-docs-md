# List package versions for a package owned by a user

`get /users/{username}/packages/{package_type}/{package_name}/versions`

Lists package versions for a public package owned by a specified user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "List package versions for a package owned by a user",
    "description": "Lists package versions for a public package owned by a specified user.\n\nOAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/get-all-package-versions-for-package-owned-by-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#list-package-versions-for-a-package-owned-by-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/package-type"
        },
        {
            "$ref": "#/components/parameters/package-name"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/package-version"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/package-versions-for-user"
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

### `#/components/examples/package-versions-for-user`

```json
{
    "value": [
        {
            "id": 3497268,
            "name": "0.3.0",
            "url": "https://api.github.com/users/octocat/packages/rubygems/octo-name/versions/3497268",
            "package_html_url": "https://github.com/octocat/octo-name-repo/packages/40201",
            "license": "MIT",
            "created_at": "2020-08-31T15:22:11Z",
            "updated_at": "2020-08-31T15:22:12Z",
            "description": "Project for octocats",
            "html_url": "https://github.com/octocat/octo-name-repo/packages/40201?version=0.3.0",
            "metadata": {
                "package_type": "rubygems"
            }
        },
        {
            "id": 387039,
            "name": "0.2.0",
            "url": "https://api.github.com/users/octocat/packages/rubygems/octo-name/versions/387039",
            "package_html_url": "https://github.com/octocat/octo-name-repo/packages/40201",
            "license": "MIT",
            "created_at": "2019-12-01T20:49:29Z",
            "updated_at": "2019-12-01T20:49:30Z",
            "description": "Project for octocats",
            "html_url": "https://github.com/octocat/octo-name-repo/packages/40201?version=0.2.0",
            "metadata": {
                "package_type": "rubygems"
            }
        },
        {
            "id": 169770,
            "name": "0.1.0",
            "url": "https://api.github.com/users/octocat/packages/rubygems/octo-name/versions/169770",
            "package_html_url": "https://github.com/octocat/octo-name-repo/packages/40201",
            "license": "MIT",
            "created_at": "2019-10-20T14:17:14Z",
            "updated_at": "2019-10-20T14:17:15Z",
            "html_url": "https://github.com/octocat/octo-name-repo/packages/40201?version=0.1.0",
            "metadata": {
                "package_type": "rubygems"
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