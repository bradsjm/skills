# MCP Protocol & Schema Conventions

## MCP primitives

- **Tools**: callable functions with typed input schemas.
- **Resources**: read-only data access points.
- **Prompts**: reusable workflow templates (pre-baked “recipes”).

## Tool definition shape (server-side)

Each tool exposes:

- `name` (unique identifier)
- `description` (how the model decides to use it)
- `inputSchema` (JSON Schema; prefer `type: "object"` with flat `properties`)

## Tool call request/response (shape)

- Request: `method: "tools/call"`, `params.name`, `params.arguments`
- Response: `result.content[]` plus `result.isError`

## Output conventions

- Prefer `content: [{ type: "text", text: "..." }]` with a concise, contextualized summary.
- Include pagination metadata via `_meta.next_page_token` when listing.

## Pagination pattern

Tool input:

- `limit` (bounded, defaulted)
- `page_token` (opaque string from previous response)

Tool output:

- `_meta.next_page_token` when more results exist

## Schema design rules

- Flatten inputs (avoid nested `filters` objects unless it’s truly a first-class concept).
- Use `enum` for bounded categories.
- Use `format` (`date`, `date-time`, `email`, `uri`, `uuid`) where applicable.
- Bound sizes (`maxItems`, `maximum`, `pattern`) to reduce prompt-injection and runaway outputs.
