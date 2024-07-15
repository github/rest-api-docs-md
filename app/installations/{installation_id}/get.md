# Get an installation for the authenticated app

`GET /app/installations/{installation_id}`

[API method documentation](https://docs.github.com/rest/apps/apps#get-an-installation-for-the-authenticated-app)

## All Parameters for "Get an installation for the authenticated app"

### Path Parameters

- `installation_id` (integer, required): The unique identifier of the installation.

## Operation Description

Enables an authenticated GitHub App to find an installation's information using the installation id.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.
