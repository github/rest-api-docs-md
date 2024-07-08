# Get the customization template for an OIDC subject claim for a repository

`GET /repos/{owner}/{repo}/actions/oidc/customization/sub`

Gets the customization template for an OpenID Connect (OIDC) subject claim.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/oidc#get-the-customization-template-for-an-oidc-subject-claim-for-a-repository)

## All Parameters for "Get the customization template for an OIDC subject claim for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.