# List assignments for a classroom

`get /classrooms/{classroom_id}/assignments`

Lists GitHub Classroom assignments for a classroom. Assignments will only be returned if the current user is an administrator of the GitHub Classroom.

## Operation Object

```json
{
    "summary": "List assignments for a classroom",
    "description": "Lists GitHub Classroom assignments for a classroom. Assignments will only be returned if the current user is an administrator of the GitHub Classroom.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/list-assignments-for-a-classroom",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#list-assignments-for-a-classroom"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/classroom-id"
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
                            "$ref": "#/components/schemas/simple-classroom-assignment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/simple-classroom-assignment"
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

### `#/components/parameters/classroom-id`

```json
{
    "name": "classroom_id",
    "description": "The unique identifier of the classroom.",
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

### `#/components/schemas/simple-classroom-assignment`

```json
{
    "title": "Simple Classroom Assignment",
    "description": "A GitHub Classroom assignment",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the repository.",
            "type": "integer",
            "example": 42
        },
        "public_repo": {
            "description": "Whether an accepted assignment creates a public repository.",
            "type": "boolean",
            "example": true
        },
        "title": {
            "description": "Assignment title.",
            "type": "string",
            "example": "Intro to Binaries"
        },
        "type": {
            "description": "Whether it's a Group Assignment or Individual Assignment.",
            "type": "string",
            "example": "individual",
            "enum": [
                "individual",
                "group"
            ]
        },
        "invite_link": {
            "description": "The link that a student can use to accept the assignment.",
            "type": "string",
            "example": "https://classroom.github.com/a/Lx7jiUgx"
        },
        "invitations_enabled": {
            "description": "Whether the invitation link is enabled. Visiting an enabled invitation link will accept the assignment.",
            "type": "boolean",
            "example": true
        },
        "slug": {
            "description": "Sluggified name of the assignment.",
            "type": "string",
            "example": "intro-to-binaries"
        },
        "students_are_repo_admins": {
            "description": "Whether students are admins on created repository on accepted assignment.",
            "type": "boolean",
            "example": true
        },
        "feedback_pull_requests_enabled": {
            "description": "Whether feedback pull request will be created on assignment acceptance.",
            "type": "boolean",
            "example": true
        },
        "max_teams": {
            "description": "The maximum allowable teams for the assignment.",
            "nullable": true,
            "type": "integer",
            "example": 0
        },
        "max_members": {
            "description": "The maximum allowable members per team.",
            "nullable": true,
            "type": "integer",
            "example": 0
        },
        "editor": {
            "description": "The selected editor for the assignment.",
            "type": "string",
            "example": "codespaces"
        },
        "accepted": {
            "description": "The number of students that have accepted the assignment.",
            "type": "integer",
            "example": 25
        },
        "submitted": {
            "description": "The number of students that have submitted the assignment.",
            "type": "integer",
            "example": 10
        },
        "passing": {
            "description": "The number of students that have passed the assignment.",
            "type": "integer",
            "example": 10
        },
        "language": {
            "description": "The programming language used in the assignment.",
            "type": "string",
            "example": "elixir"
        },
        "deadline": {
            "description": "The time at which the assignment is due.",
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:06:43Z",
            "nullable": true
        },
        "classroom": {
            "$ref": "#/components/schemas/simple-classroom"
        }
    },
    "required": [
        "id",
        "public_repo",
        "title",
        "type",
        "invite_link",
        "invitations_enabled",
        "slug",
        "students_are_repo_admins",
        "feedback_pull_requests_enabled",
        "editor",
        "accepted",
        "submitted",
        "passing",
        "language",
        "deadline",
        "classroom"
    ]
}
```

### `#/components/examples/simple-classroom-assignment`

```json
{
    "value": {
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
        "deadline": "2020-01-11T11:59:22Z",
        "classroom": {
            "id": 1296269,
            "name": "Programming Elixir",
            "archived": "false,",
            "url": "https://classroom.github.com/classrooms/1-programming-elixir"
        }
    }
}
```