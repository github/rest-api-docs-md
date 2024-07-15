# Get a discussion comment (Legacy)

`GET /teams/{team_id}/discussions/{discussion_number}/comments/{comment_number}`

[API method documentation](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment-legacy)

## All Parameters for "Get a discussion comment (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `discussion_number` (integer, required): The number that identifies the discussion.
- `comment_number` (integer, required): The number that identifies the comment.

## Operation Description

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment) endpoint.

Get a specific comment on a team discussion.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.
