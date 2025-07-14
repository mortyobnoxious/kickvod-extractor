# kickvod-extractor

A simple tool that extracts the HLS `master.m3u8` URL from any Kick.com VOD, including sub-only videos.

## How to Use

1. [**Download** `kickvod-extractor.html`](./kickvod-extractor.html) and open it in any modern browser.
2. Paste a Kick VOD URL (example: `https://kick.com/somechannel/videos/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`)
3. Click the **"Generate Master URL"** button.
4. The tool will display:
   - The direct `.m3u8` master URL
   - VOD metadata (title, duration, views, etc.)
   - Thumbnail and channel link
5. You can:
   - **Copy** the URL to clipboard to play it with a player like [MPV](https://mpv.io/) or [VLC](https://www.videolan.org/vlc/)
   - **Play** it directly in your browser using the built-in PlayHLS shortcut

Works with both public and **subscriber-only** VODs.

## How it works

1. Parses the username and VOD UUID from the given URL.
2. Queries Kick’s channel API and VOD API to find matching livestream or archive data.
3. Extracts thumbnail URL to find the session and segment IDs.
4. Combines these with the fixed AWS ID and VOD start time to reconstruct the master URL.

## Output format
https://stream.kick.com/ivs/v1/196233775518/{session_id}/{yyyy}/{MM}/{dd}/{HH}/{mm}/{segment_id}/media/hls/master.m3u8
