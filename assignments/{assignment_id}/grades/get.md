# Get assignment grades

`GET /assignments/{assignment_id}/grades`

[API method documentation](https://docs.github.com/rest/classroom/classroom#get-assignment-grades)

## All Parameters for "Get assignment grades"

### Path Parameters

- `assignment_id` (integer, required): The unique identifier of the classroom assignment.

## Operation Description

Gets grades for a GitHub Classroom assignment. Grades will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.
