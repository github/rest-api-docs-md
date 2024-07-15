# List organization webhooks

`GET /orgs/{org}/hooks`

[API method documentation](https://docs.github.com/rest/orgs/webhooks#list-organization-webhooks)

## All Parameters for "List organization webhooks"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.
