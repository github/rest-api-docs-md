# List attestations

`get /users/{username}/attestations/{subject_digest}`

List a collection of artifact attestations with a given subject digest that are associated with repositories owned by a user.

The collection of attestations returned by this endpoint is filtered according to the authenticated user's permissions; if the authenticated user cannot read a repository, the attestations associated with that repository will not be included in the response. In addition, when using a fine-grained access token the `attestations:read` permission is required.

**Please note:** in order to offer meaningful security benefits, an attestation's signature and timestamps **must** be cryptographically verified, and the identity of the attestation signer **must** be validated. Attestations can be verified using the [GitHub CLI `attestation verify` command](https://cli.github.com/manual/gh_attestation_verify). For more information, see [our guide on how to use artifact attestations to establish a build's provenance](https://docs.github.com/actions/security-guides/using-artifact-attestations-to-establish-provenance-for-builds).

## Operation Object

```json
{
    "summary": "List attestations",
    "description": "List a collection of artifact attestations with a given subject digest that are associated with repositories owned by a user.\n\nThe collection of attestations returned by this endpoint is filtered according to the authenticated user's permissions; if the authenticated user cannot read a repository, the attestations associated with that repository will not be included in the response. In addition, when using a fine-grained access token the `attestations:read` permission is required.\n\n**Please note:** in order to offer meaningful security benefits, an attestation's signature and timestamps **must** be cryptographically verified, and the identity of the attestation signer **must** be validated. Attestations can be verified using the [GitHub CLI `attestation verify` command](https://cli.github.com/manual/gh_attestation_verify). For more information, see [our guide on how to use artifact attestations to establish a build's provenance](https://docs.github.com/actions/security-guides/using-artifact-attestations-to-establish-provenance-for-builds).",
    "tags": [
        "users"
    ],
    "operationId": "users/list-attestations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/attestations#list-attestations"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        },
        {
            "$ref": "#/components/parameters/username"
        },
        {
            "name": "subject_digest",
            "description": "Subject Digest",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            },
            "x-multi-segment": true
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "attestations": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "bundle": {
                                            "$ref": "#/components/schemas/sigstore-bundle-0"
                                        },
                                        "repository_id": {
                                            "type": "integer"
                                        }
                                    }
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "value": null
                        }
                    }
                }
            }
        },
        "201": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/empty-object"
                    },
                    "examples": {
                        "default": {
                            "value": null
                        }
                    }
                }
            }
        },
        "204": {
            "description": "Response"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "users",
        "subcategory": "attestations"
    }
}
```

## References

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/pagination-before`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/pagination-after`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/sigstore-bundle-0`

```json
{
    "title": "Sigstore Bundle v0.1",
    "description": "Sigstore Bundle v0.1",
    "type": "object",
    "properties": {
        "mediaType": {
            "type": "string"
        },
        "verificationMaterial": {
            "type": "object",
            "properties": {
                "x509CertificateChain": {
                    "type": "object",
                    "properties": {
                        "certificates": {
                            "type": "array",
                            "items": {
                                "type": "object",
                                "properties": {
                                    "rawBytes": {
                                        "type": "string"
                                    }
                                }
                            }
                        }
                    }
                },
                "tlogEntries": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "logIndex": {
                                "type": "string"
                            },
                            "logId": {
                                "type": "object",
                                "properties": {
                                    "keyId": {
                                        "type": "string"
                                    }
                                }
                            },
                            "kindVersion": {
                                "type": "object",
                                "properties": {
                                    "kind": {
                                        "type": "string"
                                    },
                                    "version": {
                                        "type": "string"
                                    }
                                }
                            },
                            "integratedTime": {
                                "type": "string"
                            },
                            "inclusionPromise": {
                                "type": "object",
                                "properties": {
                                    "signedEntryTimestamp": {
                                        "type": "string"
                                    }
                                }
                            },
                            "inclusionProof": {
                                "type": "string",
                                "nullable": true
                            },
                            "canonicalizedBody": {
                                "type": "string"
                            }
                        }
                    }
                },
                "timestampVerificationData": {
                    "type": "string",
                    "nullable": true
                }
            }
        },
        "dsseEnvelope": {
            "type": "object",
            "properties": {
                "payload": {
                    "type": "string"
                },
                "payloadType": {
                    "type": "string"
                },
                "signatures": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "sig": {
                                "type": "string"
                            },
                            "keyid": {
                                "type": "string"
                            }
                        }
                    }
                }
            }
        }
    }
}
```

### `#/components/schemas/empty-object`

```json
{
    "title": "Empty Object",
    "description": "An object without any properties.",
    "type": "object",
    "properties": {},
    "additionalProperties": false
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