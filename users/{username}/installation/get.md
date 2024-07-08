# Get a user installation for the authenticated app

`GET /users/{username}/installation`

Enables an authenticated GitHub App to find the user’s installation information.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

[API method documentation](https://docs.github.com/rest/apps/apps#get-a-user-installation-for-the-authenticated-app)

## All Parameters for "Get a user installation for the authenticated app"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.