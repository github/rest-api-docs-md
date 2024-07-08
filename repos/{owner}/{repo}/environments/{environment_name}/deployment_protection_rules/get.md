# Get all deployment protection rules for an environment

`GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules`

Gets all custom deployment protection rules that are enabled for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see the [documentation for the `GET /apps/{app_slug}` endpoint](https://docs.github.com/rest/apps/apps#get-an-app).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/deployments/protection-rules#get-all-deployment-protection-rules-for-an-environment)

## All Parameters for "Get all deployment protection rules for an environment"

### Path Parameters

- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `owner` (string, required): The account owner of the repository. The name is not case sensitive.