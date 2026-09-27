# Port Digital Twin – Truck Trip Animation

A browser-based visualization and analytics tool for truck movement inside the port. The app uses Leaflet satellite mapping, SheetJS for Excel files, and Chart.js for analytics.

## Files

- `index.html` — the complete web application.
- `port_road_and_warehouse_zones.json` — default manual port-road segments and W1–W5 warehouse zones loaded automatically on a new browser/device.

## Deploy with GitHub Pages

1. Create a GitHub repository, for example `port-digital-twin`.
2. Upload `index.html` and `port_road_and_warehouse_zones.json` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Choose branch **main** and folder **/(root)**, then save.
6. Open the GitHub Pages URL after deployment finishes.

## Data workflow

The RTLS CSV, Truck Entering Excel, and Truck Exiting Excel files are selected from the user's computer. They are processed in the browser and do not need to be committed to this repository.

## Road and warehouse configuration behavior

On startup the app uses this priority:

1. A road/zone setup already saved in that browser's local storage.
2. The hosted `port_road_and_warehouse_zones.json` file.
3. Empty road/zone configuration if neither source is available.

The existing manual road editor, warehouse-zone editor, and combined JSON import/export remain available. If a user edits the hosted defaults and presses the relevant Save buttons, those edits are stored only in that browser unless they export the combined JSON and update the hosted JSON file in the repository.

## Updating the default road/zones

1. Edit the road/zones in the application.
2. Use **Combined Road + Zone Backup → Export Road + Zones JSON**.
3. Replace `port_road_and_warehouse_zones.json` in the GitHub repository with the exported file.
4. Commit the change.

New browsers/devices will then load the updated default setup automatically. Browsers that already have their own saved configuration will continue to prefer their saved version.

## Privacy note

Do not commit sensitive RTLS, entry, or exit datasets to a public repository. The application does not require those datasets to be hosted; users can select them locally from their own computer.
