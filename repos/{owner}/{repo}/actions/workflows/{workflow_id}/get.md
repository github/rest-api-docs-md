# Get a workflow

`GET /repos/{owner}/{repo}/actions/workflows/{workflow_id}`

Gets a specific workflow. You can replace `workflow_id` with the workflow
file name. For example, you could use `main.yaml`.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/actions/workflows#get-a-workflow)

## All Parameters for "Get a workflow"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `workflow_id` (, required): The ID of the workflow. You can also pass the workflow file name as a string.