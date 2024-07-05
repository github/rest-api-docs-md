# Get a DNS health check for GitHub Pages

`get /repos/{owner}/{repo}/pages/health`

Gets a health check of the DNS settings for the `CNAME` record configured for a repository's GitHub Pages.

The first request to this endpoint returns a `202 Accepted` status and starts an asynchronous background task to get the results for the domain. After the background task completes, subsequent requests to this endpoint return a `200 OK` status with the health check results in the response.

The authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a DNS health check for GitHub Pages",
    "description": "Gets a health check of the DNS settings for the `CNAME` record configured for a repository's GitHub Pages.\n\nThe first request to this endpoint returns a `202 Accepted` status and starts an asynchronous background task to get the results for the domain. After the background task completes, subsequent requests to this endpoint return a `200 OK` status with the health check results in the response.\n\nThe authenticated user must be a repository administrator, maintainer, or have the 'manage GitHub Pages settings' permission to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-pages-health-check",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pages/pages#get-a-dns-health-check-for-github-pages"
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
                        "$ref": "#/components/schemas/pages-health-check"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pages-health-check"
                        }
                    }
                }
            }
        },
        "202": {
            "description": "Empty response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/empty-object"
                    },
                    "examples": {
                        "default": {
                            "value": null
                        }
                    }
                }
            }
        },
        "400": {
            "description": "Custom domains are not available for GitHub Pages"
        },
        "422": {
            "description": "There isn't a CNAME for this page"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pages",
        "subcategory": "pages"
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

### `#/components/schemas/pages-health-check`

```json
{
    "title": "Pages Health Check Status",
    "description": "Pages Health Check Status",
    "type": "object",
    "properties": {
        "domain": {
            "type": "object",
            "properties": {
                "host": {
                    "type": "string"
                },
                "uri": {
                    "type": "string"
                },
                "nameservers": {
                    "type": "string"
                },
                "dns_resolves": {
                    "type": "boolean"
                },
                "is_proxied": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cloudflare_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_fastly_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_old_ip_address": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_a_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "has_cname_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "has_mx_records_present": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_valid_domain": {
                    "type": "boolean"
                },
                "is_apex_domain": {
                    "type": "boolean"
                },
                "should_be_a_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_github_user_domain": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_pages_dot_github_dot_com": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_fastly": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_pointed_to_github_pages_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_non_github_pages_ip_present": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_pages_domain": {
                    "type": "boolean"
                },
                "is_served_by_pages": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_valid": {
                    "type": "boolean"
                },
                "reason": {
                    "type": "string",
                    "nullable": true
                },
                "responds_to_https": {
                    "type": "boolean"
                },
                "enforces_https": {
                    "type": "boolean"
                },
                "https_error": {
                    "type": "string",
                    "nullable": true
                },
                "is_https_eligible": {
                    "type": "boolean",
                    "nullable": true
                },
                "caa_error": {
                    "type": "string",
                    "nullable": true
                }
            }
        },
        "alt_domain": {
            "type": "object",
            "nullable": true,
            "properties": {
                "host": {
                    "type": "string"
                },
                "uri": {
                    "type": "string"
                },
                "nameservers": {
                    "type": "string"
                },
                "dns_resolves": {
                    "type": "boolean"
                },
                "is_proxied": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cloudflare_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_fastly_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_old_ip_address": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_a_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "has_cname_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "has_mx_records_present": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_valid_domain": {
                    "type": "boolean"
                },
                "is_apex_domain": {
                    "type": "boolean"
                },
                "should_be_a_record": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_github_user_domain": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_pages_dot_github_dot_com": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_cname_to_fastly": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_pointed_to_github_pages_ip": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_non_github_pages_ip_present": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_pages_domain": {
                    "type": "boolean"
                },
                "is_served_by_pages": {
                    "type": "boolean",
                    "nullable": true
                },
                "is_valid": {
                    "type": "boolean"
                },
                "reason": {
                    "type": "string",
                    "nullable": true
                },
                "responds_to_https": {
                    "type": "boolean"
                },
                "enforces_https": {
                    "type": "boolean"
                },
                "https_error": {
                    "type": "string",
                    "nullable": true
                },
                "is_https_eligible": {
                    "type": "boolean",
                    "nullable": true
                },
                "caa_error": {
                    "type": "string",
                    "nullable": true
                }
            }
        }
    }
}
```

### `#/components/examples/pages-health-check`

```json
{
    "value": {
        "domain": {
            "host": "example.com",
            "uri": "http://example.com/",
            "nameservers": "default",
            "dns_resolves": true,
            "is_proxied": false,
            "is_cloudflare_ip": false,
            "is_fastly_ip": false,
            "is_old_ip_address": false,
            "is_a_record": true,
            "has_cname_record": false,
            "has_mx_records_present": false,
            "is_valid_domain": true,
            "is_apex_domain": true,
            "should_be_a_record": true,
            "is_cname_to_github_user_domain": false,
            "is_cname_to_pages_dot_github_dot_com": false,
            "is_cname_to_fastly": false,
            "is_pointed_to_github_pages_ip": true,
            "is_non_github_pages_ip_present": false,
            "is_pages_domain": false,
            "is_served_by_pages": true,
            "is_valid": true,
            "reason": null,
            "responds_to_https": true,
            "enforces_https": true,
            "https_error": null,
            "is_https_eligible": true,
            "caa_error": null
        },
        "alt_domain": {
            "host": "www.example.com",
            "uri": "http://www.example.com/",
            "nameservers": "default",
            "dns_resolves": true,
            "is_proxied": false,
            "is_cloudflare_ip": false,
            "is_fastly_ip": false,
            "is_old_ip_address": false,
            "is_a_record": true,
            "has_cname_record": false,
            "has_mx_records_present": false,
            "is_valid_domain": true,
            "is_apex_domain": true,
            "should_be_a_record": true,
            "is_cname_to_github_user_domain": false,
            "is_cname_to_pages_dot_github_dot_com": false,
            "is_cname_to_fastly": false,
            "is_pointed_to_github_pages_ip": true,
            "is_non_github_pages_ip_present": false,
            "is_pages_domain": false,
            "is_served_by_pages": true,
            "is_valid": true,
            "reason": null,
            "responds_to_https": true,
            "enforces_https": true,
            "https_error": null,
            "is_https_eligible": true,
            "caa_error": null
        }
    }
}
```

### `#/components/schemas/empty-object`

```json
{
    "title": "Empty Object",
    "description": "An object without any properties.",
    "type": "object",
    "properties": {},
    "additionalProperties": false
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