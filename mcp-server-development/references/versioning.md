# Versioning & Compatibility

## Semantic versioning

- `MAJOR.MINOR.PATCH`
  - MAJOR: breaking tool names or schema changes
  - MINOR: add new tools or backward-compatible extensions
  - PATCH: bug fixes and docs

## Backward-compat rules (practical)

- Tool names and required fields are the primary “public API”.
- Deprecate before removing; provide a migration note when changing schemas.
