# Pacelab Workout Creator — Claude Plugin

Generate structured interval workouts with Claude and import them directly into [Pacelab Intervals](https://pacelabintervals.com). Describe your goal, get a complete workout with blocks and exercises, and open it in the app with one tap.

## Install

Add this to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "pacelab-workout-creator": {
      "type": "http",
      "url": "https://pacelabintervals.com/mcp"
    }
  }
}
```

Restart Claude Desktop. The Pacelab tools will appear in the toolbar.

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
