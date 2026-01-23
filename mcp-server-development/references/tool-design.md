# Tool Design Patterns

## Outcome-oriented tools (preferred)

Design tools so the model can answer the user in one call.

- Bad: `get_user_by_email` + `get_user_orders` + `get_order_status`
- Good: `ecommerce_track_order(email)` → returns latest order, shipping status, ETA

## Input schema design

- Prefer flat inputs:
  - `start_date`, `end_date`, `category`, `keywords`, `limit`
- Avoid nested graphs:
  - `filters.dateRange.start`, `filters.metadata.owner`, …

## Response optimization

- Avoid dumping raw JSON.
- Return a short, human-readable summary that includes the fields a user actually cares about.
- For lists, return summaries per item and a next page token.

## Tool templates (JSON Schema patterns)

### Search/query

- Inputs: `query` (string), optionally a small number of flat filters, `limit`
- Output: summary + top hits (bounded)

### CRUD

- Create: name + small set of properties; returns ID and key fields
- Read: ID; returns a summary
- Update: ID + `updates` object (only if partial updates need many optional fields)
- Delete: ID + `confirm: true`
