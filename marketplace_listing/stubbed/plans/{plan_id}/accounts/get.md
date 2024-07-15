# List accounts for a plan (stubbed)

`GET /marketplace_listing/stubbed/plans/{plan_id}/accounts`

[API method documentation](https://docs.github.com/rest/apps/marketplace#list-accounts-for-a-plan-stubbed)

## All Parameters for "List accounts for a plan (stubbed)"

### Path Parameters

- `plan_id` (integer, required): The unique identifier of the plan.
### Query Parameters

- `sort` (string): The property to sort the results by.
- `direction` (string): To return the oldest accounts first, set to `asc`. Ignored without the `sort` parameter.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Returns repository and organization accounts associated with the specified plan, including free plans. For per-seat pricing, you see the list of accounts that have purchased the plan, including the number of seats purchased. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.

GitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.
