# Tree Guides

A barebones, GPS-following tree map. Open the page, tap **Follow my GPS**, and see the trees around you
(name, Latin name, size, location). No server, no database: just a static page that reads a CSV.

## Files
- `index.html` – the whole app (Leaflet + OpenStreetMap base map, PapaParse for the CSV)
- `data/victoria.csv` – test dataset (City of Victoria, BC)

## CSV columns
`Name, Latin name, Tree type, Map colour, Where, Neighbourhood, Trunk width cm, Height m, Latitude, Longitude`
Latitude/Longitude must be decimal degrees (WGS84).

## Publish with GitHub Pages
Repo → Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
Your site appears at `https://<username>.github.io/<repo>/` (GPS requires HTTPS, which Pages provides).

## Test locally
`python3 -m http.server` in this folder, then open http://localhost:8000
(Tap the map to simulate a position if you're not near the trees.)
