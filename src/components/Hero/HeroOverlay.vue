<template>
  <!-- 🔹 Top Nav -->
  <nav v-show="showUI"
       class="absolute top-0 right-0 flex space-x-6 text-sm lg:text-lg font-semibold p-6 text-white z-10 transition-opacity duration-1000"
       :class="{ 'opacity-100': showUI, 'opacity-0': !showUI }">
    <button @click="$emit('exit', 'about')" class="hover:text-blue-400 transition">About</button>
    <button @click ="$emit('exit', 'projects')" class="hover:text-blue-400 transition">Projects</button>
    <button @click ="$emit('exit', 'contact')" class="hover:text-blue-400 transition">Contact</button>
  </nav>

  <!-- 🔹 Tagline -->
  <div v-show="showUI"
       class="absolute bottom-32 md:bottom-48 lg:bottom-64 w-full flex flex-col items-center text-center text-white z-10 transition-opacity duration-1000 pointer-events-none"
       :class="{ 'opacity-100': showUI, 'opacity-0': !showUI }">
    <p class="text-md md:text-2xl lg:text-4xl font-light tracking-tighter lg:tracking-wider">
      .NET C# DEV 👨‍💻 WEB DEV 🎮 GAME DEV
    </p>
  </div>

  <!-- 🔹 Socials -->
  <div v-show="showUI"
       class="absolute bottom-6 w-full flex justify-center space-x-8 md:space-x-12 text-white z-10 transition-opacity duration-1000"
       :class="{ 'opacity-100': showUI, 'opacity-0': !showUI }">
    <a href="https://github.com/v3nd3tti" target="_blank"
       class="text-2xl md:text-6xl hover:text-blue-400 hover:scale-110 transition-transform duration-200">
      <i class="fa-brands fa-github"></i>
    </a>
    <a href="https://linkedin.com/in/v3nd3tti" target="_blank"
       class="text-2xl md:text-6xl hover:text-blue-400 hover:scale-110 transition-transform duration-200">
      <i class="fa-brands fa-linkedin"></i>
    </a>
  </div>
</template>

<script setup>
const emit = defineEmits(['exit'])

defineProps({
  showUI: {
    type: Boolean,
    default: true
  }
})
</script>