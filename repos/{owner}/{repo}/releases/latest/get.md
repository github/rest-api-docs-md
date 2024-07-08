# Get the latest release

`GET /repos/{owner}/{repo}/releases/latest`

View the latest published full release for the repository.

The latest release is the most recent non-prerelease, non-draft release, sorted by the `created_at` attribute. The `created_at` attribute is the date of the commit used for the release, and not the date when the release was drafted or published.

[API method documentation](https://docs.github.com/rest/releases/releases#get-the-latest-release)

## All Parameters for "Get the latest release"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.