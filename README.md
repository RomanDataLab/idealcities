# Ideal City masterplans

A web application displaying 15 ideal cities and masterplans from various historical periods, showing only buildings, green areas, and water bodies using OpenStreetMap data via the Overpass API.

## Features

- **15 Ideal City Masterplans**: Displays maps for historically significant planned cities
- **Filtered Data**: Shows only buildings (brown outlines), green areas (dark green lines), and water bodies (blue lines)
- **Dark Theme**: Uses OpenStreetMap dark style (CartoDB Dark Matter)
- **Responsive Grid**: 3-column grid layout that adapts to different screen sizes
- **Real-time Data**: Fetches data directly from OpenStreetMap via Overpass API
- **Hover Descriptions**: Detailed information about each masterplan including architects, funders, time periods, and ruling dynasties

## Cities Included

1. **Palmanova** - Italy
2. **Sabbioneta** - Italy
3. **Zamość** - Poland
4. **Nicosia** - Cyprus
5. **Yerevan** - Armenia
6. **Jülich** - Germany
7. **Freudenstadt** - Germany
8. **Kropyvnitsky** - Ukraine
9. **Neuf-Brisach** - France
10. **Bourtange** - Netherlands
11. **Naarden** - Netherlands
12. **Goryōkaku** - Japan
13. **Almeida** - Portugal
14. **Elvas** - Portugal
15. **Beijing** - China

## Prerequisites

- Node.js (version 14.0.0 or higher)
- npm (comes with Node.js)

## Installation

1. Clone or download this repository
2. Install dependencies:
```bash
npm install
```

## Running the Application

Start the server:
```bash
npm start
```

The application will be available at `http://localhost:3000`

## Project Structure

```
idealcities/
├── server.js          # Express server configuration
├── package.json       # Node.js dependencies and scripts
├── vercel.json        # Vercel deployment configuration
├── public/            # Static files directory
│   ├── index.html     # Main HTML file with map visualization
│   └── cities-data.js # City data with coordinates and descriptions
├── .gitignore         # Git ignore file
└── README.md          # This file
```

## Technologies Used

- **Node.js**: Server runtime
- **Express**: Web server framework
- **Leaflet.js**: Interactive map library
- **Overpass API**: Query OpenStreetMap data
- **CartoDB Dark Matter**: Dark map tiles

## How It Works

1. The Express server serves static files from the `public` directory
2. The frontend uses Leaflet.js to create interactive maps
3. For each city, an Overpass API query fetches:
   - Buildings (tagged with `building`)
   - Green areas (parks, forests, meadows, gardens, etc.)
   - Water bodies (rivers, lakes, canals, etc.)
4. The data is rendered on dark-themed maps in a responsive grid layout

## API Usage

This application uses the public Overpass API endpoint:
- `https://overpass-api.de/api/interpreter`

Please be respectful of rate limits when making requests.

## Deployment

### Deploy to Vercel

1. **Install Vercel CLI** (optional, for command-line deployment):
```bash
npm i -g vercel
```

2. **Deploy via Vercel Dashboard**:
   - Go to [vercel.com](https://vercel.com)
   - Sign in with your GitHub account
   - Click "New Project"
   - Import your GitHub repository: `RomanDataLab/idealcities`
   - Vercel will automatically detect the Node.js project
   - Click "Deploy"

3. **Deploy via CLI**:
```bash
vercel
```

The application will be automatically deployed and you'll get a URL like `https://idealcities.vercel.app`

### Environment Variables

No environment variables are required for this application.

## License

MIT License

