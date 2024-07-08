# Get a subscription plan for an account (stubbed)

`GET /marketplace_listing/stubbed/accounts/{account_id}`

Shows whether the user or organization account actively subscribes to a plan listed by the authenticated GitHub App. When someone submits a plan change that won't be processed until the end of their billing cycle, you will also see the upcoming pending change.

GitHub Apps must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint. OAuth apps must use [basic authentication](https://docs.github.com/rest/authentication/authenticating-to-the-rest-api#using-basic-authentication) with their client ID and client secret to access this endpoint.

[API method documentation](https://docs.github.com/rest/apps/marketplace#get-a-subscription-plan-for-an-account-stubbed)

## All Parameters for "Get a subscription plan for an account (stubbed)"

### Path Parameters

- `account_id` (integer, required): account_id parameter