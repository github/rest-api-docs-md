# List organization secrets

`GET /orgs/{org}/dependabot/secrets`

[API method documentation](https://docs.github.com/rest/dependabot/secrets#list-organization-secrets)

## All Parameters for "List organization secrets"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all secrets available in an organization without revealing their
encrypted values.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
