# Download a repository archive (tar)

`get /repos/{owner}/{repo}/tarball/{ref}`

Gets a redirect URL to download a tar archive for a repository. If you omit `:ref`, the repository’s default branch (usually
`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use
the `Location` header to make a second `GET` request.
**Note**: For private repositories, these links are temporary and expire after five minutes.

## Operation Object

```json
{
    "summary": "Download a repository archive (tar)",
    "description": "Gets a redirect URL to download a tar archive for a repository. If you omit `:ref`, the repository\u2019s default branch (usually\n`main`) will be used. Please make sure your HTTP framework is configured to follow redirects or you will need to use\nthe `Location` header to make a second `GET` request.\n**Note**: For private repositories, these links are temporary and expire after five minutes.",
    "tags": [
        "repos"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/contents#download-a-repository-archive-tar"
    },
    "operationId": "repos/download-tarball-archive",
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