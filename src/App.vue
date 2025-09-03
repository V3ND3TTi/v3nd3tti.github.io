<template>
  <div>
    <Hero v-if="showHero" @exit="navigate"/>

    <main v-else class="relative z-10 bg-black">
      <AboutMe id="about" />
      <Projects id="projects" />
      <Contact id="contact" />
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Hero from './components/Hero/Hero.vue'
import AboutMe from './components/AboutMe.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'

const showHero = ref(true)

function navigate(targetId) {
  showHero.value = false
  setTimeout(() => {
    document.getElementById(targetId)?.scrollIntoView({ behavior: 'smooth' })
  }, 50) // tiny delay so Hero is gone
}
</script>

<style scoped>
/* wipe default margins for a true edge-to-edge canvas */
html, body, #app {
  height: 100%;
  margin: 0;
}
</style>
