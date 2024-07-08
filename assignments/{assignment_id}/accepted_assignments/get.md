# List accepted assignments for an assignment

`GET /assignments/{assignment_id}/accepted_assignments`

Lists any assignment repositories that have been created by students accepting a GitHub Classroom assignment. Accepted assignments will only be returned if the current user is an administrator of the GitHub Classroom for the assignment.

[API method documentation](https://docs.github.com/rest/classroom/classroom#list-accepted-assignments-for-an-assignment)

## All Parameters for "List accepted assignments for an assignment"

### Path Parameters

- `assignment_id` (integer, required): The unique identifier of the classroom assignment.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."