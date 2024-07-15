# Get a deployment status

`GET /repos/{owner}/{repo}/deployments/{deployment_id}/statuses/{status_id}`

[API method documentation](https://docs.github.com/rest/deployments/statuses#get-a-deployment-status)

## All Parameters for "Get a deployment status"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `deployment_id` (integer, required): deployment_id parameter
- `status_id` (integer, required)

## Operation Description

Users with pull access can view a deployment status for a deployment:
