# MCP Server Design: Quick Reference

## Core philosophy

- Treat an MCP server as an AI-user interface: expose *capabilities* that map to user outcomes, not raw endpoints.
- Prefer 1 call → 1 complete answer. If a user question requires chaining 3–5 backend calls, hide that behind one MCP tool.

## Scope and sizing

- **One bounded context per server.**
- **Tools per server**: aim for ~5–10, hard cap ~15.

## Naming and descriptions

- Name tools with `service_domain_action` (e.g., `github_create_issue`, `slack_send_message`).
- Description template:
  - `[VERB] [OBJECT] for [CONTEXT]. When [USER INTENT], use this tool to [WHAT IT DOES]. Input constraints: [CONSTRAINTS]. Returns: [OUTPUT FORMAT].`

## Token efficiency

- Return concise summaries by default.
- Paginate after ~10 items and return a `next_page_token`.
- Avoid returning logs or large blobs; provide “how to retrieve more” instead.

## Anti-patterns

- “API wrapper” tool sets that force the model to chain multiple calls for a single user request.
- Overly generic tools (`execute_query`, `manage_user_account`) without guardrails.
- Stateless multi-step workflows (`step1_initialize`, `step2_configure`, …).
