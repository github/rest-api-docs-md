# Get the status of a GitHub Pages deployment

`GET /repos/{owner}/{repo}/pages/deployments/{pages_deployment_id}`

[API method documentation](https://docs.github.com/rest/pages/pages#get-the-status-of-a-github-pages-deployment)

## All Parameters for "Get the status of a GitHub Pages deployment"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `pages_deployment_id` (, required): The ID of the Pages deployment. You can also give the commit SHA of the deployment.

## Operation Description

Gets the current status of a GitHub Pages deployment.

The authenticated user must have read permission for the GitHub Pages site.
