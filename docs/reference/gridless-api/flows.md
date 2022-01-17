# Flows in the Client API

## GraphQL Endpoints

### Get Flow by ID
`QUERY`{ .query } `#!ts getFlow(id: String!)`

**Variables**

| Key | Value |
|------|------|
| `id` | The ID (//example) or snowflake of the Flow you want to look up. |

**Returns:** [Flow](#flow); `null` if private or not found

## Types

### Flow
| Key | Type | Description |
|-----|------|-------------|
| `id` | String | The Flow's user-friendly ID. It usually begins with `//` to denote that it's an Aqua Flowcode. |
| `snowflake` | [Snowflake](../#snowflake-ids) | The Flow's internal ID, which does not change. |
| `name` | String | The display name of the Flow. Gridless will return the ID without the leading slashes if no name is set. |
| `avatar_url` | URL (String) |  |
| `banner_url` | URL (String) |  |
| `tagline` | String or `null` | 64 characters or less |
| `description` | String or `null` | A bio, "about me", or description. |
| `alternative_ids` | List of Strings | Includes the snowflake and any Fediverse/Matrix user IDs |
| `public_permissions` | [FlowPermissions](#flowpermissions) | Users who are not a member of the Flow will always have these permissions, even if they still have overrides. |
| `joined_permissions` | FlowPermissions | Users who have joined the Flow have these permissions by default. |
| `member_permissions` | Dict of Strings to FlowPermissions | To be deprecated/changed. |
| `owner` | Flow with only `id`, or `null` | The root owner of this Flow. If null, you don't have access to read this field, or it is a user flow. Don't expect this field to stick around. |
| `parent` | Flow or `null` | The parent of this Flow. If null, the parent is private, or this flow is a user flow. |

#### `members`

**Arguments**
| Key | Type | Description |
|-----|------|-------------|
| `limit` | Integer | The number of members to limit the list to. |

**Returns:** List of [Flows](#flow) (Honestly, I have no clue WHICH members are returned from this.)

#### `content`

**Arguments**
| Key | Type | Description |
|-----|------|-------------|
| `limit` | Integer | The number of posts to return. |

**Returns:** List of [Content](./content#content) (It should return the most recent Content.)