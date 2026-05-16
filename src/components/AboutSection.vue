<template>
  <section id="about" class="py-32 px-6 sm:px-12 max-w-6xl mx-auto">
    <div class="flex flex-col items-center mb-16">
      <div class="section-pill text-brand-pink about-reveal">✦ Sobre Mí</div>
      <h2 class="text-4xl sm:text-5xl font-extrabold mt-3 about-reveal text-center" style="transition-delay: 0.1s">
        Una desarrolladora con <span class="text-gradient-main">alma creativa</span>
      </h2>
    </div>

    <!-- Bento Grid Layout -->
    <div class="grid grid-cols-1 md:grid-cols-4 gap-4 md:gap-6">
      
      <!-- Card 1: Main Text (Cols 1-2, Row 1-2) -->
      <div class="md:col-span-2 md:row-span-2 relative glass-card p-8 sm:p-10 rounded-[2rem] overflow-hidden about-reveal group border border-white/5 hover:border-brand-pink/30 hover:shadow-[0_0_30px_rgba(251,113,133,0.15)] transition-all duration-500">
          <!-- Glow orbs in background -->
          <div class="absolute -top-20 -right-20 w-48 h-48 bg-brand-pink/20 blur-[60px] rounded-full group-hover:bg-brand-pink/40 transition-colors duration-500"></div>
          <div class="absolute -bottom-20 -left-20 w-48 h-48 bg-brand-lilac/20 blur-[60px] rounded-full group-hover:bg-brand-lilac/40 transition-colors duration-500"></div>
          
          <h3 class="text-3xl font-extrabold mb-6 relative z-10 flex items-center gap-3">
            ¡Hola! Soy Bea <span class="animate-wave inline-block origin-bottom-right">👋</span>
          </h3>
          <p class="text-slate-300 leading-relaxed relative z-10 text-lg mb-4">
            Una desarrolladora con un perfil muy <span class="text-brand-pink font-semibold">creativo y perfeccionista</span>. 
            Me apasiona crear experiencias digitales donde la técnica impecable se encuentra con una <span class="text-brand-lilac font-semibold">sensibilidad estética exquisita</span>.
          </p>
          <p class="text-slate-300 leading-relaxed relative z-10 text-lg">
            Soy proactiva, me adapto rápido a los cambios y tengo un compromiso inquebrantable con la <span class="text-brand-blue font-semibold">calidad del código</span>. ¡Siempre buscando aprender algo nuevo! ✨
          </p>
      </div>

      <!-- Card 2: Titulación (Col 3-4, Row 1) -->
      <div class="md:col-span-2 relative glass-card p-6 sm:p-8 rounded-[2rem] about-reveal group overflow-hidden border border-white/5 hover:border-brand-blue/30 hover:shadow-[0_0_30px_rgba(184,212,240,0.15)] transition-all duration-500 flex flex-col sm:flex-row items-center sm:items-start text-center sm:text-left gap-4 sm:gap-6" style="transition-delay: 0.1s">
          <div class="absolute inset-0 bg-gradient-to-r from-brand-blue/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
          <div class="w-16 h-16 sm:w-20 sm:h-20 shrink-0 bg-[#15193B]/80 rounded-2xl flex items-center justify-center text-3xl sm:text-4xl shadow-inner border border-slate-700/50 group-hover:scale-110 group-hover:-rotate-6 transition-all duration-500">
            🎓
          </div>
          <div class="relative z-10">
            <div class="text-xs uppercase tracking-widest text-brand-blue font-bold mb-1">Formación</div>
            <h4 class="text-xl sm:text-2xl font-bold text-white mb-1 leading-tight">DAM <span class="hidden sm:inline font-medium">— Desarrollo Multiplataforma</span></h4>
            <p class="text-slate-400 text-sm">IES El Rincón · Promoción 2026</p>
          </div>
      </div>

      <!-- Card 3: Ubicación (Col 3, Row 2) -->
      <div class="md:col-span-1 relative glass-card p-6 sm:p-8 rounded-[2rem] about-reveal group overflow-hidden border border-white/5 hover:border-brand-mint/30 hover:shadow-[0_0_30px_rgba(184,232,216,0.15)] transition-all duration-500 flex flex-col items-center justify-center text-center" style="transition-delay: 0.2s">
          <div class="absolute inset-0 bg-gradient-to-t from-brand-mint/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
          <div class="text-5xl mb-4 group-hover:-translate-y-2 transition-transform duration-500 drop-shadow-[0_0_15px_rgba(255,255,255,0.2)]">🌍</div>
          <div class="text-[0.65rem] uppercase tracking-widest text-brand-mint font-bold mb-2">Ubicación</div>
          <h4 class="text-lg font-bold text-white leading-tight mb-1">Las Palmas de Gran Canaria</h4>
          <p class="text-xs text-slate-400">Islas Canarias, España</p>
      </div>

      <!-- Card 4: Idiomas (Col 4, Row 2) -->
      <div class="md:col-span-1 relative glass-card p-6 sm:p-8 rounded-[2rem] about-reveal group overflow-hidden border border-white/5 hover:border-brand-pink/30 hover:shadow-[0_0_30px_rgba(245,198,216,0.15)] transition-all duration-500 flex flex-col items-center justify-center text-center" style="transition-delay: 0.3s">
          <div class="absolute inset-0 bg-gradient-to-t from-brand-pink/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
          <div class="text-4xl mb-4 group-hover:rotate-12 group-hover:scale-110 transition-transform duration-500 drop-shadow-[0_0_15px_rgba(255,255,255,0.2)] flex items-center justify-center gap-1">
            🗣️
          </div>
          <div class="text-[0.65rem] uppercase tracking-widest text-brand-pink font-bold mb-2">Idiomas</div>
          <h4 class="text-base font-bold text-white leading-tight mb-1">Español <span class="text-xs font-normal text-slate-400">(Nativo)</span></h4>
          <h4 class="text-base font-bold text-white leading-tight">Inglés <span class="text-xs font-normal text-slate-400">(B2)</span></h4>
      </div>

      <!-- Card 5: Soft Skills Marquee (Col 1-4, Row 3) -->
      <div class="md:col-span-4 relative glass-card py-6 overflow-hidden rounded-[2rem] about-reveal border border-white/5 hover:border-brand-lilac/30 hover:shadow-[0_0_30px_rgba(212,179,232,0.1)] transition-all duration-500 mt-2 sm:mt-0" style="transition-delay: 0.4s">
          <!-- Gradient Masks for smooth fading on edges -->
          <div class="absolute inset-y-0 left-0 w-16 md:w-32 bg-gradient-to-r from-[#0a0c1c] to-transparent z-10 pointer-events-none rounded-l-[2rem]"></div>
          <div class="absolute inset-y-0 right-0 w-16 md:w-32 bg-gradient-to-l from-[#0a0c1c] to-transparent z-10 pointer-events-none rounded-r-[2rem]"></div>
          
          <div class="animate-marquee items-center block">
              <span class="text-base md:text-xl font-bold text-slate-400/70 uppercase tracking-widest flex items-center gap-6">
                <span>ESTÉTICA</span><span class="text-brand-pink text-xs">✦</span>
                <span>INICIATIVA</span><span class="text-brand-lilac text-xs">✦</span>
                <span>CALIDAD DE CÓDIGO</span><span class="text-brand-blue text-xs">✦</span>
                <span>CREATIVA</span><span class="text-brand-mint text-xs">✦</span>
                <span>PROACTIVA</span><span class="text-brand-pink text-xs">✦</span>
                <span>ADAPTABILIDAD</span><span class="text-brand-lilac text-xs">✦</span>
                <span>RESOLUTIVA</span><span class="text-brand-blue text-xs">✦</span>
                <span>PERFECCIONISTA</span><span class="text-brand-mint text-xs">✦</span>
                <!-- Duplicate for seamless loop -->
                <span>ESTÉTICA</span><span class="text-brand-pink text-xs">✦</span>
                <span>INICIATIVA</span><span class="text-brand-lilac text-xs">✦</span>
                <span>CALIDAD DE CÓDIGO</span><span class="text-brand-blue text-xs">✦</span>
                <span>CREATIVA</span><span class="text-brand-mint text-xs">✦</span>
                <span>PROACTIVA</span><span class="text-brand-pink text-xs">✦</span>
                <span>ADAPTABILIDAD</span><span class="text-brand-lilac text-xs">✦</span>
                <span>RESOLUTIVA</span><span class="text-brand-blue text-xs">✦</span>
                <span class="pr-6">PERFECCIONISTA</span> <!-- pr-6 to match gap -->
              </span>
          </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.fromTo('.about-reveal',
    { opacity: 0, y: 50 },
    {
      opacity: 1, y: 0, duration: 0.9, stagger: 0.15, ease: 'power3.out',
      scrollTrigger: { trigger: '#about', start: 'top 80%' }
    }
  );
});
</script>
