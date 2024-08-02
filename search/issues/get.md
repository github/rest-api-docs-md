# Search issues and pull requests

`GET /search/issues`

[API method documentation](https://docs.github.com/rest/search/search#search-issues-and-pull-requests)

## All Parameters for "Search issues and pull requests"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See "[Searching issues and pull requests](https://docs.github.com/search-github/searching-on-github/searching-issues-and-pull-requests)" for a detailed list of qualifiers. The following qualifiers are supported in the query string:
    - `type`: matches only issues (`type:issue`) or only pull requests (`type:pr`)
    - `in`: searches only the title (`in:title`), only the body (`in:body`) or only the comments (`in:comments`)
    - `user`: matches issues and pull requests in repos owned by the given user
    - `org`: matches issues and pull requests in repos owned by the given organization
    - `repo`: matches issues and pull requests in the given repo (e.g. `repo:facebook/react`)
    - `reason`: matches issues that were closed as completed (`reason:completed`) or as not planned (`reason:"not planned")
    - `author`: matches issues and pull requests created by a certain user or integration account
    - `assignee`: matches issues and pull requests that are assigned to a certain user
    - `mentions`: matches issues and pull requests that mention a certain user or team
    - `commenter`: matches issues and pull requests that contain a comment from a certain user
    - `involves`: matches issues and pull requests that involve a certain user, either via comments, assignment, creation, or mentions
    - `linked`: matches issues and pull requests that are linked to a pull request (`linked:pr`) or to an issue (`linked:issue`)
    - `label`: matches issues and pull requests with a particular label
    - `milestone`: matches issues and pull requests that are part of a certain milestone (e.g. `milestone:"overhaul"`)
    - `project`: matches issues and pull requests that are associated with a specific project, identified by project number (e.g. `project:57`)
    - `status`: matches pull requests based on the status of the commits (e.g. `status:pending` or `status:success` or `status:failure`)
    - `sha`: matches pull requests that contain a commit with a specific SHA hash with at least 7 characters
    - `head`: matches pull requests based on the head branch
    - `base`: matches pull requests based on the branch they are merging into
    - `language`: matches issues and pull requests within repositories that are written in a certain language
    - `comments`: matches issues and pull requests based on the number of comments, using greater than, less than, and range qualifiers (e.g. `comments:10` or `comments:>2` or `comments:500..1000`)
    - `reactions`: matches issues and pull requests based on the number of reactions, using greater than, less than, and range qualifiers (e.g. `reactions:10` or `reactions:>2` or `reactions:500..1000`)
    - `interactions`: matches issues and pull requests based on the number of comments and reactions, using greater than, less than, and range qualifiers (e.g. `interactions:10` or `interactions:>2` or `interactions:500..1000`)
    - `draft`: matches draft pull requests (e.g. `draft:true` or `draft:false`)
    - `review`: matches pull requests based on their review status ("none", "required", "approved", or "changes requested")
    - `reviewed-by`: matches pull requests reviewed by a particular user
    - `review-requested`: matches pull requests where a specific user is requested for review
    - `created`: matches issues and pull requests based on when they were created (e.g. `created:<2011-01-01`)
    - `updated`: matches issues and pull requests based on when they were updated (e.g. `updated:>=2013-02-01`)
    - `closed`: matches issues and pull requests based on when they were closed (e.g. `closed:2014-06-11`)
    - `merged`: matches issues and pull requests based on when they were merged (e.g. `merged:>2020-01-01`)
    - `archived`: matches issues and pull requests based on whether they are in an archived repository (e.g. `archived:true`)
    - `no`: matches issues and pull requests with missing metadata (e.g. `no:label` or `no:assignee` or `no:milestone`)
    - `is`: matches on a variety of attributes
        - only issues (`is:issue`)
        - only pull requests (`is:pr`)
        - only open items (`is:open`)
        - only closed items (`is:closed`)
        - items in the merge queue (`is:queued`)
        - items in public repos (`is:public`)
        - items in private repos (`is:private`)
        - merged pull requests (`is:merged`)
        - unmerged pull requests (`is:unmerged`)
        - items with locked or unlocked conversations (`is:locked` or `is:unlocked`)
- `sort` (string): Sorts the results of your query by the number of `comments`, `reactions`, `reactions-+1`, `reactions--1`, `reactions-smile`, `reactions-thinking_face`, `reactions-heart`, `reactions-tada`, or `interactions`. You can also sort results by how recently the items were `created` or `updated`, Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)
- `order` (string): Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Find issues by state and keyword. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for issues, you can get text match metadata for the issue **title**, issue **body**, and issue **comment body** fields when you pass the `text-match` media type. For more details about how to receive highlighted
search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you want to find the oldest unresolved Python bugs on Windows. Your query might look something like this.

`q=windows+label:bug+language:python+state:open&sort=created&order=asc`

This query searches for the keyword `windows`, within any open issue that is labeled as `bug`. The search runs across repositories whose primary language is Python. The results are sorted by creation date in ascending order, which means the oldest issues appear first in the search results.

> [!NOTE]
> For requests made by GitHub Apps with a user access token, you can't retrieve a combination of issues and pull requests in a single query. Requests that don't include the `is:issue` or `is:pull-request` qualifier will receive an HTTP `422 Unprocessable Entity` response. To get results for both issues and pull requests, you must send separate queries for issues and pull requests. For more information about the `is` qualifier, see "[Searching only issues or pull requests](https://docs.github.com/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-only-issues-or-pull-requests)."
