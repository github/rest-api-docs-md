# Search commits

`GET /search/commits`

[API method documentation](https://docs.github.com/rest/search/search#search-commits)

## All Parameters for "Search commits"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See "[Searching commits](https://docs.github.com/search-github/searching-on-github/searching-commits)" for a detailed list of qualifiers. The following qualifiers are supported in the query string:
    - `author`: matches commits authored by a particular user
    - `committer`: matches commits authored by a particular user
    - `author-name`: matches commits with a particular string in the author name
    - `committer-name`: matches commits with a particular string in the committer name
    - `author-email`: matches commits by the author's or committer's full email address
    - `committer-email`: matches commits by the author's or committer's full email address
    - `author-date`: matches commits by when they were authored (e.g. `author-date:<2016-01-01`)
    - `committer-date`: matches commits by when they were committed (e.g. `committer-date:>=2018-01-01`)
    - `merge`: filters merge commits (e.g. `merge:true` or `merge:false`)
    - `hash`: matches commits with the specified SHA-1 hash
    - `parent`: matches commits whose parent has the specified SHA-1 hash
    - `tree`: matches commits with the specified SHA-1 git tree hash
    - `user`: matches commits in repos owned by the given user
    - `org`: matches  commits in repos owned by the given organization
    - `repo`: matches commits in the given repo (e.g. `repo:facebook/react`)
    - `is`: matches on a variety of attributes
        - items in public repos (`is:public`)
        - items in private repos (`is:private`)
- `sort` (string): Sorts the results of your query by `author-date` or `committer-date`. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)
- `order` (string): Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Find commits via various criteria on the default branch (usually `main`). This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for commits, you can get text match metadata for the **message** field when you provide the `text-match` media type. For more details about how to receive highlighted search results, see [Text match
metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to find commits related to CSS in the [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife) repository. Your query would look something like this:

`q=repo:octocat/Spoon-Knife+css`
