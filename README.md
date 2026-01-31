# 📺 YouTube Skill for OpenClaw

A YouTube Data API v3 skill for OpenClaw/Clawdbot. Search videos, get channel info, check trending, and access your liked videos.

## Features

- 🔍 **Search** - Find videos, channels, playlists
- 📊 **Trending** - Check trending videos by region
- 📺 **Channel Info** - Get channel stats and recent videos
- ❤️ **Liked Videos** - Access your liked videos (OAuth)
- 📋 **Playlists** - List playlist items
- 💬 **Comments** - Get video comments

## Installation

### 1. Clone this repo
```bash
git clone https://github.com/YOUR_USERNAME/youtube-skill.git
```

### 2. Add to your PATH
```bash
chmod +x youtube-skill/scripts/yt
ln -s $(pwd)/youtube-skill/scripts/yt /usr/local/bin/yt
```

### 3. Set up API Key
Get your API key from [Google Cloud Console](https://console.cloud.google.com/apis/credentials) and enable YouTube Data API v3.

```bash
export YOUTUBE_API_KEY="your-api-key"
```

### 4. (Optional) OAuth Setup
For accessing personal data like liked videos:
```bash
yt auth
```

## Usage

```bash
# Search videos
yt search "korean cooking" --max 5

# Get trending in Korea
yt trending --region KR

# Channel info
yt channel @MrBeast --videos

# Video details with stats
yt video dQw4w9WgXcQ --stats --comments

# Your liked videos (requires OAuth)
yt liked --max 10

# Your subscriptions
yt subscriptions --alpha
```

## Commands

| Command | Description | Auth |
|---------|-------------|------|
| `search` | Search YouTube | API Key |
| `video` | Get video details | API Key |
| `channel` | Get channel info | API Key |
| `playlist` | List playlist items | API Key |
| `comments` | Get video comments | API Key |
| `trending` | Get trending videos | API Key |
| `liked` | Get liked videos | OAuth |
| `subscriptions` | Get subscriptions | OAuth |
| `my-playlists` | Get your playlists | OAuth |

## Output

All commands support `--json` for machine-readable output.

## Rate Limits

YouTube API has quota limits (10,000 units/day default):
- Search: 100 units
- Other reads: 1-3 units

## License

MIT
