<template>
    <section id="hero" class="relative w-full h-screen overflow-hidden">
        <MatrixRain />
        <HeroCanvas @ready="showUI = true"/>
        <HeroOverlay :showUI="showUI"/>
    </section>
</template>

<script setup>
import { ref } from "vue"
import HeroCanvas from './HeroCanvas.vue'
import HeroOverlay from './HeroOverlay.vue'
import MatrixRain from "./MatrixRain.vue"

const showUI = ref(false)
</script>