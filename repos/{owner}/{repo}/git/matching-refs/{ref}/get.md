# List matching references

Returns an array of references from your Git database that match the supplied name. The `:ref` in the URL must be formatted as `heads/<branch name>` for branches and `tags/<tag name>` for tags. If the `:ref` doesn't exist in the repository, but existing refs start with `:ref`, they will be returned as an array.

When you use this endpoint without providing a `:ref`, it will return an array of all the references from your Git database, including notes and stashes if they exist on the server. Anything in the namespace is returned, not just `heads` and `tags`.

**Note:** You need to explicitly [request a pull request](https://docs.github.com/rest/pulls/pulls#get-a-pull-request) to trigger a test merge commit, which checks the mergeability of pull requests. For more information, see "[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)".

If you request matching references for a branch named `feature` but the branch `feature` doesn't exist, the response can still include other matching head refs that start with the word `feature`, such as `featureA` and `featureB`.

## Operation Object

```json
{
    "summary": "List matching references",
    "description": "Returns an array of references from your Git database that match the supplied name. The `:ref` in the URL must be formatted as `heads/<branch name>` for branches and `tags/<tag name>` for tags. If the `:ref` doesn't exist in the repository, but existing refs start with `:ref`, they will be returned as an array.\n\nWhen you use this endpoint without providing a `:ref`, it will return an array of all the references from your Git database, including notes and stashes if they exist on the server. Anything in the namespace is returned, not just `heads` and `tags`.\n\n**Note:** You need to explicitly [request a pull request](https://docs.github.com/rest/pulls/pulls#get-a-pull-request) to trigger a test merge commit, which checks the mergeability of pull requests. For more information, see \"[Checking mergeability of pull requests](https://docs.github.com/rest/guides/getting-started-with-the-git-database-api#checking-mergeability-of-pull-requests)\".\n\nIf you request matching references for a branch named `feature` but the branch `feature` doesn't exist, the response can still include other matching head refs that start with the word `feature`, such as `featureA` and `featureB`.",
    "tags": [
        "git"
    ],
    "operationId": "git/list-matching-refs",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/git/refs#list-matching-references"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/git-ref"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/git-ref-items"
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

### `#/components/examples/git-ref-items`

```json
{
    "value": [
        {
            "ref": "refs/heads/feature-a",
            "node_id": "MDM6UmVmcmVmcy9oZWFkcy9mZWF0dXJlLWE=",
            "url": "https://api.github.com/repos/octocat/Hello-World/git/refs/heads/feature-a",
            "object": {
                "type": "commit",
                "sha": "aa218f56b14c9653891f9e74264a383fa43fefbd",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/aa218f56b14c9653891f9e74264a383fa43fefbd"
            }
        },
        {
            "ref": "refs/heads/feature-b",
            "node_id": "MDM6UmVmcmVmcy9oZWFkcy9mZWF0dXJlLWI=",
            "url": "https://api.github.com/repos/octocat/Hello-World/git/refs/heads/feature-b",
            "object": {
                "type": "commit",
                "sha": "612077ae6dffb4d2fbd8ce0cccaa58893b07b5ac",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/612077ae6dffb4d2fbd8ce0cccaa58893b07b5ac"
            }
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