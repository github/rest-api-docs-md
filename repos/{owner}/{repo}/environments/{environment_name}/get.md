# Get an environment

`GET /repos/{owner}/{repo}/environments/{environment_name}`

[API method documentation](https://docs.github.com/rest/deployments/environments#get-an-environment)

## All Parameters for "Get an environment"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.

## Operation Description

**Note:** To get information about name patterns that branches must match in order to deploy to this environment, see "[Get a deployment branch policy](/rest/deployments/branch-policies#get-a-deployment-branch-policy)."

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.
