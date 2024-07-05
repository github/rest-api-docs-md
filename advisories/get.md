# List global security advisories

Lists all global security advisories that match the specified parameters. If no other parameters are defined, the request will return only GitHub-reviewed advisories that are not malware.

By default, all responses will exclude advisories for malware, because malware are not standard vulnerabilities. To list advisories for malware, you must include the `type` parameter in your request, with the value `malware`. For more information about the different types of security advisories, see "[About the GitHub Advisory database](https://docs.github.com/code-security/security-advisories/global-security-advisories/about-the-github-advisory-database#about-types-of-security-advisories)."

## Operation Object

```json
{
    "summary": "List global security advisories",
    "description": "Lists all global security advisories that match the specified parameters. If no other parameters are defined, the request will return only GitHub-reviewed advisories that are not malware.\n\nBy default, all responses will exclude advisories for malware, because malware are not standard vulnerabilities. To list advisories for malware, you must include the `type` parameter in your request, with the value `malware`. For more information about the different types of security advisories, see \"[About the GitHub Advisory database](https://docs.github.com/code-security/security-advisories/global-security-advisories/about-the-github-advisory-database#about-types-of-security-advisories).\"",
    "tags": [
        "security-advisories"
    ],
    "operationId": "security-advisories/list-global-advisories",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/security-advisories/global-advisories#list-global-security-advisories"
    },
    "parameters": [
        {
            "name": "ghsa_id",
            "in": "query",
            "description": "If specified, only advisories with this GHSA (GitHub Security Advisory) identifier will be returned.",
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "type",
            "in": "query",
            "description": "If specified, only advisories of this type will be returned. By default, a request with no other parameters defined will only return reviewed advisories that are not malware.",
            "schema": {
                "type": "string",
                "enum": [
                    "reviewed",
                    "malware",
                    "unreviewed"
                ],
                "default": "reviewed"
            }
        },
        {
            "name": "cve_id",
            "description": "If specified, only advisories with this CVE (Common Vulnerabilities and Exposures) identifier will be returned.",
            "in": "query",
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "ecosystem",
            "in": "query",
            "description": "If specified, only advisories for these ecosystems will be returned.",
            "schema": {
                "$ref": "#/components/schemas/security-advisory-ecosystems"
            }
        },
        {
            "name": "severity",
            "in": "query",
            "description": "If specified, only advisories with these severities will be returned.",
            "schema": {
                "type": "string",
                "enum": [
                    "unknown",
                    "low",
                    "medium",
                    "high",
                    "critical"
                ]
            }
        },
        {
            "name": "cwes",
            "in": "query",
            "description": "If specified, only advisories with these Common Weakness Enumerations (CWEs) will be returned.\n\nExample: `cwes=79,284,22` or `cwes[]=79&cwes[]=284&cwes[]=22`",
            "schema": {
                "oneOf": [
                    {
                        "type": "string"
                    },
                    {
                        "type": "array",
                        "items": {
                            "type": "string"
                        }
                    }
                ]
            }
        },
        {
            "name": "is_withdrawn",
            "in": "query",
            "description": "Whether to only return advisories that have been withdrawn.",
            "schema": {
                "type": "boolean"
            }
        },
        {
            "name": "affects",
            "in": "query",
            "description": "If specified, only return advisories that affect any of `package` or `package@version`. A maximum of 1000 packages can be specified.\nIf the query parameter causes the URL to exceed the maximum URL length supported by your client, you must specify fewer packages.\n\nExample: `affects=package1,package2@1.0.0,package3@^2.0.0` or `affects[]=package1&affects[]=package2@1.0.0`",
            "schema": {
                "oneOf": [
                    {
                        "type": "string"
                    },
                    {
                        "type": "array",
                        "maxItems": 1000,
                        "items": {
                            "type": "string"
                        }
                    }
                ]
            }
        },
        {
            "name": "published",
            "in": "query",
            "description": "If specified, only return advisories that were published on a date or date range.\n\nFor more information on the syntax of the date range, see \"[Understanding the search syntax](https://docs.github.com/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax#query-for-dates).\"",
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "updated",
            "in": "query",
            "description": "If specified, only return advisories that were updated on a date or date range.\n\nFor more information on the syntax of the date range, see \"[Understanding the search syntax](https://docs.github.com/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax#query-for-dates).\"",
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "modified",
            "description": "If specified, only show advisories that were updated or published on a date or date range.\n\nFor more information on the syntax of the date range, see \"[Understanding the search syntax](https://docs.github.com/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax#query-for-dates).\"",
            "in": "query",
            "schema": {
                "type": "string"
            }
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "name": "per_page",
            "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "schema": {
                "type": "integer",
                "minimum": 1,
                "maximum": 100,
                "default": 30
            }
        },
        {
            "name": "sort",
            "description": "The property to sort the results by.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "updated",
                    "published"
                ],
                "default": "published"
            }
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
                            "$ref": "#/components/schemas/global-advisory"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/global-advisory-items"
                        }
                    }
                }
            }
        },
        "429": {
            "description": "Too many requests",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/basic-error"
                    }
                }
            }
        },
        "422": {
            "$ref": "#/components/responses/validation_failed_simple"
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

### `#/components/schemas/security-advisory-ecosystems`

```json
{
    "type": "string",
    "description": "The package's language or package management ecosystem.",
    "enum": [
        "rubygems",
        "npm",
        "pip",
        "maven",
        "nuget",
        "composer",
        "go",
        "rust",
        "erlang",
        "actions",
        "pub",
        "other",
        "swift"
    ]
}
```

### `#/components/parameters/pagination-before`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/pagination-after`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/direction`

```json
{
    "name": "direction",
    "description": "The direction to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "asc",
            "desc"
        ],
        "default": "desc"
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

### `#/components/examples/global-advisory-items`

```json
{
    "value": [
        {
            "id": 1,
            "ghsa_id": "GHSA-abcd-1234-efgh",
            "cve_id": "CVE-2050-00000",
            "url": "https://api.github.com/advisories/GHSA-abcd-1234-efgh",
            "html_url": "https://github.com/advisories/GHSA-abcd-1234-efgh",
            "repository_advisory_url": "https://api.github.com/repos/project/a-package/security-advisories/GHSA-abcd-1234-efgh",
            "summary": "Heartbleed security advisory",
            "description": "This bug allows an attacker to read portions of the affected server\u2019s memory, potentially disclosing sensitive information.",
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
    ]
}
```

### `#/components/schemas/basic-error`

```json
{
    "title": "Basic Error",
    "description": "Basic Error",
    "type": "object",
    "properties": {
        "message": {
            "type": "string"
        },
        "documentation_url": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "status": {
            "type": "string"
        }
    }
}
```

### `#/components/responses/validation_failed_simple`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error-simple"
            }
        }
    }
}
```