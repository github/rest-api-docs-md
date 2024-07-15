# Get a thread subscription for the authenticated user

`GET /notifications/threads/{thread_id}/subscription`

[API method documentation](https://docs.github.com/rest/activity/notifications#get-a-thread-subscription-for-the-authenticated-user)

## All Parameters for "Get a thread subscription for the authenticated user"

### Path Parameters

- `thread_id` (integer, required): The unique identifier of the notification thread. This corresponds to the value returned in the `id` field when you retrieve notifications (for example with the [`GET /notifications` operation](https://docs.github.com/rest/activity/notifications#list-notifications-for-the-authenticated-user)).

## Operation Description

This checks to see if the current user is subscribed to a thread. You can also [get a repository subscription](https://docs.github.com/rest/activity/watching#get-a-repository-subscription).

Note that subscriptions are only generated if a user is participating in a conversation--for example, they've replied to the thread, were **@mentioned**, or manually subscribe to a thread.
