# Get an assignment

Gets a GitHub Classroom assignment. Assignment will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.

## Operation Object

```json
{
    "summary": "Get an assignment",
    "description": "Gets a GitHub Classroom assignment. Assignment will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/get-an-assignment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#get-an-assignment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/assignment-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/classroom-assignment"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/classroom-assignment"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/schemas/classroom-assignment`

```json
{
    "title": "Classroom Assignment",
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
            "description": "Whether it's a group assignment or individual assignment.",
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
            "description": "Whether students are admins on created repository when a student accepts the assignment.",
            "type": "boolean",
            "example": true
        },
        "feedback_pull_requests_enabled": {
            "description": "Whether feedback pull request will be created when a student accepts the assignment.",
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
        "starter_code_repository": {
            "$ref": "#/components/schemas/simple-classroom-repository"
        },
        "classroom": {
            "$ref": "#/components/schemas/classroom"
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
        "max_teams",
        "max_members",
        "editor",
        "accepted",
        "submitted",
        "passing",
        "language",
        "deadline",
        "starter_code_repository",
        "classroom"
    ]
}
```

### `#/components/examples/classroom-assignment`

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
        "deadline": "2011-01-26T19:06:43Z",
        "stater_code_repository": {
            "id": 1296269,
            "full_name": "octocat/Hello-World",
            "html_url": "https://github.com/octocat/Hello-World",
            "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
            "private": false,
            "default_branch": "main"
        },
        "classroom": {
            "id": 1296269,
            "name": "Programming Elixir",
            "archived": "false,",
            "url": "https://classroom.github.com/classrooms/1-programming-elixir"
        }
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```