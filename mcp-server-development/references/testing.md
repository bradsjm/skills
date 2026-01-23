# Testing MCP Servers

## What to test

- Valid input cases per tool
- Invalid input cases (schema violations, missing required fields)
- Edge cases (empty results, large datasets)
- Pagination behavior and stable `next_page_token`
- Token efficiency (responses remain concise)
- Destructive confirmations (reject when `confirm` is missing/false)

## Python (pytest) pattern

- Use `pytest.mark.asyncio` for async handlers.
- Assert both `isError` and the user-facing message text.

## TypeScript (vitest) pattern

- Test `tools/list` discovery (names, descriptions, input schemas present).
- Test `tools/call` happy path and error path.
