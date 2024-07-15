# List deliveries for an app webhook

`GET /app/hook/deliveries`

[API method documentation](https://docs.github.com/rest/apps/webhooks#list-deliveries-for-an-app-webhook)

## All Parameters for "List deliveries for an app webhook"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `cursor` (string): Used for pagination: the starting delivery from which the page of deliveries is fetched. Refer to the `link` header for the next and previous page cursors.
- `redelivery` (boolean)

## Operation Description

Returns a list of webhook deliveries for the webhook configured for a GitHub App.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.
