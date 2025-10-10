# Docker MCP Gateway Plugin

This plugin integrates Docker MCP Gateway with Claude Code, providing seamless access to containerized MCP servers.

## Prerequisites

**This plugin requires one of the following:**

1. **Docker Desktop (Recommended)**
   - Version 4.28.0 or later
   - With MCP Toolkit feature enabled
   - Navigate to: Settings → Beta Features → Enable "Docker MCP Toolkit"

2. **Docker MCP Gateway CLI (Standalone)**
   - Installed independently via: `make docker-mcp` from the [mcp-gateway repository](https://github.com/docker/mcp-gateway)
   - The `docker mcp` command must be available in your PATH

### Verifying Installation

Before installing this plugin, verify the Docker MCP Gateway is available:

```bash
# Check if the docker mcp command is available
docker mcp --help

# Should display the MCP Gateway help information
```

## What This Plugin Does

When enabled, this plugin:

1. Automatically starts the Docker MCP Gateway as an MCP server within Claude Code
2. Exposes all MCP servers configured in Docker Desktop (via `docker mcp server enable`)
3. Makes containerized MCP tools, resources, and prompts available to Claude

## Available Commands

This plugin provides helpful slash commands for managing and debugging Docker MCP Gateway:

- **`/mcp-status`** - Quick status check showing enabled servers and available tools
- **`/mcp-debug`** - Comprehensive diagnostics for troubleshooting gateway issues

## Usage

### Installation

```bash
# Add the marketplace (if not already added)
/plugin marketplace add /path/to/claude-marketplace

# Install the plugin
/plugin install docker-mcp-gateway@docker-tools
```

### Configuration

This plugin uses the default Docker MCP Gateway configuration. To configure which MCP servers are available:

```bash
# List available servers in the Docker MCP catalog
docker mcp catalog show docker-mcp

# Enable specific MCP servers
docker mcp server enable <server-name>

# List currently enabled servers
docker mcp server ls

# Configure server settings (if needed)
docker mcp config write '<yaml-config>'
```

### Verification

Once the plugin is installed and Claude Code is running, the Docker MCP Gateway will automatically start. You can verify this by:

1. Running `/mcp-status` to see enabled servers and tool count
2. Checking that MCP tools are available in Claude's toolkit
3. Using Claude to interact with your enabled MCP servers
4. Running `/mcp-debug` if you encounter any issues

## Troubleshooting

### Plugin fails to start

**Error**: `command not found: docker` or `unknown command: mcp`

**Solution**: Ensure Docker Desktop is installed with Docker MCP Toolkit enabled (Settings → Beta Features), or install the docker-mcp CLI plugin.

### No MCP servers available

**Error**: Gateway starts but no tools are available

**Solution**: Enable MCP servers using `docker mcp server enable <server-name>`

### Gateway connection issues

**Error**: MCP server fails to connect

**Solution**:
1. Verify Docker daemon is running: `docker ps`
2. Check MCP server status: `docker mcp server ls`
3. Review gateway logs for errors

## Learn More

- [Docker MCP Gateway Documentation](https://github.com/docker/mcp-gateway)
- [Docker MCP Catalog](https://hub.docker.com/mcp)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Claude Code MCP Integration](https://docs.claude.com/en/docs/claude-code/mcp)

## License

MIT
