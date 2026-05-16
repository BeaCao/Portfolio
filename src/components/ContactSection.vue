<template>
  <section id="contact" class="py-32 px-6 sm:px-12 max-w-6xl mx-auto relative">
    
    <!-- Ambient glow -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[110%] h-96 bg-brand-pink/5 blur-[120px] rounded-full pointer-events-none z-0"></div>

    <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center relative z-10">
      
      <!-- Left side: Hook & Links -->
      <div class="flex flex-col text-center lg:text-left items-center lg:items-start">
        <div class="section-pill text-brand-mint contact-reveal inline-block mb-6 self-center lg:self-start shadow-lg shadow-brand-mint/10">✿ Hablemos</div>
        <h2 class="text-4xl sm:text-6xl font-extrabold mb-6 contact-reveal leading-tight" style="transition-delay: 0.1s">
          Creemos algo <br/><span class="text-gradient-main">espectacular</span> ✨
        </h2>
        <p class="text-slate-400 mb-10 text-lg contact-reveal max-w-md" style="transition-delay: 0.2s">
          Estoy siempre abierta a nuevas oportunidades, retos técnicos, colaboraciones creativas o simplemente a charlar sobre diseño y código.
        </p>

        <!-- Links Cards -->
        <div class="flex flex-col gap-4 contact-reveal" style="transition-delay: 0.3s">
          
          <a href="mailto:beacaor@gmail.com" target="_blank" class="group flex items-center gap-5 p-4 rounded-[1.5rem] bg-white/5 hover:bg-white/10 transition-all duration-500 border border-white/5 hover:border-brand-pink/30 hover:shadow-[0_10px_30px_-10px_rgba(245,198,216,0.3)] no-underline relative overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-r from-brand-pink/0 via-brand-pink/5 to-brand-pink/0 translate-x-[-100%] group-hover:translate-x-[100%] transition-transform duration-1000"></div>
            <div class="w-14 h-14 shrink-0 rounded-2xl bg-[#0a0c1c] shadow-inner border border-white/10 text-brand-pink flex items-center justify-center text-2xl group-hover:scale-110 group-hover:bg-brand-pink/20 transition-all duration-300 relative z-10">
              <span class="group-hover:hidden">✉️</span>
              <span class="hidden group-hover:inline">💌</span>
            </div>
            <div class="relative z-10 w-full">
              <div class="text-[0.65rem] uppercase tracking-widest text-brand-pink font-bold mb-0.5">Mándame un email</div>
              <div class="text-slate-200 font-medium group-hover:text-white transition-colors truncate">beacaor@gmail.com</div>
            </div>
          </a>

          <a href="https://www.linkedin.com/in/beatriz-cao-rodríguez" target="_blank" class="group flex items-center gap-5 p-4 rounded-[1.5rem] bg-white/5 hover:bg-white/10 transition-all duration-500 border border-white/5 hover:border-brand-blue/30 hover:shadow-[0_10px_30px_-10px_rgba(184,212,240,0.3)] no-underline relative overflow-hidden">
             <div class="absolute inset-0 bg-gradient-to-r from-brand-blue/0 via-brand-blue/5 to-brand-blue/0 translate-x-[-100%] group-hover:translate-x-[100%] transition-transform duration-1000"></div>
            <div class="w-14 h-14 shrink-0 rounded-2xl bg-[#0a0c1c] shadow-inner border border-white/10 text-brand-blue flex items-center justify-center text-2xl group-hover:scale-110 group-hover:bg-brand-blue/20 transition-all duration-300 relative z-10">
              <span class="group-hover:hidden">💼</span>
              <span class="hidden group-hover:inline">🤝</span>
            </div>
            <div class="relative z-10">
              <div class="text-[0.65rem] uppercase tracking-widest text-brand-blue font-bold mb-0.5">Conectemos en LinkedIn</div>
              <div class="text-slate-200 font-medium group-hover:text-white transition-colors">Beatriz Cao Rodríguez</div>
            </div>
          </a>

          <a href="https://github.com/BeaCao" target="_blank" class="group flex items-center gap-5 p-4 rounded-[1.5rem] bg-white/5 hover:bg-white/10 transition-all duration-500 border border-white/5 hover:border-brand-mint/30 hover:shadow-[0_10px_30px_-10px_rgba(184,232,216,0.3)] no-underline relative overflow-hidden">
             <div class="absolute inset-0 bg-gradient-to-r from-brand-mint/0 via-brand-mint/5 to-brand-mint/0 translate-x-[-100%] group-hover:translate-x-[100%] transition-transform duration-1000"></div>
            <div class="w-14 h-14 shrink-0 rounded-2xl bg-[#0a0c1c] shadow-inner border border-white/10 text-brand-mint flex items-center justify-center text-2xl group-hover:scale-110 group-hover:bg-brand-mint/20 transition-all duration-300 relative z-10">
              <span class="group-hover:hidden">🐙</span>
              <span class="hidden group-hover:inline">💻</span>
            </div>
            <div class="relative z-10">
              <div class="text-[0.65rem] uppercase tracking-widest text-brand-mint font-bold mb-0.5">Mis proyectos en GitHub</div>
              <div class="text-slate-200 font-medium group-hover:text-white transition-colors">@BeaCao</div>
            </div>
          </a>

        </div>
      </div>

      <!-- Right side: The Form -->
      <div class="contact-reveal" style="transition-delay: 0.4s">
        <div class="bg-[#0C0F22]/80 backdrop-blur-xl glass-card no-tilt p-8 sm:p-10 border border-brand-pink/10 hover:border-brand-pink/30 rounded-[2rem] shadow-2xl relative overflow-hidden group transition-all duration-500">
          <!-- Inner Glow -->
          <div class="absolute -top-32 -right-32 w-64 h-64 bg-brand-pink/20 blur-[80px] rounded-full group-hover:bg-brand-pink/30 transition-colors duration-700"></div>
          
          <h3 class="text-3xl font-extrabold mb-8 text-white flex items-center gap-3 relative z-10">
            Escríbeme <span class="animate-wave inline-block origin-bottom-right">👋</span>
          </h3>
          
          <form @submit="submitForm" class="flex flex-col gap-8 relative z-10">
            <input type="hidden" name="_subject" value="Nuevo mensaje desde tu portfolio! ✨">
            <input type="hidden" name="_captcha" value="false">

            <!-- Name Input -->
            <div class="flex flex-col gap-2 group/input relative">
              <label for="name" class="text-[0.65rem] uppercase tracking-widest font-bold text-slate-400 group-focus-within/input:text-brand-pink transition-colors px-2">Tu nombre</label>
              <input type="text" name="name" id="name" required placeholder="¿Cómo te llamas?" 
                class="bg-transparent border-0 border-b-2 border-slate-700/50 rounded-none px-2 py-2 text-slate-100 focus:outline-none focus:border-brand-pink focus:bg-white/[0.02] transition-all placeholder-slate-600">
            </div>

            <!-- Email Input -->
            <div class="flex flex-col gap-2 group/input relative">
              <label for="email" class="text-[0.65rem] uppercase tracking-widest font-bold text-slate-400 group-focus-within/input:text-brand-blue transition-colors px-2">Email</label>
              <input type="email" name="email" id="email" required placeholder="hola@ejemplo.com" 
                class="bg-transparent border-0 border-b-2 border-slate-700/50 rounded-none px-2 py-2 text-slate-100 focus:outline-none focus:border-brand-blue focus:bg-white/[0.02] transition-all placeholder-slate-600">
            </div>

            <!-- Message Textarea -->
            <div class="flex flex-col gap-2 group/input relative">
              <label for="message" class="text-[0.65rem] uppercase tracking-widest font-bold text-slate-400 group-focus-within/input:text-brand-lilac transition-colors px-2">Mensaje</label>
              <textarea name="message" id="message" rows="4" required placeholder="Me encantaría hablar contigo sobre..." 
                class="bg-transparent border-0 border-b-2 border-slate-700/50 rounded-none px-2 py-2 text-slate-100 focus:outline-none focus:border-brand-lilac focus:bg-white/[0.02] transition-all placeholder-slate-600 resize-none"></textarea>
            </div>

            <button type="submit" :disabled="isSubmitting" 
              class="btn-primary mt-2 w-full py-4 rounded-xl disabled:opacity-70 disabled:cursor-not-allowed flex items-center justify-center gap-3 text-sm font-bold shadow-lg shadow-brand-pink/20 hover:shadow-[0_0_30px_rgba(251,113,133,0.4)] transition-all">
              <span v-if="isSubmitting" class="text-xl animate-spin">⏳</span>
              <span v-else>Enviar carta virtual 💌</span>
            </button>

            <!-- Feedback Messages -->
            <div v-if="isSuccess" class="p-4 bg-green-500/10 border border-green-500/20 text-green-400 rounded-xl text-center text-sm font-medium mt-[-0.5rem] transition-all">
              ¡Boom! Enviado con éxito. Te respondo pronto. 🎉
            </div>
            <div v-if="isError" class="p-4 bg-red-500/10 border border-red-500/20 text-red-400 rounded-xl text-center text-sm font-medium mt-[-0.5rem] transition-all">
              Hubo un error. Por favor, inténtalo de nuevo o escríbeme por email. 😥
            </div>
          </form>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

