# Python (Dev Steward Reference)

Use this reference when writing, reviewing, or debugging Python in the current repo.

## Non-Negotiables

- Prefer compile-time safety: explicit types, narrow interfaces, and predictable control flow.
- Avoid dynamic attribute access patterns (`hasattr`, `getattr`, `obj["key"]` for attributes).
- Use `uv run` when invoking Python or scripts.
- Avoid `typing.Any` in application code; use precise types and models.

## Typing & Linting

- Type all functions (parameters + return types) and important locals.
- Run a type checker (prefer `pyright`) and make it pass with zero errors.
- Run linting/formatting (prefer `ruff`) and make it pass with zero warnings.
- Install and use stub packages (`types-*`) when needed rather than weakening types.

## Design & Testability

- Signature-first: write the full, typed signature before the implementation.
- Prefer pure functions and dependency injection for easy unit testing.
- Use Pydantic models or `dataclasses` for structured data.
- Keep public boundaries defensive: validate inputs and fail clearly.

## Error Handling & Logging

- Catch the most specific exceptions possible; never use bare `except` or broad `except Exception`.
- Use deferred/parameterized logging (no f-strings in logger calls).

## Time

- Use timezone-aware datetimes (prefer UTC) for timestamps.
- Use monotonic clocks for elapsed time measurements.

## Forbidden → Required Patterns

| Anti-Pattern | FORBIDDEN | REQUIRED |
| --- | --- | --- |
| `typing.Any` | `def process_data(data: Any) -> None:` | `def process_data(data: User) -> None:` (or other precise type) |
| Broad exceptions | `except Exception:` | `except (KeyError, TypeError):` (or other specific set) |
| f-string logging | `logger.info(f"User {user_id} logged in")` | `logger.info("User %s logged in", user_id)` |
| naive datetime | `datetime.now()` | `datetime.now(UTC)` (or other aware datetime) |
| mutable defaults | `def f(x, xs=[]): ...` | `def f(x, xs: list[T] | None = None): ...` |
| relative imports | `from .. import utils` | `from my_project.core import utils` |

## Preferred Libraries

| Purpose | Libraries |
| --- | --- |
| Data validation | Pydantic |
| Database | SQLAlchemy |
| Generative AI | Pydantic-AI, FastMCP |
| Linting & formatting | Ruff |
| Package management | UV |
| Settings | Pydantic Settings |
| Testing | Pytest |
| Type checking | Pyright |

