# Get a reference

`get /repos/{owner}/{repo}/git/ref/{ref}`

Returns a single reference from your Git database. The `:ref` in the URL must be formatted as `heads/<branch name>` for branches and `tags/<tag name>` for tags. If the `:ref` doesn't match an existing ref, a `404` is returned.

**Note:** You need to explicitly [request a pull request](https://docs.github.com/rest/pulls/pulls#get-a-pull-request) to trigger a test merge commit, which checks the mergeability of pull requests. For more information, see "[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)".

## Operation Object

```json
{
    "summary": "Get a reference",
    "description": "Returns a single reference from your Git database. The `:ref` in the URL must be formatted as `heads/<branch name>` for branches and `tags/<tag name>` for tags. If the `:ref` doesn't match an existing ref, a `404` is returned.\n\n**Note:** You need to explicitly [request a pull request](https://docs.github.com/rest/pulls/pulls#get-a-pull-request) to trigger a test merge commit, which checks the mergeability of pull requests. For more information, see \"[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)\".",
    "tags": [
        "git"
    ],
    "operationId": "git/get-ref",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/git/refs#get-a-reference"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/git-ref-only"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/git-ref"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/git-ref"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "409": {
            "$ref": "#/components/responses/conflict"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "git",
        "subcategory": "refs"
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

### `#/components/parameters/git-ref-only`

```json
{
    "name": "ref",
    "description": "The Git reference. For more information, see \"[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)\" in the Git documentation.",
    "in": "path",
    "required": true,
    "example": "heads/feature-a",
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/git-ref`

```json
{
    "title": "Git Reference",
    "description": "Git references within a repository",
    "type": "object",
    "properties": {
        "ref": {
            "type": "string"
        },
        "node_id": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "object": {
            "type": "object",
            "properties": {
                "type": {
                    "type": "string"
                },
                "sha": {
                    "description": "SHA for the reference",
                    "example": "7638417db6d59f3c431d3e1f261cc637155684cd",
                    "type": "string",
                    "minLength": 40,
                    "maxLength": 40
                },
                "url": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "type",
                "sha",
                "url"
            ]
        }
    },
    "required": [
        "ref",
        "node_id",
        "url",
        "object"
    ]
}
```

### `#/components/examples/git-ref`

```json
{
    "value": {
        "ref": "refs/heads/featureA",
        "node_id": "MDM6UmVmcmVmcy9oZWFkcy9mZWF0dXJlQQ==",
        "url": "https://api.github.com/repos/octocat/Hello-World/git/refs/heads/featureA",
        "object": {
            "type": "commit",
            "sha": "aa218f56b14c9653891f9e74264a383fa43fefbd",
            "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/aa218f56b14c9653891f9e74264a383fa43fefbd"
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

### `#/components/responses/conflict`

```json
{
    "description": "Conflict",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```