# Get the Zen of GitHub

Get a random sentence from the Zen of GitHub

## Operation Object

```json
{
    "summary": "Get the Zen of GitHub",
    "description": "Get a random sentence from the Zen of GitHub",
    "tags": [
        "meta"
    ],
    "operationId": "meta/get-zen",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/meta/meta#get-the-zen-of-github"
    },
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "string"
                    },
                    "examples": {
                        "default": {
                            "summary": "Example response",
                            "value": "Responsive is better than fast"
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
    }
}
```