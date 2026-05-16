<template>
  <div class="relative min-h-screen flex flex-col overflow-x-hidden" id="app-root">
    <!-- Cursor glow -->
    <div class="cursor-glow" ref="cursorGlow"></div>

    <!-- Grain texture overlay -->
    <div class="grain"></div>

    <!-- Aurora Background -->
    <div class="aurora-bg">
      <div class="aurora-layer"></div>
      <div class="aurora-layer"></div>
      <div class="aurora-layer"></div>
      <div class="aurora-layer"></div>
    </div>

    <!-- Particle canvas -->
    <canvas id="particle-canvas" ref="particleCanvas"></canvas>

    <!-- Floating Navigation -->
    <header class="fixed top-3 sm:top-6 w-full z-50 px-2 sm:px-4 flex justify-center pointer-events-none">
      <nav
        class="glass-card pointer-events-auto px-3 sm:px-8 py-2 sm:py-3 rounded-full flex items-center justify-between w-full max-w-4xl shadow-2xl border border-white/10 transition-all duration-500"
        :class="scrolled ? 'bg-[#0A0C1C]/85 backdrop-blur-xl shadow-brand-pink/10' : 'bg-[#0A0C1C]/40 backdrop-blur-md'">
        
        <!-- Logo -->
        <a href="#hero" class="hidden md:block text-lg sm:text-3xl font-black hover:scale-110 transition-transform duration-300 shrink-0"
          style="font-family: 'Dancing Script', cursive; background: linear-gradient(135deg, #b8d4f0, #d4b3e8, #f5c6d8); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">
          Bea ✦
        </a>
        
        <!-- Desktop Links -->
        <div class="hidden md:flex items-center gap-8 mx-6">
          <a href="#about" class="nav-link text-sm font-semibold tracking-wide hover:text-white">Sobre mí</a>
          <a href="#projects" class="nav-link text-sm font-semibold tracking-wide hover:text-white">Proyectos</a>
          <a href="#skills" class="nav-link text-sm font-semibold tracking-wide hover:text-white">Skills</a>
          <a href="#education" class="nav-link text-sm font-semibold tracking-wide hover:text-white">Formación</a>
        </div>

        <!-- Mobile Icons -->
        <div class="flex md:hidden items-center justify-center gap-4 sm:gap-6 flex-1 shrink-0 px-1">
          <a href="#about" class="flex flex-col items-center gap-0.5 hover:scale-110 hover:-translate-y-1 transition-all group">
            <span class="text-base sm:text-lg drop-shadow-md">👩🏻‍💻</span>
            <span class="text-[0.55rem] font-bold uppercase tracking-widest text-slate-400 group-hover:text-brand-pink transition-colors">Perfil</span>
          </a>
          <a href="#projects" class="flex flex-col items-center gap-0.5 hover:scale-110 hover:-translate-y-1 transition-all group">
            <span class="text-base sm:text-lg drop-shadow-md">🚀</span>
            <span class="text-[0.55rem] font-bold uppercase tracking-widest text-slate-400 group-hover:text-brand-pink transition-colors">Proyectos</span>
          </a>
          <a href="#skills" class="flex flex-col items-center gap-0.5 hover:scale-110 hover:-translate-y-1 transition-all group">
            <span class="text-base sm:text-lg drop-shadow-md">✨</span>
            <span class="text-[0.55rem] font-bold uppercase tracking-widest text-slate-400 group-hover:text-brand-pink transition-colors">Skills</span>
          </a>
          <a href="#education" class="flex flex-col items-center gap-0.5 hover:scale-110 hover:-translate-y-1 transition-all group">
            <span class="text-base sm:text-lg drop-shadow-md">🎓</span>
            <span class="text-[0.55rem] font-bold uppercase tracking-widest text-slate-400 group-hover:text-brand-pink transition-colors">Formación</span>
          </a>
        </div>

        <!-- CTA Button -->
        <a href="#contact" class="btn-primary !py-1 sm:!py-2.5 !px-2 sm:!px-7 text-[0.6rem] sm:text-sm font-bold magnetic-btn shrink-0 shadow-lg shadow-brand-pink/20">
          Contacto <span class="hidden sm:inline">💌</span>
        </a>
      </nav>
    </header>

    <main class="relative z-10">
      <HeroSection />
      <StatsBar />
      <AboutSection />
      <ProjectsSection />
      <SkillsSection />
      <EducationSection />
      <ContactSection />
    </main>

    <footer class="relative z-10 py-10 text-center border-t border-white/5">
      <p class="text-slate-500 text-sm">
        Hecho con <span class="text-brand-pink">♥</span> por
        <span class="text-gradient-main font-semibold">Beatriz Cao Rodríguez</span> — 2026
      </p>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import ScrollToPlugin from 'gsap/ScrollToPlugin';

