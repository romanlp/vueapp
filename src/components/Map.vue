<template>
  <div id="map"></div>
</template>

<script>
const mapboxgl = require("mapbox-gl");
const config = require("../../config/app.config").default;
mapboxgl.accessToken = config.mapboxToken;

const defaultLatLng = {
  lat: 51.50742,
  lng: -0.127743
};

const defaultOptions = {
  container: "map",
  style: config.mapStyles.default,
  center: [defaultLatLng.lng, defaultLatLng.lat],
  zoom: 15,
  // pitch: 45,
  attributionControl: false
};

export default {
  name: "Map",
  data() {
    return {
      route: [],
      lat: defaultLatLng.lat,
      lng: defaultLatLng.lng,
      mapType: "default"
    };
  },
  mounted() {
    console.log("this", this);
    this.loadData();
  },
  methods: {
    loadData() {
      const vm = this;
      const map = new mapboxgl.Map(defaultOptions);
      vm.map = map;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#map {
  width: 100%;
  height: 300px;
}
</style>
