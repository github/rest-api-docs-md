# Get a discussion comment

`GET /orgs/{org}/teams/{team_slug}/discussions/{discussion_number}/comments/{comment_number}`

[API method documentation](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment)

## All Parameters for "Get a discussion comment"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `team_slug` (string, required): The slug of the team name.
- `discussion_number` (integer, required): The number that identifies the discussion.
- `comment_number` (integer, required): The number that identifies the comment.

## Operation Description

Get a specific comment on a team discussion.

> [!NOTE]
> You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/discussions/{discussion_number}/comments/{comment_number}`.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.
