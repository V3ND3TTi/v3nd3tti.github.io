<template>
     <!-- Tagline centered above pinned social linkes -->
    <div
      id="overlay"
      v-show="showUI"
      class="absolute bottom-16 md:bottom-32 lg:bottom-48 w-full flex flex-col items-center justify-center text-center text-white z-10 pointer-events-none transition-opacity duration-1000"
      :class="{ 'opacity-100': showUI, 'opacity-0': !showUI }"
    >
      <p class="text-md md:text-2xl lg:text-4xl font-light tracking-tighter lg:tracking-wider">
        .NET C# DEV 👨‍💻 WEB DEV 🎮 GAME DEV
      </p>
    </div>

    <!-- Social links pinned at bottom -->
    <div 
      id="socials"
      v-show="showUI"
      class="absolute bottom-6 w-full flex justify-center space-x-8 md:space-x-12 text-white z-10 transition-opacity duration-1000"
      :class="{ 'opacity-100': showUI, 'opacity-0': !showUI }"
    >
      <a href="https://github.com/v3nd3tti" target="_blank" class="text-2xl md:text-6xl hover:text-blue-400 hover:scale-110 transition-transform duration-200"><i class="fa-brands fa-github"></i></a>
      <a href="https://linkedin.com/in/v3nd3tti" target="_blank" class="text-2xl md:text-6xl hover:text-blue-400 hover:scale-110 transition-transform duration-200"><i class="fa-brands fa-linkedin"></i></a>
    </div>
</template>

<script setup>
defineProps({
    showUI: {
        type: Boolean,
        default: true
    }
})
</script>
