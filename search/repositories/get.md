# Search repositories

`GET /search/repositories`

[API method documentation](https://docs.github.com/rest/search/search#search-repositories)

## All Parameters for "Search repositories"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See "[Searching for repositories](https://docs.github.com/articles/searching-for-repositories/)" for a detailed list of qualifiers. The following qualifiers are supported in the query string:
    - `in`: searches only the repo name (`in:name`), only the description (`in:description`), only the topics (`in:topics`), or only the README (`in:readme`)
    - `repo`: matches a specific repository name (e.g. `repo:octocat/hello-world`)
    - `user`: matches repos owned by the given user
    - `org`: matches repos owned by the given organization
    - `size`: matches repositories that match a certain size in kilobytes (e.g. `size:>=1000`)
    - `followers`: matches repos based on the number of followers (e.g. `followers:1..10`)
    - `forks`: matches repos based on the number of forks (e.g. `forks:<=5`)
    - `stars`: matches repos based on the number of stars (e.g. `stars:>1`)
    - `created`: filters repos based on the time of creation (e.g. `created:<2012-01-01`)
    - `pushed`: filters repos based on the most recent time they were pushed to (e.g. `pushed:>2013-05-24`)
    - `language`: matches repos written in the specified language
    - `topic`: matches repos that have been classified with a particular topic
    - `topics`: matches repos based on the number of topics (e.g. `topics:>10`)
    - `license`: matches repos based on the type of license (e.g. `license:apache-2.0`)
    - `mirror`: matches repos based on whether they are mirrors of repos hosted elsewhere (e.g. `mirror:false`)
    - `template`: matches repos based on whether they are templates (e.g. `template:false`)
    - `archived`: matches repos based on whether they are archived (e.g. `archived:false`)
    - `good-first-issues`: matches repos based on the number of issues tagged with "good first issue"
    - `help-wanted-issues`: matches repos based on the nymber of issues tagged with "help wanted"
    - `is`: matches on a variety of attributes
        - public repos (`is:public`)
        - private repos (`is:private`)
        - sponsorable repos (`is:sponsorable`)
- `sort` (string): Sorts the results of your query by number of `stars`, `forks`, or `help-wanted-issues` or how recently the items were `updated`. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)
- `order` (string): Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Find repositories via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for repositories, you can get text match metadata for the **name** and **description** fields when you pass the `text-match` media type. For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to search for popular Tetris repositories written in assembly code, your query might look like this:

`q=tetris+language:assembly&sort=stars&order=desc`

This query searches for repositories with the word `tetris` in the name, the description, or the README. The results are limited to repositories where the primary language is assembly. The results are sorted by stars in descending order, so that the most popular repositories appear first in the search results.
