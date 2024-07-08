# Get Copilot seat information and settings for an organization

`GET /orgs/{org}/copilot/billing`

**Note**: This endpoint is in beta and is subject to change.

Gets information about an organization's Copilot subscription, including seat breakdown
and feature policies. To configure these settings, go to your organization's settings on GitHub.com.
For more information, see "[Managing policies for Copilot in your organization](https://docs.github.com/copilot/managing-copilot/managing-policies-for-copilot-business-in-your-organization)".

Only organization owners can view details about the organization's Copilot Business or Copilot Enterprise subscription.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.

[API method documentation](https://docs.github.com/rest/copilot/copilot-user-management#get-copilot-seat-information-and-settings-for-an-organization)

## All Parameters for "Get Copilot seat information and settings for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.