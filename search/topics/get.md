# Search topics

`GET /search/topics`

[API method documentation](https://docs.github.com/rest/search/search#search-topics)

## All Parameters for "Search topics"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query).
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Find topics via various criteria. Results are sorted by best match. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api). See "[Searching topics](https://docs.github.com/articles/searching-topics/)" for a detailed list of qualifiers.

When searching for topics, you can get text match metadata for the topic's **short\_description**, **description**, **name**, or **display\_name** field when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to search for topics related to Ruby that are featured on https://github.com/topics. Your query might look like this:

`q=ruby+is:featured`

This query searches for topics with the keyword `ruby` and limits the results to find only topics that are featured. The topics that are the best match for the query appear first in the search results.
