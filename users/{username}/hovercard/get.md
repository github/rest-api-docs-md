# Get contextual information for a user

`GET /users/{username}/hovercard`

Provides hovercard information. You can find out more about someone in relation to their pull requests, issues, repositories, and organizations.

  The `subject_type` and `subject_id` parameters provide context for the person's hovercard, which returns more information than without the parameters. For example, if you wanted to find out more about `octocat` who owns the `Spoon-Knife` repository, you would use a `subject_type` value of `repository` and a `subject_id` value of `1300192` (the ID of the `Spoon-Knife` repository).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/users/users#get-contextual-information-for-a-user)

## All Parameters for "Get contextual information for a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `subject_type` (string): Identifies which additional information you'd like to receive about the person's hovercard. Can be `organization`, `repository`, `issue`, `pull_request`. **Required** when using `subject_id`.
- `subject_id` (string): Uses the ID for the `subject_type` you specified. **Required** when using `subject_type`.