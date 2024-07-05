# Get a GitHub Pages site

Gets information about a GitHub Pages site.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a GitHub Pages site",
    "description": "Gets information about a GitHub Pages site.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-pages",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pages/pages#get-a-apiname-pages-site"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/page"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/page"
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
        "category": "pages",
        "subcategory": "pages"
    }
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/page`

```json
{
    "title": "GitHub Pages",
    "description": "The configuration for GitHub Pages for a repository.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "description": "The API address for accessing this Page resource.",
            "format": "uri",
            "example": "https://api.github.com/repos/github/hello-world/pages"
        },
        "status": {
            "type": "string",
            "description": "The status of the most recent build of the Page.",
            "example": "built",
            "enum": [
                "built",
                "building",
                "errored"
            ],
            "nullable": true
        },
        "cname": {
            "description": "The Pages site's custom domain",
            "example": "example.com",
            "type": "string",
            "nullable": true
        },
        "protected_domain_state": {
            "type": "string",
            "description": "The state if the domain is verified",
            "example": "pending",
            "nullable": true,
            "enum": [
                "pending",
                "verified",
                "unverified"
            ]
        },
        "pending_domain_unverified_at": {
            "type": "string",
            "description": "The timestamp when a pending domain becomes unverified.",
            "nullable": true,
            "format": "date-time"
        },
        "custom_404": {
            "type": "boolean",
            "description": "Whether the Page has a custom 404 page.",
            "example": false,
            "default": false
        },
        "html_url": {
            "type": "string",
            "description": "The web address the Page can be accessed from.",
            "format": "uri",
            "example": "https://example.com"
        },
        "build_type": {
            "type": "string",
            "description": "The process in which the Page will be built.",
            "example": "legacy",
            "nullable": true,
            "enum": [
                "legacy",
                "workflow"
            ]
        },
        "source": {
            "$ref": "#/components/schemas/pages-source-hash"
        },
        "public": {
            "type": "boolean",
            "description": "Whether the GitHub Pages site is publicly visible. If set to `true`, the site is accessible to anyone on the internet. If set to `false`, the site will only be accessible to users who have at least `read` access to the repository that published the site.",
            "example": true
        },
        "https_certificate": {
            "$ref": "#/components/schemas/pages-https-certificate"
        },
        "https_enforced": {
            "type": "boolean",
            "description": "Whether https is enabled on the domain",
            "example": true
        }
    },
    "required": [
        "url",
        "status",
        "cname",
        "custom_404",
        "public"
    ]
}
```

### `#/components/examples/page`

```json
{
    "value": {
        "url": "https://api.github.com/repos/github/developer.github.com/pages",
        "status": "built",
        "cname": "developer.github.com",
        "custom_404": false,
        "html_url": "https://developer.github.com",
        "source": {
            "branch": "master",
            "path": "/"
        },
        "public": true,
        "pending_domain_unverified_at": "2024-04-30T19:33:31Z",
        "protected_domain_state": "verified",
        "https_certificate": {
            "state": "approved",
            "description": "Certificate is approved",
            "domains": [
                "developer.github.com"
            ],
            "expires_at": "2021-05-22"
        },
        "https_enforced": true
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