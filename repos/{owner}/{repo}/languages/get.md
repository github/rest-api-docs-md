# List repository languages

`GET /repos/{owner}/{repo}/languages`

[API method documentation](https://docs.github.com/rest/repos/repos#list-repository-languages)

## All Parameters for "List repository languages"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Lists languages for the specified repository. The value shown for each language is the number of bytes of code written in that language.
