# List notifications for the authenticated user

`GET /notifications`

[API method documentation](https://docs.github.com/rest/activity/notifications#list-notifications-for-the-authenticated-user)

## All Parameters for "List notifications for the authenticated user"

### Query Parameters

- `all` (boolean): If `true`, show notifications marked as read.
- `participating` (boolean): If `true`, only shows notifications in which the user is directly participating or mentioned.
- `since` (string): Only show results that were last updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.
- `before` (string): Only show notifications updated before the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 50). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

List all notifications for the current user, sorted by most recently updated.
