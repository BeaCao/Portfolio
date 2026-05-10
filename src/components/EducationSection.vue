<template>
  <section id="education" class="py-24 px-6 sm:px-12 max-w-5xl mx-auto relative overflow-hidden">
    
    <!-- Ambient Glow Background -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[120%] h-[600px] bg-brand-lilac/10 blur-[150px] rounded-full pointer-events-none z-0"></div>

    <div class="flex flex-col items-center mb-12 relative z-10">
      <div class="section-pill text-brand-lilac edu-reveal shadow-lg shadow-brand-lilac/10 mb-4">⟡ Formación</div>
      <h2 class="text-4xl sm:text-5xl font-extrabold text-center edu-reveal" style="transition-delay: 0.1s">
        Aprendizaje <span class="text-gradient-lilac">continuo</span>
      </h2>
    </div>

    <div class="relative z-10 flex flex-col items-center w-full">
      <!-- Magical Navigation Bubbles -->
      <div class="flex flex-wrap justify-center gap-2 sm:gap-5 mb-10 edu-reveal w-full" style="transition-delay: 0.2s">
        <button v-for="(item, i) in education" :key="item.shortTitle"
          @click="activeIndex = i"
          class="relative group rounded-3xl px-4 py-2.5 sm:px-6 sm:py-4 flex items-center gap-2 sm:gap-3 transition-all duration-500 overflow-hidden border"
          :class="activeIndex === i ? 'bg-[#1A1F40] border-white/20 shadow-[0_0_30px_rgba(212,179,232,0.25)] scale-105' : 'bg-white/5 border-white/5 hover:bg-white/10 hover:scale-105 hover:border-white/10'">
          
          <!-- Hover/Active gradient fills -->
          <div class="absolute inset-0 bg-gradient-to-r transition-opacity duration-500 opacity-0 group-hover:opacity-10"
               :class="item.colorGrad" v-if="activeIndex !== i"></div>
          <div class="absolute inset-0 bg-gradient-to-r opacity-20" :class="item.colorGrad" v-else></div>
          
          <span class="text-xl sm:text-3xl relative z-10 transition-transform duration-500" :class="activeIndex === i ? 'scale-110 drop-shadow-md' : 'group-hover:rotate-6'">
            {{ item.icon }}
          </span>
          <span class="relative z-10 font-bold uppercase tracking-widest text-[0.65rem] sm:text-xs transition-colors" :class="activeIndex === i ? 'text-white' : 'text-slate-400 group-hover:text-white'">
            {{ item.shortTitle }}
          </span>
        </button>
      </div>

      <!-- Main Showcase Container -->
      <div class="glass-card w-full p-8 sm:p-12 md:p-14 rounded-[3rem] border border-white/10 shadow-2xl relative overflow-hidden min-h-[380px] flex items-center justify-center edu-reveal bg-[#0C0F22]/80 backdrop-blur-2xl" style="transition-delay: 0.3s">
        
        <!-- Adaptive Ambient glow for current item inside card -->
        <div class="absolute top-1/2 right-0 -translate-y-1/2 w-72 h-72 blur-[100px] rounded-full pointer-events-none transition-colors duration-1000 opacity-50" :class="activeItem.glowClass"></div>

        <transition name="fade-slide" mode="out-in">
          <div :key="activeIndex" class="flex flex-col md:flex-row items-center md:items-start text-center md:text-left gap-8 md:gap-12 w-full relative z-10">
            
            <!-- Huge Visual Icon -->
            <div class="w-32 h-32 md:w-44 md:h-44 shrink-0 rounded-[2.5rem] bg-[#050714] border border-white/10 shadow-inner flex items-center justify-center text-7xl md:text-8xl transition-all duration-700 hover:scale-105 hover:rotate-3 hover:shadow-lg relative overflow-hidden group">
               <div class="absolute inset-0 opacity-20 bg-gradient-to-br" :class="activeItem.colorGrad"></div>
               <span class="relative z-10 group-hover:scale-110 transition-transform duration-500">{{ activeItem.icon }}</span>
            </div>
            
            <!-- Content -->
            <div class="flex-1 flex flex-col items-center md:items-start w-full">
              <span class="text-[0.65rem] font-bold px-4 py-1.5 rounded-full uppercase tracking-widest border mb-5 shadow-sm inline-block"
                    :class="activeItem.badgeClass">
                {{ activeItem.date }}
              </span>
              
              <h3 class="text-3xl md:text-4xl lg:text-5xl font-extrabold text-white mb-3 leading-tight drop-shadow-sm">
                {{ activeItem.title }}
              </h3>
              
              <p class="text-base md:text-lg font-extrabold mb-5" :class="activeItem.textColor">
                {{ activeItem.subtitle }} <span class="text-slate-500 font-normal mx-2 opacity-50">•</span> <span class="text-slate-300 font-normal">{{ activeItem.school }}</span>
              </p>
              
              <p class="text-slate-300 text-sm md:text-base leading-relaxed md:leading-loose max-w-2xl bg-[#0a0c1c]/40 p-5 rounded-2xl border border-white/5">
                {{ activeItem.desc }}
              </p>
            </div>
          </div>
        </transition>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted, ref, computed } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const activeIndex = ref(0);

