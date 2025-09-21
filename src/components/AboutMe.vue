<template>
  <section id="about" class="min-h-screen text-white px-6 py-16">
    <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-12">
      <!-- Profile + About stays as-is -->
      <div class="lg:col-span-1 flex flex-col items-center lg:items-start space-y-6">
        <img
          src="/images/profile.jpg"
          alt="Devon Vendetti"
          class="rounded-xl shadow-lg max-w-xs"
        />
        <div>
          <h2 class="text-4xl font-bold text-blue-400 mb-4">About Me</h2>
          <p class="text-lg leading-relaxed text-gray-300">
            Support Specialist transitioning from systems support to general IT support. Outside of IT, I enjoy web development, Unity / Unreal game development, and working on blockchain projects, giving me a unique blend of support and programming experience.
          </p>
        </div>
      </div>

      <!-- Right Column: Technical Skills with animation -->
      <div class="lg:col-span-2 space-y-8">
        <h3 class="text-3xl font-bold text-blue-300">Technical Skills</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="(card, i) in skills"
            :key="i"
            ref="skillCards"
            class="bg-gray-800 rounded-xl shadow-lg p-6 opacity-0 translate-y-6 transition-all duration-700"
          >
            <h4 class="text-xl font-semibold text-blue-200 mb-3">{{ card.title }}</h4>
            <ul class="space-y-1 text-gray-300">
              <li v-for="(item, j) in card.items" :key="j">{{ item }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- Bottom Row: Certs + Education with animation -->
    <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-5 gap-8 mt-16">
      <div ref="certs" class="bg-gray-800 rounded-xl shadow-lg p-6 md:col-span-2 opacity-0 translate-y-6 transition-all duration-700">
        <h3 class="text-3xl font-bold text-blue-300 mb-6">Certifications</h3>
        <ul class="list-disc list-inside text-gray-300 space-y-2">
          <li v-for="cert in certifications" :key="cert">{{ cert }}</li>
        </ul>
      </div>

      <div ref="edu" class="bg-gray-800 rounded-xl shadow-lg p-6 md:col-span-3 opacity-0 translate-y-6 transition-all duration-700">
        <h3 class="text-3xl font-bold text-blue-300">Education</h3>
        <ul class="space-y-4 text-gray-300">
          <li v-for="edu in education" :key="edu.institution">
            <span class="font-semibold">{{ edu.institution }}</span> — {{ edu.details }}
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const skills = [
  { title: 'Front End', items: ['Blazor (C#)', 'JavaScript / TypeScript', 'Vue.js', 'HTML5 / CSS3', 'Tailwind CSS', 'Three.js'] },
  { title: 'Back End', items: ['C#', 'ASP.NET Core', 'Node.js', 'RESTful APIs', 'SQL'] },
  { title: 'Game Development', items: ['Unity', 'C# Scripting', 'Unreal Engine', 'C++ / Blueprint Scripting', 'Blender 3D Modeling'] },
  { title: 'Mobile / Cross Platform', items: ['.NET MAUI', 'XAML UI Design', 'MVVM Pattern', 'Android & iOS Deployment'] },
  { title: 'Dev Tools', items: ['Visual Studio', 'VS Code', 'Git / GitHub', 'npm'] }
]

const certifications = [
  'ISC2 Certified in Cybersecurity (CC)',
  'Microsoft IT Support Specialist (Coursera)',
  'COMPTIA A+ (In Progress)',
  'COMPTIA Network+ (In Progress)',
  'ITIL 4 Foundation (In Progress)',
  'Microsoft Azure Fundamentals (AZ-900)',
  'Unity: Junior Programmer / Essentials',
  'Microsoft Applied Skills: ASP.NET Core Web Api',
  'Microsoft Applied Skills: C# Classes & Methods',
  'Foundational C# with Microsoft – freeCodeCamp',
]

const education = [
  { institution: 'Western Governors University', details: 'Information Technology, B.S. (2025–2027)' },
  { institution: 'Full Sail University', details: 'Game Design & Development (2003–2004)' },
  { institution: 'Air University (Air Force)', details: 'Electrical Systems Tech (1997–2003)' }
]

const skillCards = ref([])
const certs = ref(null)
const edu = ref(null)
let observer

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.remove('opacity-0', 'translate-y-6')
          entry.target.classList.add('opacity-100', 'translate-y-0')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.2 }
  )

  skillCards.value.forEach(el => observer.observe(el))
  if (certs.value) observer.observe(certs.value)
  if (edu.value) observer.observe(edu.value)
})

onBeforeUnmount(() => observer?.disconnect())
</script>
