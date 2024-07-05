# List accepted assignments for an assignment

`get /assignments/{assignment_id}/accepted_assignments`

Lists any assignment repositories that have been created by students accepting a GitHub Classroom assignment. Accepted assignments will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.

## Operation Object

```json
{
    "summary": "List accepted assignments for an assignment",
    "description": "Lists any assignment repositories that have been created by students accepting a GitHub Classroom assignment. Accepted assignments will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/list-accepted-assigments-for-an-assignment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#list-accepted-assignments-for-an-assignment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/assignment-id"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/classroom-accepted-assignment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/classroom-accepted-assignment"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "category": "classroom",
        "subcategory": "classroom"
    }
}
```

## References

### `#/components/parameters/assignment-id`

```json
{
    "name": "assignment_id",
    "description": "The unique identifier of the classroom assignment.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
    }
}
```

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/schemas/classroom-accepted-assignment`

```json
{
    "title": "Classroom Accepted Assignment",
    "description": "A GitHub Classroom accepted assignment",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the repository.",
            "type": "integer",
            "example": 42
        },
        "submitted": {
            "description": "Whether an accepted assignment has been submitted.",
            "type": "boolean",
            "example": true
        },
        "passing": {
            "description": "Whether a submission passed.",
            "type": "boolean",
            "example": true
        },
        "commit_count": {
            "description": "Count of student commits.",
            "type": "integer",
            "example": 5
        },
        "grade": {
            "description": "Most recent grade.",
            "type": "string",
            "example": "10/10"
        },
        "students": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-classroom-user"
            }
        },
        "repository": {
            "$ref": "#/components/schemas/simple-classroom-repository"
        },
        "assignment": {
            "$ref": "#/components/schemas/simple-classroom-assignment"
        }
    },
    "required": [
        "id",
        "submitted",
        "passing",
        "commit_count",
        "grade",
        "students",
        "repository",
        "assignment"
    ]
}
```

### `#/components/examples/classroom-accepted-assignment`

```json
{
    "value": {
        "id": "12,",
        "submitted": "false,",
        "passing": "false,",
        "commit_count": 5,
        "grade": "5/10",
        "students": [
            {
                "id": 1,
                "login": "octocat",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "html_url": "https://github.com/octocat"
            }
        ],
        "repository": {
            "id": 1296269,
            "full_name": "octocat/Hello-World",
            "html_url": "https://github.com/octocat/Hello-World",
            "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
            "private": false,
            "default_branch": "main"
        },
        "assignment": {
            "id": "12,",
            "public_repo": "false,",
            "title": "Intro to Binaries",
            "type": "individual",
            "invite_link": "https://classroom.github.com/a/Lx7jiUgx",
            "invitations_enabled": "true,",
            "slug": "intro-to-binaries",
            "students_are_repo_admins": false,
            "feedback_pull_requests_enabled": true,
            "max_teams": 0,
            "max_members": 0,
            "editor": "codespaces",
            "accepted": 100,
            "submitted": 40,
            "passing": 10,
            "language": "ruby",
            "classroom": {
                "id": 1296269,
                "name": "Programming Elixir",
                "archived": "false,",
                "url": "https://classroom.github.com/classrooms/1-programming-elixir"
            }
        }
    }
}
```