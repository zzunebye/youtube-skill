---
name: youtube
description: YouTube Data API v3 for searching videos, getting channel info, video details, comments, playlists, liked videos, and subscriptions. Use when Codex needs to search YouTube, get video metadata, fetch channel statistics, list playlist items, retrieve comments, or access user's liked videos and subscriptions (OAuth required for personal data).
metadata: {"clawdbot":{"emoji":"📺","requires":{"env":["YOUTUBE_API_KEY"]}}}
---

# YouTube API v3 Skill

Use `yt` CLI for YouTube Data API v3 operations.

## Setup

### Basic (API Key only)
1. Get API key from [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Enable "YouTube Data API v3" in your project
3. Set environment variable:
```bash
export YOUTUBE_API_KEY="your-api-key"
```

### OAuth (for personal data access)
```bash
yt auth
```
Follow prompts to:
1. Enter OAuth Client ID & Secret (from Google Cloud Console → OAuth 2.0 Client IDs)
2. Authorize in browser
3. Token saved to `~/.config/yt-cli/token.json`

## Commands

### Public Data (API Key)

```bash
# Search
yt search "query" [--max 10] [--type video|channel|playlist] [--region KR]

# Video details
yt video <videoId> [--stats] [--comments]

# Channel info
yt channel <channelId|@handle> [--videos] [--playlists]

# Playlist items
yt playlist <playlistId> [--max 50]

# Comments
yt comments <videoId> [--max 20] [--replies]

# Trending
yt trending [--region KR|US|HK] [--category music|gaming|news]
```

### Personal Data (OAuth required)

```bash
# Liked videos
yt liked [--max 25]

# Subscriptions
yt subscriptions [--max 25] [--alpha]

# My playlists
yt my-playlists [--max 25]

# Watch history (not available via API)
yt history
```

## Output

All commands support `--json` for machine-readable output.

## Examples

```bash
# Search Korean cooking videos
yt search "korean cooking" --max 5 --region KR

# Get video with stats
yt video dQw4w9WgXcQ --stats

# Check my liked videos
yt auth  # first time only
yt liked --max 10

# List subscriptions alphabetically
yt subscriptions --alpha
```

## Rate Limits

YouTube API has quota limits (10,000 units/day default):
- Search: 100 units
- Other reads: 1-3 units
