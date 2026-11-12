# ParkSmart — Intelligent Campus Parking

A polished, Vercel-ready campus parking management prototype built with React + Vite. It demonstrates live slot availability, digital reservations, campus-zone views, and demand forecasting.

## Features

- **Live parking dashboard** — availability, occupancy, and reserved-space counts across three campus zones.
- **Interactive slot directory** — filter by zone/status, search by slot ID, and select an available slot.
- **Digital reservations** — book a slot with name, vehicle registration, vehicle type, date, and arrival time.
- **Reservation management** — review and cancel bookings; cancellation releases the slot.
- **Demand insights** — hourly demand visualization and a time-of-day forecast.
- **Demo sensor feed** — simulated occupancy updates every 18 seconds (can be paused).
- **Local persistence** — slots and reservations are saved in browser `localStorage`.
- **Export** — download reservation and slot data as JSON.
- **Responsive UI** — desktop and mobile layouts.

## Run locally

Requirements: Node.js 18+ and npm.

```bash
npm install
npm run dev
```

Open the local URL printed by Vite.

## Build

```bash
npm run build
npm run preview
```

## Deploy to Vercel

1. Push this folder to a GitHub repository.
2. In Vercel, choose **Add New → Project** and import the repository.
3. Vercel should detect Vite automatically. Confirm:
   - Framework preset: **Vite**
   - Build command: `npm run build`
   - Output directory: `dist`
   - Install command: `npm install`
4. Click **Deploy**.

`vercel.json` includes a rewrite so client-side routes can be served correctly if routes are added later.

## Push to GitHub

Create an empty repository on GitHub, then run these commands from this project folder:

```bash
git init
git add .
git commit -m "Initial commit: ParkSmart campus parking"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ParkSmart.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username. Do not include `node_modules` or `dist`; they are excluded by `.gitignore`.

## Demo behaviour and production upgrade path

This is a complete **frontend demonstration**, not a connected physical parking installation. The sensor feed is simulated and the demand chart uses illustrative historical-pattern data. Reservations are stored in the visitor's browser, so they are not shared between devices or users.

For a real campus deployment:
1. Add a backend API (FastAPI/Node) and a shared database (PostgreSQL/Supabase).
2. Connect ESP32/IoT ultrasonic or IR sensors per bay; send occupancy events to the API over MQTT/HTTPS.
3. Replace the simulated interval in `src/App.jsx` with a WebSocket/SSE subscription to the sensor service.
4. Train a forecasting model on timestamped occupancy history and serve its predictions through the API.
5. Add authentication, role-based admin access, reservation expiry, conflict prevention, and campus-approved access controls.

## Project structure

```text
ParkSmart/
├── public/
├── src/
│   ├── App.jsx
│   ├── main.jsx
│   └── styles.css
├── .gitignore
├── index.html
├── package.json
├── vercel.json
└── README.md
```

## Tech stack

- React 18
- Vite 6
- JavaScript
- Lucide React icons
- CSS
- Browser localStorage (demo persistence)

## License

MIT — see `LICENSE`.
