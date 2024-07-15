# List public email addresses for the authenticated user

`GET /user/public_emails`

[API method documentation](https://docs.github.com/rest/users/emails#list-public-email-addresses-for-the-authenticated-user)

## All Parameters for "List public email addresses for the authenticated user"

### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists your publicly visible email address, which you can set with the
[Set primary email visibility for the authenticated user](https://docs.github.com/rest/users/emails#set-primary-email-visibility-for-the-authenticated-user)
endpoint.

OAuth app tokens and personal access tokens (classic) need the `user:email` scope to use this endpoint.
