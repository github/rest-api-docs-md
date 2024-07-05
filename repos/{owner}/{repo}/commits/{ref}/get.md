# Get a commit

Returns the contents of a single commit reference. You must have `read` access for the repository to use this endpoint.

**Note:** If there are more than 300 files in the commit diff and the default JSON media type is requested, the response will include pagination link headers for the remaining files, up to a limit of 3000 files. Each page contains the static commit information, and the only changes are to the file listing.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)." Pagination query parameters are not supported for these media types.

- **`application/vnd.github.diff`**: Returns the diff of the commit. Larger diffs may time out and return a 5xx status code.
- **`application/vnd.github.patch`**: Returns the patch of the commit. Diffs with binary data will have no `patch` property. Larger diffs may time out and return a 5xx status code.
- **`application/vnd.github.sha`**: Returns the commit's SHA-1 hash. You can use this endpoint to check if a remote reference's SHA-1 hash is the same as your local reference's SHA-1 hash by providing the local SHA-1 reference as the ETag.

**Signature verification object**

The response will include a `verification` object that describes the result of verifying the commit's signature. The following fields are included in the `verification` object:

| Name | Type | Description |
| ---- | ---- | ----------- |
| `verified` | `boolean` | Indicates whether GitHub considers the signature in this commit to be verified. |
| `reason` | `string` | The reason for verified value. Possible values and their meanings are enumerated in table below. |
| `signature` | `string` | The signature that was extracted from the commit. |
| `payload` | `string` | The value that was signed. |

These are the possible values for `reason` in the `verification` object:

| Value | Description |
| ----- | ----------- |
| `expired_key` | The key that made the signature is expired. |
| `not_signing_key` | The "signing" flag is not among the usage flags in the GPG key that made the signature. |
| `gpgverify_error` | There was an error communicating with the signature verification service. |
| `gpgverify_unavailable` | The signature verification service is currently unavailable. |
| `unsigned` | The object does not include a signature. |
| `unknown_signature_type` | A non-PGP signature was found in the commit. |
| `no_user` | No user was associated with the `committer` email address in the commit. |
| `unverified_email` | The `committer` email address in the commit was associated with a user, but the email address is not verified on their account. |
| `bad_email` | The `committer` email address in the commit is not included in the identities of the PGP key that made the signature. |
| `unknown_key` | The key that made the signature has not been registered with any user's account. |
| `malformed_signature` | There was an error parsing the signature. |
| `invalid` | The signature could not be cryptographically verified using the key whose key-id was found in the signature. |
| `valid` | None of the above errors applied, so the signature is considered to be verified. |

## Operation Object

