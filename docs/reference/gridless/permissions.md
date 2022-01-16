# Permissions

## Flow Permissions

| Permission | Description | Applies to endpoints |
|------------|-------------|----------------------|
| `view` | View profile information for the Flow[^1] | `getFlow` |
| `read` | Read Content in the Flow | `getFlow.content` |
| `post` | Post Content to the Flow | `postContent` |
| `join` | Join the Flow.<br />This permission can also have a value of `"REQUEST"`.[^2] | `joinFlow` |
| `delete` | Delete Content in the Flow | `deleteContent` for content the user did not post |
| `pin` | Pin Content to the top of the Flow | `pinContent` |
| `update` | Change the profile, features, and settings of the Flow | `updateFlow` |
<!-- got a lot more permissions to add >:D -->

### Permission values
* `"ALLOW"`
* `"DENY"`
* `"REQUEST"` -- used on the `join` permission
<!-- * `"FORCE"` -- used on the `impersonate` permission -->

[^1]: When set to `"DENY"` on `public_permissions`, the Flow is considered "private". Attempts to query a private Flow will result in a not-found condition (the query will silently return null). 
[^2]: The `"REQUEST"` permission value allows the user to *request* to join the Flow. The `join` permission has no effect outside of the Flow's `public_permissions`.