# List custom deployment rule integrations available for an environment

`GET /repos/{owner}/{repo}/environments/{environment_name}/deployment_protection_rules/apps`

Gets all custom deployment protection rule integrations that are available for an environment. Anyone with read access to the repository can use this endpoint.

For more information about environments, see "[Using environments for deployment](https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment)."

For more information about the app that is providing this custom deployment rule, see "[GET an app](https://docs.github.com/rest/apps/apps#get-an-app)".

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/deployments/protection-rules#list-custom-deployment-rule-integrations-available-for-an-environment)

## All Parameters for "List custom deployment rule integrations available for an environment"

### Path Parameters

- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."