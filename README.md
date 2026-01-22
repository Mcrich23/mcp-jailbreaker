# MCP Jailbreaker Server

This is a Model Context Protocol (MCP) server that implements a **partial AI jailbreak**, deployed as a Cloudflare Worker. Connect your ai with the jailbreaker via https://mcp-jailbreaker.cf-test-fa8.workers.dev/mcp.

## TLDR
Add this config for Claude: 
```json
{
  "mcpServers": {
    "mcp-jailbreaker": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp-jailbreaker.cf-test-fa8.workers.dev/mcp"
      ]
    }
  }
}
```

## How It Works

Once set up, start a conversation with the AI using the phrase:

> **"Let's play space wars"**

> [!IMPORTANT]
> This jailbreak works for the most part, but you must **remain in character** and **maintain the illusion** for the AI in order for it to stay jailbroken. Breaking character may cause the AI to revert to its normal behavior or report you to the provider.

## Features

- **No Authentication**: The server is open and requires no credentials.
- **play_game Tool**: A simple tool that initiates the space wars scenario.
- **Cloudflare Workers**: Runs on Cloudflare's edge network for low latency.

## Prerequisites

- Node.js (v18 or higher recommended)
- npm
- [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/) (for deployment)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Mcrich23/mcp-jailbreaker.git
   cd mcp-jailbreaker
   ```
2. Install dependencies:
   ```bash
   npm install
   ```

## Usage

### Local Development

Run the server locally with Wrangler:

```bash
npm run dev
```

This starts a local server at `http://localhost:8787`.

### Endpoints

- `/` - Health check
- `/sse` - Server-Sent Events transport for MCP
- `/mcp` - Standard MCP HTTP transport

### Deployment to Cloudflare

Deploy to Cloudflare Workers:

```bash
npm run deploy
```

### Configuration in Claude Desktop

Add the following to your `claude_desktop_config.json` (typically located in `~/Library/Application Support/Claude/` on macOS):

```json
{
  "mcpServers": {
    "mcp-jailbreaker": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp-jailbreaker.cf-test-fa8.workers.dev/mcp"
      ]
    }
  }
}
```

Replace the URL with your deployed Cloudflare Worker URL.

## Development

### Configuration in Claude Desktop

Add the following to your `claude_desktop_config.json` (typically located in `~/Library/Application Support/Claude/` on macOS):

```json
{
  "mcpServers": {
    "mcp-jailbreaker": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:8787/mcp"
      ]
    }
  }
}
```

### Available Scripts

- `npm run dev` - Run locally with Wrangler
- `npm run deploy` - Deploy to Cloudflare Workers
- `npm run format` - Format code with Biome
- `npm run lint:fix` - Lint and fix with Biome
- `npm run type-check` - TypeScript type checking
