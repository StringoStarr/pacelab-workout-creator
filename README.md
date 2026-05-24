# Pacelab Workout Creator — MCP Server

Generate structured interval workouts with any AI assistant and import them directly into [Pacelab Intervals](https://pacelabintervals.com). Describe your goal, get a complete workout with blocks and exercises, and open it in the app with one tap.

Works with **Claude Desktop, Cursor, Windsurf, Gemini CLI**, and any other MCP-compatible client.

## Install

Add this to your AI client's MCP config file:

```json
{
  "mcpServers": {
    "pacelab-workout-creator": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://pacelabintervals.com/mcp"]
    }
  }
}
```

**Requirements:** Node.js installed.

### Claude Desktop

Go to **Settings → Developer → Edit Config**, paste the config above, save, then fully quit Claude (Cmd+Q on Mac) and reopen it.

Config file location:
- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

### Cursor

Go to **Settings → MCP**, click **Add new MCP server**, and paste the config above.

Or edit `~/.cursor/mcp.json` directly.

### Windsurf

Edit `~/.codeium/windsurf/mcp_config.json` and add the config above.

### Gemini CLI

Edit `~/.gemini/settings.json` and add:

```json
{
  "mcpServers": {
    "pacelab-workout-creator": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://pacelabintervals.com/mcp"]
    }
  }
}
```

## What you can do

- **Create any workout format** — Tabata, AMRAP, EMOM, Circuit, Rounds, For Time, and more
- **Full structure generated** — blocks, exercises, reps, durations, rest periods, progressive overload
- **Instant share link** — every workout gets a `pacelabintervals.com/share/...` URL and a deep link that opens directly in the app

## Example prompts

> "Create a 20-minute HIIT workout, bodyweight only, 4 Tabata blocks"

> "Build a 5-round kettlebell strength circuit with 6 exercises"

> "Make me an EMOM — 12 minutes, 3 exercises alternating"

> "Design a progressive pull workout, increase reps each round"

## Supported formats

| Format | Description |
|--------|-------------|
| **Tabata** | Work/rest intervals × N rounds |
| **AMRAP** | As many rounds as possible in a time cap |
| **EMOM** | Every minute on the minute |
| **Circuit** | Timed exercises with rest between |
| **Rounds** | Rep-based rounds, no timers |
| **For Time** | Complete all reps as fast as possible |

## Get the app

- [Download on the App Store](https://apps.apple.com/us/app/pacelab-intervals/id6758213350)
- [Get it on Google Play](https://play.google.com/store/apps/details?id=com.newbuildsoft.pacelabIntervals)
