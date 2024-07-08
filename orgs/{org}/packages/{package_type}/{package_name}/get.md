# Get a package for an organization

`GET /orgs/{org}/packages/{package_type}/{package_name}`

Gets a specific package in an organization.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

[API method documentation](https://docs.github.com/rest/packages/packages#get-a-package-for-an-organization)

## All Parameters for "Get a package for an organization"

### Path Parameters

- `package_type` (string, required): The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.
- `package_name` (string, required): The name of the package.
- `org` (string, required): The organization name. The name is not case sensitive.