# Maven Analytics plugin

Maven plugin for Claude Code and Codex. Ask questions of your marketing data and build live reports from the Maven MCP server at `https://mcp.metricmaven.io/mcp`.

## Claude Code

Install from the Maven marketplace:

```text
/plugin marketplace add MavenData/maven-plugins
/plugin install maven@maven-plugins
```

The plugin connects to the Maven MCP server over HTTP. The first time you use a Maven tool, run `/mcp`, choose `maven`, and finish the sign-in in your browser.

For local testing from a clone of this repository, add the marketplace from the folder that contains it:

```text
/plugin marketplace add ./plugins
/plugin install maven@maven-plugins
```

## Codex

### Install

The Codex manifest is `.codex-plugin/plugin.json`. It bundles the Maven MCP server through `.codex-plugin/mcp.json` (`https://mcp.metricmaven.io/mcp`, OAuth sign-in) and shares the `skills/` folder with Claude Code. Sign in with your Maven account the first time a Maven tool runs.

The manifest does not register an `apps` / `.app.json` file, because OpenAI's plugin directory rejects submissions that include one.

### Validate

There is no `codex plugin validate` command yet. Check the manifests parse and that the bundled server file exists:

```bash
python3 -m json.tool plugins/maven-analytics/.codex-plugin/plugin.json > /dev/null
python3 -m json.tool plugins/maven-analytics/.codex-plugin/mcp.json > /dev/null
```

The OpenAI plugin portal runs the authoritative validation when the ZIP is uploaded.

## Other MCP clients

Any client that supports remote MCP servers over streamable HTTP can connect directly:

- Server URL: `https://mcp.metricmaven.io/mcp`
- Authentication: OAuth. Sign in with your Maven account when the client asks.
- Setup guide: https://www.metricmaven.io/docs/mcp
