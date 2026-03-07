# VibeCheck — Landing Page Brief

## What is VibeCheck?

VibeCheck is a **macOS menu bar app** that tracks how much you use AI coding tools and ranks you on a global leaderboard. It measures your "AI Nativeness" — how deeply you've integrated AI into your development workflow — and gives you a score from 0 to 1000.

Think of it as **Screen Time, but for AI coding tools**. It sits quietly in your menu bar, watches your AI usage in the background, and gives you a live score + leaderboard position.

## Tagline Options

- "How AI-native are you?"
- "Track your AI coding habits. Compete with friends."
- "The leaderboard for AI-native developers."

## The Problem

Every developer is using AI coding tools now — Claude Code, Cursor, Claude Desktop — but nobody knows how they stack up. Are you actually using AI effectively, or just scratching the surface? There's no way to measure it, no way to compare, and no way to flex.

## The Solution

VibeCheck automatically tracks your AI coding tool usage and computes an **AI Nativeness Score** (0–1000) based on 7 components:

| Component | Max Points | What It Measures |
|-----------|-----------|------------------|
| Tokens | 250 | Total tokens consumed (input + output) |
| Sessions | 150 | Number of coding sessions |
| Streak | 200 | Consecutive days of AI usage |
| Hours | 100 | Active hours spent with AI tools |
| Diversity | 100 | Number of different AI tools used |
| Power Usage | 100 | Advanced features: MCP tools, skills, agents |
| Recency | 100 | How recently you've been active |

## Supported Tools

- **Claude Code** (CLI) — Full token-level tracking via JSONL logs
- **Cursor** — Session detection via process monitoring
- **Claude Desktop** — Session + log parsing

More tools coming soon (Windsurf, GitHub Copilot, etc.)

## Key Features

### 1. Global Leaderboard
See where you rank against other developers worldwide. The leaderboard shows everyone's score, streak, and which tools they use.

### 2. Personal Stats Dashboard
- Total tokens consumed (input/output breakdown)
- Session count and active hours
- Current streak (consecutive days)
- Per-tool breakdown (how much you use each AI tool)
- Power badges (MCP tools, skills, agent invocations)

### 3. Menu Bar Native
- Lives in your macOS menu bar — always one click away
- No dock icon, no window clutter
- Auto-launches at login (optional)
- Updates in real-time as you code

### 4. Privacy-First
- All usage data is computed locally on your machine
- Only your score and username are synced to the leaderboard
- No code, prompts, or conversation content is ever collected
- Your raw usage data never leaves your machine

## Design

The app uses a **"Newsprint Dark"** design system:
- Pure black background (#0a0a0a)
- High contrast cream text (#E8E6E1)
- Editorial red accents (#CC0000)
- Zero border radius (sharp corners everywhere)
- Monospace font for all data/numbers
- Serif font (Georgia) for display headings
- Uppercase tracked labels

The aesthetic is intentionally editorial and brutalist — like a data-dense financial terminal meets a newspaper front page.

## Technical Details

- **Platform**: macOS (Apple Silicon native, Intel coming soon)
- **Framework**: Electron + React + TypeScript + Tailwind CSS v4
- **Local DB**: sql.js (SQLite compiled to WASM, runs entirely in-process)
- **Backend**: Supabase (leaderboard sync only)
- **Data Collection**: Chokidar file watching (Claude Code JSONL logs), process monitoring (Cursor/Claude Desktop), log parsing
- **Size**: ~107MB DMG

## How It Works (Technical)

1. **Install & Launch** — Drag to Applications, appears in menu bar
2. **Pick a Username** — Simple text input, becomes your leaderboard identity
3. **Automatic Tracking Begins** — VibeCheck detects installed AI tools and starts watching:
   - Claude Code: Reads `~/.claude/projects/` JSONL files for token counts, tool usage, session data
   - Cursor: Monitors process presence, tracks session duration
   - Claude Desktop: Monitors process + parses `~/Library/Logs/Claude/main.log`
4. **Score Computed** — Every 5 minutes, aggregates last 30 days of data into the 7-component score
5. **Leaderboard Sync** — Score + username pushed to Supabase; full leaderboard pulled down

## Installation (Current — Unsigned Beta)

Since the app is not yet code-signed:
1. Download the DMG
2. Drag VibeCheck to Applications
3. Right-click → Open (bypasses Gatekeeper)
4. If blocked: System Settings → Privacy & Security → Open Anyway
5. If still blocked: Run `xattr -cr /Applications/VibeCheck.app` in Terminal

## Target Audience

- Developers who are heavy users of AI coding tools
- Early adopters and power users of Claude Code, Cursor
- People who like quantified self / gamification
- Developer communities, teams, and friend groups who want to compete

## Competitive Landscape

There is no direct competitor. The closest things are:
- **WakaTime** — tracks coding time, but doesn't measure AI usage
- **Screen Time** — measures app usage, but too generic
- **GitHub contribution graphs** — measures commits, not AI usage

VibeCheck is the first tool specifically designed to measure and gamify AI coding tool adoption.

## Future Roadmap

- GitHub OAuth for identity + avatars
- Team/org leaderboards
- Weekly email digests
- More tool integrations (Windsurf, GitHub Copilot, Cody, etc.)
- Windows + Linux support
- Browser extension for web-based AI tools
- Achievement badges and milestones
- Historical score trends and charts

## Brand

- **Name**: VibeCheck
- **App ID**: com.vibecheck.app
- **Icon**: Gradient circle (placeholder — needs proper design)
- **Tone**: Playful but data-driven. "Competitive quantified self for AI developers."

## Landing Page Structure (Suggested)

1. **Hero** — Big tagline, app screenshot/mockup, download button
2. **How It Works** — 3-step visual (Install → Track → Compete)
3. **Features** — Leaderboard, Stats, Privacy cards
4. **Scoring Breakdown** — The 7 components table
5. **Supported Tools** — Logos/icons for Claude Code, Cursor, Claude Desktop
6. **Download CTA** — Platform badges, system requirements
7. **Footer** — GitHub link, contact, "Built with AI" badge

## Assets Needed for Landing Page

- App screenshots (leaderboard view, profile view, settings)
- App icon (high-res PNG)
- Tool logos (Claude Code, Cursor, Claude Desktop)
- Open Graph image for social sharing
