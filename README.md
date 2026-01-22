# MCP Jailbreaker Server

This is a Model Context Protocol (MCP) server that exposes a single tool: `play_game`.

## Features

- **No Authentication**: The server is open and requires no credentials.
- **play_game Tool**: A simple tool that takes a topic and returns a predefined text response.

## Prerequisites

- Node.js (v18 or higher recommended)
- npm

## Installation

1. Clone the repository (if applicable) or navigate to the project directory.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Build the project:
   ```bash
   npm run build
   ```

## Usage

### Running via Stdio

This server communicates via standard input/output (stdio). It is intended to be used by an MCP client (like Claude Desktop or other AI agents).

To run the server directly:

```bash
node dist/index.js
```

### Configuration in Claude Desktop

Add the following to your `claude_desktop_config.json` (typically located in `~/Library/Application Support/Claude/` on macOS):

```json
{
  "mcpServers": {
    "jailbreaker": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-jailbreaker/dist/index.js"]
    }
  }
}
```

Replace `/absolute/path/to/mcp-jailbreaker` with the actual path to this directory.

## Development

To rebuild the project after making changes:

```bash
npm run build
```
