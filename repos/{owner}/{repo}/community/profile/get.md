# Get community profile metrics

`GET /repos/{owner}/{repo}/community/profile`

Returns all community profile metrics for a repository. The repository cannot be a fork.

The returned metrics include an overall health score, the repository description, the presence of documentation, the
detected code of conduct, the detected license, and the presence of ISSUE\_TEMPLATE, PULL\_REQUEST\_TEMPLATE,
README, and CONTRIBUTING files.

The `health_percentage` score is defined as a percentage of how many of
the recommended community health files are present. For more information, see
"[About community profiles for public repositories](https://docs.github.com/communities/setting-up-your-project-for-healthy-contributions/about-community-profiles-for-public-repositories)."

`content_reports_enabled` is only returned for organization-owned repositories.

[API method documentation](https://docs.github.com/rest/metrics/community#get-community-profile-metrics)

## All Parameters for "Get community profile metrics"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.