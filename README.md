# Ideal Cities Maps

A web application displaying 18 ideal cities from the Renaissance period, showing only buildings, green areas, and water bodies using OpenStreetMap data via the Overpass API.

## Features

- **18 Ideal Cities**: Displays maps for historically significant planned cities
- **Filtered Data**: Shows only buildings (brown), green areas (dark green), and water bodies (blue)
- **Dark Theme**: Uses OpenStreetMap dark style (CartoDB Dark Matter)
- **Responsive Grid**: 3-column grid layout that adapts to different screen sizes
- **Real-time Data**: Fetches data directly from OpenStreetMap via Overpass API

## Cities Included

### Ideal Cities
1. Palmanova
2. Sabbioneta
3. Zamość
4. Terra del Sole
5. Pienza
6. Jülich
7. Freudenstadt
8. Alessandria (Cittadella)

### Renaissance-like Star-Fort Ideal Cities
9. Neuf-Brisach
10. Bourtange
11. Naarden
12. Goryōkaku
13. Almeida
14. Elvas

### Cities with Preserved Renaissance Planning Cores
15. Ferrara (Addizione Erculea)
16. Karlskrona
17. Valletta
18. Ljubljana

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
├── public/            # Static files directory
│   └── index.html     # Main HTML file with map visualization
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

## License

MIT License

