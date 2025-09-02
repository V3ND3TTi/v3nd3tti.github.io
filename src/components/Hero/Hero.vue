<template>
    <section id="hero" class="relative w-full h-screen overflow-hidden">
        <HeroCanvas @ready="showUI = true"/>
        <HeroOverlay :showUI="showUI"/>
    </section>
</template>

<script setup>
import { ref } from "vue"
import HeroCanvas from './HeroCanvas.vue'
import HeroOverlay from './HeroOverlay.vue'

const showUI = ref(false)
</script>