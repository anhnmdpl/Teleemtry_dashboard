# Telemetry Control Tower

Interactive, static frontend for Telemetry monitoring. **Demo data only**. The canonical operational workbook remains `Manual Check Readings` on Messer SharePoint, updated by Power Automate.

## Dashboard
- Operations Overview — six KPI cards, signal connectivity, actions and operational watchlist
- Tank Monitoring — customer/tank/RTU, level progress, current stock, reorder 45%
- Delivery Planning — forecast hours to reorder and T−24h planning deadline
- Search and filter by RTU/customer/tank/status

## Run
Open `index.html` locally, or serve this directory with `python -m http.server 8000`.

## Data
`config.js` defaults to `dataUrl: null`. Without a backend, the site displays **fictional demo data**. You can import a local JSON document (`[{rtu,customer,tank,full,stock,rate_kg_h,reading_time,status}]`), which is not uploaded to GitHub.

Reorder = **45% × Full kg** from sheet `Data`. Signal state is based on scheduled Reading batches and should be evaluated by the independent monitoring flow (e.g., 08:00 Reading checked at 08:30). No realtime signal guarantees.

## Security and production deployment
**Do not commit real customer names, RTU readings, customer files, secrets, or Excel exports.** A private repository does not make a website automatically private. GitHub Pages is not appropriate for confidential tank data. For production, deploy authenticated frontend/API with Microsoft Entra ID (e.g., Azure Static Web Apps + Functions / Graph) and access SharePoint workbook only on the server. Keep credentials server side, validate roles and CORS.

The site is **not yet connected** to a live API, Microsoft 365 SSO or automated alerts.
