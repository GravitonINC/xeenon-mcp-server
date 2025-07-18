# Xeenon MCP Server



![Xeenon MCP Server](docs/images/xeenon.png)

This project implements an [MCP server](https://spec.modelcontextprotocol.io/) for the [Xeenon API](https://xeenon.xyz).


### Installation

#### 1. Setting up your Xeenon API key:
Go to [https://xeenon.xyz/settings/developers](https://xeenon.xyz/settings/developers) and sign in to enable the access to the API. From there, you can create a new API key.

#### 2. Adding MCP config to your client:

##### Using npm:

**Cursor & Claude:**

Add the following to your `.cursor/mcp.json` or `claude_desktop_config.json` (MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`)

```javascript
{
  "mcpServers": {
    "xeenon-mcp-server": {
      "command": "npx",
      "args": ["-y", "@graviton-inc/xeenon-mcp-server@latest"],
      "env": {
        "XEENON_API_KEY": "xeen_****"
      }
    }
  }
}
```

**Zed**

Add the following to your `settings.json`

```json
{
  "context_servers": {
    "xeenon-mcp-server": {
      "command": {
        "path": "npx",
        "args": ["-y", "@graviton-inc/xeenon-mcp-server@latest"],
        "env": {
          "XEENON_API_KEY": "xeen_****"
        }
      },
      "settings": {}
    }
  }
}
```

##### Using Docker:

There are two options for running the MCP server with Docker:

###### Option 1: Using the official Docker Hub image:

Add the following to your `.cursor/mcp.json` or `claude_desktop_config.json`:

```javascript
{
  "mcpServers": {
    "xeenon-mcp-server": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e", "XEENON_API_KEY",
        "gravitonxyz/xeenon-mcp-server"
      ],
      "env": {
        "XEENON_API_KEY": "xeen_****"
      }
    }
  }
}
```

This approach:
- Uses the official Docker Hub image
- Properly handles JSON escaping via environment variables
- Provides a more reliable configuration method

###### Option 2: Building the Docker image locally:

You can also build and run the Docker image locally. First, build the Docker image:

```bash
docker-compose build
```

Then, add the following to your `.cursor/mcp.json` or `claude_desktop_config.json`:

```javascript
{
  "mcpServers": {
    "xeenon-mcp-server": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e",
        "XEENON_API_KEY=xeen_****",
        "gravitonxyz/xeenon-mcp-server"
      ]
    }
  }
}
```

Don't forget to replace `xeen_****` with your Xeenon API key. Find it in xeenon.xyz/settings/developers.


#### Installing via Smithery

[![smithery badge](https://smithery.ai/badge/@GravitonINC/xeenon-mcp-server)](https://smithery.ai/server/@GravitonINC/xeenon-mcp-server)

To install Xeenon API Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@GravitonINC/xeenon-mcp-server):

```bash
npx -y @smithery/cli install @GravitonINC/xeenon-mcp-server --client claude
```

### Examples

1. Who is following me in Xeenon?
2. What is the wallet address of my Xeenon profile?
3. Sent this message to my Xeenon chat: "Hello MCP"
4. Find a video on Xeenon about "Off the grid"
5. What is the price of $WAFF in Xeenon?


### Development

Build

```
npm run build
```

Execute

```
npx -y --prefix /path/to/local/xeenon-mcp-server @graviton-inc/xeenon-mcp-server
```

Publish

```
npm publish --access public
```
