---
permalink: /maps
layout: base 
title: maps
---

<html style="height: 100%; margin: 0; padding: 0;">
<head>
  <title>Real Estate Map</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      background-color: #007bff;
    }
    #map-container {
      height: 80vh; /* Adjust height as needed */
      width: 80%; /* Adjust width as needed */
      margin: 20px auto; /* Center the map horizontally */
      border: 2px solid #ccc; /* Add border */
      border-radius: 10px; /* Optional: Add border radius */
    }
    #map {
      height: 100%;
      width: 100%;
    }
  </style>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=default"></script>
  <script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyC9pEqmLuhD8-W86bZHiuDpCgeXlCoxVTc&callback=initMap"
  async defer></script>

  <script type="text/javascript">
    let map;

    async function initMap() {
      map = new google.maps.Map(document.getElementById("map"), {
        center: { lat: 33.000, lng: -117.200 }, // Centered at Southern California
        zoom: 8, // Adjust the zoom level as needed
        styles: [] // Remove custom styles
      });

      const markers = [
        {lat: 34.080402, lng: -118.44406, label: '10644 Bellagio Rd'}, // 10644 Bellagio Rd
        {lat: 33.579117, lng: -117.833084, label: '19 Del Mar'}, // 19 Del Mar
        {lat: 34.08456, lng: -118.42676, label: '1028 Ridgedale Dr'}, // 1028 Ridgedale Dr
        {lat: 34.088654, lng: -118.42405, label: '1210 Benedict Canyon Dr'}, // 1210 Benedict Canyon Dr
        {lat: 34.080776, lng: -118.41729, label: '912 Benedict Canyon Dr'}, // 912 Benedict Canyon Dr
        {lat: 33.582565, lng: -117.82734, label: '6 Midsummer'}, // 6 Midsummer
        {lat: 33.60714, lng: -117.91654, label: '1220 W Bay Ave'}, // 1220 W Bay Ave
        {lat: 34.022305, lng: -118.78263, label: '28026 Sea Lane Dr'}, // 28026 Sea Lane Dr
        {lat: 34.084206, lng: -118.460014, label: '10979 Chalon Rd'}, // 10979 Chalon Rd
        {lat: 34.09128, lng: -118.40844, label: '1005 N Alpine Dr'}, // 1005 N 
        {lat: 33.515034, lng: -117.75868, label: '11 Montage Way'}, // 11 Montage Way
        {lat: 33.5844, lng: -117.826164, label: '21 Spinnaker'}, // 21 Spinnaker
        {lat: 33.590073, lng: -117.838425, label: '14 Channel Vis'}, // 14 Channel Vis
        {lat: 32.829933, lng: -117.25997, label: '1547 El Camino Del Teatro'}, // 1547 El Camino Del Teatro
        {lat: 33.50018, lng: -117.68854, label: '6 Inspiration Poin'}, // 6 Inspiration Poin
        {lat: 33.580666, lng: -117.82153, label: '18 Swimmers Poin'}, // 18 Swimmers Poin
        {lat: 34.08591, lng: -118.414, label: '1005 Laurel Way'}, // 1005 Laurel Way
        {lat: 33.50726, lng: -117.75043, label: '15 Camel Point Dr'}, // 15 Camel Point Dr
        {lat: 34.097416, lng: -118.451294, label: '10702 Levico Way'}, // 10702 Levico Way
        {lat: 34.10434, lng: -118.45118, label: '1940 Bel Air Rd'}, // 1940 Bel Air Rd
        {lat: 33.01499, lng: -117.235825, label: '16627 Los Morros, Rancho Santa Fe'}, // 16627 Los Morros, Rancho Santa Fe
        {lat: 32.999237, lng: -117.1982, label: '15815 Bella Siena, Rancho Santa Fe'}, // 15815 Bella Siena, Rancho Santa Fe
        {lat: 33.017036, lng: -117.21046, label: '5757 Linea Del Cielo, Rancho Santa Fe'}, // 5757 Linea Del Cielo, Rancho Santa Fe
        {lat: 32.723553, lng: -117.25673, label: '889 Sunset Cliffs Blvd, San Diego'}, // 889 Sunset Cliffs Blvd, San Diego
        {lat: 33.58996, lng: -117.30396, label: '36852 Calle De Lobo, Murrieta'}, // 36852 Calle De Lobo, Murrieta
        {lat: 32.971294, lng: -117.26866, label: '2722 Camino Del Mar, Del Mar'}, // 2722 Camino Del Mar, Del Mar
        {lat: 32.967514, lng: -117.007576, label: '13980 Millards Ranch Ln, Poway'}, // 13980 Millards Ranch Ln, Poway
        {lat: 32.9678, lng: -117.26305, label: '2116 Balboa Ave, Del Mar'}, // 2116 Balboa Ave, Del Mar
        {lat: 32.979954, lng: -117.2677, label: '107 Via De La Valle, Del Mar'}, // 107 Via De La Valle, Del Mar
        {lat: 32.80816, lng: -117.26767, label: '5316 Calumet Ave, La Jolla'}, // 5316 Calumet Ave, La Jolla
        {lat: 32.8601, lng: -117.24844, label: '8441 Whale Watch Way, La Jolla'}, // 8441 Whale Watch Way, La Jolla
        {lat: 32.822323, lng: -117.27907, label: '225 Via Del Norte, La Jolla'}, // 225 Via Del Norte, La Jolla
        {lat: 32.966522, lng: -117.26453, label: '2008 Seaview Ave, Del Mar'}, // 2008 Seaview Ave, Del Mar
        {lat: 32.99785, lng: -117.17932, label: '16902 Via Cuesta Verde, Rancho Santa Fe'}, // 16902 Via Cuesta Verde, Rancho Santa Fe
        {lat: 33.045437, lng: -117.19682, label: '6405 Primero Izquierdo, Rancho Santa Fe'}, // 6405 Primero Izquierdo, Rancho Santa Fe
        {lat: 33.16263, lng: -117.35704, label: '2497 Ocean St B, Carlsbad'}, // 2497 Ocean St B, Carlsbad
        {lat: 33.014946, lng: -117.19397, label: '16636 El Zorro Vis, Rancho Santa Fe'}, // 16636 El Zorro Vis, Rancho Santa Fe
        {lat: 34.07774, lng: -118.40324, label: '610 N Rexford Dr, Beverly Hills'}, // 610 N Rexford Dr, Beverly Hills
        {lat: 33.0865, lng: -116.711525, label: '28428 Highway 78, Ramona'}, // 28428 Highway 78, Ramona
        {lat: 33.029053, lng: -117.23404, label: '4722 La Noria, Rancho Santa Fe'}, // 4722 La Noria, Rancho Santa Fe
        {lat: 32.99546, lng: -117.18108, label: '16715 Camino Sierra Del Sur, Rancho Santa Fe'}, // 16715 Camino Sierra Del Sur, Rancho Santa Fe
        // Add markers for the remaining houses following the same format...
      ];

      // Add markers to the map
      markers.forEach(marker => {
        const newMarker = new google.maps.Marker({
          position: marker,
          map: map,
          title: marker.label // Display label as marker title
        });

        // Add click event listener to the marker
        newMarker.addListener('click', function() {
          alert('Place: ' + marker.label + '\nLatitude: ' + this.getPosition().lat() + '\nLongitude: ' + this.getPosition().lng());
        });
      });
    }
  </script>
</head>
<body>
  <!--The div element for the map -->
  <div id="map-container">
    <div id="map"></div>
  </div>
</body>
</html>
