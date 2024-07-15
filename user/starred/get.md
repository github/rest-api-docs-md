# List repositories starred by the authenticated user

`GET /user/starred`

[API method documentation](https://docs.github.com/rest/activity/starring#list-repositories-starred-by-the-authenticated-user)

## All Parameters for "List repositories starred by the authenticated user"

### Query Parameters

- `sort` (string): The property to sort the results by. `created` means when the repository was starred. `updated` means when the repository was last pushed to.
- `direction` (string): The direction to sort the results by.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists repositories the authenticated user has starred.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.star+json`**: Includes a timestamp of when the star was created.
