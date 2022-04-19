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
      center: [-105.2056799, 39.6654274], // starting position [lng, lat]
      zoom: 16, // starting zoom
    });

    // create the popup
    const popup = new mapboxgl.Popup({ offset: 25 }).setText("Red Rocks Amphitheater, best place in the world!");

    // create DOM element for the marker
    const el = document.createElement("div");
    el.id = "marker";
    // Create a default Marker and add it to the map.
    const marker1 = new mapboxgl.Marker().setLngLat([12.554729, 55.70651]).addTo(map);
    // Create a default Marker, colored black, rotated 45 degrees.
    const marker2 = new mapboxgl.Marker({ color: "black", rotation: 45 })
      .setLngLat([-105.2056799, 39.6654274])
      .setPopup(popup)
      .addTo(map);
    console.log(map, marker1, marker2);
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
#marker {
  background-image: url("https://thissongissick.com/wp-content/uploads/2021/12/redrockssky.jpeg");
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}
.mapboxgl-popup {
  max-width: 200px;
}
</style>
