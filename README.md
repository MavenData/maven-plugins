# Maven plugins

This folder holds Maven's plugin source. Everything here is meant to be exported as the root of the public `MavenData/maven-plugins` repository. That repository does not exist yet.

## File map

- `.claude-plugin/marketplace.json`: Claude Code marketplace `maven-plugins`, listing the `maven` plugin from `./maven-analytics`.
- `maven-analytics/.claude-plugin/plugin.json`: Claude Code plugin manifest (`maven`, version 0.2.0).
- `maven-analytics/.mcp.json`: Maven MCP server for Claude Code (`https://mcp.metricmaven.io/mcp`, OAuth sign-in).
- `maven-analytics/skills/`: skills shared by Claude Code and Codex.
- `maven-analytics/.codex-plugin/plugin.json` and `maven-analytics/.codex-plugin/mcp.json`: Codex and ChatGPT plugin manifest and its bundled Maven MCP server.
- `maven-analytics/README.md`: install steps for Claude Code, Codex, and other MCP clients.

The MCP Registry manifest lives at the repository root, in `server.json`, not in this folder. It is remote-only and points at `https://mcp.metricmaven.io/mcp`.

## Install commands (after the public repo exists)

```text
/plugin marketplace add MavenData/maven-plugins
/plugin install maven@maven-plugins
```

For local testing from a checkout, run `/plugin marketplace add ./plugins` from the repository root.

## Validate

```bash
claude plugin validate plugins/maven-analytics
claude plugin validate plugins
claude plugin validate plugins/maven-analytics --strict
```

The MCP Registry manifest can be checked against its schema, `https://static.modelcontextprotocol.io/schemas/2025-12-11/server.schema.json`, with any JSON Schema draft 7 validator.
