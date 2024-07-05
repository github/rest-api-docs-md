# Get assignment grades

Gets grades for a GitHub Classroom assignment. Grades will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.

## Operation Object

```json
{
    "summary": "Get assignment grades",
    "description": "Gets grades for a GitHub Classroom assignment. Grades will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/get-assignment-grades",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#get-assignment-grades"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/classroom-assignment-grade"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/classroom-assignment-grades"
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

### `#/components/schemas/classroom-assignment-grade`

```json
{
    "title": "Classroom Assignment Grade",
    "description": "Grade for a student or groups GitHub Classroom assignment",
    "type": "object",
    "properties": {
        "assignment_name": {
            "description": "Name of the assignment",
            "type": "string"
        },
        "assignment_url": {
            "description": "URL of the assignment",
            "type": "string"
        },
        "starter_code_url": {
            "description": "URL of the starter code for the assignment",
            "type": "string"
        },
        "github_username": {
            "description": "GitHub username of the student",
            "type": "string"
        },
        "roster_identifier": {
            "description": "Roster identifier of the student",
            "type": "string"
        },
        "student_repository_name": {
            "description": "Name of the student's assignment repository",
            "type": "string"
        },
        "student_repository_url": {
            "description": "URL of the student's assignment repository",
            "type": "string"
        },
        "submission_timestamp": {
            "description": "Timestamp of the student's assignment submission",
            "type": "string"
        },
        "points_awarded": {
            "description": "Number of points awarded to the student",
            "type": "integer"
        },
        "points_available": {
            "description": "Number of points available for the assignment",
            "type": "integer"
        },
        "group_name": {
            "description": "If a group assignment, name of the group the student is in",
            "type": "string"
        }
    },
    "required": [
        "assignment_name",
        "assignment_url",
        "starter_code_url",
        "github_username",
        "roster_identifier",
        "student_repository_name",
        "student_repository_url",
        "submission_timestamp",
        "points_awarded",
        "points_available"
    ]
}
```

### `#/components/examples/classroom-assignment-grades`

```json
{
    "value": [
        {
            "assignment_name": "Introduction to Strings",
            "assignment_url": "https://classroom.github.com/classrooms/1337/assignments/1337",
            "starter_code_url": "",
            "github_username": "octocat",
            "roster_identifier": "octocat@github.com",
            "student_repository_name": "intro-to-strings-1337-octocat",
            "student_repository_url": "https://github.com/timeforschool/intro-to-strings-1337-octocat",
            "submission_timestamp": "2018-11-12 01:02",
            "points_awarded": 10,
            "points_available": 15,
            "group_name": "octocat-and-friends"
        },
        {
            "assignment_name": "Introduction to Strings",
            "assignment_url": "https://classroom.github.com/classrooms/1337/assignments/1337",
            "starter_code_url": "",
            "github_username": "monalisa",
            "roster_identifier": "monalisa@github.com",
            "student_repository_name": "intro-to-strings-1337-monalisa",
            "student_repository_url": "https://github.com/timeforschool/intro-to-strings-1337-monalisa",
            "submission_timestamp": "2018-11-12 01:11",
            "points_awarded": 15,
            "points_available": 15,
            "group_name": "monalisa-and-friends"
        }
    ]
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