<template>
  <section id="projects" class="py-32 px-6 sm:px-12 max-w-7xl mx-auto relative">
    <!-- Header -->
    <div class="flex flex-col items-center mb-20">
      <div class="section-pill text-brand-lilac project-reveal">✦ Mis Proyectos</div>
      <h2 class="text-4xl sm:text-6xl font-extrabold mt-3 project-reveal text-center" style="transition-delay: 0.1s">
        Soluciones <span class="text-gradient-main">digitales</span> con impacto
      </h2>
      <p class="text-slate-400 mt-6 max-w-2xl text-center project-reveal text-lg" style="transition-delay: 0.2s">
        Una selección de mis trabajos más recientes, donde combino diseño minimalista y funcionalidad avanzada.
      </p>
    </div>

    <!-- Projects Grid -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-10 sm:gap-16">
      <div v-for="(project, index) in projects" :key="index" 
           class="project-card-container group project-reveal"
           :style="{ transitionDelay: (0.3 + index * 0.15) + 's' }">
        
        <div class="glass-card h-full flex flex-col overflow-hidden border border-white/5 hover:border-brand-lilac/30 transition-all duration-500 rounded-[2.5rem]">
          <!-- Image Container -->
          <div class="relative aspect-video overflow-hidden">
            <img :src="project.image" :alt="project.title" 
                 class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110" />
            <div class="absolute inset-0 bg-gradient-to-t from-[#0A0C1C] via-transparent to-transparent opacity-60"></div>
            
            <!-- Tech Stack Overlay -->
            <div class="absolute top-4 right-4 flex gap-2">
              <span v-for="tech in project.stack" :key="tech" 
                    class="px-3 py-1 rounded-full bg-black/40 backdrop-blur-md border border-white/10 text-[0.65rem] font-bold uppercase tracking-wider text-white">
                {{ tech }}
              </span>
            </div>
          </div>

          <!-- Content -->
          <div class="p-8 sm:p-10 flex flex-col flex-1">
            <h3 class="text-2xl sm:text-3xl font-bold mb-4 group-hover:text-brand-lilac transition-colors duration-300">
              {{ project.title }}
            </h3>
            <p class="text-slate-400 leading-relaxed mb-8 flex-1">
              {{ project.description }}
            </p>
            
            <div class="flex items-center gap-6 mt-auto">
              <a :href="project.demo" target="_blank" 
                 class="btn-primary !px-8 !py-3 flex items-center gap-2 group/btn">
                Ver Live Demo
                <span class="text-xl transition-transform duration-300 group-hover/btn:translate-x-1">🚀</span>
              </a>
              <a v-if="project.github" :href="project.github" target="_blank"
                 class="text-slate-400 hover:text-white transition-colors flex items-center gap-2 font-medium">
                GitHub ↗
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

// Import images from assets
import animeImg from '../assets/projects/anime.jpg';
import helioImg from '../assets/projects/vision.png';

gsap.registerPlugin(ScrollTrigger);

const projects = [
  {
    title: 'Anime Tracker',
    description: 'Una aplicación sofisticada para gestionar y seguir tus series favoritas. Incluye sistema de autenticación, base de datos en tiempo real con Firebase, traducciones automáticas y una interfaz glassmorphism ultra pulida.',
    image: animeImg,
    stack: ['Vue 3', 'Firebase', 'GSAP', 'Tailwind'],
    demo: 'https://beacao.github.io/Anime-Tracker/',
    github: 'https://github.com/beacao/Anime-Tracker'
  },
  {
    title: 'HELIO Vision Store',
    description: 'E-commerce premium de estética Apple para el futuro de la computación espacial. Con configurador de productos dinámico, animaciones de alto nivel y una experiencia de usuario fluida y minimalista.',
    image: helioImg,
    stack: ['Vue 3', 'Vite', 'GSAP', 'i18n'],
    demo: 'https://beacao.github.io/helio-vision-ecommerce/',
    github: 'https://github.com/beacao/helio-vision-ecommerce'
  }
];

onMounted(() => {
  gsap.fromTo('.project-reveal',
    { opacity: 0, y: 60 },
    {
      opacity: 1, y: 0, duration: 1, stagger: 0.2, ease: 'power4.out',
      scrollTrigger: {
        trigger: '#projects',
        start: 'top 80%',
      }
    }
  );
});
</script>

<style scoped>
.project-card-container {
  perspective: 1000px;
}
</style>
