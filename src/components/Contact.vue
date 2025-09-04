<template>
  <section class="min-h-screen bg-black text-white flex flex-col py-12">
    <!-- Marquee Header -->
    <div class="overflow-hidden whitespace-nowrap border-b border-gray-700">
      <div class="animate-marquee inline-block">
        <span class="text-6xl font-bold py-4">
          Hello!&nbsp;¡Hola!&nbsp;Bonjour!&nbsp;Hallo!&nbsp;Ciao!&nbsp;こんにちは!&nbsp;안녕하세요!&nbsp;你好!&nbsp;नमस्ते!&nbsp; 
        </span>
        <span class="text-6xl font-bold py-4">
          Hello!&nbsp;¡Hola!&nbsp;Bonjour!&nbsp;Hallo!&nbsp;Ciao!&nbsp;こんにちは!&nbsp;안녕하세요!&nbsp;你好!&nbsp;नमस्ते!&nbsp; 
        </span>
      </div>
    </div>

    <!-- Contact Section -->
    <div class="flex flex-col md:flex-row flex-grow">
      <!-- Left Side -->
      <div class="md:w-1/2 p-10 flex flex-col justify-center">
        <h2 class="text-5xl font-bold mb-6">Get In Touch</h2>
        <p class="text-lg text-gray-400 mb-6">
          Whether you want to collaborate, hire me, or just talk shop —
          drop me a message. I’ll get back to you soon.
        </p>
        <div class="space-x-6 text-2xl">
          <a href="https://github.com/v3nd3tti" target="_blank" class="hover:text-purple-400">GitHub</a>
          <a href="https://www.linkedin.com/in/v3nd3tti/" target="_blank" class="hover:text-purple-400">LinkedIn</a>
        </div>
      </div>

      <!-- Right Side -->
      <div class="md:w-1/2 p-10 flex items-center justify-center">
        <form 
          action="https://formspree.io/f/mblapzao" 
          method="POST"
          target="_blank"
          class="w-full max-w-md space-y-6"
        >
          <div>
            <label class="block text-sm text-gray-400 mb-2">Name</label>
            <input 
              type="text" 
              name="name" 
              required 
              class="w-full px-4 py-2 bg-gray-900 border border-gray-700 rounded focus:ring-2 focus:ring-purple-500"
            />
          </div>
          <div>
            <label class="block text-sm text-gray-400 mb-2">Email</label>
            <input 
              type="email" 
              name="email" 
              required 
              class="w-full px-4 py-2 bg-gray-900 border border-gray-700 rounded focus:ring-2 focus:ring-purple-500"
            />
          </div>
          <div>
            <label class="block text-sm text-gray-400 mb-2">Message</label>
            <textarea 
              name="message" 
              rows="5" 
              required 
              class="w-full px-4 py-2 bg-gray-900 border border-gray-700 rounded focus:ring-2 focus:ring-purple-500"
            ></textarea>
          </div>
          <button 
            type="submit"
            class="w-full bg-purple-700 text-white font-bold py-3 px-6 rounded-lg transition"
          >
            Send Message
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
// nothing needed here, purely static form
</script>

<style>
/* Scrolling marquee animation */
@keyframes marquee {
  0% { transform: translateX(0%); }
  100% { transform: translateX(-50%); }
}

.animate-marquee {
  display: inline-block;
  white-space: nowrap;
  animation: marquee 20s linear infinite;
}
</style>
