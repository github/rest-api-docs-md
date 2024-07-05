# Get an app

`get /apps/{app_slug}`

**Note**: The `:app_slug` is just the URL-friendly name of your GitHub App. You can find this on the settings page for your GitHub App (e.g., `https://github.com/settings/apps/:app_slug`).

## Operation Object

```json
{
    "summary": "Get an app",
    "description": "**Note**: The `:app_slug` is just the URL-friendly name of your GitHub App. You can find this on the settings page for your GitHub App (e.g., `https://github.com/settings/apps/:app_slug`).",
    "tags": [
        "apps"
    ],
    "operationId": "apps/get-by-slug",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/apps#get-an-app"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/app-slug"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/integration"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/integration"
                        }
                    }
                }
            }
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
        "category": "apps",
        "subcategory": "apps"
    }
}
```

## References

### `#/components/parameters/app-slug`

```json
{
    "name": "app_slug",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/integration`

```json
{
    "title": "GitHub app",
    "description": "GitHub apps are a new way to extend GitHub. They can be installed directly on organizations and user accounts and granted access to specific repositories. They come with granular permissions and built-in webhooks. GitHub apps are first class actors within GitHub.",
    "type": "object",
    "nullable": true,
    "properties": {
        "id": {
            "description": "Unique identifier of the GitHub app",
            "example": 37,
            "type": "integer"
        },
        "slug": {
            "description": "The slug name of the GitHub app",
            "example": "probot-owners",
            "type": "string"
        },
        "node_id": {
            "type": "string",
            "example": "MDExOkludGVncmF0aW9uMQ=="
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "name": {
            "description": "The name of the GitHub app",
            "example": "Probot Owners",
            "type": "string"
        },
        "description": {
            "type": "string",
            "example": "The description of the app.",
            "nullable": true
        },
        "external_url": {
            "type": "string",
            "format": "uri",
            "example": "https://example.com"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/apps/super-ci"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-07-08T16:18:44-04:00"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-07-08T16:18:44-04:00"
        },
        "permissions": {
            "description": "The set of permissions for the GitHub app",
            "type": "object",
            "properties": {
                "issues": {
                    "type": "string"
                },
                "checks": {
                    "type": "string"
                },
                "metadata": {
                    "type": "string"
                },
                "contents": {
                    "type": "string"
                },
                "deployments": {
                    "type": "string"
                }
            },
            "additionalProperties": {
                "type": "string"
            },
            "example": {
                "issues": "read",
                "deployments": "write"
            }
        },
        "events": {
            "description": "The list of events for the GitHub app",
            "example": [
                "label",
                "deployment"
            ],
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "installations_count": {
            "description": "The number of installations associated with the GitHub app",
            "example": 5,
            "type": "integer"
        },
        "client_id": {
            "type": "string",
            "example": "\"Iv1.25b5d1e65ffc4022\""
        },
        "client_secret": {
            "type": "string",
            "example": "\"1d4b2097ac622ba702d19de498f005747a8b21d3\""
        },
        "webhook_secret": {
            "type": "string",
            "example": "\"6fba8f2fc8a7e8f2cca5577eddd82ca7586b3b6b\"",
            "nullable": true
        },
        "pem": {
            "type": "string",
            "example": "\"-----BEGIN RSA PRIVATE KEY-----\\nMIIEogIBAAKCAQEArYxrNYD/iT5CZVpRJu4rBKmmze3PVmT/gCo2ATUvDvZTPTey\\nxcGJ3vvrJXazKk06pN05TN29o98jrYz4cengG3YGsXPNEpKsIrEl8NhbnxapEnM9\\nJCMRe0P5JcPsfZlX6hmiT7136GRWiGOUba2X9+HKh8QJVLG5rM007TBER9/z9mWm\\nrJuNh+m5l320oBQY/Qq3A7wzdEfZw8qm/mIN0FCeoXH1L6B8xXWaAYBwhTEh6SSn\\nZHlO1Xu1JWDmAvBCi0RO5aRSKM8q9QEkvvHP4yweAtK3N8+aAbZ7ovaDhyGz8r6r\\nzhU1b8Uo0Z2ysf503WqzQgIajr7Fry7/kUwpgQIDAQABAoIBADwJp80Ko1xHPZDy\\nfcCKBDfIuPvkmSW6KumbsLMaQv1aGdHDwwTGv3t0ixSay8CGlxMRtRDyZPib6SvQ\\n6OH/lpfpbMdW2ErkksgtoIKBVrDilfrcAvrNZu7NxRNbhCSvN8q0s4ICecjbbVQh\\nnueSdlA6vGXbW58BHMq68uRbHkP+k+mM9U0mDJ1HMch67wlg5GbayVRt63H7R2+r\\nVxcna7B80J/lCEjIYZznawgiTvp3MSanTglqAYi+m1EcSsP14bJIB9vgaxS79kTu\\noiSo93leJbBvuGo8QEiUqTwMw4tDksmkLsoqNKQ1q9P7LZ9DGcujtPy4EZsamSJT\\ny8OJt0ECgYEA2lxOxJsQk2kI325JgKFjo92mQeUObIvPfSNWUIZQDTjniOI6Gv63\\nGLWVFrZcvQBWjMEQraJA9xjPbblV8PtfO87MiJGLWCHFxmPz2dzoedN+2Coxom8m\\nV95CLz8QUShuao6u/RYcvUaZEoYs5bHcTmy5sBK80JyEmafJPtCQVxMCgYEAy3ar\\nZr3yv4xRPEPMat4rseswmuMooSaK3SKub19WFI5IAtB/e7qR1Rj9JhOGcZz+OQrl\\nT78O2OFYlgOIkJPvRMrPpK5V9lslc7tz1FSh3BZMRGq5jSyD7ETSOQ0c8T2O/s7v\\nbeEPbVbDe4mwvM24XByH0GnWveVxaDl51ABD65sCgYB3ZAspUkOA5egVCh8kNpnd\\nSd6SnuQBE3ySRlT2WEnCwP9Ph6oPgn+oAfiPX4xbRqkL8q/k0BdHQ4h+zNwhk7+h\\nWtPYRAP1Xxnc/F+jGjb+DVaIaKGU18MWPg7f+FI6nampl3Q0KvfxwX0GdNhtio8T\\nTj1E+SnFwh56SRQuxSh2gwKBgHKjlIO5NtNSflsUYFM+hyQiPiqnHzddfhSG+/3o\\nm5nNaSmczJesUYreH5San7/YEy2UxAugvP7aSY2MxB+iGsiJ9WD2kZzTUlDZJ7RV\\nUzWsoqBR+eZfVJ2FUWWvy8TpSG6trh4dFxImNtKejCR1TREpSiTV3Zb1dmahK9GV\\nrK9NAoGAbBxRLoC01xfxCTgt5BDiBcFVh4fp5yYKwavJPLzHSpuDOrrI9jDn1oKN\\nonq5sDU1i391zfQvdrbX4Ova48BN+B7p63FocP/MK5tyyBoT8zQEk2+vWDOw7H/Z\\nu5dTCPxTIsoIwUw1I+7yIxqJzLPFgR2gVBwY1ra/8iAqCj+zeBw=\\n-----END RSA PRIVATE KEY-----\\n\""
        }
    },
    "required": [
        "id",
        "node_id",
        "owner",
        "name",
        "description",
        "external_url",
        "html_url",
        "created_at",
        "updated_at",
        "permissions",
        "events"
    ]
}
```

### `#/components/examples/integration`

```json
{
    "value": {
        "id": 1,
        "slug": "octoapp",
        "node_id": "MDExOkludGVncmF0aW9uMQ==",
        "owner": {
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
        "name": "Octocat App",
        "description": "",
        "external_url": "https://example.com",
        "html_url": "https://github.com/apps/octoapp",
        "created_at": "2017-07-08T16:18:44-04:00",
        "updated_at": "2017-07-08T16:18:44-04:00",
        "permissions": {
            "metadata": "read",
            "contents": "read",
            "issues": "write",
            "single_file": "write"
        },
        "events": [
            "push",
            "pull_request"
        ]
    }
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