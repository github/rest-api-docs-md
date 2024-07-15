# Check team permissions for a project (Legacy)

`GET /teams/{team_id}/projects/{project_id}`

[API method documentation](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project-legacy)

## All Parameters for "Check team permissions for a project (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `project_id` (integer, required): The unique identifier of the project.

## Operation Description

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Check team permissions for a project](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project) endpoint.

Checks whether a team has `read`, `write`, or `admin` permissions for an organization project. The response includes projects inherited from a parent team.
