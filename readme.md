# FlexTheGrind — Landing Page

## What is FlexTheGrind?

FlexTheGrind is a **macOS & Windows menu bar app** that tracks how much you use AI coding tools and ranks you on a global leaderboard. It measures your "AI Nativeness" — how deeply you've integrated AI into your development workflow.

Think of it as **Screen Time, but for AI coding tools**. It sits quietly in your menu bar, watches your AI usage in the background, and gives you a live score + leaderboard position.

## Tagline

- "How AI-native are you?"
- "Track your AI coding habits. Compete with friends."
- "The leaderboard for AI-native developers."

## League System

Your score places you into a league. Higher score = higher league.

| League | Score Range | Badge |
|--------|-----------|-------|
| Bronze | 0 – 399 | bronze.png |
| Silver | 400 – 799 | silver.png |
| Gold | 800 – 1399 | gold.png |
| Diamond | 1400 – 1999 | diamond.png |
| Titan | 2000 – 2799 | titan.png |
| Legend | 2800+ | king.png |

## Supported Tools

- **Claude Code** (CLI) — Full token-level tracking via JSONL logs
- **Cursor** — Session detection via process monitoring
- **Claude Desktop** — Session + log parsing

## Key Features

### 1. Global Leaderboard
See where you rank against other developers worldwide. The leaderboard shows scores, streaks, league badges, and which tools each developer uses. Rows shuffle live to simulate real-time activity.

### 2. Real-Time Stats
- Total tokens consumed (input/output breakdown)
- Session count and active hours
- Current streak (consecutive days)
- Per-tool breakdown
- League tier and badge

### 3. Menu Bar Native
- Lives in your macOS menu bar / Windows system tray
- No dock icon, no window clutter
- Auto-launches at login
- Updates in real-time as you code

### 4. Privacy-First
- All usage data is computed locally on your machine
- Only your score and username are synced to the leaderboard
- No code, prompts, or conversation content is ever collected
- Your raw usage data never leaves your machine

## Site Structure

```
/                  → index.html (landing page)
/download/         → download/index.html (OS-detecting download page, auto-starts download)
/privacy/          → privacy/index.html (privacy policy)
```

## Design

- **Fonts**: Oswald (headings), Roboto (body), JetBrains Mono (code/data elements)
- **Colors**: Green primary (#5CB832), dark secondary (#2D2D2D)
- **Aesthetic**: Developer tool meets competitive leaderboard — monospace accents, terminal-style path headers (`~/flexthegrind/leaderboard`), blinking cursor elements, kebab-case tool names
- **Badge assets**: `assets/badges/` — bronze.png, silver.png, gold.png, diamond.png, titan.png, king.png
- **Favicon**: diamond.png badge (assets/favicon-16.png, assets/favicon-32.png, assets/apple-touch-icon.png)

## Technical Details

- **Platforms**: macOS (Apple Silicon), Windows
- **Framework**: Electron + React + TypeScript + Tailwind CSS v4
- **Local DB**: sql.js (SQLite compiled to WASM)
- **Backend**: Supabase (leaderboard sync only)
- **Data Collection**: File watching (Claude Code JSONL logs), process monitoring (Cursor/Claude Desktop), log parsing

## Download

- **macOS**: `VibeCheck_0.1.0_aarch64.dmg` via GitHub Releases
- **Windows**: `FlexTheGrind_0.1.0_x64-setup.exe` via GitHub Releases
- The `/download/` page auto-detects OS and starts the download automatically

## Installation (Unsigned Beta)

Since the app is not yet code-signed:
1. Download the DMG/EXE from the download page
2. macOS: Drag to Applications → Right-click → Open (bypasses Gatekeeper)
3. If blocked: System Settings → Privacy & Security → Open Anyway
4. If still blocked: Run `xattr -cr /Applications/VibeCheck.app` in Terminal

## Brand

- **Name**: FlexTheGrind
- **Favicon**: Diamond badge crystal
- **Tone**: Developer-focused, competitive but not overly gamified. Terminal aesthetic with monospace data elements.
- **Built with**: October.dev
