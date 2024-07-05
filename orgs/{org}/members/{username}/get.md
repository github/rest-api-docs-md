# Check organization membership for a user

Check if a user is, publicly or privately, a member of the organization.

## Operation Object

```json
{
    "summary": "Check organization membership for a user",
    "description": "Check if a user is, publicly or privately, a member of the organization.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/check-membership-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/members#check-organization-membership-for-a-user"
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
            "description": "Response if requester is an organization member and user is a member"
        },
        "302": {
            "description": "Response if requester is not an organization member",
            "headers": {
                "Location": {
                    "example": "https://api.github.com/orgs/github/public_members/pezra",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        },
        "404": {
            "description": "Not Found if requester is an organization member and user is not a member"
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