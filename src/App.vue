<template>
  <div class="relative min-h-screen">
    <!-- Animated Dot Background -->
    <canvas ref="dotCanvas" class="dot-canvas"></canvas>

    <!-- Scroll Progress Indicator -->
    <div class="scroll-progress" :style="{ width: scrollProgress + '%' }"></div>

    <div class="max-w-7xl mx-auto flex flex-col relative z-10">
      <nav class="max-w-7xl px-5 md:fixed top-0 z-[98] w-screen backdrop-blur-md bg-[#0a0a0a]/80 border-b border-[#1a1a1a] rounded-b-2xl">
        <div class="container mx-auto flex flex-wrap items-center justify-between py-3">
          <button @click="redirectToHome" class="flex">
            <span class="self-center text-lg text-[#659cf0] font-semibold whitespace-nowrap hover:text-blue-400 transition-colors duration-300">
              samSiahaan();
            </span>
          </button>

          <div class="flex items-center gap-4 md:order-2">
            <!-- Language Toggle -->
            <div class="flex items-center bg-[#1a1a1a] rounded-lg p-0.5 border border-[#2a2a2a]">
              <button
                @click="setLang('en')"
                class="px-2.5 py-1 text-xs font-medium rounded-md transition-all"
                :class="lang === 'en' ? 'bg-[#659cf0] text-white' : 'text-gray-400 hover:text-white'"
              >
                EN
              </button>
              <button
                @click="setLang('id')"
                class="px-2.5 py-1 text-xs font-medium rounded-md transition-all"
                :class="lang === 'id' ? 'bg-[#659cf0] text-white' : 'text-gray-400 hover:text-white'"
              >
                ID
              </button>
            </div>

            <a 
              href="https://github.com/SamMorales11" 
              target="_blank"
              rel="noopener noreferrer"
              class="hover:opacity-80 transition-opacity"
            >
              <img class="w-8 h-8 rounded-full" src="img/Download GitHub Logo, Git Hub Icon On White Background.jpg" alt="github">
            </a>
          </div>

          <div class="hidden md:flex justify-between items-center w-full md:w-auto md:order-1" id="mobile-menu-3">
            <ul class="flex-col md:flex-row flex md:space-x-8 mt-4 md:mt-0 md:text-sm md:font-medium">
              <li>
                <router-link to="/" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.home }}
                </router-link>
              </li>
              <li>
                <router-link to="/about" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.about }}
                </router-link>
              </li>
              <li>
                <router-link to="/portfolio" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.portfolio }}
                </router-link>
              </li>
              <li>
                <router-link to="/career" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.career }}
                </router-link>
              </li>
              <li>
                <router-link to="/certificate" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.certificate }}
                </router-link>
              </li>
              <li>
                <router-link to="/contact" class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300">
                  {{ t.nav.contact }}
                </router-link>
              </li>
            </ul>
          </div>
        </div>
      </nav>

      <div class="md:mt-[80px] relative">
        <div v-if="isLoading" class="page-skeleton">
          <div class="skeleton-line w-1/3 h-8 mb-6"></div>
          <div class="skeleton-line w-2/3 h-4 mb-3"></div>
          <div class="skeleton-line w-1/2 h-4 mb-8"></div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div class="skeleton-card"></div>
            <div class="skeleton-card"></div>
          </div>
        </div>

        <router-view v-slot="{ Component }">
          <transition name="page" mode="out-in">
            <component :is="Component" v-if="!isLoading" />
          </transition>
        </router-view>
      </div>
    </div>

    <!-- Back to Top Button -->
    <button 
      v-show="showBackToTop"
      @click="scrollToTop"
      class="back-to-top"
      title="Back to top"
    >
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <polyline points="18 15 12 9 6 15"></polyline>
      </svg>
    </button>

    <!-- Mobile Bottom Navigation -->
    <footer class="block md:hidden fixed bottom-0 left-0 right-0 rounded-t-2xl border-t border-[#2a2a2a] bg-[#0a0a0a]/90 backdrop-blur-md z-[99]">
      <nav class="flex justify-around py-3 text-[11px]">
        <router-link to="/" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
          <span>{{ t.nav.home }}</span>
        </router-link>
        <router-link to="/about" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
          <span>{{ t.nav.about }}</span>
        </router-link>
        <router-link to="/portfolio" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
          <span>{{ t.nav.portfolio }}</span>
        </router-link>
        <router-link to="/career" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
          <span>{{ t.nav.career }}</span>
        </router-link>
        <router-link to="/contact" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
          <span>{{ t.nav.contact }}</span>
        </router-link>
      </nav>
    </footer>
  </div>
</template>

<script>
import { messages } from './i18n.js';

