<template>
  <div class="py-8 px-6 sm:px-12 relative z-10">
    <div class="max-w-5xl mx-auto glass-card px-8 py-6 gradient-border">
      <div class="grid grid-cols-2 sm:grid-cols-4 sm:divide-x divide-white/10 gap-y-6 sm:gap-y-0">
        <div v-for="stat in stats" :key="stat.label"
          class="px-2 sm:px-6 sm:first:pl-0 sm:last:pr-0 flex flex-col items-center text-center">
          <span class="text-3xl font-black stat-number text-gradient-main"
            :ref="el => statRefs.push(el as HTMLElement)">
            {{ stat.display }}
          </span>
          <span class="text-xs text-slate-400 mt-1 font-medium uppercase tracking-wider">{{ stat.label }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const statRefs: HTMLElement[] = [];

const stats = [
  { label: 'Tecnologías', value: 16, display: '0', suffix: '+' },
  { label: 'Idiomas', value: 2, display: '0', suffix: '' },
  { label: 'Proyectos', value: 5, display: '0', suffix: '+' },
  { label: 'Pasión', value: 100, display: '0', suffix: '%' },
];

onMounted(() => {
  gsap.fromTo(statRefs,
    { opacity: 0, y: 20 },
    {
      opacity: 1, y: 0, stagger: 0.1, duration: 0.6, ease: 'power3.out',
      scrollTrigger: { trigger: statRefs[0], start: 'top 85%' },
      onStart() {
        stats.forEach((stat, i) => {
          gsap.fromTo({ v: 0 }, { v: stat.value }, {
            duration: 1.6,
            ease: 'power2.out',
            delay: i * 0.12,
            onUpdate(this: gsap.core.Tween) {
              const v = Math.round((this.targets()[0] as { v: number }).v);
              if (statRefs[i]) statRefs[i].textContent = v + stat.suffix;
            },
          });
        });
      },
    }
  );
});
</script>