import HeroSection from './components/HeroSection.vue';
import AboutSection from './components/AboutSection.vue';
import ProjectsSection from './components/ProjectsSection.vue';
import SkillsSection from './components/SkillsSection.vue';
import EducationSection from './components/EducationSection.vue';
import ContactSection from './components/ContactSection.vue';
import StatsBar from './components/StatsBar.vue';

gsap.registerPlugin(ScrollTrigger, ScrollToPlugin);

const scrolled = ref(false);
const cursorGlow = ref<HTMLElement | null>(null);
const particleCanvas = ref<HTMLCanvasElement | null>(null);

// ─── Particles ───
interface Particle { x: number; y: number; vx: number; vy: number; radius: number; alpha: number; color: string; }
let particles: Particle[] = [];
let mouse = { x: -1000, y: -1000 };
let raf: number;

const COLORS = ['rgba(184,212,240,', 'rgba(212,179,232,', 'rgba(245,198,216,', 'rgba(184,232,216,'];

function initParticles(canvas: HTMLCanvasElement) {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  particles = [];
  const N = Math.min(120, Math.floor(window.innerWidth / 12));
  for (let i = 0; i < N; i++) {
    const color = COLORS[Math.floor(Math.random() * COLORS.length)];
    particles.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      vx: (Math.random() - 0.5) * 0.25,
      vy: (Math.random() - 0.5) * 0.25,
      radius: Math.random() * 1.8 + 0.4,
      alpha: Math.random() * 0.5 + 0.2,
      color,
    });
  }
}

function drawParticles(canvas: HTMLCanvasElement) {
  const ctx = canvas.getContext('2d');
  if (!ctx) return;
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  for (let i = 0; i < particles.length; i++) {
    const p = particles[i];
    // Mouse repulsion
    const dx = p.x - mouse.x, dy = p.y - mouse.y;
    const dist = Math.sqrt(dx * dx + dy * dy);
    if (dist < 100) {
      const force = (100 - dist) / 100;
      p.vx += (dx / dist) * force * 0.3;
      p.vy += (dy / dist) * force * 0.3;
    }
    // Friction
    p.vx *= 0.98; p.vy *= 0.98;
    p.x += p.vx; p.y += p.vy;
    if (p.x < 0) p.x = canvas.width;
    if (p.x > canvas.width) p.x = 0;
    if (p.y < 0) p.y = canvas.height;
    if (p.y > canvas.height) p.y = 0;

    // Draw
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
    ctx.fillStyle = p.color + p.alpha + ')';
    ctx.fill();

    // Connect nearby particles
    for (let j = i + 1; j < particles.length; j++) {
      const q = particles[j];
      const ddx = p.x - q.x, ddy = p.y - q.y;
      const d = Math.sqrt(ddx * ddx + ddy * ddy);
      if (d < 90) {
        ctx.beginPath();
        ctx.moveTo(p.x, p.y);
        ctx.lineTo(q.x, q.y);
        ctx.strokeStyle = p.color + (0.15 * (1 - d / 90)) + ')';
        ctx.lineWidth = 0.6;
        ctx.stroke();
      }
    }
  }
  raf = requestAnimationFrame(() => drawParticles(canvas));
}

