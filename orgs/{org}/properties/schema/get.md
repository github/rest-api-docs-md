# Get all custom properties for an organization

`get /orgs/{org}/properties/schema`

Gets all custom properties defined for an organization.
Organization members can read these properties.

## Operation Object

```json
{
    "summary": "Get all custom properties for an organization",
    "description": "Gets all custom properties defined for an organization.\nOrganization members can read these properties.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get-all-custom-properties",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/custom-properties#get-all-custom-properties-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/org-custom-property"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-custom-properties"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "custom-properties"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/org-custom-property`

```json
{
    "title": "Organization Custom Property",
    "description": "Custom property defined on an organization",
    "type": "object",
    "properties": {
        "property_name": {
            "type": "string",
            "description": "The name of the property"
        },
        "value_type": {
            "type": "string",
            "example": "single_select",
            "enum": [
                "string",
                "single_select",
                "multi_select",
                "true_false"
            ],
            "description": "The type of the value for the property"
        },
        "required": {
            "type": "boolean",
            "description": "Whether the property is required."
        },
        "default_value": {
            "oneOf": [
                {
                    "type": "string"
                },
                {
                    "type": "array",
                    "items": {
                        "type": "string"
                    }
                }
            ],
            "nullable": true,
            "description": "Default value of the property"
        },
        "description": {
            "type": "string",
            "nullable": true,
            "description": "Short description of the property"
        },
        "allowed_values": {
            "type": "array",
            "items": {
                "type": "string",
                "maxLength": 75
            },
            "maxItems": 200,
            "nullable": true,
            "description": "An ordered list of the allowed values of the property.\nThe property can have up to 200 allowed values."
        },
        "values_editable_by": {
            "type": "string",
            "nullable": true,
            "enum": [
                "org_actors",
                "org_and_repo_actors"
            ],
            "example": "org_actors",
            "description": "Who can edit the values of the property"
        }
    },
    "required": [
        "property_name",
        "value_type"
    ]
}
```

### `#/components/examples/org-custom-properties`

```json
{
    "value": [
        {
            "property_name": "environment",
            "value_type": "single_select",
            "required": true,
            "default_value": "production",
            "description": "Prod or dev environment",
            "allowed_values": [
                "production",
                "development"
            ],
            "values_editable_by": "org_actors"
        },
        {
            "property_name": "service",
            "value_type": "string"
        },
        {
            "property_name": "team",
            "value_type": "string",
            "description": "Team owning the repository"
        }
    ]
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