# Search code

`GET /search/code`

[API method documentation](https://docs.github.com/rest/search/search#search-code)

## All Parameters for "Search code"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports different qualifiers than the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See "[Searching code](https://docs.github.com/search-github/searching-on-github/searching-code)" for a detailed list of qualifiers. The following qualifiers are supported in the query string:
    - `in`: searches only the file contents (`in:file`), only the path (`in:path`) or both (`in:file,path`)
    - `user`: matches code in repos owned by the given user
    - `org`: matches code in repos owned by the given organization
    - `repo`: matches code in the given repo (e.g. `repo:facebook/react`)
    - `path`: matches code based on its location (e.g. `path:/` or `path:app/public`)
    - `language`: matches code based on the language it is written in (e.g. `language:xml`)
    - `size`: matches code based on its size in bytes (e.g. `size:>10000`)
    - `filename`: matches code files with a certain filename (e.g. `filename:test_helper`)
    - `extension`: matches code files with a certain file extension (e.g. `extension:tsx`)
- `sort` (string): **This field is deprecated.** Sorts the results of your query. Can only be `indexed`, which indicates how recently a file has been indexed by the GitHub search infrastructure. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)
- `order` (string): **This field is deprecated.** Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`. 
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Searches for query terms inside of a file. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for code, you can get text match metadata for the file **content** and file **path** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to find the definition of the `addClass` function inside [jQuery](https://github.com/jquery/jquery) repository, your query would look something like this:

`q=addClass+in:file+language:js+repo:jquery/jquery`

This query searches for the keyword `addClass` within a file's contents. The query limits the search to files where the language is JavaScript in the `jquery/jquery` repository.

Considerations for code search:

Due to the complexity of searching code, there are a few restrictions on how searches are performed:

*   Only the _default branch_ is considered. In most cases, this will be the `master` branch.
*   Only files smaller than 384 KB are searchable.
*   You must always include at least one search term when searching source code. For example, searching for [`language:go`](https://github.com/search?utf8=%E2%9C%93&q=language%3Ago&type=Code) is not valid, while [`amazing
language:go`](https://github.com/search?utf8=%E2%9C%93&q=amazing+language%3Ago&type=Code) is.

This endpoint requires you to authenticate and limits you to 10 requests per minute.
