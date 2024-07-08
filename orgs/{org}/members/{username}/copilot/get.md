# Get Copilot seat assignment details for a user

`GET /orgs/{org}/members/{username}/copilot`

**Note**: This endpoint is in beta and is subject to change.

Gets the GitHub Copilot seat assignment details for a member of an organization who currently has access to GitHub Copilot.

Only organization owners can view Copilot seat assignment details for members of their organization.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.

[API method documentation](https://docs.github.com/rest/copilot/copilot-user-management#get-copilot-seat-assignment-details-for-a-user)

## All Parameters for "Get Copilot seat assignment details for a user"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.