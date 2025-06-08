# Digital Pin Finder

Digital Pin Finder is a web application that allows users to discover and visualize locations using their geolocation or by entering a DIGIPIN, a unique 10-character code representing a specific geographic area. Built with Leaflet.js for mapping, QRCode.js for QR code generation, and a modern dark-themed UI, it provides an intuitive way to explore locations, generate shareable QR codes, and open coordinates in Google Maps.

## Features

- **Geolocation Support**: Find your current location using the browser's Geolocation API.
- **DIGIPIN Input**: Enter a DIGIPIN (e.g., `FC9-J2K-LMP`) to display its corresponding location on the map.
- **Interactive Map**: View locations on an OpenStreetMap-based map with a custom dark theme.
- **QR Code Generation**: Create QR codes for locations that link to Google Maps.
- **Google Maps Integration**: Open locations directly in Google Maps for navigation.
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices.
- **Location Accuracy**: Displays an accuracy circle for geolocation results.
- **Error Handling**: User-friendly error messages for geolocation and invalid DIGIPIN inputs.

## Technologies Used

- **HTML5** and **CSS3** for structure and styling
- **JavaScript** for interactivity
- **Leaflet.js** (v1.9.4) for mapping
- **QRCode.js** for QR code generation
- **OpenStreetMap** for map tiles
- **Geolocation API** for user location
- **Custom DIGIPIN Algorithm** for encoding/decoding geographic coordinates

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge, etc.)
- An internet connection for loading external resources (Leaflet, QRCode.js, OpenStreetMap tiles)

### Installation

1. **Clone the Repository** (if hosted on a version control platform):
   ```bash
   git clone https://github.com/niraj-ghetiya/Digipin.git
   cd Digipin
   ```

2. **Serve the Application**:
   - Since this is a static web application, you can serve it using a local server. For example, with Python:
     ```bash
     python -m http.server 8000
     ```
   - Alternatively, open `index.html` directly in a browser (note: some features like geolocation may require a server due to security restrictions).

3. **Access the Application**:
   - Open your browser and navigate to `http://localhost:8000` (or the port you specified).
   - Allow geolocation permissions when prompted for location access.


## Usage

1. **Get Your Location**:
   - Click the "Get My Location" button to use your device's geolocation.
   - The map will center on your location, display a marker, and show the corresponding DIGIPIN.

2. **Enter a DIGIPIN**:
   - Input a valid DIGIPIN (e.g., `FC9-J2K-LMP`) in the provided text field.
   - Click the "Find DIGIPIN" button or press Enter.
   - The map will update to show the location associated with the DIGIPIN.

3. **Interact with the Map**:
   - Zoom and pan to explore the area.
   - Click the marker to view location details, including coordinates and DIGIPIN.

4. **Share or Navigate**:
   - Click "Generate QR Code" to create a QR code linking to the location in Google Maps.
   - Click "Open in Google Maps" to view the location in Google Maps for navigation.

5. **Error Handling**:
   - If geolocation is denied or unavailable, an error message will appear.
   - If an invalid DIGIPIN is entered, an error message will prompt you to try again.

## DIGIPIN System

The DIGIPIN system divides a geographic region (bounded by latitudes 2.5° to 38.5° and longitudes 63.5° to 99.5°) into a grid, assigning a unique 10-character code to each area. The grid is defined by a 4x4 matrix of characters:

```
F C 9 8
J 3 2 7
K 4 5 6
L M P T
```

- **Encoding**: The `getDigiPin(lat, lon)` function converts coordinates to a DIGIPIN by recursively dividing the region into smaller grids.
- **Decoding**: The `getLatLngFromDigiPin(digipin)` function converts a DIGIPIN back to approximate coordinates (center of the grid cell).
- **Format**: DIGIPINs are 10 characters long, typically displayed with hyphens after the 3rd and 6th characters (e.g., `FC9-J2K-LMP`).

## Limitations

- **Geographic Bounds**: DIGIPINs are only valid within the defined region (lat: 2.5°–38.5°, lon: 63.5°–99.5°).
- **Geolocation Dependency**: Requires browser support for the Geolocation API and user permission.
- **Internet Connection**: Relies on external resources (Leaflet, QRCode.js, OpenStreetMap).
- **Accuracy**: Geolocation accuracy depends on the device and environment; DIGIPINs represent an area, not a precise point.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -am 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

Please follow the existing code style and include tests for new features.


## Acknowledgments

- [Leaflet.js](https://leafletjs.com/) for the mapping library
- [QRCode.js](https://davidshimjs.github.io/qrcodejs/) for QR code generation
- [OpenStreetMap](https://www.openstreetmap.org/) for map tiles