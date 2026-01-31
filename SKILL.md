---
name: youtube
description: YouTube Data API v3 for searching videos, getting channel info, video details, comments, and playlists. Use when Codex needs to search YouTube, get video metadata, fetch channel statistics, list playlist items, or retrieve comments.
metadata: {"clawdbot":{"emoji":"📺","requires":{"env":["YOUTUBE_API_KEY"]}}}
---

# YouTube API v3 Skill

Use `yt` CLI for YouTube Data API v3 operations.

## Setup

1. Get API key from [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Enable "YouTube Data API v3" in your project
3. Set environment variable:
```bash
export YOUTUBE_API_KEY="your-api-key"
```

## Commands

### Search Videos
```bash
yt search "query" [--max 10] [--type video|channel|playlist]
```

### Get Video Details
```bash
yt video <videoId> [--comments] [--stats]
```

### Get Channel Info
```bash
yt channel <channelId|@handle> [--videos] [--playlists]
```

### List Playlist Items
```bash
yt playlist <playlistId> [--max 50]
```

### Get Comments
```bash
yt comments <videoId> [--max 20] [--replies]
```

### Get Trending
```bash
yt trending [--region KR|US|HK] [--category music|gaming|news]
```

## Output

All commands support `--json` for machine-readable output.

## Examples

```bash
# Search for cooking videos
yt search "korean cooking" --max 5

# Get video stats
yt video dQw4w9WgXcQ --stats

# Get channel videos
yt channel @MrBeast --videos --max 10

# Get trending in Korea
yt trending --region KR
```

## Rate Limits

YouTube API has quota limits (10,000 units/day default). Search costs 100 units, other reads cost 1-3 units.
