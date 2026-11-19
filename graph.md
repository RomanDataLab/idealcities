# Ideal City Masterplans — Project Documentation

## Repository

| Item | Value |
|------|-------|
| GitHub | `git@github.com:RomanDataLab/idealcities.git` |
| Branch | `main` |
| Production URL | https://idealcities.vercel.app |
| Vercel project | `idealcities` (team `Herman Di's projects`) |
| GA4 Stream ID | `RDT-IDS-29` |
| GA4 Measurement ID | `G-2E348VSQ5G` |
| GTM Container | `GTM-538VHG6H` |

---

## Architecture

```
idealcities/                             # Full workspace (pushed to GitHub)
|
|-- public/                              # >>> Static web app (deployed to Vercel) <<<
|   |-- index.html                       # Main SPA (grid of interactive Leaflet maps)
|   +-- cities-data.js                   # City definitions: coordinates, bbox, descriptions
|
|-- vercel.json                          # Vercel static deploy: outputDirectory = public
|-- README.md                            # Project overview and city list
+-- graph.md                             # This file

# Local only (gitignored): server.js, package.json (Express dev server on port 3000), *.mp4
```

---

## Frontend Modules

| Module | Purpose |
|--------|---------|
| `index.html` | Main SPA: creates a 3-column grid of Leaflet maps, one per city. Fetches building/green/water data from Overpass API and renders as polygons/polylines on dark basemap |
| `cities-data.js` | Array of city objects with name, lat/lon, bbox, zoom, and description for each ideal city masterplan |

---

## Libraries + Tools

| Library | Version | Usage |
|---------|---------|-------|
| Leaflet | v1.9.4 | Map rendering (CDN) |
| CartoDB Dark Matter | - | Dark basemap tiles (requires `?key=` param) |
| Overpass API | - | OpenStreetMap data queries for buildings, parks, water |

---

## Keys + Environment

| Key | Where | Notes |
|-----|-------|-------|
| GA4 `G-2E348VSQ5G` | Hardcoded in HTML head | Shared across all RDT projects |
| GTM `GTM-538VHG6H` | Hardcoded in HTML head | Google Tag Manager container |
| CARTO basemap `cb1_3n3g_1_7e65dbf86a711155a8049b57` | `?key=` param in tile URL, `public/index.html` | Free tier, 5M tile requests/month. Since Aug 2026 CARTO serves watermarked placeholder tiles without `key`. Source: `G:\My Drive\J_Projects_Archive\config\config_cartobasemap.json`. Param name is `key`, not `api_key` |

---

## Deploy Workflow

```bash
# 1. Local dev (optional): Express server in server.js (gitignored, local only)
npm start
# -> http://localhost:3000
# Or open public/index.html directly

# 2. Commit and push (Vercel auto-deploys static from public/)
git add -A
git commit -m "description"
git push origin main

# Production: https://idealcities.vercel.app (static, no server)
```

---

## Data Sources

| Source | Content |
|--------|---------|
| [OpenStreetMap](https://www.openstreetmap.org) | Buildings, parks, water bodies via Overpass API |
| [CARTO](https://carto.com) | Dark Matter basemap tiles |
