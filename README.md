# PHES Site Explorer

An interactive, single-file web dashboard for visualizing and exploring Pumped Hydro Energy Storage (PHES) candidate sites produced by the [ANU RE100 PHES Searching](https://github.com/ANU-RE100/PHES_Searching) pipeline.

![ANU RE100](https://img.shields.io/badge/ANU-RE100-00e5a0?style=flat-square) ![License](https://img.shields.io/badge/license-GPL--3.0-blue?style=flat-square) ![No Backend](https://img.shields.io/badge/backend-none-lightgrey?style=flat-square)

---

## Overview

The PHES Searching software (C++/Python) processes Digital Elevation Models (DEMs) to identify viable pumped hydro sites. This dashboard provides a polished frontend to browse, filter, and analyse those results — no server required.

Load your own CSV output from the PHES Searching pipeline, or explore the built-in global demo dataset covering 100+ sites across 50+ countries.

---

## Features

- **Interactive Map** — Global Leaflet map with color-coded markers by energy capacity (high / mid / low)
- **3D Terrain Viewer** — Load a GeoTIFF DEM to render the terrain in 3D using Three.js, with site markers placed on the surface
- **Dual View Mode** — Side-by-side 2D map and 3D terrain simultaneously
- **Multi-criteria Filtering** — Filter sites by minimum energy (GWh), head height (m), pourpoint separation (km), region, cost class, and slope category
- **Site Detail Panel** — Click any site to see full metrics: energy, power, head, reservoir volumes, dam heights, water-rock ratio, altitude, cost class, and storage time
- **CSV Import** — Drag-and-drop or file-pick your own PHES Searching output CSV
- **Sortable Site List** — Sort by energy, head height, or cost class
- **Header Statistics** — Live-updating counts of total sites, filtered sites, and aggregate energy
- **Demo Dataset** — 100+ pre-loaded global PHES candidate sites across all major mountain regions

---

## Getting Started

No installation or build step needed. The entire application is a single HTML file.

1. Download `phes_dashboard_v2.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Explore the built-in demo data, or load your own CSV

> Requires an internet connection on first load for map tiles (OpenStreetMap) and CDN libraries (Leaflet, Three.js, GeoTIFF.js).

---

## Loading Your Own Data

The dashboard accepts CSV output from the [PHES Searching](https://github.com/ANU-RE100/PHES_Searching) pipeline. Click **Load CSV** in the sidebar and select your file.

### Supported Column Names

| Field | Accepted Headers |
|---|---|
| Site ID | `Pair Identifier`, `Identifier`, `id`, `Site ID` |
| Upper latitude | `Upper latitude`, `Latitude`, `lat` |
| Upper longitude | `Upper longitude`, `Longitude`, `lon` |
| Lower latitude | `Lower latitude`, `Lower lat` |
| Lower longitude | `Lower longitude`, `Lower lon` |
| Head (m) | `Head (m)`, `Head height (m)`, `Head` |
| Energy (GWh) | `Energy (GWh)`, `Energy` |
| Volume (GL) | `Volume (GL)`, `Water volume (GL)`, `Volume` |
| Separation (km) | `Pourpoint separation (km)`, `Separation (km)`, `Distance (km)` |
| Country | `Country` |
| Region | `Region` |
| Cost class | `Cost class`, `Cost Class`, `Cost category` |
| Slope | `Slope`, `Slope category` |

Column names are matched case-insensitively. Missing optional fields fall back to defaults.

---

## Loading a DEM (3D Terrain)

To use the 3D terrain viewer:

1. Obtain a GeoTIFF DEM file covering your region of interest (e.g. from [SRTM](https://srtm.csi.cgiar.org/) or [Copernicus DEM](https://spacedata.copernicus.eu/collections/copernicus-digital-elevation-model))
2. Click **Load GeoTIFF DEM** in the sidebar
3. Toggle the view mode button on the map to **3D** or **BOTH**

Site markers are automatically placed on the terrain surface. Sites outside the DEM bounds are noted in the terrain info panel.

---

## Filters

| Filter | Description |
|---|---|
| Min Energy | Minimum energy capacity in GWh |
| Min Head | Minimum head height in metres |
| Max Separation | Maximum pourpoint separation in km |
| Region | Filter by continental region |
| Cost Class | A (lowest cost) through E (highest cost) |
| Slope | Gentle / Moderate / Steep |

All filters apply simultaneously and update the map and site list in real time.

---

## Tech Stack

| Library | Version | Purpose |
|---|---|---|
| [Leaflet](https://leafletjs.com/) | 1.9.4 | 2D interactive map |
| [Three.js](https://threejs.org/) | r128 | 3D terrain rendering |
| [GeoTIFF.js](https://geotiffjs.github.io/) | 2.1.3 | DEM parsing |
| OpenStreetMap | — | Map tiles |

No frameworks, no build tools, no backend — pure HTML, CSS, and JavaScript.

---

## Related

- [ANU RE100 PHES Searching](https://github.com/ANU-RE100/PHES_Searching) — The upstream C++/Python tool that generates the site data visualised here
- [ANU RE100 Global](http://re100.eng.anu.edu.au/global) — Project homepage with global PHES atlas

---

## License

GPL-3.0 — consistent with the upstream [PHES Searching](https://github.com/ANU-RE100/PHES_Searching) repository.
