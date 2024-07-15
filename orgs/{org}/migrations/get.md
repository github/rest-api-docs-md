# List organization migrations

`GET /orgs/{org}/migrations`

[API method documentation](https://docs.github.com/rest/migrations/orgs#list-organization-migrations)

## All Parameters for "List organization migrations"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `exclude` (array): Exclude attributes from the API response to improve performance

## Operation Description

Lists the most recent migrations, including both exports (which can be started through the REST API) and imports (which cannot be started using the REST API).

A list of `repositories` is only returned for export migrations.
