# Get a summary of Copilot usage for enterprise members

`GET /enterprises/{enterprise}/copilot/usage`

[API method documentation](https://docs.github.com/rest/copilot/copilot-usage#get-a-summary-of-copilot-usage-for-enterprise-members)

## All Parameters for "Get a summary of Copilot usage for enterprise members"

### Path Parameters

- `enterprise` (string, required): The slug version of the enterprise name. You can also substitute this value with the enterprise id.
### Query Parameters

- `since` (string): Show usage metrics since this date. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDTHH:MM:SSZ`). Maximum value is 28 days ago.
- `until` (string): Show usage metrics until this date. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format (`YYYY-MM-DDTHH:MM:SSZ`) and should not preceed the `since` date if it is passed.
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of days of metrics to display per page (max 28). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

> [!NOTE]
> This endpoint is in beta and is subject to change.

You can use this endpoint to see a daily breakdown of aggregated usage metrics for Copilot completions and Copilot Chat in the IDE
for all users across organizations with access to Copilot within your enterprise, with a further breakdown of suggestions, acceptances,
and number of active users by editor and language for each day. See the response schema tab for detailed metrics definitions.

The response contains metrics for up to 28 days prior. Usage metrics are processed once per day for the previous day,
and the response will only include data up until yesterday. In order for an end user to be counted towards these metrics,
they must have telemetry enabled in their IDE.

Only owners and billing managers can view Copilot usage metrics for the enterprise.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:enterprise` scopes to use this endpoint.
