# List gists for the authenticated user

`GET /gists`

Lists the authenticated user's gists or if called anonymously, this endpoint returns all public gists:

[API method documentation](https://docs.github.com/rest/gists/gists#list-gists-for-the-authenticated-user)

## All Parameters for "List gists for the authenticated user"

### Query Parameters

- `since` (string): Only show results that were last updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."