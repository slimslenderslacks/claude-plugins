# Docker Tools Marketplace for Claude Code

This repository contains a Claude Code plugin marketplace that provides Docker-related plugins.

## Structure

```
claude-marketplace/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace configuration
└── plugins/
    └── docker-mcp-gateway/       # Docker MCP Gateway plugin
        ├── .claude-plugin/
        │   └── plugin.json       # Plugin manifest
        └── .mcp.json             # MCP server configuration
```

## Plugins

### docker-mcp-gateway

Integrates Docker MCP Gateway with Claude Code, enabling access to containerized MCP servers.

**Features:**
- Connects Claude Code to Docker MCP Gateway
- Provides access to all MCP servers configured in Docker Desktop
- Runs `docker mcp gateway run` as an MCP server within Claude Code

**Prerequisites:**
- Docker Desktop with MCP Toolkit enabled
- Docker MCP Gateway CLI (`docker mcp` command available)

## Usage

### Adding the Marketplace

Add this marketplace to Claude Code:

```bash
# Local development
/plugin marketplace add ./claude-marketplace

# Or via git repository
/plugin marketplace add https://github.com/your-org/claude-marketplace.git
```

### Installing the Plugin

```bash
/plugin install docker-mcp-gateway@docker-tools
```

### Verifying Installation

Once installed, the Docker MCP Gateway will be available as an MCP server in Claude Code. You can verify by checking your MCP servers in Claude Code settings.

## Development

To test changes locally:

1. Make modifications to the plugin files
2. If the marketplace is already added, update it:
   ```bash
   /plugin marketplace update docker-tools
   ```
3. Reinstall or update the plugin if needed

## License

MIT
