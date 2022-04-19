<template>
  <div class="about">
    <h1>This is a map!!</h1>
    <div id="map"></div>
  </div>
</template>

<script>
/* global mapboxgl */
export default {
  data: function () {
    return {};
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
    const map = new mapboxgl.Map({
      container: "map", // container ID
      style: "mapbox://styles/mapbox/satellite-v9", // style URL
      center: [-105.207451, 39.666508], // starting position [lng, lat]
      zoom: 16, // starting zoom
    });
    console.log(map);
  },
  methods: {},
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  width: 100%;
  height: 400px;
}
</style>
