# Get a project

`GET /projects/{project_id}`

[API method documentation](https://docs.github.com/rest/projects/projects#get-a-project)

## All Parameters for "Get a project"

### Path Parameters

- `project_id` (integer, required): The unique identifier of the project.

## Operation Description

Gets a project by its `id`. Returns a `404 Not Found` status if projects are disabled. If you do not have sufficient privileges to perform this action, a `401 Unauthorized` or `410 Gone` status is returned.
