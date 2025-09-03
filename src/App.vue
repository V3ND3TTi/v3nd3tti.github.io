<template>
  <div>
    <Transition name="fade" mode="out-in">
      <Hero v-if="showHero" @exit="navigate" key="hero" />
      <main v-else class="relative z-10" key="main">
        <AboutMe id="about" />
        <Projects id="projects" />
        <Contact id="contact" />
      </main>
    </Transition>
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
  }, 700) // match fade duration
}
</script>

<style>
/* Crossfade transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.7s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
