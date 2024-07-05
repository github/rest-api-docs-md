# Get Octocat

Get the octocat as ASCII art

## Operation Object

```json
{
    "summary": "Get Octocat",
    "description": "Get the octocat as ASCII art",
    "tags": [
        "meta"
    ],
    "operationId": "meta/get-octocat",
    "parameters": [
        {
            "name": "s",
            "in": "query",
            "description": "The words to show in Octocat's speech bubble",
            "schema": {
                "type": "string"
            },
            "required": false
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/octocat-stream": {
                    "schema": {
                        "type": "string"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/octocat"
                        }
                    }
                }
            }
        }
    },
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/meta/meta#get-octocat"
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "meta",
        "subcategory": "meta"
    }
}
```

## References

### `#/components/examples/octocat`

```json
{
    "value": "               MMM.           .MMM\n               MMMMMMMMMMMMMMMMMMM\n               MMMMMMMMMMMMMMMMMMM      ___________________________________\n              MMMMMMMMMMMMMMMMMMMMM    |                                   |\n             MMMMMMMMMMMMMMMMMMMMMMM   | Avoid administrative distraction. |\n            MMMMMMMMMMMMMMMMMMMMMMMM   |_   _______________________________|\n            MMMM::- -:::::::- -::MMMM    |/\n             MM~:~ 00~:::::~ 00~:~MM\n        .. MMMMM::.00:::+:::.00::MMMMM ..\n              .MM::::: ._. :::::MM.\n                 MMMM;:::::;MMMM\n          -MM        MMMMMMM\n          ^  M+     MMMMMMMMM\n              MMMMMMM MM MM MM\n                   MM MM MM MM\n                   MM MM MM MM\n                .~~MM~MM~MM~MM~~.\n             ~~~~MM:~MM~~~MM~:MM~~~~\n            ~~~~~~==~==~~~==~==~~~~~~\n             ~~~~~~==~==~==~==~~~~~~\n                 :~==~==~==~==~~\n"
}
```