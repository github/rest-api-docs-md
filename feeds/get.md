# Get feeds

`get /feeds`

Lists the feeds available to the authenticated user. The response provides a URL for each feed. You can then get a specific feed by sending a request to one of the feed URLs.

*   **Timeline**: The GitHub global public timeline
*   **User**: The public timeline for any user, using `uri_template`. For more information, see "[Hypermedia](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#hypermedia)."
*   **Current user public**: The public timeline for the authenticated user
*   **Current user**: The private timeline for the authenticated user
*   **Current user actor**: The private timeline for activity created by the authenticated user
*   **Current user organizations**: The private timeline for the organizations the authenticated user is a member of.
*   **Security advisories**: A collection of public announcements that provide information about security-related vulnerabilities in software on GitHub.

By default, timeline resources are returned in JSON. You can specify the `application/atom+xml` type in the `Accept` header to return timeline resources in Atom format. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

**Note**: Private feeds are only returned when [authenticating via Basic Auth](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) since current feed URIs use the older, non revocable auth tokens.

## Operation Object

```json
{
    "summary": "Get feeds",
    "description": "Lists the feeds available to the authenticated user. The response provides a URL for each feed. You can then get a specific feed by sending a request to one of the feed URLs.\n\n*   **Timeline**: The GitHub global public timeline\n*   **User**: The public timeline for any user, using `uri_template`. For more information, see \"[Hypermedia](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#hypermedia).\"\n*   **Current user public**: The public timeline for the authenticated user\n*   **Current user**: The private timeline for the authenticated user\n*   **Current user actor**: The private timeline for activity created by the authenticated user\n*   **Current user organizations**: The private timeline for the organizations the authenticated user is a member of.\n*   **Security advisories**: A collection of public announcements that provide information about security-related vulnerabilities in software on GitHub.\n\nBy default, timeline resources are returned in JSON. You can specify the `application/atom+xml` type in the `Accept` header to return timeline resources in Atom format. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n**Note**: Private feeds are only returned when [authenticating via Basic Auth](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) since current feed URIs use the older, non revocable auth tokens.",
    "tags": [
        "activity"
    ],
    "operationId": "activity/get-feeds",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/activity/feeds#get-feeds"
    },
    "parameters": [],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/feed"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/feed"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "activity",
        "subcategory": "feeds"
    }
}
```

## References

### `#/components/schemas/feed`

```json
{
    "title": "Feed",
    "description": "Feed",
    "type": "object",
    "properties": {
        "timeline_url": {
            "type": "string",
            "example": "https://github.com/timeline"
        },
        "user_url": {
            "type": "string",
            "example": "https://github.com/{user}"
        },
        "current_user_public_url": {
            "type": "string",
            "example": "https://github.com/octocat"
        },
        "current_user_url": {
            "type": "string",
            "example": "https://github.com/octocat.private?token=abc123"
        },
        "current_user_actor_url": {
            "type": "string",
            "example": "https://github.com/octocat.private.actor?token=abc123"
        },
        "current_user_organization_url": {
            "type": "string",
            "example": "https://github.com/octocat-org"
        },
        "current_user_organization_urls": {
            "type": "array",
            "example": [
                "https://github.com/organizations/github/octocat.private.atom?token=abc123"
            ],
            "items": {
                "type": "string",
                "format": "uri"
            }
        },
        "security_advisories_url": {
            "type": "string",
            "example": "https://github.com/security-advisories"
        },
        "repository_discussions_url": {
            "type": "string",
            "example": "https://github.com/{user}/{repo}/discussions",
            "description": "A feed of discussions for a given repository."
        },
        "repository_discussions_category_url": {
            "type": "string",
            "example": "https://github.com/{user}/{repo}/discussions/categories/{category}",
            "description": "A feed of discussions for a given repository and category."
        },
        "_links": {
            "type": "object",
            "properties": {
                "timeline": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "user": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "security_advisories": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "current_user": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "current_user_public": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "current_user_actor": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "current_user_organization": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "current_user_organizations": {
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/link-with-type"
                    }
                },
                "repository_discussions": {
                    "$ref": "#/components/schemas/link-with-type"
                },
                "repository_discussions_category": {
                    "$ref": "#/components/schemas/link-with-type"
                }
            },
            "required": [
                "timeline",
                "user"
            ]
        }
    },
    "required": [
        "_links",
        "timeline_url",
        "user_url"
    ]
}
```

### `#/components/examples/feed`

```json
{
    "value": {
        "timeline_url": "https://github.com/timeline",
        "user_url": "https://github.com/{user}",
        "current_user_public_url": "https://github.com/octocat",
        "current_user_url": "https://github.com/octocat.private?token=abc123",
        "current_user_actor_url": "https://github.com/octocat.private.actor?token=abc123",
        "current_user_organization_url": "",
        "current_user_organization_urls": [
            "https://github.com/organizations/github/octocat.private.atom?token=abc123"
        ],
        "security_advisories_url": "https://github.com/security-advisories",
        "_links": {
            "timeline": {
                "href": "https://github.com/timeline",
                "type": "application/atom+xml"
            },
            "user": {
                "href": "https://github.com/{user}",
                "type": "application/atom+xml"
            },
            "current_user_public": {
                "href": "https://github.com/octocat",
                "type": "application/atom+xml"
            },
            "current_user": {
                "href": "https://github.com/octocat.private?token=abc123",
                "type": "application/atom+xml"
            },
            "current_user_actor": {
                "href": "https://github.com/octocat.private.actor?token=abc123",
                "type": "application/atom+xml"
            },
            "current_user_organization": {
                "href": "",
                "type": ""
            },
            "current_user_organizations": [
                {
                    "href": "https://github.com/organizations/github/octocat.private.atom?token=abc123",
                    "type": "application/atom+xml"
                }
            ],
            "security_advisories": {
                "href": "https://github.com/security-advisories",
                "type": "application/atom+xml"
            }
        }
    }
}
```