# VOIDFILL.fm

> Live underground radio — 6 free streams, AI DJ, mood classifier, and artist discovery. No backend. No ads. No account needed.

**Live site:** [haulstreet.github.io/voidfill-fm](https://haulstreet.github.io/voidfill-fm)

---

## What it is

VOIDFILL.fm is a live underground music radio station built as a single-page web app. It streams real 24/7 audio from SomaFM alongside four AI-powered features built on the Groq API (free tier).

---

## Features

### Live Radio
- 6 real SomaFM streams — free, 24/7, no ads, no account needed
- Auto-retry across backup servers if a stream drops
- Animated waveform and vinyl that react to playback state
- Volume control with stream selector

### Streams
| Channel | Vibe |
|---|---|
| Dark Zone | Industrial · EBM · Dark Electronic |
| Groove Salad | Ambient · IDM · Downtempo |
| Drone Zone | Atmospheric · Experimental · Minimal |
| Ill Street Blues | Grimy Hip-Hop · Underground Beats |
| Suburbs of Goa | Psychedelic · Tribal · Global Bass |
| Deep Space One | Cosmic · Deep Ambient |

### AI Features (powered by Groq — free)
- **AI Artist Bios** — generates atmospheric, cryptic bios for featured artists on demand
- **Mood Classifier** — describe your vibe, get a dark/chill/hype/raw breakdown with animated bars and a stream recommendation
- **Song Recommendations** — natural language track discovery for underground music
- **AI DJ Chat** — full conversation with DJ FREQ, an AI DJ persona with deep underground music knowledge

### Content
- Underground live sets and mixes embedded from YouTube
- Artist directory with links to Spotify, SoundCloud, YouTube, and Apple Music
- Fully responsive — desktop two-column layout, mobile bottom nav with slide-in DJ panel

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Fonts | Syne · Space Mono · DM Sans via Google Fonts |
| AI | Groq API — `llama-3.3-70b-versatile` (free tier) |
| Audio | SomaFM live MP3 streams via HTML5 `<audio>` |
| Video | YouTube IFrame embeds |
| Hosting | GitHub Pages |

---

## Project structure

```
voidfill-fm/
├── index.html    ← entire app — single file, zero dependencies
└── README.md
```

No build step. No framework. No `node_modules`. Just one HTML file.

---

## Running locally

```bash
git clone https://github.com/haulstreet/voidfill-fm.git
cd voidfill-fm
open index.html
```

Audio streams load directly from SomaFM servers — no local server needed. AI features require a Groq API key (see below).

---

## API key setup

1. Sign up free at [console.groq.com](https://console.groq.com) — no credit card needed
2. Go to **API Keys** → **Create API Key** → copy it
3. Open `index.html` and find this line near the top of the `<script>`:

```javascript
const GROQ_API_KEY = "YOUR_GROQ_API_KEY_HERE";
```

4. Replace `YOUR_GROQ_API_KEY_HERE` with your key
5. Save and push — all four AI features will work immediately

> The key appears once and controls all AI features (bios, mood classifier, recommendations, DJ chat).

---

## Deploying changes

The easiest way to edit without leaving your browser:

1. Go to your GitHub repo
2. Press the `.` key — this opens **github.dev** (VS Code in the browser)
3. Edit `index.html` directly
4. Click the Source Control icon → add a commit message → **Commit & Push**
5. GitHub Pages auto-deploys within ~60 seconds

---

## Adding real artists

Find the `ARTISTS` array in `index.html` and replace the placeholder entries:

```javascript
const ARTISTS = [
  {
    name:  "Artist Name",
    genre: "GENRE",
    av:    "🎵",                              // emoji avatar
    col:   "#ff2d78",                         // accent colour (hex)
    links: {
      sc: "https://soundcloud.com/artist",
      sp: "https://open.spotify.com/artist/...",
      yt: "https://youtube.com/@artist",
      am: "https://music.apple.com/artist/..."
    },
    mood: "dark"                              // dark | chill | hype | raw
  }
]
```

Remove any `links` keys you don't have — only the ones present will render as buttons.

---

## Adding YouTube sets

Find the YouTube tab in `index.html` and add or replace `<div class="yt-card">` blocks:

```html
<div class="yt-card">
  <div class="yt-meta">
    <div>
      <div class="yt-title">SET TITLE HERE</div>
      <div class="yt-artist">ARTIST · GENRE</div>
    </div>
    <span class="mood-tag mood-dark">DARK</span>
  </div>
  <iframe width="100%" height="200"
    src="https://www.youtube.com/embed/VIDEO_ID?controls=1&modestbranding=1&rel=0"
    allowfullscreen loading="lazy"></iframe>
</div>
```

Replace `VIDEO_ID` with the 11-character ID from any YouTube URL.

---

## License

MIT — free to use, fork, and build on. Credit appreciated but not required.

---

*Built with [Claude](https://claude.ai)*
