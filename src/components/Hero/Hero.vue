<template>
    <section 
        id="hero" 
        class="fixed inset-0 w-full h-screen overflow-hidden z-50 bg-black transition-opacity duration-700"
        :class="{ 'opacity-0': exiting, 'opaticity': !exiting }"
    >
        <MatrixRain />
        <HeroCanvas @ready="showUI = true"/>
        <HeroOverlay :showUI="showUI" @exit="startExit"/>
    </section>
</template>

<script setup>
import { ref } from "vue"
import HeroCanvas from './HeroCanvas.vue'
import HeroOverlay from './HeroOverlay.vue'
import MatrixRain from "./MatrixRain.vue"

const showUI = ref(false)
const exiting = ref(false)

const emit = defineEmits(['exit'])

function startExit(targetId) {
    exiting.value = true
    setTimeout(() => {
        emit('exit', targetId) // bubble up to App.vue after fade out
    }, 700) // match duration 700 above
}
</script>