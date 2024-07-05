# Get a Dependabot alert

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

## Operation Object

```json
{
    "summary": "Get a Dependabot alert",
    "description": "OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.",
    "tags": [
        "dependabot"
    ],
    "operationId": "dependabot/get-alert",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependabot/alerts#get-a-dependabot-alert"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/dependabot-alert"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/dependabot-alert-open"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "dependabot",
        "subcategory": "alerts"
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

### `#/components/parameters/dependabot-alert-number`

```json
{
    "name": "alert_number",
    "in": "path",
    "description": "The number that identifies a Dependabot alert in its repository.\nYou can find this at the end of the URL for a Dependabot alert within GitHub,\nor in `number` fields in the response from the\n`GET /repos/{owner}/{repo}/dependabot/alerts` operation.",
    "required": true,
    "schema": {
        "$ref": "#/components/schemas/alert-number"
    }
}
```

### `#/components/schemas/dependabot-alert`

```json
{
    "type": "object",
    "description": "A Dependabot alert.",
    "properties": {
        "number": {
            "$ref": "#/components/schemas/alert-number"
        },
        "state": {
            "type": "string",
            "description": "The state of the Dependabot alert.",
            "readOnly": true,
            "enum": [
                "auto_dismissed",
                "dismissed",
                "fixed",
                "open"
            ]
        },
        "dependency": {
            "type": "object",
            "description": "Details for the vulnerable dependency.",
            "readOnly": true,
            "properties": {
                "package": {
                    "$ref": "#/components/schemas/dependabot-alert-package"
                },
                "manifest_path": {
                    "type": "string",
                    "description": "The full path to the dependency manifest file, relative to the root of the repository.",
                    "readOnly": true
                },
                "scope": {
                    "type": "string",
                    "description": "The execution scope of the vulnerable dependency.",
                    "readOnly": true,
                    "nullable": true,
                    "enum": [
                        "development",
                        "runtime"
                    ]
                }
            }
        },
        "security_advisory": {
            "$ref": "#/components/schemas/dependabot-alert-security-advisory"
        },
        "security_vulnerability": {
            "$ref": "#/components/schemas/dependabot-alert-security-vulnerability"
        },
        "url": {
            "$ref": "#/components/schemas/alert-url"
        },
        "html_url": {
            "$ref": "#/components/schemas/alert-html-url"
        },
        "created_at": {
            "$ref": "#/components/schemas/alert-created-at"
        },
        "updated_at": {
            "$ref": "#/components/schemas/alert-updated-at"
        },
        "dismissed_at": {
            "$ref": "#/components/schemas/alert-dismissed-at"
        },
        "dismissed_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "dismissed_reason": {
            "type": "string",
            "description": "The reason that the alert was dismissed.",
            "nullable": true,
            "enum": [
                "fix_started",
                "inaccurate",
                "no_bandwidth",
                "not_used",
                "tolerable_risk"
            ]
        },
        "dismissed_comment": {
            "type": "string",
            "description": "An optional comment associated with the alert's dismissal.",
            "nullable": true,
            "maxLength": 280
        },
        "fixed_at": {
            "$ref": "#/components/schemas/alert-fixed-at"
        },
        "auto_dismissed_at": {
            "$ref": "#/components/schemas/alert-auto-dismissed-at"
        }
    },
    "required": [
        "number",
        "state",
        "dependency",
        "security_advisory",
        "security_vulnerability",
        "url",
        "html_url",
        "created_at",
        "updated_at",
        "dismissed_at",
        "dismissed_by",
        "dismissed_reason",
        "dismissed_comment",
        "fixed_at"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/dependabot-alert-open`

```json
{
    "value": {
        "number": 1,
        "state": "open",
        "dependency": {
            "package": {
                "ecosystem": "pip",
                "name": "ansible"
            },
            "manifest_path": "path/to/requirements.txt",
            "scope": "runtime"
        },
        "security_advisory": {
            "ghsa_id": "GHSA-8f4m-hccc-8qph",
            "cve_id": "CVE-2021-20191",
            "summary": "Insertion of Sensitive Information into Log File in ansible",
            "description": "A flaw was found in ansible. Credentials, such as secrets, are being disclosed in console log by default and not protected by no_log feature when using those modules. An attacker can take advantage of this information to steal those credentials. The highest threat from this vulnerability is to data confidentiality.",
            "vulnerabilities": [
                {
                    "package": {
                        "ecosystem": "pip",
                        "name": "ansible"
                    },
                    "severity": "medium",
                    "vulnerable_version_range": ">= 2.9.0, < 2.9.18",
                    "first_patched_version": {
                        "identifier": "2.9.18"
                    }
                },
                {
                    "package": {
                        "ecosystem": "pip",
                        "name": "ansible"
                    },
                    "severity": "medium",
                    "vulnerable_version_range": "< 2.8.19",
                    "first_patched_version": {
                        "identifier": "2.8.19"
                    }
                },
                {
                    "package": {
                        "ecosystem": "pip",
                        "name": "ansible"
                    },
                    "severity": "medium",
                    "vulnerable_version_range": ">= 2.10.0, < 2.10.7",
                    "first_patched_version": {
                        "identifier": "2.10.7"
                    }
                }
            ],
            "severity": "medium",
            "cvss": {
                "vector_string": "CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:N/A:N",
                "score": 5.5
            },
            "cwes": [
                {
                    "cwe_id": "CWE-532",
                    "name": "Insertion of Sensitive Information into Log File"
                }
            ],
            "identifiers": [
                {
                    "type": "GHSA",
                    "value": "GHSA-8f4m-hccc-8qph"
                },
                {
                    "type": "CVE",
                    "value": "CVE-2021-20191"
                }
            ],
            "references": [
                {
                    "url": "https://nvd.nist.gov/vuln/detail/CVE-2021-20191"
                },
                {
                    "url": "https://access.redhat.com/security/cve/cve-2021-20191"
                },
                {
                    "url": "https://bugzilla.redhat.com/show_bug.cgi?id=1916813"
                }
            ],
            "published_at": "2021-06-01T17:38:00Z",
            "updated_at": "2021-08-12T23:06:00Z",
            "withdrawn_at": null
        },
        "security_vulnerability": {
            "package": {
                "ecosystem": "pip",
                "name": "ansible"
            },
            "severity": "medium",
            "vulnerable_version_range": "< 2.8.19",
            "first_patched_version": {
                "identifier": "2.8.19"
            }
        },
        "url": "https://api.github.com/repos/octocat/hello-world/dependabot/alerts/1",
        "html_url": "https://github.com/octocat/hello-world/security/dependabot/1",
        "created_at": "2022-06-14T15:21:52Z",
        "updated_at": "2022-06-14T15:21:52Z",
        "dismissed_at": null,
        "dismissed_by": null,
        "dismissed_reason": null,
        "dismissed_comment": null,
        "fixed_at": null
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
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