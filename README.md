# Tree Guides – London, Ontario

A barebones, GPS-following tree map. Open the page, tap **Follow my GPS**, and see the trees around you:
common name, scientific name, trunk diameter, street address and where the tree is (boulevard, park, etc.).
No server, no database: just a static page that reads CSV files.

## Files
- `index.html` – the whole app (Leaflet + OpenStreetMap base map, PapaParse for the CSVs)
- `data/species.json` – one entry per species: scientific name, common name, tree count, fun fact, check flag
- `data/trees/*.csv` – 198,175 trees split into 0.05° map tiles, so the page only downloads the few files near you

## Tree CSV columns
`id, lat, lon, sp, dia, addr, loc`

| Column | Meaning |
|---|---|
| `id` | City GlobalID (unique per tree, braces removed) |
| `lat`, `lon` | Decimal degrees (WGS84), converted from UTM zone 17N (EPSG:26917) |
| `sp` | Row number in `species.json` (0 = first entry) |
| `dia` | Trunk diameter in cm (blank when the city value was 0 or a 999 placeholder) |
| `addr` | Street number + street |
| `loc` | Boulevard, Park, Golf, Boundary, Private, Municipal, Island |

## Data notes
- Source: City of London forestry inventory, cleaned in Excel (6 rows without coordinates removed).
- About 1,230 trees have a scientific name that disagrees with their common name in the city data.
  Their species entries have `"chk":1` and the popup shows a warning.
- The fun-fact text came from the cleaned spreadsheet and is only present for rarer species.
- Species whose scientific name was missing show the common name only.

## Publish with GitHub Pages
Repo → Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
Site: `https://<username>.github.io/<repo>/` (GPS requires HTTPS, which Pages provides).

## Test locally
`python3 -m http.server` in this folder, then open http://localhost:8000
(Tap the map to simulate a position if you're not in London.)
