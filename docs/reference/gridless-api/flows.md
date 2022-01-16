# Flows in the Client API

## GraphQL Endpoints

### Get Flow by ID
`QUERY`{ .query } `#!ts getFlow(id: String!)`

**Variables**

| Key | Value |
|------|------|
| `id` | The ID (//example) or snowflake of the Flow you want to look up.

**Returns:** [Flow](#flow); `null` if private or not found

## Types

### Flow
| Key | Type | Description |
|-----|------|-------------|
| `id` | String | The Flow's user-friendly ID. It 