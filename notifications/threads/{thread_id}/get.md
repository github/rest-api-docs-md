# Get a thread

`GET /notifications/threads/{thread_id}`

Gets information about a notification thread.

[API method documentation](https://docs.github.com/rest/activity/notifications#get-a-thread)

## All Parameters for "Get a thread"

### Path Parameters

- `thread_id` (integer, required): The unique identifier of the notification thread. This corresponds to the value returned in the `id` field when you retrieve notifications (for example with the [`GET /notifications` operation](https://docs.github.com/rest/activity/notifications#list-notifications-for-the-authenticated-user)).