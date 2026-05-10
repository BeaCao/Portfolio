<template>
  <section id="hero" class="relative min-h-screen flex items-center justify-center overflow-hidden pt-20">
    <!-- Central glow halo -->
    <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
      <div class="w-[700px] h-[700px] rounded-full"
        style="background: radial-gradient(circle, rgba(212,179,232,0.1) 0%, rgba(184,212,240,0.05) 40%, transparent 70%);">
      </div>
    </div>

    <div class="relative z-10 text-center px-6 max-w-5xl mx-auto select-none">
      <!-- Greeting chip -->
      <div
        class="hero-chip inline-flex items-center gap-2 px-4 py-2 rounded-full glass-card text-sm font-medium mb-10 text-brand-lilac magnetic-btn">
        <span class="sparkle text-lg">✨</span>
        Bienvenido a mi portfolio
        <span class="sparkle text-lg">✨</span>
      </div>

      <!-- Name -->
      <h1 class="font-black leading-tight mb-5">
        <span class="block text-white hero-word" style="font-size: clamp(2.5rem, 12vw, 8rem); letter-spacing: -0.02em;">
          Beatriz
        </span>
        <span class="block text-gradient-main hero-word"
          style="font-size: clamp(2.5rem, 12vw, 8rem); letter-spacing: -0.02em;">
          Cao Rodríguez
        </span>
      </h1>

      <!-- Subtitle -->
      <div
        class="flex flex-col sm:flex-row items-center justify-center gap-2 sm:gap-3 text-lg sm:text-2xl font-light text-slate-300 mb-14 hero-subtitle">
        <span>Desarrolladora</span>
        <div class="flex items-center gap-1">
          <span class="text-brand-pink font-semibold px-3 py-1 rounded-full text-base sm:text-xl"
            style="background: rgba(245,198,216,0.1); border: 1px solid rgba(245,198,216,0.2);"
            id="type-text">Multiplataforma</span>
          <span class="type-cursor text-brand-lilac font-thin text-2xl sm:text-3xl leading-none">|</span>
        </div>
      </div>

      <!-- CTAs -->
      <div class="hero-ctas flex flex-wrap items-center justify-center gap-5">
        <a href="#about" class="btn-primary magnetic-btn">Conóceme mejor 🌸</a>
        <a href="#projects" class="btn-outline magnetic-btn">Ver mis proyectos →</a>
      </div>

      <!-- Decorative symbols flying around -->
      <div class="float-el absolute text-brand-lilac/40 text-4xl font-black select-none hidden lg:block"
        style="top: 15%; left: 6%;">✦</div>
      <div class="float-el absolute text-brand-blue/35 text-3xl select-none hidden lg:block"
        style="top: 35%; right: 5%; animation-delay: -2s">◇</div>
      <div class="float-el absolute text-brand-pink/45 text-2xl select-none hidden lg:block"
        style="bottom: 30%; left: 8%; animation-delay: -4s">✿</div>
      <div class="float-el absolute text-brand-mint/35 text-3xl select-none hidden lg:block"
        style="bottom: 20%; right: 8%; animation-delay: -1s">⟡</div>
      <div class="float-el absolute text-brand-lilac/30 text-2xl select-none hidden lg:block"
        style="top: 60%; left: 3%; animation-delay: -3s">◈</div>
      <div class="float-el absolute text-brand-pink/30 text-xl select-none hidden lg:block"
        style="top: 15%; right: 12%; animation-delay: -5s">❋</div>
    </div>

    <!-- Scroll indicator -->
    <div
      class="hero-scroll absolute bottom-10 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-slate-500 text-xs">
      <div class="scroll-mouse w-6 h-9 rounded-full border border-slate-600/80 flex pt-1.5 justify-center">
        <div class="scroll-dot w-1.5 h-2.5 rounded-full bg-gradient-to-b from-brand-lilac to-brand-pink"></div>
      </div>
      <span class="tracking-widest uppercase text-[10px]">Scroll</span>
    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const roles = [
  'Multiplataforma 💻',
  'Frontend con Vue y Angular 💚🔴',
  'Backend con Java y Kotlin ☕🟣',
  'Móvil con Ionic 📱',
  'Bases de Datos SQL 🗄️',
  'Creativa y Detallista ✨'
];

