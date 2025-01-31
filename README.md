<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Map with Leaflet</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        #map {
            height: 600px; /* Adjust map height as needed */
            width: 100%; /* Make the map take up the full width */
        }
    </style>
</head>
<body>
    <h1>Interactive map so you can search for whatever you want</h1>
    <div id="map"></div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script>
        // Initialize the map
        var map = L.map('map').setView([51.505, -0.09], 13); // Coordinates for London, with zoom level 13

        // Add a tile layer (background map)
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        // Add a marker to the map
        var marker = L.marker([51.5, -0.09]).addTo(map);
        marker.bindPopup('<b>Hello world!</b><br>I am a popup.').openPopup();

        // Add a circle to the map
        var circle = L.circle([51.508, -0.11], {
            color: 'red',
            fillColor: '#f03',
            fillOpacity: 0.5,
            radius: 500
        }).addTo(map);
        circle.bindPopup('I am a circle.');

        // Add a polygon to the map
        var polygon = L.polygon([
            [51.509, -0.08],
            [51.503, -0.06],
            [51.51, -0.047]
        ]).addTo(map);
        polygon.bindPopup('I am a polygon.');
    </script>
</body>
</html>

