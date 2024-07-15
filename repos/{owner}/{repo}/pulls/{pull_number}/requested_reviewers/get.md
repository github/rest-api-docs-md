# Get all requested reviewers for a pull request

`GET /repos/{owner}/{repo}/pulls/{pull_number}/requested_reviewers`

[API method documentation](https://docs.github.com/rest/pulls/review-requests#get-all-requested-reviewers-for-a-pull-request)

## All Parameters for "Get all requested reviewers for a pull request"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `pull_number` (integer, required): The number that identifies the pull request.

## Operation Description

Gets the users or teams whose review is requested for a pull request. Once a requested reviewer submits a review, they are no longer considered a requested reviewer. Their review will instead be returned by the [List reviews for a pull request](https://docs.github.com/rest/pulls/reviews#list-reviews-for-a-pull-request) operation.
