# Get a repository installation for the authenticated app

`GET /repos/{owner}/{repo}/installation`

[API method documentation](https://docs.github.com/rest/apps/apps#get-a-repository-installation-for-the-authenticated-app)

## All Parameters for "Get a repository installation for the authenticated app"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Enables an authenticated GitHub App to find the repository's installation information. The installation's account type will be either an organization or a user account, depending which account the repository belongs to.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.
