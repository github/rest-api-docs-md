# List events for the authenticated user

`GET /users/{username}/events`

[API method documentation](https://docs.github.com/rest/activity/events#list-events-for-the-authenticated-user)

## All Parameters for "List events for the authenticated user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

If you are authenticated as the given user, you will see your private events. Otherwise, you'll only see public events.
