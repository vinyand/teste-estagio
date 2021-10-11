<template>
  <div id="mapid"></div>
</template>

<script>
import leaflet from "leaflet";
import { onMounted } from "vue";

export default {
  name: "Map",
  setup() {
    let mymap;

    onMounted(() => {
      mymap = leaflet.map("mapid").setView([51.505, -0.09], 13);

      leaflet
        .tileLayer(
          "https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1Ijoid2VsZG9jYXJ2YWxobyIsImEiOiJja3VuNmlxM3gzemhqMzJuemF6bDJ5ZWFxIn0.bqEjZuNrb-_QDHdtyFIWtA",
          {
            attribution:
              'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
            maxZoom: 18,
            id: "mapbox/streets-v11",
            tileSize: 512,
            zoomOffset: -1,
            accessToken:
              "pk.eyJ1Ijoid2VsZG9jYXJ2YWxobyIsImEiOiJja3VuNmlxM3gzemhqMzJuemF6bDJ5ZWFxIn0.bqEjZuNrb-_QDHdtyFIWtA",
          }
        )
        .addTo(mymap);
    });
  },
};
</script>

<style>
#mapid {
  height: 100vh;
}
</style>