export default {
  data() {
    return {
      animationId: null,
      particles: [],
      ctx: null,
      width: 0,
      height: 0,
      isLoading: false,
      scrollProgress: 0,
      showBackToTop: false,
      lang: localStorage.getItem('lang') || 'en'
    }
  },
  computed: {
    t() {
      return messages[this.lang];
    }
  },
  provide() {
    return {
      lang: () => this.lang,
      t: () => this.t,
      setLang: this.setLang
    }
  },
  watch: {
    $route() {
      this.isLoading = true;
      setTimeout(() => {
        this.isLoading = false;
      }, 350);
    }
  },
  methods: {
    setLang(lang) {
      this.lang = lang;
      localStorage.setItem('lang', lang);
    },
    redirectToHome() {
      this.$router.push('/')
    },
    handleScroll() {
      const scrollTop = window.scrollY;
      const docHeight = document.documentElement.scrollHeight - window.innerHeight;
      this.scrollProgress = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
      this.showBackToTop = scrollTop > 400;
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    },
    initCanvas() {
      const canvas = this.$refs.dotCanvas;
      if (!canvas) return;
      this.ctx = canvas.getContext('2d');
      this.resizeCanvas();
      this.createParticles();
      this.animate();
      window.addEventListener('resize', this.resizeCanvas);
    },
    resizeCanvas() {
      const canvas = this.$refs.dotCanvas;
      if (!canvas) return;
      this.width = window.innerWidth;
      this.height = window.innerHeight;
      canvas.width = this.width;
      canvas.height = this.height;
      this.createParticles();
    },
    createParticles() {
      const particleCount = Math.floor((this.width * this.height) / 7000);
      this.particles = [];
      for (let i = 0; i < particleCount; i++) {
        this.particles.push({
          x: Math.random() * this.width,
          y: Math.random() * this.height,
          size: Math.random() * 1.8 + 0.8,
          speedX: (Math.random() - 0.5) * 0.22,
          speedY: (Math.random() - 0.5) * 0.22,
          opacity: Math.random() * 0.4 + 0.1
        });
      }
    },
    animate() {
      if (!this.ctx) return;
      this.ctx.clearRect(0, 0, this.width, this.height);
      this.particles.forEach(p => {
        p.x += p.speedX;
        p.y += p.speedY;
        if (p.x < 0) p.x = this.width;
        if (p.x > this.width) p.x = 0;
        if (p.y < 0) p.y = this.height;
        if (p.y > this.height) p.y = 0;
        this.ctx.fillStyle = `rgba(101, 156, 240, ${p.opacity})`;
        this.ctx.fillRect(p.x, p.y, p.size, p.size);
      });
      this.animationId = requestAnimationFrame(this.animate);
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.initCanvas();
    });
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    if (this.animationId) cancelAnimationFrame(this.animationId);
    window.removeEventListener('resize', this.resizeCanvas);
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

::-webkit-scrollbar {
  width: 5px; 
  height: 5px; 
}

::-webkit-scrollbar-track {
  background: hsl(240, 1%, 17%);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb {
  background: #659cf0;
  border-radius: 5px;
}

body {
  font-family: 'Poppins', sans-serif;
  background: hsl(0, 0%, 7%);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #e5e5e5;
  min-height: 100vh;
  overflow-x: hidden;
}

.dot-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
}

.nav-link.router-link-exact-active {
  color: #ffffff !important;
  position: relative;
}

.nav-link.router-link-exact-active::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 100%;
  height: 2px;
  border-radius: 2px;
  background-color: #659cf0;
}

footer .router-link-exact-active {
  color: #659cf0 !important;
}

.page-enter-active,
.page-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.page-enter-from {
  opacity: 0;
  transform: translateY(12px);
}

.page-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}

.page-skeleton {
  padding: 2rem 1rem;
  animation: skeleton-pulse 1.4s ease-in-out infinite;
}

.skeleton-line {
  background: linear-gradient(90deg, #1a1a1a 25%, #252525 50%, #1a1a1a 75%);
  background-size: 200% 100%;
  border-radius: 8px;
  animation: skeleton-shimmer 1.4s infinite;
}

.skeleton-card {
  height: 180px;
  background: linear-gradient(90deg, #1a1a1a 25%, #252525 50%, #1a1a1a 75%);
  background-size: 200% 100%;
  border-radius: 16px;
  animation: skeleton-shimmer 1.4s infinite;
}

@keyframes skeleton-shimmer {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}

@keyframes skeleton-pulse {
  0%, 100% { opacity: 0.7; }
  50% { opacity: 1; }
}

.scroll-progress {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background: linear-gradient(90deg, #659cf0, #93c5fd);
  z-index: 9999;
  transition: width 0.1s ease-out;
  box-shadow: 0 0 8px rgba(101, 156, 240, 0.5);
}

.back-to-top {
  position: fixed;
  bottom: 80px;
  right: 24px;
  width: 44px;
  height: 44px;
  border-radius: 12px;
  background: #141414;
  border: 1px solid #2a2a2a;
  color: #659cf0;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 90;
  transition: all 0.3s ease;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.back-to-top:hover {
  background: #659cf0;
  color: white;
  border-color: #659cf0;
  transform: translateY(-3px);
  box-shadow: 0 6px 25px rgba(101, 156, 240, 0.3);
}

@media (min-width: 768px) {
  .back-to-top {
    bottom: 32px;
    right: 32px;
  }
}
</style>