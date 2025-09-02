<template>
  <div class="relative w-full h-screen">
    <MatrixRain />
    <Hero />
  </div>
</template>

<script setup>
import MatrixRain from './components/MatrixRain.vue'
import Hero from './components/Hero/Hero.vue';
</script>


<style scoped>
/* wipe default margins for a true edge-to-edge canvas */
html, body, #app {
  height: 100%;
  margin: 0;
}
</style>
