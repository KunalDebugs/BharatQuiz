# Bharat Quiz — States of India

A single-page, no-build quiz site covering all 28 Indian states (224 questions): search or filter states by region, choose History / Geography / Mixed, pick a timer (1/2/3/5/10 min), and answer against the clock.

Everything lives in one file — `index.html` — with no dependencies to install and no build step, so it deploys to Vercel in under a minute.

**Interactive features:** live search + region chips over the state grid, a circular countdown ring, running score/accuracy/streak stats, keyboard shortcuts (`1`–`4` to answer), a personal-best tracker per state/category/duration saved in the browser (`localStorage`), a full answer-review list after each round, a "copy result" button, and a confetti celebration for strong scores.

## Deploy to Vercel (pick one)

**Option A — Vercel CLI (fastest)**
```bash
npm i -g vercel      # if you don't have it already
cd india-state-quiz
vercel               # follow the prompts, accept the defaults
vercel --prod        # promote to your production URL
```
Vercel will detect it as a static site automatically — no framework, no build command needed.

**Option B — Drag and drop**
1. Go to https://vercel.com/new
2. Choose "Deploy" → drag the `india-state-quiz` folder onto the page (or the zipped folder).
3. Leave the build settings blank/default and click Deploy.

**Option C — GitHub**
1. Push this folder to a new GitHub repo.
2. In Vercel, "Add New Project" → import the repo.
3. Framework preset: **Other** (static). No build command, no output directory override needed.
4. Deploy.

## Editing content

- All questions live in the `QUESTIONS` object near the top of the `<script>` tag in `index.html`. Each state is `{ region: "...", items: [ {c, q, o, a}, ... ] }`, where `c` is the category (`History`/`Geography`), `q` is the question, `o` is an array of four options, and `a` is the index of the correct option.
- To add a new state, add a new key with the same shape; it appears automatically in the search/region filters and the grid.
- Regions used for filtering: North, South, East, West, Central, Northeast — set per state via the `region` field.
- To change timer options, edit the `DURATIONS` array (values are in minutes).
- Personal bests are stored per browser via `localStorage`, keyed by state + category + duration — clearing site data resets them.

## Notes

- Fonts (Fraunces / Inter) load from Google Fonts via CDN — works fine on Vercel, no local font files needed.
- No backend, no environment variables, no database — it's fully static and works offline once loaded.
