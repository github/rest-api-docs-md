# Get a license

`get /licenses/{license}`

Gets information about a specific license. For more information, see "[Licensing a repository ](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)."

## Operation Object

```json
{
    "summary": "Get a license",
    "description": "Gets information about a specific license. For more information, see \"[Licensing a repository ](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository).\"",
    "tags": [
        "licenses"
    ],
    "operationId": "licenses/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/licenses/licenses#get-a-license"
    },
    "parameters": [
        {
            "name": "license",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/license"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/license"
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
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "licenses",
        "subcategory": "licenses"
    }
}
```

## References

### `#/components/schemas/license`

```json
{
    "title": "License",
    "description": "License",
    "type": "object",
    "properties": {
        "key": {
            "type": "string",
            "example": "mit"
        },
        "name": {
            "type": "string",
            "example": "MIT License"
        },
        "spdx_id": {
            "type": "string",
            "example": "MIT",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/licenses/mit",
            "nullable": true
        },
        "node_id": {
            "type": "string",
            "example": "MDc6TGljZW5zZW1pdA=="
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "http://choosealicense.com/licenses/mit/"
        },
        "description": {
            "type": "string",
            "example": "A permissive license that is short and to the point. It lets people do anything with your code with proper attribution and without warranty."
        },
        "implementation": {
            "type": "string",
            "example": "Create a text file (typically named LICENSE or LICENSE.txt) in the root of your source code and copy the text of the license into the file. Replace [year] with the current year and [fullname] with the name (or names) of the copyright holders."
        },
        "permissions": {
            "type": "array",
            "example": [
                "commercial-use",
                "modifications",
                "distribution",
                "sublicense",
                "private-use"
            ],
            "items": {
                "type": "string"
            }
        },
        "conditions": {
            "type": "array",
            "example": [
                "include-copyright"
            ],
            "items": {
                "type": "string"
            }
        },
        "limitations": {
            "type": "array",
            "example": [
                "no-liability"
            ],
            "items": {
                "type": "string"
            }
        },
        "body": {
            "type": "string",
            "example": "\n\nThe MIT License (MIT)\n\nCopyright (c) [year] [fullname]\n\nPermission is hereby granted, free of charge, to any person obtaining a copy\nof this software and associated documentation files (the \"Software\"), to deal\nin the Software without restriction, including without limitation the rights\nto use, copy, modify, merge, publish, distribute, sublicense, and/or sell\ncopies of the Software, and to permit persons to whom the Software is\nfurnished to do so, subject to the following conditions:\n\nThe above copyright notice and this permission notice shall be included in all\ncopies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\nIMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,\nFITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE\nAUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER\nLIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,\nOUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE\nSOFTWARE.\n"
        },
        "featured": {
            "type": "boolean",
            "example": true
        }
    },
    "required": [
        "key",
        "name",
        "url",
        "spdx_id",
        "node_id",
        "html_url",
        "description",
        "implementation",
        "permissions",
        "conditions",
        "limitations",
        "body",
        "featured"
    ]
}
```

### `#/components/examples/license`

```json
{
    "value": {
        "key": "mit",
        "name": "MIT License",
        "spdx_id": "MIT",
        "url": "https://api.github.com/licenses/mit",
        "node_id": "MDc6TGljZW5zZW1pdA==",
        "html_url": "http://choosealicense.com/licenses/mit/",
        "description": "A permissive license that is short and to the point. It lets people do anything with your code with proper attribution and without warranty.",
        "implementation": "Create a text file (typically named LICENSE or LICENSE.txt) in the root of your source code and copy the text of the license into the file. Replace [year] with the current year and [fullname] with the name (or names) of the copyright holders.",
        "permissions": [
            "commercial-use",
            "modifications",
            "distribution",
            "sublicense",
            "private-use"
        ],
        "conditions": [
            "include-copyright"
        ],
        "limitations": [
            "no-liability"
        ],
        "body": "\n\nThe MIT License (MIT)\n\nCopyright (c) [year] [fullname]\n\nPermission is hereby granted, free of charge, to any person obtaining a copy\nof this software and associated documentation files (the \"Software\"), to deal\nin the Software without restriction, including without limitation the rights\nto use, copy, modify, merge, publish, distribute, sublicense, and/or sell\ncopies of the Software, and to permit persons to whom the Software is\nfurnished to do so, subject to the following conditions:\n\nThe above copyright notice and this permission notice shall be included in all\ncopies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\nIMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,\nFITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE\nAUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER\nLIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,\nOUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE\nSOFTWARE.\n",
        "featured": true
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```