<script>
/* global mapboxgl */

export default {
  data: function () {
    return {
      places: [],
    };
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_API_KEY;
    const map = new mapboxgl.Map({
      container: "map", // container ID
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-87.6298, 41.8781], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });

    console.log(map);

    // make a web request to get places from a backend...
    this.places = [
      { lat: -25.363, lng: 131.044, description: "A place in Australia" },
      { lat: -33.8675, lng: 151.207, description: "The main city!" },
    ];
    this.places.forEach((place) => {
      const popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
      const marker1 = new mapboxgl.Marker()
        .setLngLat([place.lng, place.lat])
        .setPopup(popup)
        .addTo(map);
      console.log(marker1);
    });
  },
};
</script>

<template>
  <h1>Map stuff</h1>
  <div id="map"></div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  height: 500px;
}
</style>
