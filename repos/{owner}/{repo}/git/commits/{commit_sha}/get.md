# Get a commit object

`get /repos/{owner}/{repo}/git/commits/{commit_sha}`

Gets a Git [commit object](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects).

To get the contents of a commit, see "[Get a commit](/rest/commits/commits#get-a-commit)."

**Signature verification object**

The response will include a `verification` object that describes the result of verifying the commit's signature. The following fields are included in the `verification` object:

| Name | Type | Description |
| ---- | ---- | ----------- |
| `verified` | `boolean` | Indicates whether GitHub considers the signature in this commit to be verified. |
| `reason` | `string` | The reason for verified value. Possible values and their meanings are enumerated in the table below. |
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
    "summary": "Get a commit object",
    "description": "Gets a Git [commit object](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects).\n\nTo get the contents of a commit, see \"[Get a commit](/rest/commits/commits#get-a-commit).\"\n\n**Signature verification object**\n\nThe response will include a `verification` object that describes the result of verifying the commit's signature. The following fields are included in the `verification` object:\n\n| Name | Type | Description |\n| ---- | ---- | ----------- |\n| `verified` | `boolean` | Indicates whether GitHub considers the signature in this commit to be verified. |\n| `reason` | `string` | The reason for verified value. Possible values and their meanings are enumerated in the table below. |\n| `signature` | `string` | The signature that was extracted from the commit. |\n| `payload` | `string` | The value that was signed. |\n\nThese are the possible values for `reason` in the `verification` object:\n\n| Value | Description |\n| ----- | ----------- |\n| `expired_key` | The key that made the signature is expired. |\n| `not_signing_key` | The \"signing\" flag is not among the usage flags in the GPG key that made the signature. |\n| `gpgverify_error` | There was an error communicating with the signature verification service. |\n| `gpgverify_unavailable` | The signature verification service is currently unavailable. |\n| `unsigned` | The object does not include a signature. |\n| `unknown_signature_type` | A non-PGP signature was found in the commit. |\n| `no_user` | No user was associated with the `committer` email address in the commit. |\n| `unverified_email` | The `committer` email address in the commit was associated with a user, but the email address is not verified on their account. |\n| `bad_email` | The `committer` email address in the commit is not included in the identities of the PGP key that made the signature. |\n| `unknown_key` | The key that made the signature has not been registered with any user's account. |\n| `malformed_signature` | There was an error parsing the signature. |\n| `invalid` | The signature could not be cryptographically verified using the key whose key-id was found in the signature. |\n| `valid` | None of the above errors applied, so the signature is considered to be verified. |",
    "tags": [
        "git"
    ],
    "operationId": "git/get-commit",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/git/commits#get-a-commit-object"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/commit-sha"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/git-commit"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/git-commit-2"
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

### `#/components/parameters/commit-sha`

```json
{
    "name": "commit_sha",
    "description": "The SHA of the commit.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/git-commit`

```json
{
    "title": "Git Commit",
    "description": "Low-level Git commit operations within a repository",
    "type": "object",
    "properties": {
        "sha": {
            "description": "SHA for the commit",
            "example": "7638417db6d59f3c431d3e1f261cc637155684cd",
            "type": "string"
        },
        "node_id": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "author": {
            "description": "Identifying information for the git-user",
            "type": "object",
            "properties": {
                "date": {
                    "description": "Timestamp of the commit",
                    "example": "2014-08-09T08:02:04+12:00",
                    "format": "date-time",
                    "type": "string"
                },
                "email": {
                    "type": "string",
                    "description": "Git email address of the user",
                    "example": "monalisa.octocat@example.com"
                },
                "name": {
                    "description": "Name of the git user",
                    "example": "Monalisa Octocat",
                    "type": "string"
                }
            },
            "required": [
                "email",
                "name",
                "date"
            ]
        },
        "committer": {
            "description": "Identifying information for the git-user",
            "type": "object",
            "properties": {
                "date": {
                    "description": "Timestamp of the commit",
                    "example": "2014-08-09T08:02:04+12:00",
                    "format": "date-time",
                    "type": "string"
                },
                "email": {
                    "type": "string",
                    "description": "Git email address of the user",
                    "example": "monalisa.octocat@example.com"
                },
                "name": {
                    "description": "Name of the git user",
                    "example": "Monalisa Octocat",
                    "type": "string"
                }
            },
            "required": [
                "email",
                "name",
                "date"
            ]
        },
        "message": {
            "description": "Message describing the purpose of the commit",
            "example": "Fix #42",
            "type": "string"
        },
        "tree": {
            "type": "object",
            "properties": {
                "sha": {
                    "description": "SHA for the commit",
                    "example": "7638417db6d59f3c431d3e1f261cc637155684cd",
                    "type": "string"
                },
                "url": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "sha",
                "url"
            ]
        },
        "parents": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "sha": {
                        "description": "SHA for the commit",
                        "example": "7638417db6d59f3c431d3e1f261cc637155684cd",
                        "type": "string"
                    },
                    "url": {
                        "type": "string",
                        "format": "uri"
                    },
                    "html_url": {
                        "type": "string",
                        "format": "uri"
                    }
                },
                "required": [
                    "sha",
                    "url",
                    "html_url"
                ]
            }
        },
        "verification": {
            "type": "object",
            "properties": {
                "verified": {
                    "type": "boolean"
                },
                "reason": {
                    "type": "string"
                },
                "signature": {
                    "type": "string",
                    "nullable": true
                },
                "payload": {
                    "type": "string",
                    "nullable": true
                }
            },
            "required": [
                "verified",
                "reason",
                "signature",
                "payload"
            ]
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        }
    },
    "required": [
        "sha",
        "node_id",
        "url",
        "html_url",
        "author",
        "committer",
        "tree",
        "message",
        "parents",
        "verification"
    ]
}
```

### `#/components/examples/git-commit-2`

```json
{
    "value": {
        "sha": "7638417db6d59f3c431d3e1f261cc637155684cd",
        "node_id": "MDY6Q29tbWl0NmRjYjA5YjViNTc4NzVmMzM0ZjYxYWViZWQ2OTVlMmU0MTkzZGI1ZQ==",
        "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/7638417db6d59f3c431d3e1f261cc637155684cd",
        "html_url": "https://github.com/octocat/Hello-World/commit/7638417db6d59f3c431d3e1f261cc637155684cd",
        "author": {
            "date": "2014-11-07T22:01:45Z",
            "name": "Monalisa Octocat",
            "email": "octocat@github.com"
        },
        "committer": {
            "date": "2014-11-07T22:01:45Z",
            "name": "Monalisa Octocat",
            "email": "octocat@github.com"
        },
        "message": "added readme, because im a good github citizen",
        "tree": {
            "url": "https://api.github.com/repos/octocat/Hello-World/git/trees/691272480426f78a0138979dd3ce63b77f706feb",
            "sha": "691272480426f78a0138979dd3ce63b77f706feb"
        },
        "parents": [
            {
                "url": "https://api.github.com/repos/octocat/Hello-World/git/commits/1acc419d4d6a9ce985db7be48c6349a0475975b5",
                "sha": "1acc419d4d6a9ce985db7be48c6349a0475975b5",
                "html_url": "https://github.com/octocat/Hello-World/commit/7638417db6d59f3c431d3e1f261cc637155684cd"
            }
        ],
        "verification": {
            "verified": false,
            "reason": "unsigned",
            "signature": null,
            "payload": null
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