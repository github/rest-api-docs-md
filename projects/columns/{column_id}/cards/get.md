# List project cards

`GET /projects/columns/{column_id}/cards`

[API method documentation](https://docs.github.com/rest/projects/cards#list-project-cards)

## All Parameters for "List project cards"

### Path Parameters

- `column_id` (integer, required): The unique identifier of the column.
### Query Parameters

- `archived_state` (string): Filters the project cards that are returned by the card's state.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the project cards in a project.
