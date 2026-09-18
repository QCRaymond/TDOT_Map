# TDOT 2026 QC Field Operations — v6

## Deploy on GitHub Pages
Upload **both** `index.html` and `sites.geojson` into the root of your `TDOT_Map` repository. Commit both files, wait for GitHub Pages deployment, and hard-refresh the site. The normal Pages URL will load the preconfigured Google Sheet automatically; allow a few seconds for the first data refresh.

## Data ownership and updating
- Live operational rows come from the Google Sheet `All Sites` tab, read-only, with an automatic refresh approximately every five minutes while the page is open. The configured source is the **copy previously shared for the demo**; change `DEFAULT_SHEET_URL` in `index.html` when switching to Mark's authoritative sheet.
- Map points come from `sites.geojson`, converted from `175093 - TDOT 2026 Master (1).kml` (1,128 unique point IDs). To add/replace sites, regenerate this file from a revised KML, preserving the FeatureCollection shape and unique `properties.siteId` identifiers matching Sheet Site ID, then commit the new `sites.geojson`. Reload the website. The HTML does not need to be regenerated for geographic updates.
- If a new Sheet site lacks a GeoJSON point, the dashboard can map it if the Sheet exposes valid `Latitude` and `Longitude` columns; otherwise it is reported as unmapped. GeoJSON coordinates take precedence for matching sites.
- Reconciliation is **unfiltered**: Sheet records, all GeoJSON points, matching/mapped rows, sheet rows without usable coordinates, and GeoJSON sites absent from the currently connected sheet. Discrepancy details expand beneath the metrics. The current Sheet copy may contain fewer active rows than the master KML.

## Access and caveats
GitHub Pages and the HTML snapshot/GeoJSON are publicly accessible; the `QC INTERNAL` badge is not an authentication control. Read-only Google Sheets link sharing should be reviewed before distributing the URL outside QC. The browser code does not write to Sheets.