const education = [
  {
    title: 'Grado Superior en DAM',
    shortTitle: 'DAM',
    subtitle: 'Desarrollo de Apps Multiplataforma',
    school: 'IES El Rincón',
    date: 'En Curso',
    icon: '💻',
    desc: 'Formación de alto nivel especializada en el ciclo de vida del software, incluyendo desarrollo web, móvil y arquitecturas de escritorio utilizando tecnologías e industrias como Java, Kotlin, Vue y bases de datos relacionales.',
    colorGrad: 'from-brand-blue to-brand-mint',
    badgeClass: 'bg-brand-blue/10 text-brand-blue border-brand-blue/30',
    textColor: 'text-brand-blue',
    glowClass: 'bg-brand-blue'
  },
  {
    title: 'Certificación Angular',
    shortTitle: 'Angular',
    subtitle: 'Nivel 1 — General',
    school: 'Oficial',
    date: '2026',
    icon: '🔴',
    desc: 'Acreditación oficial orientada a dominar los fundamentos del framework más potente creado por Google: inyección de dependencias, routing avanzado, manipulación del DOM y state management avanzado.',
    colorGrad: 'from-brand-pink to-red-400',
    badgeClass: 'bg-brand-pink/10 text-brand-pink border-brand-pink/30',
    textColor: 'text-brand-pink',
    glowClass: 'bg-brand-pink'
  },
  {
    title: 'Técnico Sup. en Salud',
    shortTitle: 'Salud',
    subtitle: 'Salud Ambiental',
    school: 'IES Nº1 · Gijón',
    date: '2019 – 2021',
    icon: '🔬',
    desc: 'Ciencia orientada a la planificación de salud pública. Esto incluye un control riguroso de riesgos ambientales, protocolos preventivos y el análisis avanzado de calidad biológica en aguas y alimentos.',
    colorGrad: 'from-brand-mint to-teal-400',
    badgeClass: 'bg-brand-mint/10 text-brand-mint border-brand-mint/30',
    textColor: 'text-brand-mint',
    glowClass: 'bg-brand-mint'
  },
  {
    title: 'Clínica y Enfermería',
    shortTitle: 'TCAE',
    subtitle: 'Cuidados Auxiliares de Enfermería',
    school: 'IES Nº1 · Gijón',
    date: '2017 – 2018',
    icon: '🏥',
    desc: 'Vocación por la asistencia y atención vital pormenorizada a pacientes. Dominio de preparación de material médico, protocolos quirúrgicos y soporte directo en entornos hospitalarios de alta exigencia.',
    colorGrad: 'from-brand-lilac to-fuchsia-400',
    badgeClass: 'bg-brand-lilac/10 text-brand-lilac border-brand-lilac/30',
    textColor: 'text-brand-lilac',
    glowClass: 'bg-brand-lilac'
  }
];

const activeItem = computed(() => education[activeIndex.value]);

onMounted(() => {
  gsap.fromTo('.edu-reveal',
    { opacity: 0, y: 30 },
    {
      opacity: 1, y: 0, duration: 0.8, stagger: 0.12, ease: 'power3.out',
      scrollTrigger: { trigger: '#education', start: 'top 85%' }
    }
  );
});
</script>

<style scoped>
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(15px) scale(0.98);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-15px) scale(0.98);
}
</style>
