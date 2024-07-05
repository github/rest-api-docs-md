# Search topics

`get /search/topics`

Find topics via various criteria. Results are sorted by best match. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api). See "[Searching topics](https://docs.github.com/articles/searching-topics/)" for a detailed list of qualifiers.

When searching for topics, you can get text match metadata for the topic's **short\_description**, **description**, **name**, or **display\_name** field when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to search for topics related to Ruby that are featured on https://github.com/topics. Your query might look like this:

`q=ruby+is:featured`

This query searches for topics with the keyword `ruby` and limits the results to find only topics that are featured. The topics that are the best match for the query appear first in the search results.

## Operation Object

```json
{
    "summary": "Search topics",
    "description": "Find topics via various criteria. Results are sorted by best match. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api). See \"[Searching topics](https://docs.github.com/articles/searching-topics/)\" for a detailed list of qualifiers.\n\nWhen searching for topics, you can get text match metadata for the topic's **short\\_description**, **description**, **name**, or **display\\_name** field when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).\n\nFor example, if you want to search for topics related to Ruby that are featured on https://github.com/topics. Your query might look like this:\n\n`q=ruby+is:featured`\n\nThis query searches for topics with the keyword `ruby` and limits the results to find only topics that are featured. The topics that are the best match for the query appear first in the search results.",
    "tags": [
        "search"
    ],
    "operationId": "search/topics",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/search/search#search-topics"
    },
    "parameters": [
        {
            "name": "q",
            "description": "The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query).",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string"
            }
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "required": [
                            "total_count",
                            "incomplete_results",
                            "items"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "incomplete_results": {
                                "type": "boolean"
                            },
                            "items": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/topic-search-result-item"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/topic-search-result-item-paginated"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "search",
        "subcategory": "search"
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

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
    }
}
```

### `#/components/schemas/topic-search-result-item`

```json
{
    "title": "Topic Search Result Item",
    "description": "Topic Search Result Item",
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "display_name": {
            "type": "string",
            "nullable": true
        },
        "short_description": {
            "type": "string",
            "nullable": true
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "created_by": {
            "type": "string",
            "nullable": true
        },
        "released": {
            "type": "string",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "featured": {
            "type": "boolean"
        },
        "curated": {
            "type": "boolean"
        },
        "score": {
            "type": "number"
        },
        "repository_count": {
            "type": "integer",
            "nullable": true
        },
        "logo_url": {
            "type": "string",
            "format": "uri",
            "nullable": true
        },
        "text_matches": {
            "$ref": "#/components/schemas/search-result-text-matches"
        },
        "related": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "object",
                "properties": {
                    "topic_relation": {
                        "type": "object",
                        "properties": {
                            "id": {
                                "type": "integer"
                            },
                            "name": {
                                "type": "string"
                            },
                            "topic_id": {
                                "type": "integer"
                            },
                            "relation_type": {
                                "type": "string"
                            }
                        }
                    }
                }
            }
        },
        "aliases": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "object",
                "properties": {
                    "topic_relation": {
                        "type": "object",
                        "properties": {
                            "id": {
                                "type": "integer"
                            },
                            "name": {
                                "type": "string"
                            },
                            "topic_id": {
                                "type": "integer"
                            },
                            "relation_type": {
                                "type": "string"
                            }
                        }
                    }
                }
            }
        }
    },
    "required": [
        "name",
        "display_name",
        "short_description",
        "description",
        "created_by",
        "released",
        "created_at",
        "updated_at",
        "featured",
        "curated",
        "score"
    ]
}
```

### `#/components/examples/topic-search-result-item-paginated`

```json
{
    "value": {
        "total_count": 6,
        "incomplete_results": false,
        "items": [
            {
                "name": "ruby",
                "display_name": "Ruby",
                "short_description": "Ruby is a scripting language designed for simplified object-oriented programming.",
                "description": "Ruby was developed by\u00a0Yukihiro \"Matz\" Matsumoto\u00a0in 1995 with the intent of having an easily readable programming language. It is integrated with the Rails framework to create dynamic web-applications. Ruby's syntax is similar to that of Perl and Python.",
                "created_by": "Yukihiro Matsumoto",
                "released": "December 21, 1995",
                "created_at": "2016-11-28T22:03:59Z",
                "updated_at": "2017-10-30T18:16:32Z",
                "featured": true,
                "curated": true,
                "score": 1
            },
            {
                "name": "rails",
                "display_name": "Rails",
                "short_description": "Ruby on Rails (Rails) is a web application framework written in Ruby.",
                "description": "Ruby on Rails (Rails) is a web application framework written in Ruby. It is meant to help simplify the building of complex websites.",
                "created_by": "David Heinemeier Hansson",
                "released": "December 13 2005",
                "created_at": "2016-12-09T17:03:50Z",
                "updated_at": "2017-10-30T16:20:19Z",
                "featured": true,
                "curated": true,
                "score": 1
            },
            {
                "name": "python",
                "display_name": "Python",
                "short_description": "Python is a dynamically typed programming language.",
                "description": "Python is a dynamically typed programming language designed by Guido Van Rossum. Much like the programming language Ruby, Python was designed to be easily read by programmers. Because of its large following and many libraries, Python can be implemented and used to do anything from webpages to scientific research.",
                "created_by": "Guido van Rossum",
                "released": "February 20, 1991",
                "created_at": "2016-12-07T00:07:02Z",
                "updated_at": "2017-10-27T22:45:43Z",
                "featured": true,
                "curated": true,
                "score": 1
            },
            {
                "name": "jekyll",
                "display_name": "Jekyll",
                "short_description": "Jekyll is a simple, blog-aware static site generator.",
                "description": "Jekyll is a blog-aware, site generator written in Ruby. It takes raw text files, runs it through a renderer and produces a publishable static website.",
                "created_by": "Tom Preston-Werner",
                "released": "2008",
                "created_at": "2016-12-16T21:53:08Z",
                "updated_at": "2017-10-27T19:00:24Z",
                "featured": true,
                "curated": true,
                "score": 1
            },
            {
                "name": "sass",
                "display_name": "Sass",
                "short_description": "Sass is a stable extension to classic CSS.",
                "description": "Sass is a stylesheet language with a main implementation in Ruby. It is an extension of CSS that makes improvements to the old stylesheet format, such as being able to declare variables and using a cleaner nesting syntax.",
                "created_by": "Hampton Catlin, Natalie Weizenbaum, Chris Eppstein",
                "released": "November 28, 2006",
                "created_at": "2016-12-16T21:53:45Z",
                "updated_at": "2018-01-16T16:30:40Z",
                "featured": true,
                "curated": true,
                "score": 1
            },
            {
                "name": "homebrew",
                "display_name": "Homebrew",
                "short_description": "Homebrew is a package manager for macOS.",
                "description": "Homebrew is a package manager for Apple's macOS operating system. It simplifies the installation of software and is popular in the Ruby on Rails community.",
                "created_by": "Max Howell",
                "released": "2009",
                "created_at": "2016-12-17T20:30:44Z",
                "updated_at": "2018-02-06T16:14:56Z",
                "featured": true,
                "curated": true,
                "score": 1
            }
        ]
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```