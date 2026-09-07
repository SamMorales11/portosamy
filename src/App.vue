<template>
  <div class="max-w-7xl mx-auto flex flex-col relative">

    <nav class="max-w-7xl px-5 md:fixed top-0 z-[98] w-screen backdrop-blur-md bg-[#0a0a0a]/80 border-b border-[#1a1a1a]">
      <div class="container mx-auto flex flex-wrap items-center justify-between py-3">
        <button @click="redirectToHome" class="flex">
          <span class="self-center text-lg text-[#659cf0] font-semibold whitespace-nowrap hover:text-blue-400 transition-colors duration-300">
            samSiahaan();
          </span>
        </button>

        <div class="flex md:order-2">
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
              <router-link 
                to="/"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                Home
              </router-link>
            </li>
            <li>
              <router-link 
                to="/about"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                About
              </router-link>
            </li>
            <li>
              <router-link 
                to="/portfolio"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                Portfolio
              </router-link>
            </li>
            <li>
              <router-link 
                to="/career"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                Career
              </router-link>
            </li>
            <li>
              <router-link 
                to="/certificate"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                Certificate
              </router-link>
            </li>
            <li>
              <router-link 
                to="/contact"
                class="nav-link text-gray-400 hover:text-white block py-2 md:py-0 transition-colors duration-300"
              >
                Contact
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="md:mt-[80px]">
      <router-view />
    </div>
  </div>

  <!-- Mobile Bottom Navigation -->
  <footer class="block md:hidden fixed bottom-0 left-0 right-0 rounded-t-2xl border-t border-[#2a2a2a] bg-[#0a0a0a]/90 backdrop-blur-md z-[99]">
    <nav class="flex justify-around py-3 text-[11px]">
      <router-link to="/" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
        <span>Home</span>
      </router-link>
      <router-link to="/about" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
        <span>About</span>
      </router-link>
      <router-link to="/portfolio" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
        <span>Portfolio</span>
      </router-link>
      <router-link to="/career" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
        <span>Career</span>
      </router-link>
      <router-link to="/contact" class="flex flex-col items-center gap-0.5 text-gray-400 hover:text-[#659cf0] transition-colors">
        <span>Contact</span>
      </router-link>
    </nav>
  </footer>
</template>

<script>
export default {
  methods: {
    redirectToHome() {
      this.$router.push('/')
    }
  },
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
}

/* Active nav link style */
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

/* Mobile active state */
footer .router-link-exact-active {
  color: #659cf0 !important;
}
</style>