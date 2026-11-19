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
|-- public/                              # >>> Static web app (served by Express) <<<
|   |-- index.html                       # Main SPA (grid of interactive Leaflet maps)
|   +-- cities-data.js                   # City definitions: coordinates, bbox, descriptions
|
|-- server.js                            # Express server (port 3000): static files
|-- vercel.json                          # Vercel routing: all requests -> server.js (@vercel/node)
|-- package.json                         # Node deps: express
|-- README.md                            # Project overview and city list
+-- graph.md                             # This file
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
| Express | ^4.18 | Local + Vercel server, static file serving |
| Leaflet | v1.9.4 | Map rendering (CDN) |
| CartoDB Dark Matter | - | Dark basemap tiles |
| Overpass API | - | OpenStreetMap data queries for buildings, parks, water |

---

## Keys + Environment

| Key | Where | Notes |
|-----|-------|-------|
| GA4 `G-2E348VSQ5G` | Hardcoded in HTML head | Shared across all RDT projects |
| GTM `GTM-538VHG6H` | Hardcoded in HTML head | Google Tag Manager container |
| CARTO basemap tiles | None | `basemaps.cartocdn.com` is a public keyless CDN; verified HTTP 200 with no `api_key` param. No CARTO API key exists or is needed |

---

## Deploy Workflow

```bash
# 1. Start local dev server
npm start
# -> http://localhost:3000

# 2. Commit and push (Vercel auto-deploys from GitHub)
git add -A
git commit -m "description"
git push origin main

# Production: https://idealcities.vercel.app
```

---

## Data Sources

| Source | Content |
|--------|---------|
| [OpenStreetMap](https://www.openstreetmap.org) | Buildings, parks, water bodies via Overpass API |
| [CARTO](https://carto.com) | Dark Matter basemap tiles |
