# List releases

This returns a list of releases, which does not include regular Git tags that have not been associated with a release. To get a list of Git tags, use the [Repository Tags API](https://docs.github.com/rest/repos/repos#list-repository-tags).

Information about published releases are available to everyone. Only users with push access will receive listings for draft releases.

## Operation Object

```json
{
    "summary": "List releases",
    "description": "This returns a list of releases, which does not include regular Git tags that have not been associated with a release. To get a list of Git tags, use the [Repository Tags API](https://docs.github.com/rest/repos/repos#list-repository-tags).\n\nInformation about published releases are available to everyone. Only users with push access will receive listings for draft releases.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-releases",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/releases/releases#list-releases"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
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
                            "$ref": "#/components/schemas/release"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/release-items"
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
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "releases",
        "subcategory": "releases"
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

### `#/components/schemas/release`

```json
{
    "title": "Release",
    "description": "A release.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "assets_url": {
            "type": "string",
            "format": "uri"
        },
        "upload_url": {
            "type": "string"
        },
        "tarball_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "zipball_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "tag_name": {
            "description": "The name of the tag.",
            "example": "v1.0.0",
            "type": "string"
        },
        "target_commitish": {
            "description": "Specifies the commitish value that determines where the Git tag is created from.",
            "example": "master",
            "type": "string"
        },
        "name": {
            "type": "string",
            "nullable": true
        },
        "body": {
            "type": "string",
            "nullable": true
        },
        "draft": {
            "description": "true to create a draft (unpublished) release, false to create a published one.",
            "example": false,
            "type": "boolean"
        },
        "prerelease": {
            "description": "Whether to identify the release as a prerelease or a full release.",
            "example": false,
            "type": "boolean"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "published_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "author": {
            "$ref": "#/components/schemas/simple-user"
        },
        "assets": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/release-asset"
            }
        },
        "body_html": {
            "type": "string"
        },
        "body_text": {
            "type": "string"
        },
        "mentions_count": {
            "type": "integer"
        },
        "discussion_url": {
            "description": "The URL of the release discussion.",
            "type": "string",
            "format": "uri"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        }
    },
    "required": [
        "assets_url",
        "upload_url",
        "tarball_url",
        "zipball_url",
        "created_at",
        "published_at",
        "draft",
        "id",
        "node_id",
        "author",
        "html_url",
        "name",
        "prerelease",
        "tag_name",
        "target_commitish",
        "assets",
        "url"
    ]
}
```

### `#/components/examples/release-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/releases/1",
            "html_url": "https://github.com/octocat/Hello-World/releases/v1.0.0",
            "assets_url": "https://api.github.com/repos/octocat/Hello-World/releases/1/assets",
            "upload_url": "https://uploads.github.com/repos/octocat/Hello-World/releases/1/assets{?name,label}",
            "tarball_url": "https://api.github.com/repos/octocat/Hello-World/tarball/v1.0.0",
            "zipball_url": "https://api.github.com/repos/octocat/Hello-World/zipball/v1.0.0",
            "id": 1,
            "node_id": "MDc6UmVsZWFzZTE=",
            "tag_name": "v1.0.0",
            "target_commitish": "master",
            "name": "v1.0.0",
            "body": "Description of the release",
            "draft": false,
            "prerelease": false,
            "created_at": "2013-02-27T19:35:32Z",
            "published_at": "2013-02-27T19:35:32Z",
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
            "assets": [
                {
                    "url": "https://api.github.com/repos/octocat/Hello-World/releases/assets/1",
                    "browser_download_url": "https://github.com/octocat/Hello-World/releases/download/v1.0.0/example.zip",
                    "id": 1,
                    "node_id": "MDEyOlJlbGVhc2VBc3NldDE=",
                    "name": "example.zip",
                    "label": "short description",
                    "state": "uploaded",
                    "content_type": "application/zip",
                    "size": 1024,
                    "download_count": 42,
                    "created_at": "2013-02-27T19:35:32Z",
                    "updated_at": "2013-02-27T19:35:32Z",
                    "uploader": {
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
                    }
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