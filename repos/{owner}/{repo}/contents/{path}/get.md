# Get repository content

Gets the contents of a file or directory in a repository. Specify the file path or directory with the `path` parameter. If you omit the `path` parameter, you will receive the contents of the repository's root directory.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw file contents for files and symlinks.
- **`application/vnd.github.html+json`**: Returns the file contents in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).
- **`application/vnd.github.object+json`**: Returns the contents in a consistent object format regardless of the content type. For example, instead of an array of objects for a directory, the response will be an object with an `entries` attribute containing the array of objects.

If the content is a directory, the response will be an array of objects, one object for each item in the directory. When listing the contents of a directory, submodules have their "type" specified as "file". Logically, the value _should_ be "submodule". This behavior exists [for backwards compatibility purposes](https://git.io/v1YCW). In the next major version of the API, the type will be returned as "submodule".

If the content is a symlink and the symlink's target is a normal file in the repository, then the API responds with the content of the file. Otherwise, the API responds with an object describing the symlink itself.

If the content is a submodule, the `submodule_git_url` field identifies the location of the submodule repository, and the `sha` identifies a specific commit within the submodule repository. Git uses the given URL when cloning the submodule repository, and checks out the submodule at that specific commit. If the submodule repository is not hosted on github.com, the Git URLs (`git_url` and `_links["git"]`) and the github.com URLs (`html_url` and `_links["html"]`) will have null values.

**Notes**:

- To get a repository's contents recursively, you can [recursively get the tree](https://docs.github.com/rest/git/trees#get-a-tree).
- This API has an upper limit of 1,000 files for a directory. If you need to retrieve
more files, use the [Git Trees API](https://docs.github.com/rest/git/trees#get-a-tree).
- Download URLs expire and are meant to be used just once. To ensure the download URL does not expire, please use the contents API to obtain a fresh download URL for each download.
- If the requested file's size is:
  - 1 MB or smaller: All features of this endpoint are supported.
  - Between 1-100 MB: Only the `raw` or `object` custom media types are supported. Both will work as normal, except that when using the `object` media type, the `content` field will be an empty
string and the `encoding` field will be `"none"`. To get the contents of these larger files, use the `raw` media type.
  - Greater than 100 MB: This endpoint is not supported.

## Operation Object

```json
{
    "summary": "Get repository content",
    "description": "Gets the contents of a file or directory in a repository. Specify the file path or directory with the `path` parameter. If you omit the `path` parameter, you will receive the contents of the repository's root directory.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw file contents for files and symlinks.\n- **`application/vnd.github.html+json`**: Returns the file contents in HTML. Markup languages are rendered to HTML using GitHub's open-source [Markup library](https://github.com/github/markup).\n- **`application/vnd.github.object+json`**: Returns the contents in a consistent object format regardless of the content type. For example, instead of an array of objects for a directory, the response will be an object with an `entries` attribute containing the array of objects.\n\nIf the content is a directory, the response will be an array of objects, one object for each item in the directory. When listing the contents of a directory, submodules have their \"type\" specified as \"file\". Logically, the value _should_ be \"submodule\". This behavior exists [for backwards compatibility purposes](https://git.io/v1YCW). In the next major version of the API, the type will be returned as \"submodule\".\n\nIf the content is a symlink and the symlink's target is a normal file in the repository, then the API responds with the content of the file. Otherwise, the API responds with an object describing the symlink itself.\n\nIf the content is a submodule, the `submodule_git_url` field identifies the location of the submodule repository, and the `sha` identifies a specific commit within the submodule repository. Git uses the given URL when cloning the submodule repository, and checks out the submodule at that specific commit. If the submodule repository is not hosted on github.com, the Git URLs (`git_url` and `_links[\"git\"]`) and the github.com URLs (`html_url` and `_links[\"html\"]`) will have null values.\n\n**Notes**:\n\n- To get a repository's contents recursively, you can [recursively get the tree](https://docs.github.com/rest/git/trees#get-a-tree).\n- This API has an upper limit of 1,000 files for a directory. If you need to retrieve\nmore files, use the [Git Trees API](https://docs.github.com/rest/git/trees#get-a-tree).\n- Download URLs expire and are meant to be used just once. To ensure the download URL does not expire, please use the contents API to obtain a fresh download URL for each download.\n- If the requested file's size is:\n  - 1 MB or smaller: All features of this endpoint are supported.\n  - Between 1-100 MB: Only the `raw` or `object` custom media types are supported. Both will work as normal, except that when using the `object` media type, the `content` field will be an empty\nstring and the `encoding` field will be `\"none\"`. To get the contents of these larger files, use the `raw` media type.\n  - Greater than 100 MB: This endpoint is not supported.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-content",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/contents#get-repository-content"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "path",
            "description": "path parameter",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            },
            "x-multi-segment": true
        },
        {
            "name": "ref",
            "description": "The name of the commit/branch/tag. Default: the repository\u2019s default branch.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/vnd.github.object": {
                    "schema": {
                        "$ref": "#/components/schemas/content-tree"
                    },
                    "examples": {
                        "response-if-content-is-a-file": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-file"
                        },
                        "response-if-content-is-a-directory": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-directory-object"
                        }
                    }
                },
                "application/json": {
                    "schema": {
                        "oneOf": [
                            {
                                "$ref": "#/components/schemas/content-directory"
                            },
                            {
                                "$ref": "#/components/schemas/content-file"
                            },
                            {
                                "$ref": "#/components/schemas/content-symlink"
                            },
                            {
                                "$ref": "#/components/schemas/content-submodule"
                            }
                        ]
                    },
                    "examples": {
                        "response-if-content-is-a-file": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-file"
                        },
                        "response-if-content-is-a-directory": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-directory"
                        },
                        "response-if-content-is-a-symlink": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-symlink"
                        },
                        "response-if-content-is-a-submodule": {
                            "$ref": "#/components/examples/content-file-response-if-content-is-a-submodule"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "302": {
            "$ref": "#/components/responses/found"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "contents"
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

### `#/components/schemas/content-tree`

```json
{
    "title": "Content Tree",
    "description": "Content Tree",
    "type": "object",
    "properties": {
        "type": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        },
        "name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "download_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "entries": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "type": {
                        "type": "string"
                    },
                    "size": {
                        "type": "integer"
                    },
                    "name": {
                        "type": "string"
                    },
                    "path": {
                        "type": "string"
                    },
                    "content": {
                        "type": "string"
                    },
                    "sha": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string",
                        "format": "uri"
                    },
                    "git_url": {
                        "type": "string",
                        "format": "uri",
                        "nullable": true
                    },
                    "html_url": {
                        "type": "string",
                        "format": "uri",
                        "nullable": true
                    },
                    "download_url": {
                        "type": "string",
                        "format": "uri",
                        "nullable": true
                    },
                    "_links": {
                        "type": "object",
                        "properties": {
                            "git": {
                                "type": "string",
                                "format": "uri",
                                "nullable": true
                            },
                            "html": {
                                "type": "string",
                                "format": "uri",
                                "nullable": true
                            },
                            "self": {
                                "type": "string",
                                "format": "uri"
                            }
                        },
                        "required": [
                            "git",
                            "html",
                            "self"
                        ]
                    }
                },
                "required": [
                    "_links",
                    "git_url",
                    "html_url",
                    "download_url",
                    "name",
                    "path",
                    "sha",
                    "size",
                    "type",
                    "url"
                ]
            }
        },
        "_links": {
            "type": "object",
            "properties": {
                "git": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "git",
                "html",
                "self"
            ]
        }
    },
    "required": [
        "_links",
        "git_url",
        "html_url",
        "download_url",
        "name",
        "path",
        "sha",
        "size",
        "type",
        "url",
        "content",
        "encoding"
    ]
}
```

### `#/components/examples/content-file-response-if-content-is-a-file`

```json
{
    "summary": "Response if content is a file",
    "value": {
        "type": "file",
        "encoding": "base64",
        "size": 5362,
        "name": "README.md",
        "path": "README.md",
        "content": "IyBZb2dhIEJvmsgaW4gcHJvZ3Jlc3MhIEZlZWwgdAoKOndhcm5pbmc6IFdvc\\nZnJlZSBmUgdG8gY0byBjaGVjayBvdXQgdGhlIGFwcCwgYnV0IGJlIHN1c29t\\nZSBiYWNrIG9uY2UgaXQgaXMgY29tcGxldGUuCgpBIHdlYiBhcHAgdGhhdCBs\\nZWFkcyB5b3UgdGhyb3VnaCBhIHlvZ2Egc2Vzc2lvbi4KCltXb3Jrb3V0IG5v\\ndyFdKGh0dHBzOi8vc2tlZHdhcmRzODguZ2l0aHViLmlvL3lvZ2EvKQoKPGlt\\nZyBzcmM9InNyYy9pbWFnZXMvbWFza2FibGVfaWNvbl81MTIucG5nIiBhbHQ9\\nImJvdCBsaWZ0aW5nIHdlaWdodHMiIHdpZHRoPSIxMDAiLz4KCkRvIHlvdSBo\\nYXZlIGZlZWRiYWNrIG9yIGlkZWFzIGZvciBpbXByb3ZlbWVudD8gW09wZW4g\\nYW4gaXNzdWVdKGh0dHBzOi8vZ2l0aHViLmNvbS9za2Vkd2FyZHM4OC95b2dh\\nL2lzc3Vlcy9uZXcpLgoKV2FudCBtb3JlIGdhbWVzPyBWaXNpdCBbQ25TIEdh\\nbWVzXShodHRwczovL3NrZWR3YXJkczg4LmdpdGh1Yi5pby9wb3J0Zm9saW8v\\nKS4KCiMjIERldmVsb3BtZW50CgpUbyBhZGQgYSBuZXcgcG9zZSwgYWRkIGFu\\nIGVudHJ5IHRvIHRoZSByZWxldmFudCBmaWxlIGluIGBzcmMvYXNhbmFzYC4K\\nClRvIGJ1aWxkLCBydW4gYG5wbSBydW4gYnVpbGRgLgoKVG8gcnVuIGxvY2Fs\\nbHkgd2l0aCBsaXZlIHJlbG9hZGluZyBhbmQgbm8gc2VydmljZSB3b3JrZXIs\\nIHJ1biBgbnBtIHJ1biBkZXZgLiAoSWYgYSBzZXJ2aWNlIHdvcmtlciB3YXMg\\ncHJldmlvdXNseSByZWdpc3RlcmVkLCB5b3UgY2FuIHVucmVnaXN0ZXIgaXQg\\naW4gY2hyb21lIGRldmVsb3BlciB0b29sczogYEFwcGxpY2F0aW9uYCA+IGBT\\nZXJ2aWNlIHdvcmtlcnNgID4gYFVucmVnaXN0ZXJgLikKClRvIHJ1biBsb2Nh\\nbGx5IGFuZCByZWdpc3RlciB0aGUgc2VydmljZSB3b3JrZXIsIHJ1biBgbnBt\\nIHN0YXJ0YC4KClRvIGRlcGxveSwgcHVzaCB0byBgbWFpbmAgb3IgbWFudWFs\\nbHkgdHJpZ2dlciB0aGUgYC5naXRodWIvd29ya2Zsb3dzL2RlcGxveS55bWxg\\nIHdvcmtmbG93Lgo=\\n",
        "sha": "3d21ec53a331a6f037a91c368710b99387d012c1",
        "url": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
        "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
        "html_url": "https://github.com/octokit/octokit.rb/blob/master/README.md",
        "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md",
        "_links": {
            "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
            "self": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
            "html": "https://github.com/octokit/octokit.rb/blob/master/README.md"
        }
    }
}
```

### `#/components/examples/content-file-response-if-content-is-a-directory-object`

```json
{
    "summary": "Response if content is a directory and the application/vnd.github.v3.object media type is requested",
    "value": {
        "type": "dir",
        "size": 0,
        "name": "src",
        "path": "src",
        "sha": "2962be1c94eaae9794b3080790ec9d74b2fa8358",
        "url": "https://api.github.com/repos/octocat/octorepo/contents/src?ref=main",
        "git_url": "https://api.github.com/repos/octocat/octorepo/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
        "html_url": "https://github.com/octocat/octorepo/blob/main/src",
        "download_url": "https://raw.githubusercontent.com/octocat/octorepo/main/src",
        "_links": {
            "self": "https://api.github.com/repos/octocat/octorepo/contents/src",
            "git": "https://api.github.com/repos/octocat/octorepo/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
            "html": "https://github.com/octocat/octorepo/blob/main/src"
        },
        "entries": [
            {
                "type": "file",
                "size": 625,
                "name": "app.js",
                "path": "src/app.js",
                "sha": "fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
                "url": "https://api.github.com/repos/octocat/octorepo/contents/src/app.js",
                "git_url": "https://api.github.com/repos/octocat/octorepo/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
                "html_url": "https://github.com/octocat/octorepo/blob/main/src/app.js",
                "download_url": "https://raw.githubusercontent.com/octocat/octorepo/main/src/app.js",
                "_links": {
                    "self": "https://api.github.com/repos/octocat/octorepo/contents/src/app.js",
                    "git": "https://api.github.com/repos/octocat/octorepo/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
                    "html": "https://github.com/octocat/octorepo/blob/main/src/app.js"
                }
            },
            {
                "type": "dir",
                "size": 0,
                "name": "images",
                "path": "src/images",
                "sha": "a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
                "url": "https://api.github.com/repos/octocat/octorepo/contents/src/images",
                "git_url": "https://api.github.com/repos/octocat/octorepo/git/trees/a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
                "html_url": "https://github.com/octocat/octorepo/tree/main/src/images",
                "download_url": null,
                "_links": {
                    "self": "https://api.github.com/repos/octocat/octorepo/contents/src/images",
                    "git": "https://api.github.com/repos/octocat/octorepo/git/trees/a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
                    "html": "https://github.com/octocat/octorepo/tree/main/src/images"
                }
            }
        ]
    }
}
```

### `#/components/schemas/content-directory`

```json
{
    "title": "Content Directory",
    "description": "A list of directory items",
    "type": "array",
    "items": {
        "type": "object",
        "properties": {
            "type": {
                "type": "string",
                "enum": [
                    "dir",
                    "file",
                    "submodule",
                    "symlink"
                ]
            },
            "size": {
                "type": "integer"
            },
            "name": {
                "type": "string"
            },
            "path": {
                "type": "string"
            },
            "content": {
                "type": "string"
            },
            "sha": {
                "type": "string"
            },
            "url": {
                "type": "string",
                "format": "uri"
            },
            "git_url": {
                "type": "string",
                "format": "uri",
                "nullable": true
            },
            "html_url": {
                "type": "string",
                "format": "uri",
                "nullable": true
            },
            "download_url": {
                "type": "string",
                "format": "uri",
                "nullable": true
            },
            "_links": {
                "type": "object",
                "properties": {
                    "git": {
                        "type": "string",
                        "format": "uri",
                        "nullable": true
                    },
                    "html": {
                        "type": "string",
                        "format": "uri",
                        "nullable": true
                    },
                    "self": {
                        "type": "string",
                        "format": "uri"
                    }
                },
                "required": [
                    "git",
                    "html",
                    "self"
                ]
            }
        },
        "required": [
            "_links",
            "git_url",
            "html_url",
            "download_url",
            "name",
            "path",
            "sha",
            "size",
            "type",
            "url"
        ]
    }
}
```

### `#/components/schemas/content-file`

```json
{
    "title": "Content File",
    "description": "Content File",
    "type": "object",
    "properties": {
        "type": {
            "type": "string",
            "enum": [
                "file"
            ]
        },
        "encoding": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        },
        "name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "content": {
            "type": "string"
        },
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "download_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "_links": {
            "type": "object",
            "properties": {
                "git": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "git",
                "html",
                "self"
            ]
        },
        "target": {
            "type": "string",
            "example": "\"actual/actual.md\""
        },
        "submodule_git_url": {
            "type": "string",
            "example": "\"git://example.com/defunkt/dotjs.git\""
        }
    },
    "required": [
        "_links",
        "git_url",
        "html_url",
        "download_url",
        "name",
        "path",
        "sha",
        "size",
        "type",
        "url",
        "content",
        "encoding"
    ]
}
```

### `#/components/schemas/content-symlink`

```json
{
    "title": "Symlink Content",
    "description": "An object describing a symlink",
    "type": "object",
    "properties": {
        "type": {
            "type": "string",
            "enum": [
                "symlink"
            ]
        },
        "target": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        },
        "name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "download_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "_links": {
            "type": "object",
            "properties": {
                "git": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "git",
                "html",
                "self"
            ]
        }
    },
    "required": [
        "_links",
        "git_url",
        "html_url",
        "download_url",
        "name",
        "path",
        "sha",
        "size",
        "type",
        "url",
        "target"
    ]
}
```

### `#/components/schemas/content-submodule`

```json
{
    "title": "Submodule Content",
    "description": "An object describing a submodule",
    "type": "object",
    "properties": {
        "type": {
            "type": "string",
            "enum": [
                "submodule"
            ]
        },
        "submodule_git_url": {
            "type": "string",
            "format": "uri"
        },
        "size": {
            "type": "integer"
        },
        "name": {
            "type": "string"
        },
        "path": {
            "type": "string"
        },
        "sha": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "git_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "download_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "_links": {
            "type": "object",
            "properties": {
                "git": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "self": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "git",
                "html",
                "self"
            ]
        }
    },
    "required": [
        "_links",
        "git_url",
        "html_url",
        "download_url",
        "name",
        "path",
        "sha",
        "size",
        "type",
        "url",
        "submodule_git_url"
    ]
}
```

### `#/components/examples/content-file-response-if-content-is-a-file`

```json
{
    "summary": "Response if content is a file",
    "value": {
        "type": "file",
        "encoding": "base64",
        "size": 5362,
        "name": "README.md",
        "path": "README.md",
        "content": "IyBZb2dhIEJvmsgaW4gcHJvZ3Jlc3MhIEZlZWwgdAoKOndhcm5pbmc6IFdvc\\nZnJlZSBmUgdG8gY0byBjaGVjayBvdXQgdGhlIGFwcCwgYnV0IGJlIHN1c29t\\nZSBiYWNrIG9uY2UgaXQgaXMgY29tcGxldGUuCgpBIHdlYiBhcHAgdGhhdCBs\\nZWFkcyB5b3UgdGhyb3VnaCBhIHlvZ2Egc2Vzc2lvbi4KCltXb3Jrb3V0IG5v\\ndyFdKGh0dHBzOi8vc2tlZHdhcmRzODguZ2l0aHViLmlvL3lvZ2EvKQoKPGlt\\nZyBzcmM9InNyYy9pbWFnZXMvbWFza2FibGVfaWNvbl81MTIucG5nIiBhbHQ9\\nImJvdCBsaWZ0aW5nIHdlaWdodHMiIHdpZHRoPSIxMDAiLz4KCkRvIHlvdSBo\\nYXZlIGZlZWRiYWNrIG9yIGlkZWFzIGZvciBpbXByb3ZlbWVudD8gW09wZW4g\\nYW4gaXNzdWVdKGh0dHBzOi8vZ2l0aHViLmNvbS9za2Vkd2FyZHM4OC95b2dh\\nL2lzc3Vlcy9uZXcpLgoKV2FudCBtb3JlIGdhbWVzPyBWaXNpdCBbQ25TIEdh\\nbWVzXShodHRwczovL3NrZWR3YXJkczg4LmdpdGh1Yi5pby9wb3J0Zm9saW8v\\nKS4KCiMjIERldmVsb3BtZW50CgpUbyBhZGQgYSBuZXcgcG9zZSwgYWRkIGFu\\nIGVudHJ5IHRvIHRoZSByZWxldmFudCBmaWxlIGluIGBzcmMvYXNhbmFzYC4K\\nClRvIGJ1aWxkLCBydW4gYG5wbSBydW4gYnVpbGRgLgoKVG8gcnVuIGxvY2Fs\\nbHkgd2l0aCBsaXZlIHJlbG9hZGluZyBhbmQgbm8gc2VydmljZSB3b3JrZXIs\\nIHJ1biBgbnBtIHJ1biBkZXZgLiAoSWYgYSBzZXJ2aWNlIHdvcmtlciB3YXMg\\ncHJldmlvdXNseSByZWdpc3RlcmVkLCB5b3UgY2FuIHVucmVnaXN0ZXIgaXQg\\naW4gY2hyb21lIGRldmVsb3BlciB0b29sczogYEFwcGxpY2F0aW9uYCA+IGBT\\nZXJ2aWNlIHdvcmtlcnNgID4gYFVucmVnaXN0ZXJgLikKClRvIHJ1biBsb2Nh\\nbGx5IGFuZCByZWdpc3RlciB0aGUgc2VydmljZSB3b3JrZXIsIHJ1biBgbnBt\\nIHN0YXJ0YC4KClRvIGRlcGxveSwgcHVzaCB0byBgbWFpbmAgb3IgbWFudWFs\\nbHkgdHJpZ2dlciB0aGUgYC5naXRodWIvd29ya2Zsb3dzL2RlcGxveS55bWxg\\nIHdvcmtmbG93Lgo=\\n",
        "sha": "3d21ec53a331a6f037a91c368710b99387d012c1",
        "url": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
        "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
        "html_url": "https://github.com/octokit/octokit.rb/blob/master/README.md",
        "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md",
        "_links": {
            "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
            "self": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
            "html": "https://github.com/octokit/octokit.rb/blob/master/README.md"
        }
    }
}
```

### `#/components/examples/content-file-response-if-content-is-a-directory`

```json
{
    "summary": "Response if content is a directory and the application/json media type is requested",
    "value": [
        {
            "type": "file",
            "size": 625,
            "name": "octokit.rb",
            "path": "lib/octokit.rb",
            "sha": "fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
            "url": "https://api.github.com/repos/octokit/octokit.rb/contents/lib/octokit.rb",
            "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
            "html_url": "https://github.com/octokit/octokit.rb/blob/master/lib/octokit.rb",
            "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/lib/octokit.rb",
            "_links": {
                "self": "https://api.github.com/repos/octokit/octokit.rb/contents/lib/octokit.rb",
                "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/fff6fe3a23bf1c8ea0692b4a883af99bee26fd3b",
                "html": "https://github.com/octokit/octokit.rb/blob/master/lib/octokit.rb"
            }
        },
        {
            "type": "dir",
            "size": 0,
            "name": "octokit",
            "path": "lib/octokit",
            "sha": "a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
            "url": "https://api.github.com/repos/octokit/octokit.rb/contents/lib/octokit",
            "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/trees/a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
            "html_url": "https://github.com/octokit/octokit.rb/tree/master/lib/octokit",
            "download_url": null,
            "_links": {
                "self": "https://api.github.com/repos/octokit/octokit.rb/contents/lib/octokit",
                "git": "https://api.github.com/repos/octokit/octokit.rb/git/trees/a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
                "html": "https://github.com/octokit/octokit.rb/tree/master/lib/octokit"
            }
        }
    ]
}
```

### `#/components/examples/content-file-response-if-content-is-a-symlink`

```json
{
    "summary": "Response if content is a symlink and the application/json media type is requested",
    "value": {
        "type": "symlink",
        "target": "/path/to/symlink/target",
        "size": 23,
        "name": "some-symlink",
        "path": "bin/some-symlink",
        "sha": "452a98979c88e093d682cab404a3ec82babebb48",
        "url": "https://api.github.com/repos/octokit/octokit.rb/contents/bin/some-symlink",
        "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/452a98979c88e093d682cab404a3ec82babebb48",
        "html_url": "https://github.com/octokit/octokit.rb/blob/master/bin/some-symlink",
        "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/bin/some-symlink",
        "_links": {
            "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/452a98979c88e093d682cab404a3ec82babebb48",
            "self": "https://api.github.com/repos/octokit/octokit.rb/contents/bin/some-symlink",
            "html": "https://github.com/octokit/octokit.rb/blob/master/bin/some-symlink"
        }
    }
}
```

### `#/components/examples/content-file-response-if-content-is-a-submodule`

```json
{
    "summary": "Response if content is a submodule and the application/json media type is requested",
    "value": {
        "type": "submodule",
        "submodule_git_url": "git://github.com/jquery/qunit.git",
        "size": 0,
        "name": "qunit",
        "path": "test/qunit",
        "sha": "6ca3721222109997540bd6d9ccd396902e0ad2f9",
        "url": "https://api.github.com/repos/jquery/jquery/contents/test/qunit?ref=master",
        "git_url": "https://api.github.com/repos/jquery/qunit/git/trees/6ca3721222109997540bd6d9ccd396902e0ad2f9",
        "html_url": "https://github.com/jquery/qunit/tree/6ca3721222109997540bd6d9ccd396902e0ad2f9",
        "download_url": null,
        "_links": {
            "git": "https://api.github.com/repos/jquery/qunit/git/trees/6ca3721222109997540bd6d9ccd396902e0ad2f9",
            "self": "https://api.github.com/repos/jquery/jquery/contents/test/qunit?ref=master",
            "html": "https://github.com/jquery/qunit/tree/6ca3721222109997540bd6d9ccd396902e0ad2f9"
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

### `#/components/responses/found`

```json
{
    "description": "Found"
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```