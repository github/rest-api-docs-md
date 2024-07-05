# Get a repository README for a directory

Gets the README from a repository directory.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw file contents. This is the default if you do not specify a media type.
- **`application/vnd.github.html+json`**: Returns the README in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).

## Operation Object

```json
{
    "summary": "Get a repository README for a directory",
    "description": "Gets the README from a repository directory.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw file contents. This is the default if you do not specify a media type.\n- **`application/vnd.github.html+json`**: Returns the README in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-readme-in-directory",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/contents#get-a-repository-readme-for-a-directory"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "dir",
            "description": "The alternate path to look for a README file",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            },
            "x-multi-segment": true
        },
        {
            "name": "ref",
            "description": "The name of the commit/branch/tag. Default: the repository\u2019s default branch.",
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
                        "$ref": "#/components/schemas/content-file"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/content-file"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "contents"
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

### `#/components/schemas/content-file`

```json
{
    "title": "Content File",
    "description": "Content File",
    "type": "object",
    "properties": {
        "type": {
            "type": "string",
            "enum": [
                "file"
            ]
        },
        "encoding": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        },
        "name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "content": {
            "type": "string"
        },
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "download_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "_links": {
            "type": "object",
            "properties": {
                "git": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "git",
                "html",
                "self"
            ]
        },
        "target": {
            "type": "string",
            "example": "\"actual/actual.md\""
        },
        "submodule_git_url": {
            "type": "string",
            "example": "\"git://example.com/defunkt/dotjs.git\""
        }
    },
    "required": [
        "_links",
        "git_url",
        "html_url",
        "download_url",
        "name",
        "path",
        "sha",
        "size",
        "type",
        "url",
        "content",
        "encoding"
    ]
}
```

### `#/components/examples/content-file`

```json
{
    "value": {
        "type": "file",
        "encoding": "base64",
        "size": 5362,
        "name": "README.md",
        "path": "README.md",
        "content": "encoded content ...",
        "sha": "3d21ec53a331a6f037a91c368710b99387d012c1",
        "url": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
        "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
        "html_url": "https://github.com/octokit/octokit.rb/blob/master/README.md",
        "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md",
        "_links": {
            "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
            "self": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
            "html": "https://github.com/octokit/octokit.rb/blob/master/README.md"
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