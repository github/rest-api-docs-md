# Get a webhook configuration for a repository

`GET /repos/{owner}/{repo}/hooks/{hook_id}/config`

Returns the webhook configuration for a repository. To get more information about the webhook, including the `active` state and `events`, use "[Get a repository webhook](/rest/webhooks/repos#get-a-repository-webhook)."

OAuth app tokens and personal access tokens (classic) need the `read:repo_hook` or `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/repos/webhooks#get-a-webhook-configuration-for-a-repository)

## All Parameters for "Get a webhook configuration for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.