# Get an import status

View the progress of an import.

**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).

**Import status**

This section includes details about the possible values of the `status` field of the Import Progress response.

An import that does not have errors will progress through these steps:

*   `detecting` - the "detection" step of the import is in progress because the request did not include a `vcs` parameter. The import is identifying the type of source control present at the URL.
*   `importing` - the "raw" step of the import is in progress. This is where commit data is fetched from the original repository. The import progress response will include `commit_count` (the total number of raw commits that will be imported) and `percent` (0 - 100, the current progress through the import).
*   `mapping` - the "rewrite" step of the import is in progress. This is where SVN branches are converted to Git branches, and where author updates are applied. The import progress response does not include progress information.
*   `pushing` - the "push" step of the import is in progress. This is where the importer updates the repository on GitHub. The import progress response will include `push_percent`, which is the percent value reported by `git push` when it is "Writing objects".
*   `complete` - the import is complete, and the repository is ready on GitHub.

If there are problems, you will see one of these in the `status` field:

*   `auth_failed` - the import requires authentication in order to connect to the original repository. To update authentication for the import, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.
*   `error` - the import encountered an error. The import progress response will include the `failed_step` and an error message. Contact [GitHub Support](https://support.github.com/contact?tags=dotcom-rest-api) for more information.
*   `detection_needs_auth` - the importer requires authentication for the originating repository to continue detection. To update authentication for the import, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.
*   `detection_found_nothing` - the importer didn't recognize any source control at the URL. To resolve, [Cancel the import](https://docs.github.com/rest/migrations/source-imports#cancel-an-import) and [retry](https://docs.github.com/rest/migrations/source-imports#start-an-import) with the correct URL.
*   `detection_found_multiple` - the importer found several projects or repositories at the provided URL. When this is the case, the Import Progress response will also include a `project_choices` field with the possible project choices as values. To update project choice, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.

**The project_choices field**

When multiple projects are found at the provided URL, the response hash will include a `project_choices` field, the value of which is an array of hashes each representing a project choice. The exact key/value pairs of the project hashes will differ depending on the version control type.

**Git LFS related fields**

This section includes details about Git LFS related fields that may be present in the Import Progress response.

*   `use_lfs` - describes whether the import has been opted in or out of using Git LFS. The value can be `opt_in`, `opt_out`, or `undecided` if no action has been taken.
*   `has_large_files` - the boolean value describing whether files larger than 100MB were found during the `importing` step.
*   `large_files_size` - the total size in gigabytes of files larger than 100MB found in the originating repository.
*   `large_files_count` - the total number of files larger than 100MB found in the originating repository. To see a list of these files, make a "Get Large Files" request.

## Operation Object

```json
{
    "summary": "Get an import status",
    "description": "View the progress of an import.\n\n**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).\n\n**Import status**\n\nThis section includes details about the possible values of the `status` field of the Import Progress response.\n\nAn import that does not have errors will progress through these steps:\n\n*   `detecting` - the \"detection\" step of the import is in progress because the request did not include a `vcs` parameter. The import is identifying the type of source control present at the URL.\n*   `importing` - the \"raw\" step of the import is in progress. This is where commit data is fetched from the original repository. The import progress response will include `commit_count` (the total number of raw commits that will be imported) and `percent` (0 - 100, the current progress through the import).\n*   `mapping` - the \"rewrite\" step of the import is in progress. This is where SVN branches are converted to Git branches, and where author updates are applied. The import progress response does not include progress information.\n*   `pushing` - the \"push\" step of the import is in progress. This is where the importer updates the repository on GitHub. The import progress response will include `push_percent`, which is the percent value reported by `git push` when it is \"Writing objects\".\n*   `complete` - the import is complete, and the repository is ready on GitHub.\n\nIf there are problems, you will see one of these in the `status` field:\n\n*   `auth_failed` - the import requires authentication in order to connect to the original repository. To update authentication for the import, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.\n*   `error` - the import encountered an error. The import progress response will include the `failed_step` and an error message. Contact [GitHub Support](https://support.github.com/contact?tags=dotcom-rest-api) for more information.\n*   `detection_needs_auth` - the importer requires authentication for the originating repository to continue detection. To update authentication for the import, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.\n*   `detection_found_nothing` - the importer didn't recognize any source control at the URL. To resolve, [Cancel the import](https://docs.github.com/rest/migrations/source-imports#cancel-an-import) and [retry](https://docs.github.com/rest/migrations/source-imports#start-an-import) with the correct URL.\n*   `detection_found_multiple` - the importer found several projects or repositories at the provided URL. When this is the case, the Import Progress response will also include a `project_choices` field with the possible project choices as values. To update project choice, please see the [Update an import](https://docs.github.com/rest/migrations/source-imports#update-an-import) section.\n\n**The project_choices field**\n\nWhen multiple projects are found at the provided URL, the response hash will include a `project_choices` field, the value of which is an array of hashes each representing a project choice. The exact key/value pairs of the project hashes will differ depending on the version control type.\n\n**Git LFS related fields**\n\nThis section includes details about Git LFS related fields that may be present in the Import Progress response.\n\n*   `use_lfs` - describes whether the import has been opted in or out of using Git LFS. The value can be `opt_in`, `opt_out`, or `undecided` if no action has been taken.\n*   `has_large_files` - the boolean value describing whether files larger than 100MB were found during the `importing` step.\n*   `large_files_size` - the total size in gigabytes of files larger than 100MB found in the originating repository.\n*   `large_files_count` - the total number of files larger than 100MB found in the originating repository. To see a list of these files, make a \"Get Large Files\" request.",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/get-import-status",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/source-imports#get-an-import-status"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/import"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/import"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "503": {
            "$ref": "#/components/responses/porter_maintenance"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "migrations",
        "subcategory": "source-imports",
        "deprecationDate": "2023-10-12",
        "removalDate": "2024-04-12"
    },
    "deprecated": true
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/import`

```json
{
    "title": "Import",
    "description": "A repository import from an external source.",
    "type": "object",
    "properties": {
        "vcs": {
            "type": "string",
            "nullable": true
        },
        "use_lfs": {
            "type": "boolean"
        },
        "vcs_url": {
            "description": "The URL of the originating repository.",
            "type": "string"
        },
        "svc_root": {
            "type": "string"
        },
        "tfvc_project": {
            "type": "string"
        },
        "status": {
            "type": "string",
            "enum": [
                "auth",
                "error",
                "none",
                "detecting",
                "choose",
                "auth_failed",
                "importing",
                "mapping",
                "waiting_to_push",
                "pushing",
                "complete",
                "setup",
                "unknown",
                "detection_found_multiple",
                "detection_found_nothing",
                "detection_needs_auth"
            ]
        },
        "status_text": {
            "type": "string",
            "nullable": true
        },
        "failed_step": {
            "type": "string",
            "nullable": true
        },
        "error_message": {
            "type": "string",
            "nullable": true
        },
        "import_percent": {
            "type": "integer",
            "nullable": true
        },
        "commit_count": {
            "type": "integer",
            "nullable": true
        },
        "push_percent": {
            "type": "integer",
            "nullable": true
        },
        "has_large_files": {
            "type": "boolean"
        },
        "large_files_size": {
            "type": "integer"
        },
        "large_files_count": {
            "type": "integer"
        },
        "project_choices": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "vcs": {
                        "type": "string"
                    },
                    "tfvc_project": {
                        "type": "string"
                    },
                    "human_name": {
                        "type": "string"
                    }
                }
            }
        },
        "message": {
            "type": "string"
        },
        "authors_count": {
            "type": "integer",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "authors_url": {
            "type": "string",
            "format": "uri"
        },
        "repository_url": {
            "type": "string",
            "format": "uri"
        },
        "svn_root": {
            "type": "string"
        }
    },
    "required": [
        "vcs",
        "vcs_url",
        "status",
        "url",
        "repository_url",
        "html_url",
        "authors_url"
    ]
}
```

### `#/components/examples/import`

```json
{
    "value": {
        "vcs": "subversion",
        "use_lfs": true,
        "vcs_url": "http://svn.mycompany.com/svn/myproject",
        "status": "complete",
        "status_text": "Done",
        "has_large_files": true,
        "large_files_size": 132331036,
        "large_files_count": 1,
        "authors_count": 4,
        "url": "https://api.github.com/repos/octocat/socm/import",
        "html_url": "https://import.github.com/octocat/socm/import",
        "authors_url": "https://api.github.com/repos/octocat/socm/import/authors",
        "repository_url": "https://api.github.com/repos/octocat/socm"
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/porter_maintenance`

```json
{
    "description": "Unavailable due to service under maintenance.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```