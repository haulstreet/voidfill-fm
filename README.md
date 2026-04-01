# VOIDFILL.fm

> Underground radio for independent and emerging artists — powered by AI.

Live demo: [voidfill.fm](https://your-username.github.io/voidfill-fm)

---

## What it is

VOIDFILL.fm is a live underground music radio station built as a single-page web app. It features real SoundCloud and YouTube embeds alongside four AI-powered features built on the Anthropic Claude API.

## Features

- **SoundCloud player** — embedded live rotation of underground tracks
- **YouTube sessions** — full video sets from featured artists
- **Artist directory** — cards with links to Spotify, SoundCloud, YouTube, and Apple Music
- **AI artist bios** — Claude generates atmospheric bios on demand for each artist
- **AI mood classifier** — describe your vibe, get a dark/chill/hype/raw breakdown with animated bars
- **AI song recommendations** — natural language track discovery powered by Claude
- **AI DJ chat** — full conversation with DJ FREQ, an AI DJ persona with deep underground music knowledge
- **Fully responsive** — desktop two-column layout, mobile bottom nav with slide-in DJ panel

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Fonts | Syne (display), Space Mono (mono), DM Sans (body) via Google Fonts |
| AI | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Embeds | SoundCloud Widget API, YouTube IFrame API |
| Hosting | GitHub Pages |

## Project structure

```
voidfill-fm/
├── index.html       # entire app — single file, zero dependencies
└── README.md
```

## Running locally

No build step needed. Just open `index.html` in your browser:

```bash
git clone https://github.com/your-username/voidfill-fm.git
cd voidfill-fm
open index.html
```

> **Note:** AI features require an Anthropic API key. See setup below.

## API key setup

The app calls the Anthropic API directly from the browser. This is fine for portfolio/demo use. For a production deployment, move API calls to a serverless backend to protect your key.

**Quick demo setup (client-side):**

In `index.html`, find every `fetch("https://api.anthropic.com/v1/messages"` call and add your key to the headers:

```javascript
headers: {
  "Content-Type": "application/json",
  "x-api-key": "YOUR_API_KEY_HERE",
  "anthropic-version": "2023-06-01"
}
```

**Production setup (recommended):**

Deploy a lightweight serverless function on Vercel or Netlify that proxies the Anthropic API call, keeping your key server-side.

## Deploying to GitHub Pages

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, select **Deploy from a branch**
4. Choose `main` branch, `/ (root)` folder
5. Click **Save** — your site will be live at `https://your-username.github.io/voidfill-fm`

## Adding real artists

In `index.html`, find the `ARTISTS` array and replace the placeholder entries:

```javascript
const ARTISTS = [
  {
    name: "Artist Name",
    genre: "GENRE",
    av: "🎵",                          // emoji avatar
    col: "#ff2d78",                    // accent color
    links: {
      sc: "https://soundcloud.com/...",
      sp: "https://open.spotify.com/...",
      yt: "https://youtube.com/...",
      am: "https://music.apple.com/..."
    },
    mood: "dark"                       // dark | chill | hype | raw
  }
]
```

## License

MIT — use freely, credit appreciated.
