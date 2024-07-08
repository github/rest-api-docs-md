# List public events

`GET /events`

We delay the public events feed by five minutes, which means the most recent event returned by the public events API actually occurred at least five minutes ago.

[API method documentation](https://docs.github.com/rest/activity/events#list-public-events)

## All Parameters for "List public events"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."