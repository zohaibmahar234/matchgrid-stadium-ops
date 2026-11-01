# Matchgrid · Aldmere Arena

A live 3D match-day operations dashboard for a fictional football stadium, built as a **single HTML file** with [Three.js](https://threejs.org) (loaded from a CDN). No build step, no backend.

**Live demo:** `https://<your-username>.github.io/<repo-name>/` (after enabling GitHub Pages, see below)

## What it does
- Night-time 3D stadium: two-tier bowl, roof ring, floodlights, pitch, LED boards, big screens, plaza, train stop, car park, ring road and city.
- Match-day simulation: fans arrive by train, car and road, pass security, queue at 4 gates (8 turnstiles each) and fill the stands block by block.
- Two teams (4-4-2), live ball, goals with net, fireworks, torches and crowd celebration.
- Operations dashboard: fans inside, gate waits, food orders, security screened, gate status, trend chart, incident log (CSV export), rule-based AI Ops Copilot.
- Scenarios: close a gate, train delay, rain, heightened security, fire-alarm evacuation, medical incident, crowd heatmap, one-click demo.

## Controls
| Key | Action |
|---|---|
| Drag / right-drag / wheel | Orbit / pan / zoom (pinch on touch) |
| Click | Select gate, stand block or player |
| `1` `2` `3` | Speed 1x / 4x / 16x |
| `F` | Floodlights |
| `G` / `M` | Goal for team CR7 / Messi |
| `S` | Security level |
| `E` | Fire alarm (evacuation) |
| `H` | Heatmap |
| `L` | Light: Clear / Night |
| `Q` | Quality High / Low |
| `R` | Reset camera |
| `Esc` | Deselect |

## Plug in real data
Open the browser console, or set a config **before** the page script runs:

```html
<script>window.MATCHGRID_CONFIG={capacity:45000,feedUrl:'wss://your-server/feed'}</script>
```

Push data at any time (this switches the dashboard from simulation to your numbers):

```js
Matchgrid.push({ inside: 30000, gates: { A: { wait: 9, open: 8, queue: 240 }, B: { wait: 2 } } })
Matchgrid.useSim() // back to the simulator
```

## Deploy on GitHub Pages
1. Create a new repository on GitHub (public).
2. Upload `index.html`, `README.md` and `.nojekyll` (Add file → Upload files → Commit).
3. Go to **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then Save.
4. After a minute your site is live at `https://<your-username>.github.io/<repo-name>/`.

Or with git:

```bash
git init && git add . && git commit -m "Matchgrid"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Notes
- Team and player names are fan-style labels only; no real logos or likenesses are used.
- The AI Ops Copilot is rule-based. It can be wired to an LLM API in `ask()`.
- Needs a WebGL-capable browser. If the frame rate drops, switch Quality to Low (`Q`).

## License
MIT
