# List all Copilot seat assignments for an organization

`GET /orgs/{org}/copilot/billing/seats`

[API method documentation](https://docs.github.com/rest/copilot/copilot-user-management#list-all-copilot-seat-assignments-for-an-organization)

## All Parameters for "List all Copilot seat assignments for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

**Note**: This endpoint is in beta and is subject to change.

Lists all active Copilot seats for an organization with a Copilot Business or Copilot Enterprise subscription.
Only organization owners can view assigned seats.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.