```json
{
    "summary": "Get a commit",
    "description": "Returns the contents of a single commit reference. You must have `read` access for the repository to use this endpoint.\n\n**Note:** If there are more than 300 files in the commit diff and the default JSON media type is requested, the response will include pagination link headers for the remaining files, up to a limit of 3000 files. Each page contains the static commit information, and the only changes are to the file listing.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\" Pagination query parameters are not supported for these media types.\n\n- **`application/vnd.github.diff`**: Returns the diff of the commit. Larger diffs may time out and return a 5xx status code.\n- **`application/vnd.github.patch`**: Returns the patch of the commit. Diffs with binary data will have no `patch` property. Larger diffs may time out and return a 5xx status code.\n- **`application/vnd.github.sha`**: Returns the commit's SHA-1 hash. You can use this endpoint to check if a remote reference's SHA-1 hash is the same as your local reference's SHA-1 hash by providing the local SHA-1 reference as the ETag.\n\n**Signature verification object**\n\nThe response will include a `verification` object that describes the result of verifying the commit's signature. The following fields are included in the `verification` object:\n\n| Name | Type | Description |\n| ---- | ---- | ----------- |\n| `verified` | `boolean` | Indicates whether GitHub considers the signature in this commit to be verified. |\n| `reason` | `string` | The reason for verified value. Possible values and their meanings are enumerated in table below. |\n| `signature` | `string` | The signature that was extracted from the commit. |\n| `payload` | `string` | The value that was signed. |\n\nThese are the possible values for `reason` in the `verification` object:\n\n| Value | Description |\n| ----- | ----------- |\n| `expired_key` | The key that made the signature is expired. |\n| `not_signing_key` | The \"signing\" flag is not among the usage flags in the GPG key that made the signature. |\n| `gpgverify_error` | There was an error communicating with the signature verification service. |\n| `gpgverify_unavailable` | The signature verification service is currently unavailable. |\n| `unsigned` | The object does not include a signature. |\n| `unknown_signature_type` | A non-PGP signature was found in the commit. |\n| `no_user` | No user was associated with the `committer` email address in the commit. |\n| `unverified_email` | The `committer` email address in the commit was associated with a user, but the email address is not verified on their account. |\n| `bad_email` | The `committer` email address in the commit is not included in the identities of the PGP key that made the signature. |\n| `unknown_key` | The key that made the signature has not been registered with any user's account. |\n| `malformed_signature` | There was an error parsing the signature. |\n| `invalid` | The signature could not be cryptographically verified using the key whose key-id was found in the signature. |\n| `valid` | None of the above errors applied, so the signature is considered to be verified. |",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-commit",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/commits/commits#get-a-commit"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/commit-ref"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/commit"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/commit"
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
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        },
        "409": {
            "$ref": "#/components/responses/conflict"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "commits",
        "subcategory": "commits"
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

### `#/components/parameters/commit-ref`

```json
{
    "name": "ref",
    "description": "The commit reference. Can be a commit SHA, branch name (`heads/BRANCH_NAME`), or tag name (`tags/TAG_NAME`). For more information, see \"[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)\" in the Git documentation.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/commit`

```json
{
    "title": "Commit",
    "description": "Commit",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "sha": {
            "type": "string",
            "example": "6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "node_id": {
            "type": "string",
            "example": "MDY6Q29tbWl0NmRjYjA5YjViNTc4NzVmMzM0ZjYxYWViZWQ2OTVlMmU0MTkzZGI1ZQ=="
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/commit/6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e/comments"
        },
        "commit": {
            "type": "object",
            "properties": {
                "url": {
                    "type": "string",
                    "format": "uri",
                    "example": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e"
                },
                "author": {
                    "$ref": "#/components/schemas/nullable-git-user"
                },
                "committer": {
                    "$ref": "#/components/schemas/nullable-git-user"
                },
                "message": {
                    "type": "string",
                    "example": "Fix all the bugs"
                },
                "comment_count": {
                    "type": "integer",
                    "example": 0
                },
                "tree": {
                    "type": "object",
                    "properties": {
                        "sha": {
                            "type": "string",
                            "example": "827efc6d56897b048c772eb4087f854f46256132"
                        },
                        "url": {
                            "type": "string",
                            "format": "uri",
                            "example": "https://api.github.com/repos/octocat/Hello-World/tree/827efc6d56897b048c772eb4087f854f46256132"
                        }
                    },
                    "required": [
                        "sha",
                        "url"
                    ]
                },
                "verification": {
                    "$ref": "#/components/schemas/verification"
                }
            },
            "required": [
                "author",
                "committer",
                "comment_count",
                "message",
                "tree",
                "url"
            ]
        },
        "author": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "committer": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "parents": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "sha": {
                        "type": "string",
                        "example": "7638417db6d59f3c431d3e1f261cc637155684cd"
                    },
                    "url": {
                        "type": "string",
                        "format": "uri",
                        "example": "https://api.github.com/repos/octocat/Hello-World/commits/7638417db6d59f3c431d3e1f261cc637155684cd"
                    },
                    "html_url": {
                        "type": "string",
                        "format": "uri",
                        "example": "https://github.com/octocat/Hello-World/commit/7638417db6d59f3c431d3e1f261cc637155684cd"
                    }
                },
                "required": [
                    "sha",
                    "url"
                ]
            }
        },
        "stats": {
            "type": "object",
            "properties": {
                "additions": {
                    "type": "integer"
                },
                "deletions": {
                    "type": "integer"
                },
                "total": {
                    "type": "integer"
                }
            }
        },
        "files": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/diff-entry"
            }
        }
    },
    "required": [
        "url",
        "sha",
        "node_id",
        "html_url",
        "comments_url",
        "commit",
        "author",
        "committer",
        "parents"
    ]
}
```

