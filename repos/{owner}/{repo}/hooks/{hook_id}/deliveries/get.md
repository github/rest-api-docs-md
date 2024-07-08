# List deliveries for a repository webhook

`GET /repos/{owner}/{repo}/hooks/{hook_id}/deliveries`

Returns a list of webhook deliveries for a webhook configured in a repository.

[API method documentation](https://docs.github.com/rest/repos/webhooks#list-deliveries-for-a-repository-webhook)

## All Parameters for "List deliveries for a repository webhook"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `cursor` (string): Used for pagination: the starting delivery from which the page of deliveries is fetched. Refer to the `link` header for the next and previous page cursors.
- `redelivery` (boolean)