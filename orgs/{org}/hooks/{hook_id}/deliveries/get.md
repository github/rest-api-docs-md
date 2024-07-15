# List deliveries for an organization webhook

`GET /orgs/{org}/hooks/{hook_id}/deliveries`

[API method documentation](https://docs.github.com/rest/orgs/webhooks#list-deliveries-for-an-organization-webhook)

## All Parameters for "List deliveries for an organization webhook"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `cursor` (string): Used for pagination: the starting delivery from which the page of deliveries is fetched. Refer to the `link` header for the next and previous page cursors.
- `redelivery` (boolean)

## Operation Description

Returns a list of webhook deliveries for a webhook configured in an organization.

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.
