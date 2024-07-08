# Get a custom deployment protection rule

`GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/{protection_rule_id}`

Gets an enabled custom deployment protection rule for an environment. Anyone with read access to the repository can use this endpoint. For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see [`GET /apps/{app_slug}`](https://docs.github.com/rest/apps/apps#get-an-app).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/deployments/protection-rules#get-a-custom-deployment-protection-rule)

## All Parameters for "Get a custom deployment protection rule"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
- `protection_rule_id` (integer, required): The unique identifier of the protection rule.