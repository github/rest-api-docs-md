# Download a repository archive (zip)

`get /repos/{owner}/{repo}/zipball/{ref}`

Gets a redirect URL to download a zip archive for a repository. If you omit `:ref`, the repository’s default branch (usually
`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use
the `Location` header to make a second `GET` request.

**Note**: For private repositories, these links are temporary and expire after five minutes. If the repository is empty, you will receive a 404 when you follow the redirect.

## Operation Object

```json
{
    "summary": "Download a repository archive (zip)",
    "description": "Gets a redirect URL to download a zip archive for a repository. If you omit `:ref`, the repository\u2019s default branch (usually\n`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use\nthe `Location` header to make a second `GET` request.\n\n**Note**: For private repositories, these links are temporary and expire after five minutes. If the repository is empty, you will receive a 404 when you follow the redirect.",
    "tags": [
        "repos"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/contents#download-a-repository-archive-zip"
    },
    "operationId": "repos/download-zipball-archive",
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "ref",
            "in": "path",
            "required": true,
            "x-multi-segment": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "302": {
            "description": "Response",
            "headers": {
                "Location": {
                    "example": "https://codeload.github.com/me/myprivate/legacy.zip/master?login=me&token=thistokenexpires",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "contents"
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