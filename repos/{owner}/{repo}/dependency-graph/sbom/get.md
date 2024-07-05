# Export a software bill of materials (SBOM) for a repository.

Exports the software bill of materials (SBOM) for a repository in SPDX JSON format.

## Operation Object

```json
{
    "summary": "Export a software bill of materials (SBOM) for a repository.",
    "description": "Exports the software bill of materials (SBOM) for a repository in SPDX JSON format.",
    "tags": [
        "dependency-graph"
    ],
    "operationId": "dependency-graph/export-sbom",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependency-graph/sboms#export-a-software-bill-of-materials-sbom-for-a-repository"
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
                        "$ref": "#/components/schemas/dependency-graph-spdx-sbom"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/dependency-graph-export-sbom-response"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "category": "dependency-graph",
        "subcategory": "sboms"
    }
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

### `#/components/schemas/dependency-graph-spdx-sbom`

```json
{
    "title": "Dependency Graph SPDX SBOM",
    "description": "A schema for the SPDX JSON format returned by the Dependency Graph.",
    "type": "object",
    "properties": {
        "sbom": {
            "type": "object",
            "properties": {
                "SPDXID": {
                    "type": "string",
                    "example": "SPDXRef-DOCUMENT",
                    "description": "The SPDX identifier for the SPDX document."
                },
                "spdxVersion": {
                    "type": "string",
                    "example": "SPDX-2.3",
                    "description": "The version of the SPDX specification that this document conforms to."
                },
                "creationInfo": {
                    "type": "object",
                    "properties": {
                        "created": {
                            "type": "string",
                            "example": "2021-11-03T00:00:00Z",
                            "description": "The date and time the SPDX document was created."
                        },
                        "creators": {
                            "type": "array",
                            "items": {
                                "type": "string",
                                "example": "GitHub"
                            },
                            "description": "The tools that were used to generate the SPDX document."
                        }
                    },
                    "required": [
                        "created",
                        "creators"
                    ]
                },
                "name": {
                    "type": "string",
                    "example": "github/github",
                    "description": "The name of the SPDX document."
                },
                "dataLicense": {
                    "type": "string",
                    "example": "CC0-1.0",
                    "description": "The license under which the SPDX document is licensed."
                },
                "documentDescribes": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "example": "github/github"
                    },
                    "description": "The name of the repository that the SPDX document describes."
                },
                "documentNamespace": {
                    "type": "string",
                    "example": "https://github.com/example/dependency_graph/sbom-123",
                    "description": "The namespace for the SPDX document."
                },
                "packages": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "SPDXID": {
                                "type": "string",
                                "example": "SPDXRef-Package",
                                "description": "A unique SPDX identifier for the package."
                            },
                            "name": {
                                "type": "string",
                                "example": "rubygems:github/github",
                                "description": "The name of the package."
                            },
                            "versionInfo": {
                                "type": "string",
                                "example": "1.0.0",
                                "description": "The version of the package. If the package does not have an exact version specified,\na version range is given."
                            },
                            "downloadLocation": {
                                "type": "string",
                                "example": "NOASSERTION",
                                "description": "The location where the package can be downloaded,\nor NOASSERTION if this has not been determined."
                            },
                            "filesAnalyzed": {
                                "type": "boolean",
                                "example": false,
                                "description": "Whether the package's file content has been subjected to\nanalysis during the creation of the SPDX document."
                            },
                            "licenseConcluded": {
                                "type": "string",
                                "example": "MIT",
                                "description": "The license of the package as determined while creating the SPDX document."
                            },
                            "licenseDeclared": {
                                "type": "string",
                                "example": "NOASSERTION",
                                "description": "The license of the package as declared by its author, or NOASSERTION if this information\nwas not available when the SPDX document was created."
                            },
                            "supplier": {
                                "type": "string",
                                "example": "NOASSERTION",
                                "description": "The distribution source of this package, or NOASSERTION if this was not determined."
                            },
                            "copyrightText": {
                                "type": "string",
                                "example": "Copyright (c) 1985 GitHub.com",
                                "description": "The copyright holders of the package, and any dates present with those notices, if available."
                            },
                            "externalRefs": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "referenceCategory": {
                                            "type": "string",
                                            "example": "PACKAGE-MANAGER",
                                            "description": "The category of reference to an external resource this reference refers to."
                                        },
                                        "referenceLocator": {
                                            "type": "string",
                                            "example": "pkg:gem/rails@6.0.1",
                                            "description": "A locator for the particular external resource this reference refers to."
                                        },
                                        "referenceType": {
                                            "type": "string",
                                            "example": "purl",
                                            "description": "The category of reference to an external resource this reference refers to."
                                        }
                                    },
                                    "required": [
                                        "referenceCategory",
                                        "referenceLocator",
                                        "referenceType"
                                    ]
                                }
                            }
                        }
                    },
                    "required": [
                        "SPDXID",
                        "name",
                        "versionInfo",
                        "downloadLocation",
                        "filesAnalyzed",
                        "supplier"
                    ]
                }
            },
            "required": [
                "SPDXID",
                "spdxVersion",
                "creationInfo",
                "name",
                "dataLicense",
                "documentDescribes",
                "documentNamespace",
                "packages"
            ]
        }
    },
    "required": [
        "sbom"
    ]
}
```

### `#/components/examples/dependency-graph-export-sbom-response`

```json
{
    "value": {
        "sbom": {
            "SPDXID": "SPDXRef-DOCUMENT",
            "spdxVersion": "SPDX-2.3",
            "creationInfo": {
                "created": "2021-09-01T00:00:00Z",
                "creators": [
                    "Tool: GitHub.com-Dependency-Graph"
                ]
            },
            "name": "github/example",
            "dataLicense": "CC0-1.0",
            "documentDescribes": [
                "github/example"
            ],
            "documentNamespace": "https://github.com/github/example/dependency_graph/sbom-abcdef123456",
            "packages": [
                {
                    "SPDXID": "SPDXRef-Package",
                    "name": "rubygems:rails",
                    "versionInfo": "1.0.0",
                    "downloadLocation": "NOASSERTION",
                    "filesAnalyzed": false,
                    "licenseConcluded": "MIT",
                    "licenseDeclared": "MIT",
                    "copyrightText": "Copyright (c) 1985 GitHub.com"
                }
            ]
        }
    }
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
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

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```