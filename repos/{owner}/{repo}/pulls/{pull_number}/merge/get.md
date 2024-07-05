# Check if a pull request has been merged

Checks if a pull request has been merged into the base branch. The HTTP status of the response indicates whether or not the pull request has been merged; the response body is empty.

## Operation Object

```json
{
    "summary": "Check if a pull request has been merged",
    "description": "Checks if a pull request has been merged into the base branch. The HTTP status of the response indicates whether or not the pull request has been merged; the response body is empty.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/check-if-merged",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/pulls#check-if-a-pull-request-has-been-merged"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/pull-number"
        }
    ],
    "responses": {
        "204": {
            "description": "Response if pull request has been merged"
        },
        "404": {
            "description": "Not Found if pull request has not been merged"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "pulls"
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

### `#/components/parameters/pull-number`

```json
{
    "name": "pull_number",
    "description": "The number that identifies the pull request.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```