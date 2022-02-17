<script>
/* global mapboxgl */

export default {
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_API_KEY;
    const map = new mapboxgl.Map({
      container: "map", // container ID
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-87.6298, 41.8781], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });

    console.log(map);
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
