# Get a tree

`get /repos/{owner}/{repo}/git/trees/{tree_sha}`

Returns a single tree using the SHA1 value or ref name for that tree.

If `truncated` is `true` in the response then the number of items in the `tree` array exceeded our maximum limit. If you need to fetch more items, use the non-recursive method of fetching trees, and fetch one sub-tree at a time.


**Note**: The limit for the `tree` array is 100,000 entries with a maximum size of 7 MB when using the `recursive` parameter.

## Operation Object

```json
{
    "summary": "Get a tree",
    "description": "Returns a single tree using the SHA1 value or ref name for that tree.\n\nIf `truncated` is `true` in the response then the number of items in the `tree` array exceeded our maximum limit. If you need to fetch more items, use the non-recursive method of fetching trees, and fetch one sub-tree at a time.\n\n\n**Note**: The limit for the `tree` array is 100,000 entries with a maximum size of 7 MB when using the `recursive` parameter.",
    "tags": [
        "git"
    ],
    "operationId": "git/get-tree",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/git/trees#get-a-tree"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "tree_sha",
            "description": "The SHA1 value or ref (branch or tag) name of the tree.",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            },
            "x-multi-segment": true
        },
        {
            "name": "recursive",
            "description": "Setting this parameter to any value returns the objects or subtrees referenced by the tree specified in `:tree_sha`. For example, setting `recursive` to any of the following will enable returning objects or subtrees: `0`, `1`, `\"true\"`, and `\"false\"`. Omit this parameter to prevent recursively returning objects or subtrees.",
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
                        "$ref": "#/components/schemas/git-tree"
                    },
                    "examples": {
                        "default-response": {
                            "$ref": "#/components/examples/git-tree-default-response"
                        },
                        "response-recursively-retrieving-a-tree": {
                            "$ref": "#/components/examples/git-tree-response-recursively-retrieving-a-tree"
                        }
                    }
                }
            }
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
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
        "subcategory": "trees"
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

### `#/components/schemas/git-tree`

```json
{
    "title": "Git Tree",
    "description": "The hierarchy between files in a Git repository.",
    "type": "object",
    "properties": {
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "truncated": {
            "type": "boolean"
        },
        "tree": {
            "description": "Objects specifying a tree structure",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "path": {
                        "type": "string",
                        "example": "test/file.rb"
                    },
                    "mode": {
                        "type": "string",
                        "example": "040000"
                    },
                    "type": {
                        "type": "string",
                        "example": "tree"
                    },
                    "sha": {
                        "type": "string",
                        "example": "23f6827669e43831def8a7ad935069c8bd418261"
                    },
                    "size": {
                        "type": "integer",
                        "example": 12
                    },
                    "url": {
                        "type": "string",
                        "example": "https://api.github.com/repos/owner-482f3203ecf01f67e9deb18e/BBB_Private_Repo/git/blobs/23f6827669e43831def8a7ad935069c8bd418261"
                    }
                }
            },
            "example": [
                {
                    "path": "file.rb",
                    "mode": "100644",
                    "type": "blob",
                    "size": 30,
                    "sha": "44b4fc6d56897b048c772eb4087f854f46256132",
                    "url": "https://api.github.com/repos/octocat/Hello-World/git/blobs/44b4fc6d56897b048c772eb4087f854f46256132",
                    "properties": {
                        "path": {
                            "type": "string"
                        },
                        "mode": {
                            "type": "string"
                        },
                        "type": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        },
                        "sha": {
                            "type": "string"
                        },
                        "url": {
                            "type": "string"
                        }
                    },
                    "required": [
                        "path",
                        "mode",
                        "type",
                        "sha",
                        "url",
                        "size"
                    ]
                }
            ]
        }
    },
    "required": [
        "sha",
        "url",
        "tree",
        "truncated"
    ]
}
```

### `#/components/examples/git-tree-default-response`

```json
{
    "summary": "Default response",
    "value": {
        "sha": "9fb037999f264ba9a7fc6274d15fa3ae2ab98312",
        "url": "https://api.github.com/repos/octocat/Hello-World/trees/9fb037999f264ba9a7fc6274d15fa3ae2ab98312",
        "tree": [
            {
                "path": "file.rb",
                "mode": "100644",
                "type": "blob",
                "size": 30,
                "sha": "44b4fc6d56897b048c772eb4087f854f46256132",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/blobs/44b4fc6d56897b048c772eb4087f854f46256132"
            },
            {
                "path": "subdir",
                "mode": "040000",
                "type": "tree",
                "sha": "f484d249c660418515fb01c2b9662073663c242e",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/blobs/f484d249c660418515fb01c2b9662073663c242e"
            },
            {
                "path": "exec_file",
                "mode": "100755",
                "type": "blob",
                "size": 75,
                "sha": "45b983be36b73c0788dc9cbcb76cbb80fc7bb057",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/blobs/45b983be36b73c0788dc9cbcb76cbb80fc7bb057"
            }
        ],
        "truncated": false
    }
}
```

### `#/components/examples/git-tree-response-recursively-retrieving-a-tree`

```json
{
    "summary": "Response recursively retrieving a tree",
    "value": {
        "sha": "fc6274d15fa3ae2ab983129fb037999f264ba9a7",
        "url": "https://api.github.com/repos/octocat/Hello-World/trees/fc6274d15fa3ae2ab983129fb037999f264ba9a7",
        "tree": [
            {
                "path": "subdir/file.txt",
                "mode": "100644",
                "type": "blob",
                "size": 132,
                "sha": "7c258a9869f33c1e1e1f74fbb32f07c86cb5a75b",
                "url": "https://api.github.com/repos/octocat/Hello-World/git/7c258a9869f33c1e1e1f74fbb32f07c86cb5a75b"
            }
        ],
        "truncated": false
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