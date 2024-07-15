# List assignments for a classroom

`GET /classrooms/{classroom_id}/assignments`

[API method documentation](https://docs.github.com/rest/classroom/classroom#list-assignments-for-a-classroom)

## All Parameters for "List assignments for a classroom"

### Path Parameters

- `classroom_id` (integer, required): The unique identifier of the classroom.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists GitHub Classroom assignments for a classroom. Assignments will only be returned if the current user is an administrator of the GitHub Classroom.
