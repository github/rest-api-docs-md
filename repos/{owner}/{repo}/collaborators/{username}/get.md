# Check if a user is a repository collaborator

`get /repos/{owner}/{repo}/collaborators/{username}`

For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.

Team members will include the members of child teams.

The authenticated user must have push access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "Check if a user is a repository collaborator",
    "description": "For organization-owned repositories, the list of collaborators includes outside collaborators, organization members that are direct collaborators, organization members with access through team memberships, organization members with access through default organization permissions, and organization owners.\n\nTeam members will include the members of child teams.\n\nThe authenticated user must have push access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `read:org` and `repo` scopes to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/check-collaborator",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/collaborators/collaborators#check-if-a-user-is-a-repository-collaborator"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "204": {
            "description": "Response if user is a collaborator"
        },
        "404": {
            "description": "Not Found if user is not a collaborator"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "collaborators",
        "subcategory": "collaborators"
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