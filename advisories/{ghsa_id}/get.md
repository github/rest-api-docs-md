# Get a global security advisory

Gets a global security advisory using its GitHub Security Advisory (GHSA) identifier.

## Operation Object

```json
{
    "summary": "Get a global security advisory",
    "description": "Gets a global security advisory using its GitHub Security Advisory (GHSA) identifier.",
    "tags": [
        "security-advisories"
    ],
    "operationId": "security-advisories/get-global-advisory",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/security-advisories/global-advisories#get-a-global-security-advisory"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/ghsa_id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/global-advisory"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/global-advisory"
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
        "category": "security-advisories",
        "subcategory": "global-advisories"
    }
}
```

## References

### `#/components/parameters/ghsa_id`

```json
{
    "name": "ghsa_id",
    "description": "The GHSA (GitHub Security Advisory) identifier of the advisory.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/global-advisory`

```json
{
    "description": "A GitHub Security Advisory.",
    "type": "object",
    "properties": {
        "ghsa_id": {
            "type": "string",
            "description": "The GitHub Security Advisory ID.",
            "readOnly": true
        },
        "cve_id": {
            "type": "string",
            "description": "The Common Vulnerabilities and Exposures (CVE) ID.",
            "nullable": true,
            "readOnly": true
        },
        "url": {
            "type": "string",
            "description": "The API URL for the advisory.",
            "readOnly": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "description": "The URL for the advisory.",
            "readOnly": true
        },
        "repository_advisory_url": {
            "type": "string",
            "format": "uri",
            "description": "The API URL for the repository advisory.",
            "readOnly": true,
            "nullable": true
        },
        "summary": {
            "type": "string",
            "description": "A short summary of the advisory.",
            "maxLength": 1024
        },
        "description": {
            "type": "string",
            "description": "A detailed description of what the advisory entails.",
            "maxLength": 65535,
            "nullable": true
        },
        "type": {
            "type": "string",
            "description": "The type of advisory.",
            "readOnly": true,
            "enum": [
                "reviewed",
                "unreviewed",
                "malware"
            ]
        },
        "severity": {
            "type": "string",
            "description": "The severity of the advisory.",
            "enum": [
                "critical",
                "high",
                "medium",
                "low",
                "unknown"
            ]
        },
        "source_code_location": {
            "type": "string",
            "format": "uri",
            "description": "The URL of the advisory's source code.",
            "nullable": true
        },
        "identifiers": {
            "type": "array",
            "nullable": true,
            "readOnly": true,
            "items": {
                "type": "object",
                "properties": {
                    "type": {
                        "type": "string",
                        "description": "The type of identifier.",
                        "enum": [
                            "CVE",
                            "GHSA"
                        ]
                    },
                    "value": {
                        "type": "string",
                        "description": "The identifier value."
                    }
                },
                "required": [
                    "type",
                    "value"
                ]
            }
        },
        "references": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "string",
                "description": "URLs with more information regarding the advisory."
            }
        },
        "published_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was published, in ISO 8601 format.",
            "readOnly": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was last updated, in ISO 8601 format.",
            "readOnly": true
        },
        "github_reviewed_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was reviewed by GitHub, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "nvd_published_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time when the advisory was published in the National Vulnerability Database, in ISO 8601 format.\nThis field is only populated when the advisory is imported from the National Vulnerability Database.",
            "readOnly": true,
            "nullable": true
        },
        "withdrawn_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was withdrawn, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "vulnerabilities": {
            "type": "array",
            "description": "The products and respective version ranges affected by the advisory.",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/vulnerability"
            }
        },
        "cvss": {
            "type": "object",
            "nullable": true,
            "properties": {
                "vector_string": {
                    "type": "string",
                    "description": "The CVSS vector.",
                    "nullable": true
                },
                "score": {
                    "type": "number",
                    "description": "The CVSS score.",
                    "minimum": 0,
                    "maximum": 10,
                    "nullable": true,
                    "readOnly": true
                }
            },
            "required": [
                "vector_string",
                "score"
            ]
        },
        "cwes": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "object",
                "properties": {
                    "cwe_id": {
                        "type": "string",
                        "description": "The Common Weakness Enumeration (CWE) identifier."
                    },
                    "name": {
                        "type": "string",
                        "description": "The name of the CWE.",
                        "readOnly": true
                    }
                },
                "required": [
                    "cwe_id",
                    "name"
                ]
            }
        },
        "credits": {
            "type": "array",
            "description": "The users who contributed to the advisory.",
            "nullable": true,
            "readOnly": true,
            "items": {
                "type": "object",
                "properties": {
                    "user": {
                        "$ref": "#/components/schemas/simple-user"
                    },
                    "type": {
                        "$ref": "#/components/schemas/security-advisory-credit-types"
                    }
                },
                "required": [
                    "user",
                    "type"
                ]
            }
        }
    },
    "required": [
        "ghsa_id",
        "cve_id",
        "url",
        "html_url",
        "repository_advisory_url",
        "summary",
        "description",
        "type",
        "severity",
        "source_code_location",
        "identifiers",
        "references",
        "published_at",
        "updated_at",
        "github_reviewed_at",
        "nvd_published_at",
        "withdrawn_at",
        "vulnerabilities",
        "cvss",
        "cwes",
        "credits"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/global-advisory`

```json
{
    "value": {
        "ghsa_id": "GHSA-abcd-1234-efgh",
        "cve_id": "CVE-2050-00000",
        "url": "https://api.github.com/advisories/GHSA-abcd-1234-efgh",
        "html_url": "https://github.com/advisories/GHSA-abcd-1234-efgh",
        "repository_advisory_url": "https://api.github.com/repos/project/a-package/security-advisories/GHSA-abcd-1234-efgh",
        "summary": "A short summary of the advisory.",
        "description": "A detailed description of what the advisory entails.",
        "type": "reviewed",
        "severity": "high",
        "source_code_location": "https://github.com/project/a-package",
        "identifiers": [
            {
                "type": "GHSA",
                "value": "GHSA-abcd-1234-efgh"
            },
            {
                "type": "CVE",
                "value": "CVE-2050-00000"
            }
        ],
        "references": [
            "https://nvd.nist.gov/vuln/detail/CVE-2050-00000"
        ],
        "published_at": "2023-03-23T02:30:56Z",
        "updated_at": "2023-03-24T02:30:56Z",
        "github_reviewed_at": "2023-03-23T02:30:56Z",
        "nvd_published_at": "2023-03-25T02:30:56Z",
        "withdrawn_at": null,
        "vulnerabilities": [
            {
                "package": {
                    "ecosystem": "npm",
                    "name": "a-package"
                },
                "first_patched_version": "1.0.3",
                "vulnerable_version_range": "<=1.0.2",
                "vulnerable_functions": [
                    "a_function"
                ]
            }
        ],
        "cvss": {
            "vector_string": "CVSS:3.1/AV:N/AC:H/PR:H/UI:R/S:C/C:H/I:H/A:H",
            "score": 7.6
        },
        "cwes": [
            {
                "cwe_id": "CWE-400",
                "name": "Uncontrolled Resource Consumption"
            }
        ],
        "credits": [
            {
                "user": {
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
                "type": "analyst"
            }
        ]
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