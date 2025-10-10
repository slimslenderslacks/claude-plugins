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

Add this marketplace to Claude Code using one of the following methods:

**If your git works with SSH:**
```bash
/plugin marketplace add docker/claude-marketplace
```

**If your git doesn't work with SSH (or prefer HTTPS):**
```bash
/plugin marketplace add https://github.com/docker/claude-marketplace.git
```

### Installing the Plugin

Once the marketplace is added, you can browse available plugins and install the Docker MCP Gateway plugin:

```bash
# Browse all plugins in the docker-tools marketplace
/plugin

# Install the docker-mcp-gateway plugin
/plugin install docker-mcp-gateway@docker-tools
```

### Troubleshooting Commands

If the MCP Gateway server isn't working as expected, the plugin provides two diagnostic slash commands to help identify and resolve issues:

- **`/docker-mcp-gateway:mcp-status`** - Quick health check showing enabled servers and available tools
- **`/docker-mcp-gateway:mcp-debug`** - Comprehensive diagnostics to troubleshoot installation and configuration problems

These commands will automatically check your Docker MCP Gateway setup and provide actionable recommendations if problems are found.

### Verifying Installation

Once installed, the Docker MCP Gateway will be available as an MCP server in Claude Code. You can verify by:

1. Running `/docker-mcp-gateway:mcp-status` to see enabled servers and tool count
2. Checking that MCP tools are available in Claude's toolkit
3. Using Claude to interact with your configured MCP servers

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
