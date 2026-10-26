# Tree Guides – London, Ontario

A barebones, GPS-following tree map. Open the page, tap **Follow my GPS**, and see the trees around you.
No server, no database: just a static page that reads CSV files.

## Files
- `index.html` – the whole app (Leaflet + OpenStreetMap base map, PapaParse for the CSVs)
- `data/london/*.csv` – the City of London tree locations (872,044 trees), split into 0.05° tiles
  so the page only downloads the few files near you. Columns: `id, lat, lon`.

## Data notes
Source file used UTM zone 17N (EPSG:26917) metres; converted to WGS84 lat/lon. The source has no species
information yet - that's the next step (a separate species/guide CSV matched by tree `id`).

## Publish with GitHub Pages
Repo → Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
Site: `https://<username>.github.io/<repo>/` (GPS requires HTTPS, which Pages provides).

## Test locally
`python3 -m http.server` in this folder, then open http://localhost:8000
