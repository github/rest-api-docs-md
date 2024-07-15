# Get a package for the authenticated user

`GET /user/packages/{package_type}/{package_name}`

[API method documentation](https://docs.github.com/rest/packages/packages#get-a-package-for-the-authenticated-user)

## All Parameters for "Get a package for the authenticated user"

### Path Parameters

- `package_type` (string, required): The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.
- `package_name` (string, required): The name of the package.

## Operation Description

Gets a specific package for a package owned by the authenticated user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."
