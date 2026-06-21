# SATURDAYBOX

A retro CRT "TV" that broadcasts cartoons on a shared, wall-clock-synced schedule —
every visitor sees the same moment, like real broadcast TV. Channel surfing, an
on-screen TV guide, analog-static transitions, volume, power, and fullscreen.

Static single-file site (`index.html`). Video + schedule live in a public
Cloudflare R2 bucket.

## Configure
Edit the CONFIG block at the top of the `<script>` in `index.html`:

- `BASE_URL` — your public R2 base URL (no trailing slash)
- `manifest.json` (in the bucket) lists clips:

```json
[
  { "title": "Saturday Morning Cartoons", "file": "cn-saturday-morning.mp4", "duration": 6724, "channel": "02" }
]
```

`duration` is in **seconds** and must be accurate for sync. Clips sharing a
`channel` loop together; new channel numbers become new surfable channels.

## Controls
P power · ←/→ channel · ↑/↓ volume · M mute · G guide · F fullscreen
(touch-friendly on mobile).

## Deploy
Static — deploy the folder to Vercel (no build step).
