<template>
  <section id="about" class="min-h-screen flex items-center justify-center bg-gray-900 text-white px-6 py-16">
    <Transition
      enter-active-class="transition duration-1000 ease-out"
      enter-from-class="opacity-0 translate-y-6"
      enter-to-class="opacity-100 translate-y-0"
    >
      <div v-if="visible" class="max-w-3xl text-center space-y-6">
        <h2 class="text-4xl font-bold text-blue-400">About Me</h2>
        <p class="text-lg leading-relaxed">
          I’m <span class="font-semibold">Devon Vendetti</span>, a C# / .NET developer with a
          background in systems support and a passion for building everything
          from web apps to blockchain projects.
        </p>

        <ul class="space-y-2 text-blue-300">
          <li>• C# / .NET 9 / Blazor</li>
          <li>• Unity Game Development</li>
          <li>• Rust & Go</li>
          <li>• Blockchain (KredChain)</li>
        </ul>
      </div>
    </Transition>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue"

const visible = ref(false)
let observer

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) visible.value = true
    },
    { threshold: 0.2 }
  )
  observer.observe(document.getElementById("about"))
})

onBeforeUnmount(() => observer?.disconnect())
</script>
