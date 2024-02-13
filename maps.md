---
permalink: /maps
layout: maps
title: maps
---
<!DOCTYPE html>
<html style="height: 100%; margin: 0; padding: 0;">
<head>
  <title>Add Map</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
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
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.js"></script>

  <script type="module">
    /**
     * @license
     * Copyright 2019 goole LLC. All Rights Reserved.
     * SPDX-Liense-Identifier: Apache-2.0
     */
    let map;

    async function initMap() {
      const { Map } = await google.maps.importLibrary("maps");

      map = new Map(document.getElementById("map"), {
        center: { lat: 33.000, lng: -117.200 }, // Centered at Southern California
        zoom: 8, // Adjust he zoom level as needed
        styles: [] // Remove custom styles
      });

      // Sample markers with different latitudes and longitudes
      const markers = [
        {lat: 33.118, lng: -117.131, label: 'Del Norte High School'}, // Del Norte High School
        {lat: 33.6846, lng: -117.8265, label: 'Disneyland'}, // Disneyland
        {lat: 34.0522, lng: -118.2437, label: 'Hollywood'}, // Hollywood
        {lat: 37.7749, lng: -122.4194, label: 'San Francisco'} // San Francisco
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

    initMap();
  </script>
</head>
<body>
  <!--The div element for the map -->
  <div id="map-container">
    <div id="map"></div>
  </div>

  <!-- prettier-ignore -->
  <script>(g=>{var h,a,k,p="The Google Maps JavaScript API",c="google",l="importLibrary",q="__ib__",m=document,b=window;b=b[c]||(b[c]={});var d=b.maps||(b.maps={}),r=new Set,e=new URLSearchParams,u=()=>h||(h=new Promise(async(f,n)=>{await (a=m.createElement("script"));e.set("libraries",[...r]+"");for(k in g)e.set(k.replace(/[A-Z]/g,t=>"_"+t[0].toLowerCase()),g[k]);e.set("callback",c+".maps."+q);a.src=`https://maps.${c}apis.com/maps/api/js?`+e;d[q]=f;a.onerror=()=>h=n(Error(p+" could not load."));a.nonce=m.querySelector("script[nonce]")?.nonce||"";m.head.append(a)}));d[l]?console.warn(p+" only loads once. Ignoring:",g):d[l]=(f,...n)=>r.add(f)&&u().then(()=>d[l](f,...n))})
    ({key: "AIzaSyC9pEqmLuhD8-W86bZHiuDpCgeXlCoxVTc ", v: "beta"});</script>
</body>
</html>


