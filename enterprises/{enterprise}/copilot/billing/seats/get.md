# List all Copilot seat assignments for an enterprise

`GET /enterprises/{enterprise}/copilot/billing/seats`

[API method documentation](https://docs.github.com/rest/copilot/copilot-user-management#list-all-copilot-seat-assignments-for-an-enterprise)

## All Parameters for "List all Copilot seat assignments for an enterprise"

### Path Parameters

- `enterprise` (string, required): The slug version of the enterprise name. You can also substitute this value with the enterprise id.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

> [!NOTE]
> This endpoint is in beta and is subject to change.

Lists all active Copilot seats across organizations or enterprise teams for an enterprise with a Copilot Business or Copilot Enterprise subscription.

Users with access through multiple organizations or enterprise teams will only be counted toward `total_seats` once.

For each organization or enterprise team which grants Copilot access to a user, a seat detail object will appear in the `seats` array.

Only enterprise owners and billing managers can view assigned Copilot seats across their child organizations or enterprise teams.

Personal access tokens (classic) need either the `manage_billing:copilot` or `read:enterprise` scopes to use this endpoint.
