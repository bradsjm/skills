---
name: mcp-server-development
description: Develop, review, and refactor Model Context Protocol (MCP) servers in Python or TypeScript/Node.js. Use when designing MCP tool/resource/prompt contracts, implementing an MCP server (stdio/SSE/Streamable HTTP), tightening JSON Schema inputs, improving error handling, adding security guardrails (secret scrubbing, permissions, destructive confirmations), and creating tests for MCP tools.
---

# MCP Server Development

## Quick start

- Treat an MCP server as an AI-user interface (outcomes), not an endpoint wrapper.
- Keep the server small: one bounded context, ~5–15 tools max.
- Design tool contracts first: names, descriptions, flat input schemas, concise outputs.
- Implement with an SDK (Python or TypeScript), validate inputs, and return structured errors.
- Test for correctness, safety, and token efficiency.

## Workflow

1. Define the server’s bounded context and user outcomes (see `references/quick-reference.md`).
2. Draft tool contracts (names, descriptions, schemas, outputs) (see `references/tool-design.md`).
3. Choose an implementation library and transport (see `references/python-libraries.md` or `references/typescript-libraries.md`).
4. Implement validation, errors, and pagination conventions (see `references/protocol-and-schemas.md`).
5. Add security guardrails (see `references/security.md`) and observability (see `references/observability.md`).
6. Add tests (see `references/testing.md`) and set a versioning policy (see `references/versioning.md`).

## Reference map

- Contract/design: `references/quick-reference.md`, `references/tool-design.md`
- Protocol/schema/pagination: `references/protocol-and-schemas.md`
- Security: `references/security.md`
- Observability: `references/observability.md`
- Testing: `references/testing.md`
- Libraries: `references/python-libraries.md`, `references/typescript-libraries.md`
- Versioning: `references/versioning.md`

## Rules of thumb

- Prefer a single tool call per user request; merge underlying API calls behind the tool boundary.
- Flatten inputs; avoid nested “filters/metadata” objects unless truly necessary.
- Return LLM-optimized summaries, not raw JSON dumps; paginate long lists.
- Make destructive actions require explicit confirmation (`confirm: true`) and never echo secrets.
- TypeScript SDK: Prefer `McpServer` (`@modelcontextprotocol/sdk/server/mcp.js`) over the lower-level `Server` (`@modelcontextprotocol/sdk/server/index.js`), which is deprecated for most use cases. Use `Server` only for advanced/low-level control when necessary.
