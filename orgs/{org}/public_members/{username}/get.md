# Check public organization membership for a user

Check if the provided user is a public member of the organization.

## Operation Object

```json
{
    "summary": "Check public organization membership for a user",
    "description": "Check if the provided user is a public member of the organization.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/check-public-membership-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/members#check-public-organization-membership-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "204": {
            "description": "Response if user is a public member"
        },
        "404": {
            "description": "Not Found if user is not a public member"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "members"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```