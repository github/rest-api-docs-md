# Get a repository webhook

`GET /repos/{owner}/{repo}/hooks/{hook_id}`

[API method documentation](https://docs.github.com/rest/repos/webhooks#get-a-repository-webhook)

## All Parameters for "Get a repository webhook"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.

## Operation Description

Returns a webhook configured in a repository. To get only the webhook `config` properties, see "[Get a webhook configuration for a repository](/rest/webhooks/repo-config#get-a-webhook-configuration-for-a-repository)."
