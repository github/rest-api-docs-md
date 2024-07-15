# Get a delivery for a repository webhook

`GET /repos/{owner}/{repo}/hooks/{hook_id}/deliveries/{delivery_id}`

[API method documentation](https://docs.github.com/rest/repos/webhooks#get-a-delivery-for-a-repository-webhook)

## All Parameters for "Get a delivery for a repository webhook"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `hook_id` (integer, required): The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.
- `delivery_id` (integer, required)

## Operation Description

Returns a delivery for a webhook configured in a repository.
