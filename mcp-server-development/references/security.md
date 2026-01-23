# Security & Safety for MCP Servers

## Non-negotiables

- Never return secrets in tool outputs (tokens, API keys, passwords, credit cards).
- Require explicit confirmation for destructive actions (e.g., `confirm: true`).
- Apply least privilege: separate read/write/admin capabilities.

## Input hardening

- Validate all tool inputs before doing work.
- Constrain untrusted strings:
  - Length limits
  - Allow-lists via `enum` / `pattern` where possible
  - Reject obviously malicious patterns for sensitive contexts

## Error messages

- Prefer specific, user-actionable errors:
  - “User not found: 'a@b.com'. Verify the email or confirm the user exists in your org.”
- Avoid opaque “500 internal error” messages.

## Audit logging

Log every tool call with:

- timestamp, user/session identifier (if available), tool name, duration
- **scrubbed** arguments (redact secret-ish keys)
- success/failure and a small result summary (not full payloads)
