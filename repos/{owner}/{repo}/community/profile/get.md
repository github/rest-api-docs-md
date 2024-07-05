# Get community profile metrics

`get /repos/{owner}/{repo}/community/profile`

Returns all community profile metrics for a repository. The repository cannot be a fork.

The returned metrics include an overall health score, the repository description, the presence of documentation, the
detected code of conduct, the detected license, and the presence of ISSUE\_TEMPLATE, PULL\_REQUEST\_TEMPLATE,
README, and CONTRIBUTING files.

The `health_percentage` score is defined as a percentage of how many of
the recommended community health files are present. For more information, see
"[About community profiles for public repositories](https://docs.github.com/communities/setting-up-your-project-for-healthy-contributions/about-community-profiles-for-public-repositories)."

`content_reports_enabled` is only returned for organization-owned repositories.

## Operation Object

```json
{
    "summary": "Get community profile metrics",
    "description": "Returns all community profile metrics for a repository. The repository cannot be a fork.\n\nThe returned metrics include an overall health score, the repository description, the presence of documentation, the\ndetected code of conduct, the detected license, and the presence of ISSUE\\_TEMPLATE, PULL\\_REQUEST\\_TEMPLATE,\nREADME, and CONTRIBUTING files.\n\nThe `health_percentage` score is defined as a percentage of how many of\nthe recommended community health files are present. For more information, see\n\"[About community profiles for public repositories](https://docs.github.com/communities/setting-up-your-project-for-healthy-contributions/about-community-profiles-for-public-repositories).\"\n\n`content_reports_enabled` is only returned for organization-owned repositories.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-community-profile-metrics",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/community#get-community-profile-metrics"
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
                        "$ref": "#/components/schemas/community-profile"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/community-profile"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "metrics",
        "subcategory": "community"
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

### `#/components/schemas/community-profile`

```json
{
    "title": "Community Profile",
    "description": "Community Profile",
    "type": "object",
    "properties": {
        "health_percentage": {
            "type": "integer",
            "example": 100
        },
        "description": {
            "type": "string",
            "example": "My first repository on GitHub!",
            "nullable": true
        },
        "documentation": {
            "type": "string",
            "example": "example.com",
            "nullable": true
        },
        "files": {
            "type": "object",
            "properties": {
                "code_of_conduct": {
                    "$ref": "#/components/schemas/nullable-code-of-conduct-simple"
                },
                "code_of_conduct_file": {
                    "$ref": "#/components/schemas/nullable-community-health-file"
                },
                "license": {
                    "$ref": "#/components/schemas/nullable-license-simple"
                },
                "contributing": {
                    "$ref": "#/components/schemas/nullable-community-health-file"
                },
                "readme": {
                    "$ref": "#/components/schemas/nullable-community-health-file"
                },
                "issue_template": {
                    "$ref": "#/components/schemas/nullable-community-health-file"
                },
                "pull_request_template": {
                    "$ref": "#/components/schemas/nullable-community-health-file"
                }
            },
            "required": [
                "code_of_conduct",
                "code_of_conduct_file",
                "license",
                "contributing",
                "readme",
                "issue_template",
                "pull_request_template"
            ]
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-02-28T19:09:29Z",
            "nullable": true
        },
        "content_reports_enabled": {
            "type": "boolean",
            "example": true
        }
    },
    "required": [
        "health_percentage",
        "description",
        "documentation",
        "files",
        "updated_at"
    ]
}
```

### `#/components/examples/community-profile`

```json
{
    "value": {
        "health_percentage": 100,
        "description": "My first repository on GitHub!",
        "documentation": null,
        "files": {
            "code_of_conduct": {
                "name": "Contributor Covenant",
                "key": "contributor_covenant",
                "url": "https://api.github.com/codes_of_conduct/contributor_covenant",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/CODE_OF_CONDUCT.md"
            },
            "code_of_conduct_file": {
                "url": "https://api.github.com/repos/octocat/Hello-World/contents/CODE_OF_CONDUCT.md",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/CODE_OF_CONDUCT.md"
            },
            "contributing": {
                "url": "https://api.github.com/repos/octocat/Hello-World/contents/CONTRIBUTING",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/CONTRIBUTING"
            },
            "issue_template": {
                "url": "https://api.github.com/repos/octocat/Hello-World/contents/ISSUE_TEMPLATE",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/ISSUE_TEMPLATE"
            },
            "pull_request_template": {
                "url": "https://api.github.com/repos/octocat/Hello-World/contents/PULL_REQUEST_TEMPLATE",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/PULL_REQUEST_TEMPLATE"
            },
            "license": {
                "name": "MIT License",
                "key": "mit",
                "spdx_id": "MIT",
                "url": "https://api.github.com/licenses/mit",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/LICENSE",
                "node_id": "MDc6TGljZW5zZW1pdA=="
            },
            "readme": {
                "url": "https://api.github.com/repos/octocat/Hello-World/contents/README.md",
                "html_url": "https://github.com/octocat/Hello-World/blob/master/README.md"
            }
        },
        "updated_at": "2017-02-28T19:09:29Z",
        "content_reports_enabled": true
    }
}
```