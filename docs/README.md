# Project Volusia — Frontend Documentation

> Documentation for the Project Volusia frontend portal.

---

## Quick Links

| Resource | URL |
|----------|-----|
| **Live Portal** | https://zqmlabs.com |
| **Data Portal** | https://data.zqmlabs.com |
| **Backend Repo** | https://github.com/ZQM-Computing/zqmlabs-portal |
| **API Endpoint** | https://zqmlabs.com/health |
| **Connection Guide** | [CONNECTION.md](../CONNECTION.md) |

---

## Overview

The frontend is a React/TypeScript application built with Vite, Tailwind CSS, Nivo charts, and Leaflet maps. It displays data from the backend API and static JSON files served by nginx.

---

## Tech Stack

| Layer | Tech | License |
|-------|------|---------|
| Framework | React 18 + Vite + TypeScript | MIT |
| Charts | Nivo (D3-based) | MIT |
| Maps | Leaflet + react-leaflet | BSD-2 |
| Styling | Tailwind CSS | MIT |
| Backend | FastAPI (Python) | MIT |
| Web Server | nginx (NSSM service) | BSD |

---

## Pages

| Category | Route | Description |
|----------|-------|-------------|
| Economic | `/data/economic/` | Economic indicators, business data |
| Tourism | `/data/tourism/` | Tourism metrics, events, visitor volume |
| Real Estate | `/data/real-estate/` | Property data, housing market |
| Demographics | `/data/demographics/` | Population, census data |
| Transportation | `/data/transportation/` | Transit, infrastructure, traffic |
| Climate | `/data/climate/` | Weather, climate data |
| Housing | `/data/housing/` | Housing affordability, availability |
| Public Safety | `/data/public-safety/` | Crime, emergency services |
| Health | `/data/health/` | Health outcomes, hospital data |
| Education | `/data/education/` | Schools, performance metrics |
| Government Finance | `/data/government-finance/` | Budget, spending, taxation |

---

## Data Sources

The frontend uses two data sources:

1. **Static JSON files** (primary) — nginx serves pre-generated HTML pages from `C:/Users/zqmco/scoop/persist/nginx/html/data/`
2. **Live API** (fallback) — Real-time data from backend at `127.0.0.1:8000`

See [CONNECTION.md](../CONNECTION.md) for details.

---

## Development

```bash
npm install
npm run dev          # http://localhost:5173
npm run build        # outputs to dist/
npm run preview      # http://localhost:4173
```

---

## Deployment

### nginx (Automatic)

`deploy.py` regenerates static pages, syncs to nginx, and restarts the service:

```bash
python deploy.py              # Full pipeline
python deploy.py --dry-run    # Preview changes
python deploy.py --skip-generate  # Skip static generation
python deploy.py --skip-restart   # Skip nginx restart
```

The nginx service runs via NSSM (`Volusia-Nginx`). Static assets are cached for 1 year (hashed filenames).

---

## Repository Structure

```
zqmlabs-portal/
├── backend/          # FastAPI backend (main.py, gamification.py)
├── src/              # React/Vite frontend source
├── data/             # Static JSON data files (11 categories)
├── nginx/            # nginx configuration
├── scripts/          # Deployment and utility scripts
├── public/           # Static assets
└── docker-compose.yml
```

---

## License

MIT © 2026 ZQM Labs / ZQM Computing
