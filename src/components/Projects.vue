<template>
  <section id="projects" class="max-w-5xl mx-auto mt-12 scroll-mt-14">
     <h2 class="text-4xl font-bold text-white mx-4">Projects</h2>
    <p class="mt-2 text-lg text-gray-400 text-justify mx-4">
      A showcase of my work in .NET, Web, & Game Development.
    </p>
    <div class="border-b border-gray-700 mt-4 mb-4"></div>
 
    <!-- Preview Scroller -->
    <div ref="scroller" class="flex space-x-4 overflow-x-auto scrollbar-hide scroll-smooth px-10 pb-4">
      <div 
        v-for="(project, i) in projects" 
        :key="i"
        @click="active = i"
        class="flex-shrink-0 w-64 h-48 rounded-lg cursor-pointer overflow-hidden border-2 transition"
        :class="active === i ? 'border-blue-500' : 'border-gray-700'"
      >
        <img :src="project.image" class="w-full h-full object-cover" />
      </div>
    </div>

    <!-- Active Project Showcase -->
    <transition name="fade">
      <div v-if="projects[active]" class="mt-4 mx-4">
        <img 
          v-if="!projects[active].video"
          :src="projects[active].image" 
          class="w-full max-h-[500px] object-cover rounded-xl shadow-lg"
        />
        <iframe 
          v-else
          :src="projects[active].video"
          class="w-full h-[400px] rounded-xl shadow-lg"
          frameborder="0"
          allowfullscreen
        ></iframe>

        <h2 class="mt-4 text-3xl font-bold">{{ projects[active].title }}</h2>
        <p class="mt-1 text-gray-400 italic">{{ projects[active].stack }}</p>
        <p class="mt-4 whitespace-pre-line text-justify">{{ projects[active].description }}</p>
        <div class="mt-4 flex gap-4 mb-20">
          <a 
            v-if="projects[active].github" 
            :href="projects[active].github" 
            target="_blank" 
            rel="noopener noreferrer"
            class="px-4 py-2 bg-gray-800 hover:bg-gray-700 rounded-lg text-white font-medium"
          >
            GitHub
          </a>
          <a 
            v-if="projects[active].demo" 
            :href="projects[active].demo" 
            target="_blank" 
            rel="noopener noreferrer"
            class="px-4 py-2 bg-blue-600 hover:bg-blue-500 rounded-lg text-white font-medium"
          >
            Live Demo
          </a>
        </div>
      </div>
    </transition>
  </section>
</template>

<script setup>
import { NumberController } from "three/examples/jsm/libs/lil-gui.module.min.js";
import { ref } from "vue"

const active = ref(0)

