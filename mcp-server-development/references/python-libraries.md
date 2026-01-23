# Python MCP Server Libraries

## Official SDK: `mcp` (Model Context Protocol Python SDK)

- Docs/spec entry point: https://modelcontextprotocol.io
- Source: https://github.com/modelcontextprotocol/python-sdk
- PyPI: https://pypi.org/project/mcp/
- Provides server/client building blocks and standard transports (commonly stdio, SSE, and streamable HTTP).

## High-level framework: `fastmcp`

- Source: https://github.com/jlowin/fastmcp
- PyPI: https://pypi.org/project/fastmcp/
- A Pythonic framework for building MCP servers/clients, often used to reduce boilerplate.

## Selection guidance

- Prefer the official SDK when you need the lowest-level control and strict adherence to spec.
- Prefer `fastmcp` when you want fast iteration with ergonomic decorators and structured typing.

## Practical notes

- Use `uv run` for running example servers and CLIs in a clean environment.
- Prefer typed models (e.g., Pydantic) for input validation and internal domain objects.
