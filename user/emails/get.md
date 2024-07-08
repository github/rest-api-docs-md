# List email addresses for the authenticated user

`GET /user/emails`

Lists all of your email addresses, and specifies which one is visible
to the public.

OAuth app tokens and personal access tokens (classic) need the `user:email` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/users/emails#list-email-addresses-for-the-authenticated-user)

## All Parameters for "List email addresses for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."