const projects = [
  {
    title: "Flagship Project",
    stack: "Vue, ThreeJS, Tailwind, Node",
    description: "Of course my flagship project is this very project you're visiting right meow. I spent 6 hours in Blender learning the software for the 3D logo on the landing page. If you weren't aware you can interact with the logo: spin it like crazy, move it, resize it. And the Matrix effects, well that's just paying respects to one of my favorite movie franchises. I'll keep updating as I add more projects. Thanks for stopping by!",
    image: "/images/v3nd3ttiSS.png",
    github: "https://github.com/V3ND3TTi/v3nd3tti.github.io",
    demo: "https://v3ndetti.github.io",
    video: null
  },
  {
    title: "Blazing Pizza",
    stack: "Full Stack w/.NET, ASP.NET Core API (controller), Blazor Server, SQLite DB",
    description: "Capstone project from learning the full .NET web development stack. Built this out to just shy of adding authorization and a payment provider. Maybe I'll add those features in the future but for now I'll be happy with what I've got.",
    image: "/images/BlazingPizzaSS.png",
    github: "https://github.com/V3ND3TTi/BlazingPizza",
    demo: null,
    video: "/videos/BlazingPizza.mp4",
  },
  {
    title: "Construction Runner",
    stack: "Unity, C# WebGL Build",
    description: "Construction Runner is a 3D side scroller where you sprint through an endless worksite filled with danger. Press space to jump over obstacles. Collisions mean instant game over.",
    image: "/images/ConstructionRunner.png",
    github: "https://github.com/V3ND3TTi/Unity6-GameEffects",
    demo: "https://play.unity.com/en/games/fca42332-f14a-4db9-9b08-ec6987578a0a/construction-runner",
    video: null,
  },
  {
    title: "Unity 6.2 Demo",
    stack: "Unity, C#, WebGL Build",
    description: "Fun little tutorial where you take control of a robot, and run around this small scene collecting stars. I'm horrible with MnK so I'm glad controllers are supported out of the box.",
    image: "/images/UnityTutorialSS.png",
    github: "https://github.com/V3ND3TTi/Unity6-Demo",
    demo: "https://play.unity.com/en/games/1cc25514-8524-4ec5-8552-17e7765654dc/unity-6-demo",
    video: null,
  },
  {
    title: "Unity: Inept Guard",
    stack: "Unity, C# WebGL Build",
    description: "Beginner project to get familiar with setting up Unity scenes, game management, and scripting. I might return to this to replace the generic capsules with real character models but for now it's time to move on to more advance Unity topics. NOTE: You won't be able to play this on mobile.",
    image: "/images/IneptGuard.png",
    github: "https://github.com/V3ND3TTi/Unity.Inept-Guard",
    demo: "https://play.unity.com/en/games/0e45439f-3240-4a8d-abfd-faeb35e7153f/inept-guard",
    video: null,
  },
  {
    title: "Connect Four",
    stack: ".NET Blazor Server",
    description: "Connect four game built entirely with Blazor Server.",
    image: "/images/ConnectFourSS.png",
    github: "https://github.com/V3ND3TTi/ConnectFour",
    demo: null,
    video: "/videos/ConnectFour.mp4",
  },
  {
  title: "V's Pizzeria",
  stack: "Svelte Front End, ASP.NET Minimal API, SQLite DB",
  description: "Another project I'm too cheap to host so here's a short video demo. I expanded upon a Microsoft Learn lesson about building minimal APIs by expanding it with an interactive front end to consume the API. All CRUD operations are stored in SQLite DB.",
  image: "/images/PizzaStoreSS.png",
  github: "https://github.com/V3ND3TTi/pizza-store",
  demo: null,
  video: "/videos/PizzaStore.mp4",
  },
  {
    title: "Unity Essentials Scenes",
    stack: "Unity, C#, WebGL Build",
    description: "Interactive Unity prototype showcasing multiple scenes from the Unity Essentials pathway. NOTE: You won't be able to play this on mobile.",
    image: "/images/UnityEssentialsSS.png",
    github: "https://github.com/V3ND3TTi/Unity-Essentials",
    demo: "https://play.unity.com/en/games/e69c4cde-4ffe-4b4e-91b2-e449cc0f31e9/webbuild",
    video: null
  },
  {
    title: "Modern Web aka PRESTIGE WORLDWIDE",
    stack: "C#, .NET, Blazor Server, SQLite",
    description: ".NET Blazor Server w/ASP.NET API. SQLite for the DB. Fun project but I'm too cheap to host it for a live demo so here's a video.",
    image: "/images/PrestigeWorldwideSS.png",
    github: "https://github.com/V3ND3TTi/ModernWeb",
    demo: null,
    video: "/videos/ModernWeb.mp4",
  },
  {
    title: "KoinLab",
    stack: "NextJS (React), TypeScript, Tailwind",
    description: "This is the latest version of KoinLab, one of my personal sites. Mostly just practice to consume CoinGecko's API for live prices. I planned on launching my blockchain project through KoinLab but found out there was already a CoinLab. Not that I'm ever going to launch my crypto project.",
    image: "/images/koinlabSS.png",
    github: "https://github.com/V3ND3TTi/KoinLab-Nextjs",
    demo: "https://koinlab.net",
    video: null,
  },
  {
    title: "KoinLab.NET",
    stack: ".NET Blazor WASM, Azure",
    description: "My site koinlab.net, except hosted on Azure now since I replaced it with the NextJS version.",
    image: "/images/koinlabNetSS.png",
    github: "https://github.com/V3ND3TTi/KoinLab.NET",
    demo: "https://agreeable-field-06a85f61e.4.azurestaticapps.net",
    video: null,
  },
  {
    title: "Pong",
    stack: "HTML, CSS, JavaScript",
    description: "Want to play the worst game of pong ever?! This is where you can do it! I should eventually go back and tweak this to improve the gameplay. Considering the stack it was built with (HTML5 Canvas) it's slightly impressive.",
    image: "/images/pongSS.png",
    github: "https://github.com/V3ND3TTi/HTML5-Canvas-Pong",
    demo: "https://v3nd3tti.github.io/HTML5-Canvas-Pong",
    video: null,
  },
  {
    title: "CW Collections V2",
    stack: "Astro",
    description: "Remake of the original using Astro. I though Astro was the greatest thing since sliced bread (at the time, early 2023).",
    image: "/images/cwastroSS.png",
    github: "https://github.com/V3ND3TTi/cw-astro",
    demo: "https://cw-collections.netlify.app",
    video: null,
  },
  {
    title: "Cindy Wu Collections",
    stack: "Vanilla!! HTML, CSS & JQuery 😂",
    description: "I spent so much time on this site, it's kinda wild thinking back to this. I ended up making many different versions of this site to practice new stacks but this was the very first back in 2022. Can't believe it's been 3 years already.",
    image: "/images/cwcSS.png",
    github: "https://github.com/V3ND3TTi/CWsite",
    demo: "https://v3nd3tti.github.io/CWsite",
    video: null,
  },
  {
    title: "vendetti.DEV",
    stack: "Astro",
    description: "One of the many iterations my personal site has taken on over the years. First, there was dv3.dev and then vendetti.dev. Believe this was built in early 2023.",
    image: "images/dotdevSS.png",
    github: "https://github.com/V3ND3TTi/dv3-astro",
    demo: "https://v1dotdev.netlify.app",
    video: null,
  },
  {
    title: "DV3",
    stack: "HTML, CSS & JQuery",
    image: "/images/dv3SS.png",
    description: "Hilarious looking back and realizing I used the same JQuery across almost all my sites in 2022 & 2023 🤣. I was so proud of DV3.dev at the time though. The typewriter on the landing page was next level for me.",
    github: "https://github.com/V3ND3TTi/DV3",
    demo: "https://v3nd3tti.github.io/DV3",
    video: null,
  },
  {
    title: "The most adorable penguin EVER!",
    stack: "Pure CSS",
    image: "/images/fccpenguinSS.png",
    description: "In 2021, I was learning Python and blockchain (and not learning either very well). In 2022, came my run at web development. First some courses on Udemy, and then freeCodeCamp where I created this little guy. It's been quite the journey!",
    github: null,
    demo: "https://codepen.io/V3ND3TTi/pen/BamQgNN",
    video: null,
  },
]
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
