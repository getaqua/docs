# Gridless API
The Gridless API is the main GraphQL API which Gridless provides to clients, such as Seaworld and other apps. The API can be categorized into multiple main groups, which we have done for these docs, because humans are built to categorize things.

* [Flows](./flows): including users, communities, and the following and joining mechanics.
* [Content](./content): posts that users make in Flows.
* [Chat](./chat): including chatrooms and messages.

## GraphQL Endpoints

### Check the Logged-In User
`QUERY`{ .query } `#!ts getMe`

This endpoint allows you to check the scopes on your token and get the user's Flow.

**Returns: ThisUser** (exclusive response type)

| Key | Type | Description |
:-----|------|-------------|
| :warning: `user` | User | This field is essentially a partial Flow, so it's best to just use `flow` instead. This field is set to be removed very soon. |
| `flow` | [Flow](./flows#flow) | The user's Flow. Use this to get the user's ID, name, and profile picture. |
| `username` | String | The user's username, which is used for login. |
| :material-info-outline: `verifiedEmail` | Boolean | Whether the user has verified their email address. `true` by default. NOTE: the field is likely to be renamed to `verified_email` and it also doesn't work yet. |
| :material-info-outline: `tokenPermissions` | List of Strings | The list of scopes your application was granted. NOTE: this field is likely to be renamed to `scopes`. |