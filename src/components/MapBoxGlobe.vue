<template>
  <div ref="mapContainer" class="map-container"></div>
</template>

<script setup lang="ts">
  import 'mapbox-gl/dist/mapbox-gl.css';
  import mapboxgl from 'mapbox-gl'; // or "const mapboxgl = require('mapbox-gl');"
  import { onMounted, ref } from 'vue';

  const mapContainer = ref<HTMLElement>();

  onMounted(() => {
    mapboxgl.accessToken =
      'pk.eyJ1IjoicmFubmQyMyIsImEiOiJja3d3OHlidzQwMWQ3Mm9xdmpyODFmaGF4In0.eEwCsb4-3ZoxFTrJTpTF3Q';
    const map = new mapboxgl.Map({
      container: mapContainer.value!, // container ID
      style: 'mapbox://styles/mapbox/streets-v11', // style URL
      center: [-74.5, 40], // starting position [lng, lat]
      zoom: 2, // starting zoom
      projection: 'globe', // display the map as a 3D globe
    } as any);
    map.on('style.load', () => {
      map.setFog({}); // Set the default atmosphere style
    });
  });
</script>

<style scoped>
  .map-container {
    width: 100vw;
    height: 100vh;
  }
</style>
