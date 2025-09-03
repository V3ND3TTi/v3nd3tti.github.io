<template>
  <nav class="fixed top-0 left-0 w-full bg-gray-900/80 backdrop-blur-md z-50 border-b border-gray-800">
    <div class="max-w-6xl mx-auto flex justify-between items-center px-6 py-3 text-white">
      
      <!-- Home -->
      <button @click="goHome" class="text-xl font-bold text-blue-400 hover:text-blue-300">
        Home
      </button>

      <!-- Links -->
      <div class="flex space-x-6">
        <a href="#about" class="hover:text-blue-400 transition">About</a>
        <a href="#projects" class="hover:text-blue-400 transition">Projects</a>
        <a href="#contact" class="hover:text-blue-400 transition">Contact</a>
      </div>
    </div>
  </nav>
</template>

<script setup>
const emit = defineEmits(['goHome'])

function goHome() {
  emit('goHome')
}
</script>
