# Pacelab Workout Creator — MCP Server

Design interval workouts in conversation and have them land in your phone,
ready to run. Describe what you want — a twelve minute AMRAP, a Tabata
finisher, a pull day you can actually finish — and it is saved straight to your
[Pacelab Intervals](https://pacelabintervals.com) library.

It also reads back. Connected to your account, an assistant can see what you
have actually been training — how often, how long, which movements you keep
coming back to — so "build me something harder than last Tuesday" produces
something grounded in your own history rather than a generic template.

Works with **Claude**, **ChatGPT**, **Cursor**, **Windsurf**, **Gemini CLI**,
and any other MCP-compatible client.

## You need a free account

Every tool needs a connected Pacelab Intervals account — the workouts are
saved to *your* library, and the history is *your* history, so there is nothing
meaningful to do anonymously.

Create one in the app ([iOS](https://apps.apple.com/us/app/pacelab-intervals/id6758213350)
· [Android](https://play.google.com/store/apps/details?id=com.newbuildsoft.pacelabIntervals))
or directly on the sign-in screen that appears when you connect. It is free,
with no subscription for any of this.

## Server URL

```
https://pacelabintervals.com/mcp
```

Transport is **streamable HTTP**. Authentication is OAuth 2.0 — your client
discovers it automatically, opens a Pacelab sign-in page, and you approve the
connection there. No API keys to copy, no config file to hand-edit.

## Install

### Claude

Go to **Customize → Connectors → Add → Add custom connector**, paste the server
URL above, and complete the sign-in. Custom connectors are available on Free,
Pro and Max plans; on Team and Enterprise the same setting lives under
**Organization Settings → Connectors**.

Setup walkthrough: <https://pacelabintervals.com/claude>

### ChatGPT

**Settings → Connectors → Create**, then paste the server URL. Developer mode
may need to be enabled first under **Settings → Connectors → Advanced**.

Setup walkthrough: <https://pacelabintervals.com/chatgpt>

### Cursor

**Settings → MCP → Add new MCP server**, then add:

```json
{
  "mcpServers": {
    "pacelab-workout-creator": {
      "url": "https://pacelabintervals.com/mcp"
    }
  }
}
```

### Clients without remote MCP support

Some clients still only speak stdio. Those need a bridge, which requires
Node.js:

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

Use this only if your client cannot take a URL directly — connecting to the URL
is simpler and has no Node.js dependency. Config file locations:

| Client | Path |
|---|---|
| Gemini CLI | `~/.gemini/settings.json` |
| Windsurf | `~/.codeium/windsurf/mcp_config.json` |

## What you can do

**Build workouts** in any of Pacelab's formats, with per-exercise reps, work and
rest intervals, loads, tempo, and progressive rep or time schemes.

**Train from your history.** The assistant can read your completed sessions —
frequency, typical session length, which movements you have and have not been
doing, difficulty and exhaustion you reported — and program the next session
against it.

**Plan a week.** Schedule workouts to specific dates, read back what you already
have planned, and avoid double-booking a day. Scheduled sessions appear in the
app's calendar with reminders.

**Run a challenge.** Give a workout a deadline, share the link, and read the
leaderboard back. Ranking follows the format: fixed-window workouts (AMRAP,
Tabata, EMOM, timed) rank by total reps, because everyone's duration is
identical by construction; everything else ranks by time, fastest first.

## Tools

| Tool | |
|---|---|
| `create_workout` | Build a workout; optionally make it a challenge |
| `update_workout` | Replace a workout's structure |
| `schedule_workout` | Put a workout on a date and time |
| `list_scheduled_workouts` | Read the training calendar |
| `list_my_workouts` | Browse the library |
| `get_workout` | One workout in full |
| `get_workout_history` | Completed sessions, stats, movements trained |
| `get_challenge_results` | A challenge leaderboard |
| `get_workout_formats` | Reference for block types and valid values |

Six are read-only and three write; none delete anything.

## Example prompts

> "Create a 20-minute HIIT workout, bodyweight only, 4 Tabata blocks"

> "Look at my last month and build me something that hits what I've been skipping"

> "Build a 5-round kettlebell strength circuit with 6 exercises"

> "Make me an EMOM — 12 minutes, 3 exercises alternating"

> "Plan three sessions for next week and put them in my calendar"

> "Turn that into a challenge that ends Sunday, and show me the leaderboard"

## Supported formats

| Format | Description |
|--------|-------------|
| **Tabata** | Work/rest intervals × N rounds |
| **AMRAP** | As many rounds as possible in a time cap |
| **EMOM** | Every minute on the minute |
| **Circuit** | Timed exercises with rest between |
| **Rounds** | Rep-based rounds, no timers |
| **For Time** | Complete all reps as fast as possible |
| **Timed** | Each exercise has its own duration per round |

## Privacy

The connector reads and writes only your own Pacelab data, through Pacelab's
own API. It does not read your conversation history, your assistant's memory,
or your files.

You can disconnect at any time from your AI client's connector settings, and
revoke the connection server-side from your Pacelab account settings, which
invalidates all outstanding refresh tokens.

Privacy policy: <https://pacelabintervals.com/privacy>
Terms: <https://pacelabintervals.com/terms>
Support: <https://pacelabintervals.com/support>

## Get the app

- [Download on the App Store](https://apps.apple.com/us/app/pacelab-intervals/id6758213350)
- [Get it on Google Play](https://play.google.com/store/apps/details?id=com.newbuildsoft.pacelabIntervals)
