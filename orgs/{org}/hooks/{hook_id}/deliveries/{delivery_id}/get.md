# Get a webhook delivery for an organization webhook

`GET /orgs/{org}/hooks/{hook_id}/deliveries/{delivery_id}`

[API method documentation](https://docs.github.com/rest/orgs/webhooks#get-a-webhook-delivery-for-an-organization-webhook)

## All Parameters for "Get a webhook delivery for an organization webhook"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.
- `delivery_id` (integer, required)

## Operation Description

Returns a delivery for a webhook configured in an organization.

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.
