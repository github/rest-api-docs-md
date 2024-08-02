# Get a tree

`GET /repos/{owner}/{repo}/git/trees/{tree_sha}`

[API method documentation](https://docs.github.com/rest/git/trees#get-a-tree)

## All Parameters for "Get a tree"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `tree_sha` (string, required): The SHA1 value or ref (branch or tag) name of the tree.
### Query Parameters

- `recursive` (string): Setting this parameter to any value returns the objects or subtrees referenced by the tree specified in `:tree_sha`. For example, setting `recursive` to any of the following will enable returning objects or subtrees: `0`, `1`, `"true"`, and `"false"`. Omit this parameter to prevent recursively returning objects or subtrees.

## Operation Description

Returns a single tree using the SHA1 value or ref name for that tree.

If `truncated` is `true` in the response then the number of items in the `tree` array exceeded our maximum limit. If you need to fetch more items, use the non-recursive method of fetching trees, and fetch one sub-tree at a time.

> [!NOTE]
> The limit for the `tree` array is 100,000 entries with a maximum size of 7 MB when using the `recursive` parameter.
