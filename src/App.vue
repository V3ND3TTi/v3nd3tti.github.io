<template>
  <div>
    <Hero />
  </div>
</template>

<script setup>
import Hero from './components/Hero/Hero.vue';
</script>


<style scoped>
/* wipe default margins for a true edge-to-edge canvas */
html, body, #app {
  height: 100%;
  margin: 0;
}
</style>