### `#/components/examples/commit`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "node_id": "MDY6Q29tbWl0NmRjYjA5YjViNTc4NzVmMzM0ZjYxYWViZWQ2OTVlMmU0MTkzZGI1ZQ==",
        "html_url": "https://github.com/octocat/Hello-World/commit/6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "comments_url": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e/comments",
        "commit": {
            "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "author": {
                "name": "Monalisa Octocat",
                "email": "mona@github.com",
                "date": "2011-04-14T16:00:49Z"
            },
            "committer": {
                "name": "Monalisa Octocat",
                "email": "mona@github.com",
                "date": "2011-04-14T16:00:49Z"
            },
            "message": "Fix all the bugs",
            "tree": {
                "url": "https://api.github.com/repos/octocat/Hello-World/tree/6dcb09b5b57875f334f61aebed695e2e4193db5e",
                "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e"
            },
            "comment_count": 0,
            "verification": {
                "verified": false,
                "reason": "unsigned",
                "signature": null,
                "payload": null
            }
        },
        "author": {
            "login": "octocat",
            "id": 1,
            "node_id": "MDQ6VXNlcjE=",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "gravatar_id": "",
            "url": "https://api.github.com/users/octocat",
            "html_url": "https://github.com/octocat",
            "followers_url": "https://api.github.com/users/octocat/followers",
            "following_url": "https://api.github.com/users/octocat/following{/other_user}",
            "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
            "organizations_url": "https://api.github.com/users/octocat/orgs",
            "repos_url": "https://api.github.com/users/octocat/repos",
            "events_url": "https://api.github.com/users/octocat/events{/privacy}",
            "received_events_url": "https://api.github.com/users/octocat/received_events",
            "type": "User",
            "site_admin": false
        },
        "committer": {
            "login": "octocat",
            "id": 1,
            "node_id": "MDQ6VXNlcjE=",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "gravatar_id": "",
            "url": "https://api.github.com/users/octocat",
            "html_url": "https://github.com/octocat",
            "followers_url": "https://api.github.com/users/octocat/followers",
            "following_url": "https://api.github.com/users/octocat/following{/other_user}",
            "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
            "organizations_url": "https://api.github.com/users/octocat/orgs",
            "repos_url": "https://api.github.com/users/octocat/repos",
            "events_url": "https://api.github.com/users/octocat/events{/privacy}",
            "received_events_url": "https://api.github.com/users/octocat/received_events",
            "type": "User",
            "site_admin": false
        },
        "parents": [
            {
                "url": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e",
                "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e"
            }
        ],
        "stats": {
            "additions": 104,
            "deletions": 4,
            "total": 108
        },
        "files": [
            {
                "filename": "file1.txt",
                "additions": 10,
                "deletions": 2,
                "changes": 12,
                "status": "modified",
                "raw_url": "https://github.com/octocat/Hello-World/raw/7ca483543807a51b6079e54ac4cc392bc29ae284/file1.txt",
                "blob_url": "https://github.com/octocat/Hello-World/blob/7ca483543807a51b6079e54ac4cc392bc29ae284/file1.txt",
                "patch": "@@ -29,7 +29,7 @@\n....."
            }
        ]
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

### `#/components/responses/internal_error`

```json
{
    "description": "Internal Error",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
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