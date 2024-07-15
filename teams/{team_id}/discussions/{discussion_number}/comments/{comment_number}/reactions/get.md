# List reactions for a team discussion comment (Legacy)

`GET /teams/{team_id}/discussions/{discussion_number}/comments/{comment_number}/reactions`

[API method documentation](https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-team-discussion-comment-legacy)

## All Parameters for "List reactions for a team discussion comment (Legacy)"

### Path Parameters

- `team_id` (integer, required): The unique identifier of the team.
- `discussion_number` (integer, required): The number that identifies the discussion.
- `comment_number` (integer, required): The number that identifies the comment.
### Query Parameters

- `content` (string): Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to a team discussion comment.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [`List reactions for a team discussion comment`](https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-team-discussion-comment) endpoint.

List the reactions to a [team discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment).

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.
