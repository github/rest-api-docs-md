# List repository languages

Lists languages for the specified repository. The value shown for each language is the number of bytes of code written in that language.

## Operation Object

```json
{
    "summary": "List repository languages",
    "description": "Lists languages for the specified repository. The value shown for each language is the number of bytes of code written in that language.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-languages",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/repos#list-repository-languages"
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
                        "$ref": "#/components/schemas/language"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/language"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "repos"
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

### `#/components/schemas/language`

```json
{
    "title": "Language",
    "description": "Language",
    "type": "object",
    "additionalProperties": {
        "type": "integer"
    }
}
```

### `#/components/examples/language`

```json
{
    "value": {
        "C": 78769,
        "Python": 7769
    }
}
```