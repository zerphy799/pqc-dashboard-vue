# PQC Bridge | Sprint 1 dashboard

A Vue 3, Vue Router and Vite rebuild of the Sprint 1 dashboard at `e3c366b`. It uses the same schema, default fixture and reporting rules. The default load shows 8 connection segments, 5 PQC (62.5%), 2 fallback and 1 unknown. The three perspectives use the same snapshot.

## Preview the production build

After `npm run build`, run the following with Python 3 and open http://127.0.0.1:8010/. The production build runs offline.

```sh
python -m http.server 8010 --bind 127.0.0.1 --directory dist
```

## Develop

Requires Node.js 22.12+ or 24.

```sh
npm ci
npm run dev
```

Open the URL printed by Vite. Run `npm test` for the model suite and `npm run build` to build the static site into `dist/`. Run `npm run preview` to serve the production build locally. Serve the site over HTTP.

## Data and UI

- Historical mode compares observations with the snapshot time. Current-time mode compares the same observations with the browser clock. The reporting threshold is 24 hours.
- Local JSON import stays in the browser. Reset demo restores the bundled fixture. Search checks supported text fields; filters only change the inventory.
- Routes cover the overview, Sarah's security review, Michael's migration planning, Emma's executive briefing, connection inventory, individual evidence, the dataset and the interpretation guide. Inventory records, role cases, and long evidence text use paging within the viewport. Evidence stays on the selected connection and field while the clock updates.
- `model.mjs` owns validation and reporting. `src/dashboard.js` owns the shared snapshot and filters. `src/router.js` defines the routes. Hash navigation supports opening a route directly from a plain static server.
- This dashboard uses synthetic data independently of Device/Gateway/Cloud. Reported migration, fallback, and suspected downgrade scenarios have the limits documented in the interface.
- This frontend is the working dashboard increment. Scrum records, team evaluation and Moodle submissions are tracked separately.
