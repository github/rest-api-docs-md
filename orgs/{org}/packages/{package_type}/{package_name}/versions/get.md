# List package versions for a package owned by an organization

`GET /orgs/{org}/packages/{package_type}/{package_name}/versions`

[API method documentation](https://docs.github.com/rest/packages/packages#list-package-versions-for-a-package-owned-by-an-organization)

## All Parameters for "List package versions for a package owned by an organization"

### Path Parameters

- `package_type` (string, required): The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.
- `package_name` (string, required): The name of the package.
- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `state` (string): The state of the package, either active or deleted.

## Operation Description

Lists package versions for a package owned by an organization.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint if the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."
