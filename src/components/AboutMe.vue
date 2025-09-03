<template>
  <section id="about" class="min-h-screen bg-gray-900 text-white px-6 py-16">
    <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-12">
      
      <!-- Left Column: Profile + About -->
      <div class="lg:col-span-1 flex flex-col items-center lg:items-start space-y-6">
        <img
          src="/profile.jpg"
          alt="Devon Vendetti"
          class="rounded-xl shadow-lg max-w-xs"
        />
        <div>
          <h2 class="text-4xl font-bold text-blue-400 mb-4">About Me</h2>
          <p class="text-lg leading-relaxed text-gray-300">
            Aspiring <span class="font-semibold">C# / .NET Developer</span> with a background in
            <span class="font-semibold">technical support</span>. Focused on building
            <span class="font-semibold">modern web apps with .NET</span>, creating
            <span class="font-semibold">cross-platform mobile apps with MAUI</span>,
            and exploring <span class="font-semibold">Unity game development</span>.
          </p>
        </div>
      </div>

      <!-- Right Column: Technical Skills -->
      <div class="lg:col-span-2 space-y-8">
        <h3 class="text-3xl font-bold text-blue-300">Technical Skills</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <!-- Front End -->
          <div class="bg-gray-800 rounded-xl shadow-lg p-6">
            <h4 class="text-xl font-semibold text-blue-200 mb-3">Front End</h4>
            <ul class="space-y-1 text-gray-300">
              <li>Blazor (C#)</li>
              <li>JavaScript / TypeScript</li>
              <li>Vue.js</li>
              <li>HTML5 / CSS3</li>
              <li>Tailwind CSS</li>
              <li>Three.js</li>
            </ul>
          </div>

          <!-- Back End -->
          <div class="bg-gray-800 rounded-xl shadow-lg p-6">
            <h4 class="text-xl font-semibold text-blue-200 mb-3">Back End</h4>
            <ul class="space-y-1 text-gray-300">
              <li>C#</li>
              <li>ASP.NET Core</li>
              <li>Node.js</li>
              <li>RESTful APIs</li>
              <li>SQL</li>
            </ul>
          </div>

          <!-- Game Development -->
          <div class="bg-gray-800 rounded-xl shadow-lg p-6">
            <h4 class="text-xl font-semibold text-blue-200 mb-3">Game Development</h4>
            <ul class="space-y-1 text-gray-300">
              <li>Unity</li>
              <li>C# Scripting</li>
              <li>WebGL Builds</li>
              <li>Blender 3D Modeling</li>
            </ul>
          </div>

          <!-- Mobile / Cross Platform -->
          <div class="bg-gray-800 rounded-xl shadow-lg p-6">
            <h4 class="text-xl font-semibold text-blue-200 mb-3">Mobile / Cross Platform</h4>
            <ul class="space-y-1 text-gray-300">
              <li>.NET MAUI</li>
              <li>XAML UI Design</li>
              <li>MVVM Pattern</li>
              <li>Android & iOS Deployment</li>
            </ul>
          </div>

          <!-- Dev Tools -->
          <div class="bg-gray-800 rounded-xl shadow-lg p-6">
            <h4 class="text-xl font-semibold text-blue-200 mb-3">Dev Tools</h4>
            <ul class="space-y-1 text-gray-300">
              <li>Visual Studio</li>
              <li>VS Code</li>
              <li>Git / GitHub</li>
              <li>npm</li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- Bottom Row: Certs + Education -->
    <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-8 mt-16">
      
      <!-- Certifications -->
      <div>
        <h3 class="text-3xl font-bold text-blue-300 mb-6">Certifications</h3>
        <div class="bg-gray-800 rounded-xl shadow-lg p-6">
          <ul class="list-disc list-inside text-gray-300 space-y-2">
            <li>Microsoft Applied Skills: ASP.NET Core Web App</li>
            <li>Microsoft Applied Skills: C# Classes & Methods</li>
            <li>Foundational C# with Microsoft – freeCodeCamp</li>
            <li>Microsoft Azure Fundamentals (AZ-900)</li>
            <li>Unity: Game Design Essentials</li>
          </ul>
        </div>
      </div>

      <!-- Education -->
      <div>
        <h3 class="text-3xl font-bold text-blue-300 mb-6">Education</h3>
        <div class="bg-gray-800 rounded-xl shadow-lg p-6">
          <ul class="space-y-4 text-gray-300">
            <li>
              <span class="font-semibold">Western Governors University</span> — B.S. Software Engineering (2025–2027)
            </li>
            <li>
              <span class="font-semibold">Full Sail University</span> — Game Design & Development (2003–2004)
            </li>
            <li>
              <span class="font-semibold">Community College of the Air Force</span> — Electrical Systems (1997–2003)
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
