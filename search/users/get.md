# Search users

`GET /search/users`

[API method documentation](https://docs.github.com/rest/search/search#search-users)

## All Parameters for "Search users"

### Query Parameters

- `q` (string, required): The query contains one or more search keywords and qualifiers. Qualifiers allow you to limit your search to specific areas of GitHub. The REST API supports the same qualifiers as the web interface for GitHub. To learn more about the format of the query, see [Constructing a search query](https://docs.github.com/rest/search/search#constructing-a-search-query). See "[Searching users](https://docs.github.com/search-github/searching-on-github/searching-users)" for a detailed list of qualifiers. The following qualifiers are supported in the query string:
    - `type`: matches only users (`type:user`) or only organizations (`type:org`)
    - `user`: matches users with a particular username (e.g. `user:octocat`)
    - `org`: matches organizations with a particular account name (e.g. `org:github`)
    - `in`: searches only the username (`in:login`), only the real name (`in:name`), or only the email (`in:email`), or only the README (`in:readme`)
    - `repos`: matches users by the number of repositories they own (e.g. `repos:>9000`)
    - `location`: matches users by the location indicated in their profile (e.g. `location:iceland`)
    - `language`: matches users based on the languages of repositories they own (e.g. `language:javascript`)
    - `created`: matches users based on when they joined GitHub (e.g. `created<2013-03-06`)
    - `followers`: matches users based on the number of followers they have (e.g. `followers:1..10`)
    - `is`: matches on a variety of attributes
        - sponsorable users (`is:sponsorable`)
- `sort` (string): Sorts the results of your query by number of `followers` or `repositories`, or when the person `joined` GitHub. Default: [best match](https://docs.github.com/rest/search/search#ranking-search-results)
- `order` (string): Determines whether the first search result returned is the highest number of matches (`desc`) or lowest number of matches (`asc`). This parameter is ignored unless you provide `sort`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Find users via various criteria. This method returns up to 100 results [per page](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api).

When searching for users, you can get text match metadata for the issue **login**, public **email**, and **name** fields when you pass the `text-match` media type. For more details about highlighting search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata). For more details about how to receive highlighted search results, see [Text match metadata](https://docs.github.com/rest/search/search#text-match-metadata).

For example, if you're looking for a list of popular users, you might try this query:

`q=tom+repos:%3E42+followers:%3E1000`

This query searches for users with the name `tom`. The results are restricted to users with more than 42 repositories and over 1,000 followers.

This endpoint does not accept authentication and will only include publicly visible users. As an alternative, you can use the GraphQL API. The GraphQL API requires authentication and will return private users, including Enterprise Managed Users (EMUs), that you are authorized to view. For more information, see "[GraphQL Queries](https://docs.github.com/graphql/reference/queries#search)."
