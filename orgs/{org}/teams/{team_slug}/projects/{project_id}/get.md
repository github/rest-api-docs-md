# Check team permissions for a project

`GET /orgs/{org}/teams/{team_slug}/projects/{project_id}`

[API method documentation](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project)

## All Parameters for "Check team permissions for a project"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
- `project_id` (integer, required): The unique identifier of the project.

## Operation Description

Checks whether a team has `read`, `write`, or `admin` permissions for an organization project. The response includes projects inherited from a parent team.

> [!NOTE]
> You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/projects/{project_id}`.
