# GitHub API Root

Get Hypermedia links to resources accessible in GitHub's REST API

## Operation Object

```json
{
    "summary": "GitHub API Root",
    "description": "Get Hypermedia links to resources accessible in GitHub's REST API",
    "tags": [
        "meta"
    ],
    "operationId": "meta/root",
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/root"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/root"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "meta",
        "subcategory": "meta"
    },
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/meta/meta#github-api-root"
    }
}
```

## References

### `#/components/schemas/root`

```json
{
    "type": "object",
    "properties": {
        "current_user_url": {
            "type": "string",
            "format": "uri-template"
        },
        "current_user_authorizations_html_url": {
            "type": "string",
            "format": "uri-template"
        },
        "authorizations_url": {
            "type": "string",
            "format": "uri-template"
        },
        "code_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "commit_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "emails_url": {
            "type": "string",
            "format": "uri-template"
        },
        "emojis_url": {
            "type": "string",
            "format": "uri-template"
        },
        "events_url": {
            "type": "string",
            "format": "uri-template"
        },
        "feeds_url": {
            "type": "string",
            "format": "uri-template"
        },
        "followers_url": {
            "type": "string",
            "format": "uri-template"
        },
        "following_url": {
            "type": "string",
            "format": "uri-template"
        },
        "gists_url": {
            "type": "string",
            "format": "uri-template"
        },
        "hub_url": {
            "type": "string",
            "format": "uri-template",
            "deprecated": true
        },
        "issue_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "issues_url": {
            "type": "string",
            "format": "uri-template"
        },
        "keys_url": {
            "type": "string",
            "format": "uri-template"
        },
        "label_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "notifications_url": {
            "type": "string",
            "format": "uri-template"
        },
        "organization_url": {
            "type": "string",
            "format": "uri-template"
        },
        "organization_repositories_url": {
            "type": "string",
            "format": "uri-template"
        },
        "organization_teams_url": {
            "type": "string",
            "format": "uri-template"
        },
        "public_gists_url": {
            "type": "string",
            "format": "uri-template"
        },
        "rate_limit_url": {
            "type": "string",
            "format": "uri-template"
        },
        "repository_url": {
            "type": "string",
            "format": "uri-template"
        },
        "repository_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "current_user_repositories_url": {
            "type": "string",
            "format": "uri-template"
        },
        "starred_url": {
            "type": "string",
            "format": "uri-template"
        },
        "starred_gists_url": {
            "type": "string",
            "format": "uri-template"
        },
        "topic_search_url": {
            "type": "string",
            "format": "uri-template"
        },
        "user_url": {
            "type": "string",
            "format": "uri-template"
        },
        "user_organizations_url": {
            "type": "string",
            "format": "uri-template"
        },
        "user_repositories_url": {
            "type": "string",
            "format": "uri-template"
        },
        "user_search_url": {
            "type": "string",
            "format": "uri-template"
        }
    },
    "required": [
        "current_user_url",
        "current_user_authorizations_html_url",
        "authorizations_url",
        "code_search_url",
        "commit_search_url",
        "emails_url",
        "emojis_url",
        "events_url",
        "feeds_url",
        "followers_url",
        "following_url",
        "gists_url",
        "issue_search_url",
        "issues_url",
        "keys_url",
        "label_search_url",
        "notifications_url",
        "organization_url",
        "organization_repositories_url",
        "organization_teams_url",
        "public_gists_url",
        "rate_limit_url",
        "repository_url",
        "repository_search_url",
        "current_user_repositories_url",
        "starred_url",
        "starred_gists_url",
        "user_url",
        "user_organizations_url",
        "user_repositories_url",
        "user_search_url"
    ]
}
```

### `#/components/examples/root`

```json
{
    "value": {
        "current_user_url": "https://api.github.com/user",
        "current_user_authorizations_html_url": "https://github.com/settings/connections/applications{/client_id}",
        "authorizations_url": "https://api.github.com/authorizations",
        "code_search_url": "https://api.github.com/search/code?q={query}{&page,per_page,sort,order}",
        "commit_search_url": "https://api.github.com/search/commits?q={query}{&page,per_page,sort,order}",
        "emails_url": "https://api.github.com/user/emails",
        "emojis_url": "https://api.github.com/emojis",
        "events_url": "https://api.github.com/events",
        "feeds_url": "https://api.github.com/feeds",
        "followers_url": "https://api.github.com/user/followers",
        "following_url": "https://api.github.com/user/following{/target}",
        "gists_url": "https://api.github.com/gists{/gist_id}",
        "hub_url": "https://api.github.com/hub",
        "issue_search_url": "https://api.github.com/search/issues?q={query}{&page,per_page,sort,order}",
        "issues_url": "https://api.github.com/issues",
        "keys_url": "https://api.github.com/user/keys",
        "label_search_url": "https://api.github.com/search/labels?q={query}&repository_id={repository_id}{&page,per_page}",
        "notifications_url": "https://api.github.com/notifications",
        "organization_url": "https://api.github.com/orgs/{org}",
        "organization_repositories_url": "https://api.github.com/orgs/{org}/repos{?type,page,per_page,sort}",
        "organization_teams_url": "https://api.github.com/orgs/{org}/teams",
        "public_gists_url": "https://api.github.com/gists/public",
        "rate_limit_url": "https://api.github.com/rate_limit",
        "repository_url": "https://api.github.com/repos/{owner}/{repo}",
        "repository_search_url": "https://api.github.com/search/repositories?q={query}{&page,per_page,sort,order}",
        "current_user_repositories_url": "https://api.github.com/user/repos{?type,page,per_page,sort}",
        "starred_url": "https://api.github.com/user/starred{/owner}{/repo}",
        "starred_gists_url": "https://api.github.com/gists/starred",
        "topic_search_url": "https://api.github.com/search/topics?q={query}{&page,per_page}",
        "user_url": "https://api.github.com/users/{user}",
        "user_organizations_url": "https://api.github.com/user/orgs",
        "user_repositories_url": "https://api.github.com/users/{user}/repos{?type,page,per_page,sort}",
        "user_search_url": "https://api.github.com/search/users?q={query}{&page,per_page,sort,order}"
    }
}
```