function scrambleText(element: HTMLElement, finalText: string, duration = 600) {
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789✦◇✿⟡';
  let iteration = 0;
  const totalIterations = Math.ceil(duration / 30);
  const interval = setInterval(() => {
    element.textContent = finalText
      .split('')
      .map((char, i) => {
        if (char === ' ') return ' ';
        if (i < Math.floor((iteration / totalIterations) * finalText.length)) return char;
        return chars[Math.floor(Math.random() * chars.length)];
      })
      .join('');
    iteration++;
    if (iteration >= totalIterations) {
      clearInterval(interval);
      element.textContent = finalText;
    }
  }, 30);
}

onMounted(() => {
  // Hero entrance
  const tl = gsap.timeline({ defaults: { ease: 'power4.out' } });
  tl.fromTo('.hero-chip', { opacity: 0, y: -24, scale: 0.8 }, { opacity: 1, y: 0, scale: 1, duration: 0.9 })
    .fromTo('.hero-word', { opacity: 0, y: 70, skewY: 5 }, { opacity: 1, y: 0, skewY: 0, stagger: 0.15, duration: 1.1 }, '-=0.5')
    .fromTo('.hero-subtitle', { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.8 }, '-=0.6')
    .fromTo('.hero-ctas', { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.8 }, '-=0.5')
    .fromTo('.float-el', { opacity: 0, scale: 0, rotation: -90 }, { opacity: 1, scale: 1, rotation: 0, stagger: 0.1, duration: 0.6 }, '-=0.4')
    .fromTo('.hero-scroll', { opacity: 0 }, { opacity: 1, duration: 0.5 }, '-=0.2');

  // Typing effect
  let roleIndex = 0;
  let isDeleting = false;
  let charIndex = 0;
  const typeEl = document.getElementById('type-text');

  function type() {
    if (!typeEl) return;
    const current = roles[roleIndex];
    if (isDeleting) {
      typeEl.textContent = current.substring(0, --charIndex);
      if (charIndex <= 0) { isDeleting = false; roleIndex = (roleIndex + 1) % roles.length; setTimeout(type, 400); return; }
    } else {
      typeEl.textContent = current.substring(0, ++charIndex);
      if (charIndex >= current.length) { isDeleting = true; setTimeout(type, 2000); return; }
    }
    setTimeout(type, isDeleting ? 55 : 90);
  }
  setTimeout(type, 1800);

  // Cursor blink
  gsap.to('.type-cursor', { opacity: 0, duration: 0.55, repeat: -1, yoyo: true, ease: 'steps(1)' });

  // Floating symbols
  gsap.to('.float-el', {
    y: 'random(-20, 20)',
    x: 'random(-10, 10)',
    rotation: 'random(-15, 15)',
    duration: 'random(2.5, 4.5)',
    repeat: -1, yoyo: true, ease: 'sine.inOut',
    stagger: { amount: 1.5 },
  });

  // Sparkle pulse
  gsap.to('.sparkle', {
    scale: 1.4, rotation: 30,
    duration: 1.2, repeat: -1, yoyo: true, ease: 'sine.inOut', stagger: 0.3,
  });

  // Scroll mouse Bob
  gsap.to('.scroll-dot', {
    y: 14, duration: 1, repeat: -1, yoyo: true, ease: 'power1.inOut',
    onRepeat() { gsap.to('.scroll-mouse', { borderColor: 'rgba(212,179,232,0.7)', duration: 0.5, yoyo: true, repeat: 1 }); }
  });

  // Parallax on scroll
  gsap.to('.float-el', {
    y: -60,
    ease: 'none',
    scrollTrigger: { trigger: '#hero', start: 'top top', end: 'bottom top', scrub: true },
  });
});
</script>

<style scoped>
.hero-word {
  will-change: transform, opacity;
}
</style>