// ─── Shooting Stars ───
function spawnShootingStar() {
  const s = document.createElement('div');
  s.className = 'shooting-star';
  const size = Math.random() * 2 + 1;
  const startX = Math.random() * window.innerWidth;
  const startY = Math.random() * (window.innerHeight * 0.6);
  s.style.cssText = `left:${startX}px;top:${startY}px;width:${size}px;height:${size}px;`;
  document.body.appendChild(s);
  const tailEl = document.createElement('div');
  tailEl.style.cssText = `position:absolute;top:50%;right:100%;transform:translateY(-50%);
    height:1px;width:${80 + Math.random() * 120}px;
    background:linear-gradient(to left, rgba(255,255,255,0.9), transparent);`;
  s.appendChild(tailEl);
  const angle = 30 + Math.random() * 20;
  const rad = (angle * Math.PI) / 180;
  const dist = 300 + Math.random() * 200;
  gsap.fromTo(s,
    { x: 0, y: 0, opacity: 1 },
    {
      x: Math.cos(rad) * dist,
      y: Math.sin(rad) * dist,
      opacity: 0,
      duration: 0.8 + Math.random() * 0.5,
      ease: 'power1.out',
      onComplete: () => s.remove(),
    }
  );
}

// ─── Confetti burst on load ───
function spawnConfetti() {
  const icons = ['✦', '✿', '◇', '⟡', '✨', '♡', '◈', '❋'];
  for (let i = 0; i < 20; i++) {
    setTimeout(() => {
      const el = document.createElement('div');
      el.className = 'confetti-icon';
      el.textContent = icons[Math.floor(Math.random() * icons.length)];
      el.style.cssText = `left:${Math.random() * 100}vw;top:${Math.random() * 100}vh;font-size:${0.8 + Math.random() * 1.4}rem;`;
      const colors = ['#b8d4f0', '#d4b3e8', '#f5c6d8', '#b8e8d8'];
      el.style.color = colors[Math.floor(Math.random() * colors.length)];
      document.body.appendChild(el);
      gsap.fromTo(el,
        { opacity: 0, scale: 0, y: 0, x: 0 },
        {
          opacity: 0.6,
          scale: 1,
          y: -80 - Math.random() * 120,
          x: (Math.random() - 0.5) * 100,
          duration: 1.5,
          ease: 'power2.out',
          onComplete: () => {
            gsap.to(el, { opacity: 0, duration: 0.5, onComplete: () => el.remove() });
          }
        }
      );
    }, i * 80);
  }
}

// ─── 3D Card Tilt ───
function initCardTilt() {
  document.querySelectorAll<HTMLElement>('.glass-card:not(.no-tilt)').forEach(card => {
    // Add highlight div
    const highlight = document.createElement('div');
    highlight.className = 'tilt-highlight';
    card.appendChild(highlight);

    card.addEventListener('mousemove', (e: MouseEvent) => {
      const rect = card.getBoundingClientRect();
      const cx = rect.left + rect.width / 2;
      const cy = rect.top + rect.height / 2;
      const dx = e.clientX - cx;
      const dy = e.clientY - cy;
      const rotX = (-dy / (rect.height / 2)) * 8;
      const rotY = (dx / (rect.width / 2)) * 8;
      gsap.to(card, {
        rotateX: rotX, rotateY: rotY,
        scale: 1.02,
        duration: 0.3, ease: 'power2.out',
        boxShadow: `${rotY * -1}px ${rotX}px 40px rgba(212,179,232,0.2), 0 20px 60px rgba(0,0,0,0.4)`,
      });
      const hx = ((e.clientX - rect.left) / rect.width) * 100;
      const hy = ((e.clientY - rect.top) / rect.height) * 100;
      highlight.style.left = `${hx}%`;
      highlight.style.top = `${hy}%`;
    });

    card.addEventListener('mouseleave', () => {
      gsap.to(card, {
        rotateX: 0, rotateY: 0, scale: 1,
        duration: 0.5, ease: 'power3.out',
        boxShadow: '0 8px 32px rgba(0,0,0,0.4)',
      });
    });
  });
}

// ─── Magnetic Buttons ───
function initMagneticButtons() {
  document.querySelectorAll<HTMLElement>('.magnetic-btn').forEach(btn => {
    btn.addEventListener('mousemove', (e: MouseEvent) => {
      const rect = btn.getBoundingClientRect();
      const dx = e.clientX - (rect.left + rect.width / 2);
      const dy = e.clientY - (rect.top + rect.height / 2);
      gsap.to(btn, { x: dx * 0.35, y: dy * 0.35, duration: 0.3, ease: 'power2.out' });
    });
    btn.addEventListener('mouseleave', () => {
      gsap.to(btn, { x: 0, y: 0, duration: 0.5, ease: 'elastic.out(1, 0.5)' });
    });
  });
}

