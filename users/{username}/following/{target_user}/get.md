# Check if a user follows another user



## Operation Object

```json
{
    "summary": "Check if a user follows another user",
    "description": "",
    "tags": [
        "users"
    ],
    "operationId": "users/check-following-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/followers#check-if-a-user-follows-another-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
        },
        {
            "name": "target_user",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "204": {
            "description": "if the user follows the target user"
        },
        "404": {
            "description": "if the user does not follow the target user"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "users",
        "subcategory": "followers"
    }
}
```

## References

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