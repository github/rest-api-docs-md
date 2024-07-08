# Get a user

`GET /users/{username}`

Provides publicly available information about someone with a GitHub account.

The `email` key in the following response is the publicly visible email address from your GitHub [profile page](https://github.com/settings/profile). When setting up your profile, you can select a primary email address to be “public” which provides an email entry for this endpoint. If you do not set a public email address for `email`, then it will have a value of `null`. You only see publicly visible email addresses when authenticated with GitHub. For more information, see [Authentication](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#authentication).

The Emails API enables you to list all of your email addresses, and toggle a primary email to be visible publicly. For more information, see "[Emails API](https://docs.github.com/rest/users/emails)".

[API method documentation](https://docs.github.com/rest/users/users#get-a-user)

## All Parameters for "Get a user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.