# TypeScript/Node MCP Server Libraries

## Official SDK: `@modelcontextprotocol/sdk`

- Docs/spec entry point: https://modelcontextprotocol.io
- Source: https://github.com/modelcontextprotocol/typescript-sdk
- npm: https://www.npmjs.com/package/@modelcontextprotocol/sdk
- Provides server primitives and transports (commonly stdio and SSE).

## Scaffolding: `create-typescript-server`

- Source: https://github.com/modelcontextprotocol/create-typescript-server
- Use when you want a ready-to-run skeleton with recommended project layout.

## Community framework: `mcp-framework`

- Site: https://mcp-framework.com/
- Source: https://github.com/QuantGeekDev/mcp-framework
- A TypeScript framework that focuses on fast setup, auto-discovery, and ergonomic tool definitions.

## Selection guidance

- Prefer **Mastra** when you want to author MCP servers/clients as part of a Mastra app (expose agents/tools/workflows, integrate auth, and reuse Mastra primitives).
- Prefer the **official SDK** for maximum portability and spec fidelity with minimal framework assumptions.
- Prefer a **mcp-framewor** when you want conventions/auto-discovery and faster iteration.
