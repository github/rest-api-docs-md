# Get a webhook configuration for an organization

`GET /orgs/{org}/hooks/{hook_id}/config`

[API method documentation](https://docs.github.com/rest/orgs/webhooks#get-a-webhook-configuration-for-an-organization)

## All Parameters for "Get a webhook configuration for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.

## Operation Description

Returns the webhook configuration for an organization. To get more information about the webhook, including the `active` state and `events`, use "[Get an organization webhook ](/rest/orgs/webhooks#get-an-organization-webhook)."

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.