const handleScroll = () => { scrolled.value = window.scrollY > 40; };
const handleMouseMove = (e: MouseEvent) => {
  mouse.x = e.clientX; mouse.y = e.clientY;
  if (cursorGlow.value) {
    gsap.to(cursorGlow.value, { x: e.clientX, y: e.clientY, duration: 0.7, ease: 'power2.out' });
  }

  if (Math.random() > 0.6) {
    const trail = document.createElement('div');
    const icons = ['✨', '✦', '·', '•'];
    trail.textContent = icons[Math.floor(Math.random() * icons.length)];
    trail.style.cssText = `position: fixed; left: ${e.clientX}px; top: ${e.clientY}px; pointer-events: none; z-index: 9998; font-size: ${Math.random() * 0.8 + 0.4}rem; color: rgba(245, 198, 216, 0.8); text-shadow: 0 0 5px rgba(245, 198, 216, 0.5);`;
    document.body.appendChild(trail);
    gsap.to(trail, {
      y: e.clientY + 20 + Math.random() * 40,
      x: e.clientX + (Math.random() - 0.5) * 40,
      opacity: 0, scale: 0.5, duration: 1 + Math.random(), ease: 'power2.out',
      onComplete: () => trail.remove()
    });
  }
};

const handleMouseClick = (e: MouseEvent) => {
  const numSparks = 8 + Math.floor(Math.random() * 6);
  const colors = ['#f5c6d8', '#b8d4f0', '#d4b3e8'];
  for (let i = 0; i < numSparks; i++) {
    const spark = document.createElement('div');
    spark.textContent = '✨';
    spark.style.cssText = `position: fixed; left: ${e.clientX}px; top: ${e.clientY}px; pointer-events: none; z-index: 9999; font-size: ${Math.random() * 0.5 + 0.5}rem; color: ${colors[Math.floor(Math.random() * colors.length)]};`;
    document.body.appendChild(spark);
    const angle = (Math.PI * 2 * i) / numSparks + (Math.random() * 0.5);
    const radius = 40 + Math.random() * 80;
    gsap.to(spark, {
      x: e.clientX + Math.cos(angle) * radius,
      y: e.clientY + Math.sin(angle) * radius,
      opacity: 0, scale: 0, rotation: Math.random() * 180 - 90,
      duration: 0.6 + Math.random() * 0.4, ease: 'power3.out',
      onComplete: () => spark.remove()
    });
  }
};
const handleResize = () => {
  if (particleCanvas.value) initParticles(particleCanvas.value);
};

let shootingStarInterval: ReturnType<typeof setInterval>;

onMounted(() => {
  if (particleCanvas.value) {
    initParticles(particleCanvas.value);
    drawParticles(particleCanvas.value);
  }

  window.addEventListener('scroll', handleScroll);
  window.addEventListener('mousemove', handleMouseMove);
  window.addEventListener('click', handleMouseClick);
  window.addEventListener('resize', handleResize);

  // Smooth scroll
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (this: HTMLAnchorElement, e: Event) {
      e.preventDefault();
      const t = this.getAttribute('href');
      if (t) gsap.to(window, { duration: 1.2, scrollTo: { y: t, offsetY: 80 }, ease: 'power3.inOut' });
    });
  });

  // Shooting stars every 2-4s
  shootingStarInterval = setInterval(() => {
    spawnShootingStar();
  }, 2500 + Math.random() * 1500);

  // Initial confetti burst
  setTimeout(spawnConfetti, 800);
  setTimeout(spawnConfetti, 3000);

  // Init special effects after components mount
  setTimeout(() => {
    initCardTilt();
    initMagneticButtons();
  }, 500);

  // Re-run tilt/magnetic when new content appears
  ScrollTrigger.addEventListener('refresh', () => {
    initCardTilt();
    initMagneticButtons();
  });
});

onBeforeUnmount(() => {
  cancelAnimationFrame(raf);
  clearInterval(shootingStarInterval);
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('mousemove', handleMouseMove);
  window.removeEventListener('click', handleMouseClick);
  window.removeEventListener('resize', handleResize);
});
</script>
