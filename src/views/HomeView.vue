<template>
  <main class="relative min-h-[80vh] md:min-h-[85vh] flex items-center justify-center px-4 md:px-8 overflow-hidden">
    <!-- Subtle background glow -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-blue-500/5 rounded-full blur-[120px] pointer-events-none"></div>

    <div class="w-full max-w-6xl mx-auto flex flex-col-reverse md:flex-row items-center justify-between gap-10 md:gap-16 py-12 md:py-0">
      
      <!-- Left Content -->
      <div class="flex-1 text-center md:text-left space-y-5 z-10">
        <!-- Greeting -->
        <p class="text-[#659cf0] text-sm md:text-base font-medium tracking-wide fadein-up">
          Hello World, I'm
        </p>

        <!-- Name -->
        <h1 class="text-4xl sm:text-5xl md:text-6xl font-bold text-white leading-tight fadein-up" style="animation-delay: 100ms">
          Samuel Siahaan
        </h1>

        <!-- Typewriter Role -->
        <div class="h-8 md:h-10 flex items-center justify-center md:justify-start">
          <h2
            class="typewrite text-xl md:text-2xl font-semibold text-transparent bg-clip-text bg-gradient-to-r from-blue-300 via-[#659cf0] to-blue-500 fadein-up"
            style="animation-delay: 200ms"
            ref="typewriter"
          >
            <span class="wrap">{{ txt }}</span>
          </h2>
        </div>

        <!-- Short Bio -->
        <p class="text-gray-300 text-sm md:text-base max-w-lg mx-auto md:mx-0 leading-relaxed fadein-up" style="animation-delay: 300ms">
          A Balikpapan-based Software Engineer passionate about building impactful digital solutions. 
          Focused on clean architecture, scalable systems, and turning ideas into real-world products.
        </p>

        <!-- Info Badges -->
        <div class="flex flex-wrap items-center justify-center md:justify-start gap-3 pt-1 fadein-up" style="animation-delay: 400ms">
          <span class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-full bg-[#1a1a1a] border border-[#2a2a2a] text-xs text-gray-300">
            <svg class="w-3.5 h-3.5 text-[#659cf0]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            Balikpapan, Indonesia
          </span>
          <span class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-full bg-[#1a1a1a] border border-[#2a2a2a] text-xs text-gray-300">
            <svg class="w-3.5 h-3.5 text-[#659cf0]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
            </svg>
            3+ Years Experience
          </span>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-wrap items-center justify-center md:justify-start gap-3 pt-4 fadein-up" style="animation-delay: 500ms">
          <router-link
            to="/portfolio"
            class="inline-flex items-center gap-2 px-5 py-2.5 rounded-lg bg-[#659cf0] text-white text-sm font-medium hover:bg-blue-500 transition-all duration-300 hover:shadow-[0_0_20px_rgba(101,156,240,0.4)]"
          >
            View Projects
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </router-link>

          <router-link
            to="/contact"
            class="inline-flex items-center gap-2 px-5 py-2.5 rounded-lg border border-[#333] text-gray-300 text-sm font-medium hover:border-[#659cf0] hover:text-[#659cf0] transition-all duration-300"
          >
            Contact Me
          </router-link>
        </div>
      </div>

      <!-- Right Content - Avatar -->
      <div class="relative flex justify-center md:justify-end fadein-right z-10">
        <!-- Glow ring -->
        <div class="absolute inset-0 rounded-full bg-[#659cf0]/20 blur-2xl scale-90"></div>
        
        <div class="relative">
          <img
            alt="Samuel Siahaan"
            fetchpriority="high"
            width="400"
            height="400"
            decoding="async"
            class="w-56 h-56 sm:w-64 sm:h-64 md:w-80 md:h-80 object-cover rounded-full border-[3px] border-[#659cf0]/60 shadow-[0_0_60px_rgba(101,156,240,0.25)]"
            src="img/Screenshot 2026-02-20 103528.jpg"
          />
          
          <!-- Decorative ring -->
          <div class="absolute -inset-3 rounded-full border border-[#659cf0]/20 pointer-events-none"></div>
          <div class="absolute -inset-6 rounded-full border border-[#659cf0]/10 pointer-events-none"></div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      toRotate: [
        "Web Developer",
        "Full-stack Engineer",
        "Informatics Student",
        "CyberSecurity Enthusiast"
      ],
      period: 2000,
      txt: '',
      loopNum: 0,
      isDeleting: false,
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.tick();
    });
  },
  methods: {
    tick() {
      const typewriter = this.$refs.typewriter;
      if (!typewriter) return;

      const i = this.loopNum % this.toRotate.length;
      const fullTxt = this.toRotate[i];

      this.txt = this.isDeleting
        ? fullTxt.substring(0, this.txt.length - 1)
        : fullTxt.substring(0, this.txt.length + 1);

      typewriter.innerHTML = `<span class="wrap">${this.txt}</span>`;

      let delta = 200 - Math.random() * 100;

      if (this.isDeleting) {
        delta /= 2;
      }

      if (!this.isDeleting && this.txt === fullTxt) {
        delta = this.period;
        this.isDeleting = true;
      } else if (this.isDeleting && this.txt === '') {
        this.isDeleting = false;
        this.loopNum++;
        delta = 500;
      }

      setTimeout(() => {
        this.tick();
      }, delta);
    },
  },
};
</script>

<style scoped>
.typewrite > .wrap {
  border-right: 0.08em solid #659cf0;
  padding-right: 2px;
}

.fadein-up {
  opacity: 0;
  animation: fadeInUp 0.6s ease-out forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 24px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.fadein-right {
  opacity: 0;
  animation: fadeInRight 0.7s ease-out forwards;
  animation-delay: 300ms;
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>