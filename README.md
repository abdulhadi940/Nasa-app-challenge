# Will It Rain On My Parade? - NASA Space Apps (React + Node)

This project is a simple demo app for the NASA Space Apps Challenge:
"Will It Rain On My Parade?"  
It uses the NASA POWER API (no credentials needed) and Google Maps (API key required)
to fetch weather data for a selected location and date, display a summary, a 7-day rainfall chart,
and allow map-based coordinate picking.

## What is included
- `server/` - Node.js Express backend that proxies requests to NASA POWER API
- `client/` - React frontend (Create React App style) with:
  - Google Maps integration (click on map to pick coordinates)
  - Chart (Recharts) showing historical rainfall
- `azure-deploy.yml` - GitHub Actions workflow (example) to deploy to Azure Web App
- `.env.example` - env var examples

## Quick local setup (recommended)
1. Copy the repo to your machine or unzip the provided package.
2. Create a Google Maps API key: https://console.cloud.google.com/apis/credentials
   - Enable "Maps JavaScript API"
3. From project root, create env files:

### server/.env
```
PORT=4000
NASA_POWER_COMMUNITY=RE
```

### client/.env
```
REACT_APP_GOOGLE_MAPS_KEY=YOUR_GOOGLE_MAPS_API_KEY
REACT_APP_NASA_COMMUNITY=RE
REACT_APP_BACKEND_URL=http://localhost:4000
```

4. Install and run both projects:
```bash
# from project root
cd server
npm install
node index.js
# in a new terminal
cd ../client
npm install
npm start
```

Frontend will open at http://localhost:3000 and backend at http://localhost:4000.

## Azure Deployment (one-click pipeline)
`azure-deploy.yml` is a sample GitHub Actions workflow which deploys to an Azure Web App.
You need to set the following GitHub Secrets in your repo:
- `AZURE_WEBAPP_PUBLISH_PROFILE` (from Azure Portal > Get publish profile)
- `REACT_APP_GOOGLE_MAPS_KEY`
- `REACT_APP_NASA_COMMUNITY` (optional)

The workflow builds both server and client and deploys to Azure App Service.

## Notes
- Google Maps requires a valid billing-enabled Google Cloud project and API key.
- NASA POWER API is free and does not require an API key.
- Replace placeholders in `.env` files with your values before running.

Good luck at the challenge! If you want, I can also create a GitHub repo and push this code for you.
