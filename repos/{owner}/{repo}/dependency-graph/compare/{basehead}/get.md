# Get a diff of the dependencies between commits

`get /repos/{owner}/{repo}/dependency-graph/compare/{basehead}`

Gets the diff of the dependency changes between two commits of a repository, based on the changes to the dependency manifests made in those commits.

## Operation Object

```json
{
    "summary": "Get a diff of the dependencies between commits",
    "description": "Gets the diff of the dependency changes between two commits of a repository, based on the changes to the dependency manifests made in those commits.",
    "tags": [
        "dependency-graph"
    ],
    "operationId": "dependency-graph/diff-range",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependency-graph/dependency-review#get-a-diff-of-the-dependencies-between-commits"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "basehead",
            "description": "The base and head Git revisions to compare. The Git revisions will be resolved to commit SHAs. Named revisions will be resolved to their corresponding HEAD commits, and an appropriate merge base will be determined. This parameter expects the format `{base}...{head}`.",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "$ref": "#/components/parameters/manifest-path"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/dependency-graph-diff"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/diff-range-response"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/dependency_review_forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "category": "dependency-graph",
        "subcategory": "dependency-review"
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

### `#/components/parameters/manifest-path`

```json
{
    "name": "name",
    "description": "The full path, relative to the repository root, of the dependency manifest file.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/dependency-graph-diff`

```json
{
    "title": "Dependency Graph Diff",
    "description": "A diff of the dependencies between two commits.",
    "type": "array",
    "items": {
        "type": "object",
        "properties": {
            "change_type": {
                "type": "string",
                "enum": [
                    "added",
                    "removed"
                ]
            },
            "manifest": {
                "type": "string",
                "example": "path/to/package-lock.json"
            },
            "ecosystem": {
                "type": "string",
                "example": "npm"
            },
            "name": {
                "type": "string",
                "example": "@actions/core"
            },
            "version": {
                "type": "string",
                "example": "1.0.0"
            },
            "package_url": {
                "type": "string",
                "nullable": true,
                "example": "pkg:/npm/%40actions/core@1.1.0"
            },
            "license": {
                "type": "string",
                "nullable": true,
                "example": "MIT"
            },
            "source_repository_url": {
                "type": "string",
                "nullable": true,
                "example": "https://github.com/github/actions"
            },
            "vulnerabilities": {
                "type": "array",
                "items": {
                    "type": "object",
                    "properties": {
                        "severity": {
                            "type": "string",
                            "example": "critical"
                        },
                        "advisory_ghsa_id": {
                            "type": "string",
                            "example": "GHSA-rf4j-j272-fj86"
                        },
                        "advisory_summary": {
                            "type": "string",
                            "example": "A summary of the advisory."
                        },
                        "advisory_url": {
                            "type": "string",
                            "example": "https://github.com/advisories/GHSA-rf4j-j272-fj86"
                        }
                    },
                    "required": [
                        "severity",
                        "advisory_ghsa_id",
                        "advisory_summary",
                        "advisory_url"
                    ]
                }
            },
            "scope": {
                "description": "Where the dependency is utilized. `development` means that the dependency is only utilized in the development environment. `runtime` means that the dependency is utilized at runtime and in the development environment.",
                "type": "string",
                "enum": [
                    "unknown",
                    "runtime",
                    "development"
                ]
            }
        },
        "required": [
            "change_type",
            "manifest",
            "ecosystem",
            "name",
            "version",
            "package_url",
            "license",
            "source_repository_url",
            "vulnerabilities",
            "scope"
        ]
    }
}
```

### `#/components/examples/diff-range-response`

```json
{
    "value": [
        {
            "change_type": "removed",
            "manifest": "package.json",
            "ecosystem": "npm",
            "name": "helmet",
            "version": "4.6.0",
            "package_url": "pkg:npm/helmet@4.6.0",
            "license": "MIT",
            "source_repository_url": "https://github.com/helmetjs/helmet",
            "vulnerabilities": []
        },
        {
            "change_type": "added",
            "manifest": "package.json",
            "ecosystem": "npm",
            "name": "helmet",
            "version": "5.0.0",
            "package_url": "pkg:npm/helmet@5.0.0",
            "license": "MIT",
            "source_repository_url": "https://github.com/helmetjs/helmet",
            "vulnerabilities": []
        },
        {
            "change_type": "added",
            "manifest": "Gemfile",
            "ecosystem": "rubygems",
            "name": "ruby-openid",
            "version": "2.7.0",
            "package_url": "pkg:gem/ruby-openid@2.7.0",
            "license": null,
            "source_repository_url": "https://github.com/openid/ruby-openid",
            "vulnerabilities": [
                {
                    "severity": "critical",
                    "advisory_ghsa_id": "GHSA-fqfj-cmh6-hj49",
                    "advisory_summary": "Ruby OpenID",
                    "advisory_url": "https://github.com/advisories/GHSA-fqfj-cmh6-hj49"
                }
            ]
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

### `#/components/responses/dependency_review_forbidden`

```json
{
    "description": "Response if GitHub Advanced Security is not enabled for this repository",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```