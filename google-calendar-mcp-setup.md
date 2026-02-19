# Google Calendar MCP Setup Guide

## Overview

This guide walks through setting up the Google Calendar MCP server for Claude Code, allowing you to read, add, and edit calendar events directly from Claude Code.

## Configuration Location

Claude Code stores MCP server configurations in:
- **File**: `~/.config/claude/config.json`
- **Directory created**: `~/.config/claude/` (already exists)

## Setup Steps

### 1. Get Google OAuth Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project or select existing one
3. Navigate to **APIs & Services → Credentials**
4. Click **Create Credentials → OAuth 2.0 Client ID**
5. Configure OAuth consent screen if needed
6. Select **Desktop app** as application type
7. Download credentials and note:
   - `GOOGLE_CLIENT_ID`
   - `GOOGLE_CLIENT_SECRET`

### 2. Install Google Calendar MCP Server

```bash
npm install -g @modelcontextprotocol/server-google-calendar
```

### 3. Configure Claude Code

Create or edit `~/.config/claude/config.json`:

```json
{
  "mcpServers": {
    "google-calendar": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-google-calendar"],
      "env": {
        "GOOGLE_CLIENT_ID": "your-client-id-here",
        "GOOGLE_CLIENT_SECRET": "your-client-secret-here"
      }
    }
  }
}
```

### 4. Restart Claude Code

After configuration, restart Claude Code for the MCP server to be loaded.

### 5. First Run Authentication

On first use, you'll need to authenticate with Google Calendar through an OAuth flow.

## What You'll Be Able To Do

Once configured, you can:
- Read calendar events
- Create new events
- Edit existing events
- Delete events
- Query events by date range
- Manage multiple calendars

## Troubleshooting

- Run `/doctor` in Claude Code to check MCP server status
- Check logs if authentication fails
- Verify OAuth credentials are correct
- Ensure Google Calendar API is enabled in Google Cloud Console

## References

- [Claude Code MCP Documentation](https://code.claude.com/docs/en/mcp)
- [MCP Server Google Calendar Package](https://www.npmjs.com/package/@modelcontextprotocol/server-google-calendar)
