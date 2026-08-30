# Red Rangers — Committee & Squad Presentation

## Slide flow
1. **Cover**
2. **"Meet The Committee" intro** — title card listing every committee name/role before the reveals start
3. **Committee members**, one full-screen reveal per person (in `order`)
4. **"Meet The Squad" intro** — title card listing every player before the reveals start (only appears once `"players"` isn't empty)
5. **Players**, one full-screen reveal per person (in `order`)
6. **Outro**

## Folder structure
```
red-rangers-presentation/
├── index.html      ← the presentation (HTML/CSS/JS, no build step)
├── data.json        ← all editable content lives here
└── images/          ← every photo, referenced by path from data.json
```

## Running it
Browsers block `fetch()` from loading a local file when you just double-click
`index.html` (it'll show a "Can't load data.json" message). Run a tiny local
server from inside this folder instead:

```bash
python3 -m http.server 8000
```
then open **http://localhost:8000** in your browser.

No Python? Any of these also work:
- VS Code → install the "Live Server" extension → right-click `index.html` → "Open with Live Server"
- `npx serve .`
- Upload the whole folder to any static host (Netlify, Vercel, GitHub Pages, your club website) — it'll work with no server setup once it's actually online.

## Adding / editing committee members
Open `data.json`. Each entry in `"committee"` looks like this:

```json
{ "order": 7, "name": "Full Name", "role": "Their Title", "category": "Group Label", "image": "images/your-file.jpg" }
```

- `order` controls priority — lower numbers appear first. Renumber freely, gaps are fine.
- `image` is just a path to a file inside `images/`. Drop your photo in that folder and point to it.
- Leave `"name": ""` if you only want the role shown (used for the Organizer slide since no name was given).

## Adding players
`"players"` starts empty, showing a "Lineup Dropping Soon" placeholder. Add entries like:

```json
{ "order": 6, "name": "Player Name", "position": "Forward", "image": "images/players/name.jpg" }
```

- `order` controls reveal sequence — lower numbers appear first, same as committee.
- As soon as the array isn't empty, a "Meet The Squad" intro slide appears automatically,
  followed by one full-screen reveal slide per player (in order) — no code changes needed.
- `position` and `image` are optional. Since the current player images are already fully
  designed poster graphics (name/logo baked in), each one is shown edge-to-edge rather than
  cropped into a circle — swap in a plain headshot instead if you'd rather use the compact
  photo-grid card style.

## Navigation
Arrow keys / swipe / on-screen dots and arrows / play button for autoplay.
