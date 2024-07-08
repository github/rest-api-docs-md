# List public repositories

`GET /repositories`

Lists all public repositories in the order that they were created.

Note:
- For GitHub Enterprise Server, this endpoint will only list repositories available to all users on the enterprise.
- Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of repositories.

[API method documentation](https://docs.github.com/rest/repos/repos#list-public-repositories)

## All Parameters for "List public repositories"

### Query Parameters

- `since` (integer): A repository ID. Only return repositories with an ID greater than this ID.