<template>
  <section id="skills" class="py-24 px-6 sm:px-12 max-w-5xl mx-auto relative">
    
    <!-- Decorative background glow -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[120%] h-96 bg-brand-blue/5 blur-[120px] rounded-full pointer-events-none z-0"></div>

    <div class="flex flex-col items-center mb-14 relative z-10">
      <div class="section-pill text-brand-blue skills-reveal shadow-lg shadow-brand-blue/5 mb-3">◇ Mis Habilidades</div>
      <h2 class="text-4xl sm:text-5xl font-extrabold text-center skills-reveal" style="transition-delay: 0.1s">
        Mi stack <span class="text-gradient-blue">tecnológico</span>
      </h2>
      <p class="text-slate-400 mt-4 text-center max-w-xl skills-reveal text-lg" style="transition-delay: 0.2s">
        Mis herramientas favoritas organizadas en su propio ecosistema. ✨
      </p>
    </div>

    <!-- 2x2 Bento Grid -->
    <div class="relative w-full">
      <!-- Use negative margins to let the scroll bleed to the edge of the screen -->
      <div class="flex md:grid overflow-x-auto md:overflow-visible snap-x snap-mandatory md:snap-none pb-4 md:pb-0 grid-cols-1 md:grid-cols-2 gap-4 md:gap-6 relative z-10 [&::-webkit-scrollbar]:hidden [-ms-overflow-style:none] [scrollbar-width:none] -mx-6 px-6 sm:-mx-12 sm:px-12 md:mx-0 md:px-0 touch-pan-x overscroll-x-contain">
        
        <!-- Frontend -->
        <div class="min-w-[85vw] sm:min-w-[70vw] md:min-w-0 snap-center glass-card p-6 sm:p-8 rounded-[2rem] skills-reveal border border-white/5 hover:border-brand-pink/40 hover:shadow-[0_10px_40px_-10px_rgba(245,198,216,0.25)] transition-all duration-500 overflow-hidden relative group" style="transition-delay: 0.2s">
          <div class="absolute -top-16 -right-16 w-48 h-48 bg-brand-pink/20 blur-[60px] rounded-full group-hover:bg-brand-pink/30 group-hover:scale-110 transition-all duration-700"></div>
          <div class="absolute inset-0 bg-gradient-to-br from-[#0C0F22]/90 to-[#0C0F22]/60 -z-10"></div>
          
          <div class="flex items-center gap-4 mb-6">
            <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-pink/20 to-transparent border border-brand-pink/30 flex items-center justify-center text-3xl shadow-inner group-hover:rotate-12 transition-transform duration-500">🎨</div>
            <h3 class="text-2xl font-extrabold text-white tracking-wide">Frontend</h3>
          </div>
          
          <div class="flex flex-wrap gap-3">
            <span v-for="s in frontend" :key="s.name" 
              class="group/skill flex items-center gap-2 px-4 py-2.5 rounded-xl bg-[#1A1E4A]/50 border border-white/5 font-semibold text-sm text-slate-300 transition-all duration-300 hover:-translate-y-1 hover:bg-brand-pink/15 hover:border-brand-pink/50 hover:text-white cursor-default shadow-sm hover:shadow-lg hover:shadow-brand-pink/20">
              <span class="text-lg group-hover/skill:scale-125 group-hover/skill:rotate-6 transition-transform duration-300">{{ s.icon }}</span> 
              <span>{{ s.name }}</span>
            </span>
          </div>
        </div>

        <!-- Backend -->
        <div class="min-w-[85vw] sm:min-w-[70vw] md:min-w-0 snap-center glass-card p-6 sm:p-8 rounded-[2rem] skills-reveal border border-white/5 hover:border-brand-blue/40 hover:shadow-[0_10px_40px_-10px_rgba(184,212,240,0.25)] transition-all duration-500 overflow-hidden relative group" style="transition-delay: 0.3s">
          <div class="absolute -top-16 -right-16 w-48 h-48 bg-brand-blue/20 blur-[60px] rounded-full group-hover:bg-brand-blue/30 group-hover:scale-110 transition-all duration-700"></div>
          <div class="absolute inset-0 bg-gradient-to-br from-[#0C0F22]/90 to-[#0C0F22]/60 -z-10"></div>
          
          <div class="flex items-center gap-4 mb-6">
            <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-blue/20 to-transparent border border-brand-blue/30 flex items-center justify-center text-3xl shadow-inner group-hover:-rotate-12 transition-transform duration-500">⚙️</div>
            <h3 class="text-2xl font-extrabold text-white tracking-wide">Backend</h3>
          </div>
          
          <div class="flex flex-wrap gap-3">
            <span v-for="s in backend" :key="s.name" 
              class="group/skill flex items-center gap-2 px-4 py-2.5 rounded-xl bg-[#1A1E4A]/50 border border-white/5 font-semibold text-sm text-slate-300 transition-all duration-300 hover:-translate-y-1 hover:bg-brand-blue/15 hover:border-brand-blue/50 hover:text-white cursor-default shadow-sm hover:shadow-lg hover:shadow-brand-blue/20">
              <span class="text-lg group-hover/skill:scale-125 group-hover/skill:-rotate-6 transition-transform duration-300">{{ s.icon }}</span> 
              <span>{{ s.name }}</span>
            </span>
          </div>
        </div>

        <!-- Mobile -->
        <div class="min-w-[85vw] sm:min-w-[70vw] md:min-w-0 snap-center glass-card p-6 sm:p-8 rounded-[2rem] skills-reveal border border-white/5 hover:border-brand-mint/40 hover:shadow-[0_10px_40px_-10px_rgba(184,232,216,0.25)] transition-all duration-500 overflow-hidden relative group" style="transition-delay: 0.4s">
          <div class="absolute -bottom-16 -left-16 w-48 h-48 bg-brand-mint/20 blur-[60px] rounded-full group-hover:bg-brand-mint/30 group-hover:scale-110 transition-all duration-700"></div>
          <div class="absolute inset-0 bg-gradient-to-br from-[#0C0F22]/90 to-[#0C0F22]/60 -z-10"></div>
          
          <div class="flex items-center gap-4 mb-6">
            <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-mint/20 to-transparent border border-brand-mint/30 flex items-center justify-center text-3xl shadow-inner group-hover:rotate-12 transition-transform duration-500">📱</div>
            <h3 class="text-2xl font-extrabold text-white tracking-wide">Mobile</h3>
          </div>
          
          <div class="flex flex-wrap gap-3">
            <span v-for="s in mobile" :key="s.name" 
              class="group/skill flex items-center gap-2 px-4 py-2.5 rounded-xl bg-[#1A1E4A]/50 border border-white/5 font-semibold text-sm text-slate-300 transition-all duration-300 hover:-translate-y-1 hover:bg-brand-mint/15 hover:border-brand-mint/50 hover:text-white cursor-default shadow-sm hover:shadow-lg hover:shadow-brand-mint/20">
              <span class="text-lg group-hover/skill:scale-125 group-hover/skill:rotate-6 transition-transform duration-300">{{ s.icon }}</span> 
              <span>{{ s.name }}</span>
            </span>
          </div>
        </div>

        <!-- Tools -->
        <div class="min-w-[85vw] sm:min-w-[70vw] md:min-w-0 snap-center glass-card p-6 sm:p-8 rounded-[2rem] skills-reveal border border-white/5 hover:border-brand-lilac/40 hover:shadow-[0_10px_40px_-10px_rgba(212,179,232,0.25)] transition-all duration-500 overflow-hidden relative group" style="transition-delay: 0.5s">
          <div class="absolute -bottom-16 -left-16 w-48 h-48 bg-brand-lilac/20 blur-[60px] rounded-full group-hover:bg-brand-lilac/30 group-hover:scale-110 transition-all duration-700"></div>
          <div class="absolute inset-0 bg-gradient-to-br from-[#0C0F22]/90 to-[#0C0F22]/60 -z-10"></div>
          
          <div class="flex items-center gap-4 mb-6">
            <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-brand-lilac/20 to-transparent border border-brand-lilac/30 flex items-center justify-center text-3xl shadow-inner group-hover:-rotate-12 transition-transform duration-500">🛠️</div>
            <h3 class="text-2xl font-extrabold text-white tracking-wide">Herramientas</h3>
          </div>
          
          <div class="flex flex-wrap gap-3">
            <span v-for="s in tools" :key="s.name" 
              class="group/skill flex items-center gap-2 px-4 py-2.5 rounded-xl bg-[#1A1E4A]/50 border border-white/5 font-semibold text-sm text-slate-300 transition-all duration-300 hover:-translate-y-1 hover:bg-brand-lilac/15 hover:border-brand-lilac/50 hover:text-white cursor-default shadow-sm hover:shadow-lg hover:shadow-brand-lilac/20">
              <span class="text-lg group-hover/skill:scale-125 group-hover/skill:-rotate-6 transition-transform duration-300">{{ s.icon }}</span> 
              <span>{{ s.name }}</span>
            </span>
          </div>
        </div>

      </div>
    </div>

    <!-- Swipe indicator at bottom -->
    <div class="md:hidden flex items-center justify-center mt-6 gap-2 opacity-80">
      <span class="text-[0.65rem] font-bold uppercase tracking-widest text-brand-pink">Desliza para ver más</span>
      <div class="w-6 h-6 rounded-full flex items-center justify-center text-brand-pink animate-bounce-right">
        <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const frontend = [
  { name: 'Vue.js', icon: '💚' },
  { name: 'Angular', icon: '🔴' },
  { name: 'JavaScript', icon: '🟡' },
  { name: 'TypeScript', icon: '🔷' },
  { name: 'HTML5', icon: '🧡' },
  { name: 'CSS3', icon: '💙' },
  { name: 'Tailwind CSS', icon: '🌊' },
  { name: 'Bootstrap', icon: '💜' },
];

const backend = [
  { name: 'Java', icon: '☕' },
  { name: 'PHP', icon: '🐘' },
  { name: 'PostgreSQL', icon: '🐘' },
  { name: 'MySQL', icon: '🗄️' },
];

const mobile = [
  { name: 'Kotlin', icon: '🟣' },
  { name: 'Ionic', icon: '⚡' },
  { name: 'Android Studio', icon: '🤖' },
];

const tools = [
  { name: 'Git', icon: '🔀' },
  { name: 'AWS', icon: '☁️' },
  { name: 'Antigravity', icon: '🚀' },
  { name: 'IntelliJ IDEA', icon: '🧠' },
  { name: 'VS Code', icon: '💻' },
  { name: 'XML', icon: '📄' },
];

onMounted(() => {
  gsap.fromTo('.skills-reveal',
    { opacity: 0, y: 30 },
    {
      opacity: 1, y: 0, duration: 0.8, stagger: 0.15, ease: 'power3.out',
      scrollTrigger: { trigger: '#skills', start: 'top 80%' }
    }
  );
});
</script>