const isSubmitting = ref(false);
const isSuccess = ref(false);
const isError = ref(false);

const submitForm = async (e: Event) => {
  e.preventDefault();
  isSubmitting.value = true;
  isError.value = false;
  isSuccess.value = false;

  const form = e.target as HTMLFormElement;
  const formData = new FormData(form);

  try {
    const response = await fetch("https://formsubmit.co/ajax/beacaor@gmail.com", {
      method: "POST",
      body: formData,
      headers: {
        'Accept': 'application/json'
      }
    });
    
    if (response.ok) {
      isSuccess.value = true;
      form.reset();
      setTimeout(() => {
        isSuccess.value = false;
      }, 6000);
    } else {
      isError.value = true;
      setTimeout(() => {
        isError.value = false;
      }, 6000);
    }
  } catch (error) {
    isError.value = true;
    setTimeout(() => {
        isError.value = false;
    }, 6000);
  } finally {
    isSubmitting.value = false;
  }
};

onMounted(() => {
  gsap.fromTo('.contact-reveal',
    { opacity: 0, y: 40 },
    {
      opacity: 1, y: 0, duration: 0.8, stagger: 0.12, ease: 'power3.out',
      scrollTrigger: { trigger: '#contact', start: 'top 80%' }
    }
  );
});
</script>
