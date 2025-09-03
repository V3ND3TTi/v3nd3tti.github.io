<template>
    <section id="hero" class="fixed inset-0 w-full h-screen overflow-hidden z-50 bg-black">
        <MatrixRain />
        <HeroCanvas @ready="showUI = true"/>
        <HeroOverlay :showUI="showUI"@exit="startExit"/>
    </section>
</template>

<script setup>
import { ref } from "vue"
import HeroCanvas from './HeroCanvas.vue'
import HeroOverlay from './HeroOverlay.vue'
import MatrixRain from "./MatrixRain.vue"

const showUI = ref(false)
</script>