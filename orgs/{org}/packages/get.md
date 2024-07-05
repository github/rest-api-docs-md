# List packages for an organization

`get /orgs/{org}/packages`

Lists packages in an organization readable by the user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "List packages for an organization",
    "description": "Lists packages in an organization readable by the user.\n\nOAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/list-packages-for-organization",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#list-packages-for-an-organization"
    },
    "parameters": [
        {
            "name": "package_type",
            "description": "The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.",
            "in": "query",
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
        },
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/package-visibility"
        },
        {
            "name": "page",
            "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 1
            }
        },
        {
            "name": "per_page",
            "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 30
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
                            "$ref": "#/components/schemas/package"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/packages-for-org"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "400": {
            "$ref": "#/components/responses/package_es_list_error"
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

### `#/components/parameters/package-visibility`

```json
{
    "name": "visibility",
    "description": "The selected visibility of the packages.  This parameter is optional and only filters an existing result set.\n\nThe `internal` visibility is only supported for GitHub Packages registries that allow for granular permissions. For other ecosystems `internal` is synonymous with `private`.\nFor the list of GitHub Packages registries that support granular permissions, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#granular-permissions-for-userorganization-scoped-packages).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "public",
            "private",
            "internal"
        ]
    }
}
```

### `#/components/schemas/package`

```json
{
    "title": "Package",
    "description": "A software package",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the package.",
            "type": "integer",
            "example": 1
        },
        "name": {
            "description": "The name of the package.",
            "type": "string",
            "example": "super-linter"
        },
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
        "url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/packages/container/super-linter"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/package/super-linter"
        },
        "version_count": {
            "description": "The number of versions of the package.",
            "type": "integer",
            "example": 1
        },
        "visibility": {
            "type": "string",
            "example": "private",
            "enum": [
                "private",
                "public"
            ]
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "repository": {
            "$ref": "#/components/schemas/nullable-minimal-repository"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "id",
        "name",
        "package_type",
        "visibility",
        "url",
        "html_url",
        "version_count",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/packages-for-org`

```json
{
    "value": [
        {
            "id": 197,
            "name": "hello_docker",
            "package_type": "container",
            "owner": {
                "login": "github",
                "id": 9919,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
                "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/github",
                "html_url": "https://github.com/github",
                "followers_url": "https://api.github.com/users/github/followers",
                "following_url": "https://api.github.com/users/github/following{/other_user}",
                "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/github/subscriptions",
                "organizations_url": "https://api.github.com/users/github/orgs",
                "repos_url": "https://api.github.com/users/github/repos",
                "events_url": "https://api.github.com/users/github/events{/privacy}",
                "received_events_url": "https://api.github.com/users/github/received_events",
                "type": "Organization",
                "site_admin": false
            },
            "version_count": 1,
            "visibility": "private",
            "url": "https://api.github.com/orgs/github/packages/container/hello_docker",
            "created_at": "2020-05-19T22:19:11Z",
            "updated_at": "2020-05-19T22:19:11Z",
            "html_url": "https://github.com/orgs/github/packages/container/package/hello_docker"
        },
        {
            "id": 198,
            "name": "goodbye_docker",
            "package_type": "container",
            "owner": {
                "login": "github",
                "id": 9919,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
                "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/github",
                "html_url": "https://github.com/github",
                "followers_url": "https://api.github.com/users/github/followers",
                "following_url": "https://api.github.com/users/github/following{/other_user}",
                "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/github/subscriptions",
                "organizations_url": "https://api.github.com/users/github/orgs",
                "repos_url": "https://api.github.com/users/github/repos",
                "events_url": "https://api.github.com/users/github/events{/privacy}",
                "received_events_url": "https://api.github.com/users/github/received_events",
                "type": "Organization",
                "site_admin": false
            },
            "version_count": 2,
            "visibility": "private",
            "url": "https://api.github.com/orgs/github/packages/container/goodbye_docker",
            "created_at": "2020-05-20T22:19:11Z",
            "updated_at": "2020-05-20T22:19:11Z",
            "html_url": "https://github.com/orgs/github/packages/container/package/goodbye_docker"
        }
    ]
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

### `#/components/responses/package_es_list_error`

```json
{
    "description": "The value of `per_page` multiplied by `page` cannot be greater than 10000."
}
```