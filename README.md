# SP Neighborhood Map — Nubank Relocation Guide

An interactive choropleth map of São Paulo's 96 official districts, scored and colored by criteria relevant to Nubank employees relocating to the city.

## Quick Start

```bash
cd sp-neighborhood-map
python3 -m http.server 8080
# open http://localhost:8080
```

## Features

- **Choropleth map** — districts colored red → yellow → green by composite score
- **Weight sliders** — reprioritize criteria in real time (distance to Nubank, safety, walkability, rent, etc.)
- **Hover tooltip** — district name and composite score on hover
- **Click popup + sidebar** — full breakdown of individual scores per district
- **Load CSV** — drop in an edited CSV to update all scores instantly
- **Download CSV** — export the current dataset to edit in Excel or Numbers

## Customizing Scores

Edit `data/neighborhoods.csv` (open in any spreadsheet app):

| Column | Range | Meaning |
|--------|-------|---------|
| `district` | text | Must match GeoJSON district name |
| `distance_to_nubank` | 1–10 | 10 = very close to Pinheiros |
| `safety` | 1–10 | 10 = very safe |
| `walkability` | 1–10 | 10 = extremely walkable |
| `traffic` | 1–10 | 10 = very low traffic |
| `rent_price` | 1–10 | 10 = very affordable |
| `buy_price` | 1–10 | 10 = very affordable to buy |
| `green_spaces` | 1–10 | 10 = abundant parks |
| `nightlife` | 1–10 | 10 = vibrant scene |
| `family_friendly` | 1–10 | 10 = excellent for families |
| `notes` | text | Free-text notes shown in sidebar |

Districts not in the CSV default to **5** for all criteria.

After editing, use the **Load CSV** button in the sidebar to apply changes.

## Data Sources

- **GeoJSON**: [codigourbano/distritos-sp](https://github.com/codigourbano/distritos-sp) (São Paulo's 96 official districts)
- **Scores**: Manually curated based on neighborhood research; your mileage may vary
- **Map tiles**: CartoDB Dark Matter (OpenStreetMap data)

## Tech Stack

- [Leaflet.js](https://leafletjs.com/) — map rendering
- [chroma.js](https://gka.github.io/chroma.js/) — color scale
- [PapaParse](https://www.papaparse.com/) — CSV parsing
- Vanilla HTML/CSS/JS — no build step required
