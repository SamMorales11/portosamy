<template>
  <div class="container mx-auto px-4 md:px-8 py-8 md:py-12">
    <div class="max-w-5xl mx-auto space-y-12">

      <!-- ===== About Me Card ===== -->
      <div class="bg-[#141414] border border-[#2a2a2a] rounded-2xl p-6 md:p-8">
        <header class="mb-6">
          <h1 class="text-2xl md:text-3xl font-bold text-white flex items-center gap-3">
            {{ t().about.title }}
            <span class="h-[2px] w-16 md:w-32 bg-[#659cf0] rounded-full"></span>
          </h1>
        </header>

        <section class="flex flex-col md:flex-row gap-8 items-center md:items-start">
          <!-- Photo -->
          <div class="shrink-0">
            <img
              class="w-40 h-40 md:w-48 md:h-48 rounded-full object-cover border-2 border-[#659cf0]/40 shadow-[0_0_30px_rgba(101,156,240,0.15)]"
              src="img/Screenshot 2026-02-20 103528.jpg"
              alt="Samuel Siahaan"
            />
          </div>

          <!-- Bio -->
          <div class="flex-1 text-left">
            <p class="text-gray-300 text-sm md:text-base leading-relaxed mb-4 text-justify">
              Hi everyone! My name is <span class="text-white font-medium">Samuel Benedicto Siahaan</span>, an Informatics student and Balikpapan based Full-Stack Developer with an active focus on Data Analytics and Cybersecurity. Over the past three years, I have dedicated myself to engineering impactful digital solutions, approaching software development not merely as a technical task, but as a craft that balances functional precision with aesthetic elegance.
            </p>
            <p class="text-gray-300 text-sm md:text-base leading-relaxed mb-4 text-justify">
              My core focus centers on designing maintainable, scalable architectures backed by data driven insights and security first principles. I combine full-stack development expertise with analytical rigor to solve complex business problems, maintaining high standards for code quality, system efficiency, and clear, proactive communication.
            </p>
            <p class="text-gray-400 text-sm mt-6">
              Best regards,
            </p>
            <p class="font-signature text-[#659cf0] text-2xl mt-1">samuel</p>
          </div>
        </section>
      </div>

      <!-- ===== Technical Arsenal ===== -->
      <div>
        <div class="flex items-center gap-3 mb-6">
          <h2 class="text-xl md:text-2xl font-bold text-white">{{ t().about.technical }}</h2>
          <span class="h-[2px] flex-1 bg-gradient-to-r from-[#659cf0]/50 to-transparent rounded-full"></span>
        </div>

        <!-- Tabs -->
        <div class="flex gap-3 mb-6">
          <button
            @click="activeTab = 1"
            :class="activeTab === 1 ? 'bg-[#659cf0] text-white' : 'bg-[#1a1a1a] text-gray-400 hover:text-white'"
            class="px-4 py-2 rounded-lg text-sm font-medium transition-colors"
          >
            {{ t().about.techStack }}
          </button>
          <button
            @click="activeTab = 2"
            :class="activeTab === 2 ? 'bg-[#659cf0] text-white' : 'bg-[#1a1a1a] text-gray-400 hover:text-white'"
            class="px-4 py-2 rounded-lg text-sm font-medium transition-colors"
          >
            {{ t().about.tools }}
          </button>
        </div>

        <!-- Tech Stack -->
        <div v-show="activeTab === 1" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4">
          <div
            v-for="item in tech"
            :key="item.id"
            class="item-tech flex items-center gap-3 rounded-xl border border-[#2a2a2a] bg-[#141414] px-3 py-3 hover:border-[#659cf0]/40 transition-all duration-300 cursor-default"
          >
            <div class="w-10 h-10 flex items-center justify-center shrink-0">
              <img
                :src="item.imageUrl"
                :alt="item.name"
                class="w-8 h-8 object-contain"
                loading="lazy"
              />
            </div>
            <div class="min-w-0">
              <p class="text-sm font-medium text-white truncate">{{ item.name }}</p>
              <p class="text-xs text-gray-500">{{ item.status }}</p>
            </div>
          </div>
        </div>

        <!-- Tools -->
        <div v-show="activeTab === 2" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4">
          <div
            v-for="item in tools"
            :key="item.id"
            class="item-tech flex items-center gap-3 rounded-xl border border-[#2a2a2a] bg-[#141414] px-3 py-3 hover:border-[#659cf0]/40 transition-all duration-300 cursor-default"
          >
            <div class="w-10 h-10 flex items-center justify-center shrink-0">
              <img
                :src="item.imageUrl"
                :alt="item.name"
                class="w-8 h-8 object-contain"
                loading="lazy"
              />
            </div>
            <div class="min-w-0">
              <p class="text-sm font-medium text-white truncate">{{ item.name }}</p>
              <p class="text-xs text-gray-500">{{ item.status }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- ===== GitHub Contributions ===== -->
      <div>
        <div class="flex items-center gap-3 mb-6">
          <h2 class="text-xl md:text-2xl font-bold text-white">{{ t().about.github }}</h2>
          <span class="h-[2px] flex-1 bg-gradient-to-r from-[#659cf0]/50 to-transparent rounded-full"></span>
        </div>

        <div class="bg-[#141414] border border-[#2a2a2a] rounded-2xl p-5 md:p-6 overflow-x-auto">
          <div class="github-chart-wrapper">
            <img
              src="https://ghchart.rshah.org/659cf0/SamMorales11"
              alt="SamMorales11 GitHub Contributions"
              class="w-full max-w-full github-chart"
              loading="lazy"
            />
          </div>

          <div class="flex justify-between items-center mt-4 text-xs text-gray-500">
            <a 
              href="https://github.com/SamMorales11" 
              target="_blank" 
              rel="noopener noreferrer"
              class="hover:text-[#659cf0] transition-colors"
            >
              {{ t().about.viewGithub }}
            </a>
            <span>Less → More</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'AboutView',
  inject: ['t'],
  data() {
    return {
      activeTab: 1,
      tech: [
        {
          id: 1,
          name: 'HTML',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/1051/1051277.png',
          status: 'Advanced'
        },
        {
          id: 2,
          name: 'CSS',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/732/732190.png',
          status: 'Advanced'
        },
        {
          id: 3,
          name: 'PHP',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-php-2038871-1720084.png',
          status: 'Intermediate'
        },
        {
          id: 4,
          name: 'Javascript',
          imageUrl: 'https://img.icons8.com/?size=100&id=108784&format=png&color=000000',
          status: 'Advance'
        },
        {
          id: 5,
          name: 'Laravel',
          imageUrl: 'https://cdn.worldvectorlogo.com/logos/laravel-2.svg',
          status: 'Intermediate'
        },
        {
          id: 6,
          name: 'Typescript',
          imageUrl: 'https://img.icons8.com/?size=100&id=nCj4PvnCO0tZ&format=png&color=000000',
          status: 'Intermediate'
        },
        {
          id: 7,
          name: 'VueJS',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-vue-282497.png?f=webp',
          status: 'Intermediate'
        },
        {
          id: 8,
          name: 'Python',
          imageUrl: 'https://img.icons8.com/?size=100&id=13441&format=png&color=000000',
          status: 'Advance'
        },
        {
          id: 9,
          name: 'Golang',
          imageUrl: 'https://img.icons8.com/?size=100&id=7ej5ASIwdQXG&format=png&color=000000',
          status: 'Intermediate'
        },
        {
          id: 10,
          name: 'Tailwind',
          imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg',
          status: 'Intermediate'
        },
        {
          id: 11,
          name: 'Bootstrap',
          imageUrl: 'https://getbootstrap.com/docs/5.2/assets/brand/bootstrap-logo-shadow.png',
          status: 'Intermediate'
        },
        {
          id: 12,
          name: 'ReactJS',
          imageUrl: 'https://cdn4.iconfinder.com/data/icons/logos-3/600/React.js_logo-512.png',
          status: 'Intermediate'
        },
        {
          id: 13,
          name: 'NextJS',
          imageUrl: 'https://img.icons8.com/?size=100&id=MWiBjkuHeMVq&format=png&color=000000',
          status: 'Intermediate'
        },
        {
          id: 14,
          name: 'Pandas',
          imageUrl: 'https://img.icons8.com/?size=100&id=xSkewUSqtErH&format=png&color=000000',
          status: 'Advanced'
        },
         {
          id: 15,
          name: 'Numpy',
          imageUrl: 'https://img.icons8.com/?size=100&id=aR9CXyMagKIS&format=png&color=000000',
          status: 'Advanced'
        },
         {
          id: 16,
          name: 'Linux',
          imageUrl: 'https://img.icons8.com/?size=100&id=17842&format=png&color=000000',
          status: 'Intermediate'
        },
      ],
      tools: [
        {
          id: 1,
          name: 'Git',
          imageUrl: 'https://img.icons8.com/?size=100&id=6Qr2kBSBemvq&format=png&color=000000',
          status: 'Version Control'
        },
        {
          id: 2,
          name: 'GitHub',
          imageUrl: 'https://img.icons8.com/?size=100&id=efFfwotdkiU5&format=png&color=000000',
          status: 'Community Building'
        },
        {
          id: 3,
          name: 'NPM',
          imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-npm-3-1175132.png',
          status: 'Package Manager'
        },
        {
          id: 4,
          name: 'MySQL',
          imageUrl: 'https://cdn-icons-png.flaticon.com/512/5968/5968313.png',
          status: 'Database'
        },
        {
          id: 5,
          name: 'Postgresql',
          imageUrl: 'https://img.icons8.com/?size=100&id=38561&format=png&color=000000',
          status: 'Database'
        },
        {
          id: 6,
          name: 'Notion',
          imageUrl: 'https://img.icons8.com/?size=100&id=lVWXUlZQdwgv&format=png&color=000000',
          status: 'Project Management'
        },
        {
          id: 7,
          name: 'Docker',
          imageUrl: 'https://img.icons8.com/?size=100&id=cdYUlRaag9G9&format=png&color=000000',
          status: 'Devops Tools'
        },
        {
          id: 8,
          name: 'Postman',
          imageUrl: 'https://img.icons8.com/?size=100&id=QEQQKirln6Tf&format=png&color=000000',
          status: 'API Testing'
        },
         {
          id: 9,
          name: 'Visual Studio Code',
          imageUrl: 'https://img.icons8.com/?size=100&id=0OQR1FYCuA9f&format=png&color=000000',
          status: 'Source Code Editor'
        },
        {
          id: 10,
          name: 'Jupyter Notebook',
          imageUrl: 'https://img.icons8.com/?size=100&id=J0SgMWzAxqFj&format=png&color=000000',
          status: 'Data Analysis'
        },
         {
          id: 11,
          name: 'Tableau',
          imageUrl: 'https://img.icons8.com/?size=100&id=9Kvi1p1F0tUo&format=png&color=000000',
          status: 'Data Visualization'
        },
        {
          id: 12,
          name: 'Kali Linux',
          imageUrl: 'https://img.icons8.com/?size=100&id=qBWtR72kluCU&format=png&color=000000',
          status: 'Penetration Testing'
        },
         {
          id: 13,
          name: 'Arch Linux',
          imageUrl: 'https://img.icons8.com/?size=100&id=uIXgLv5iSlLJ&format=png&color=000000',
          status: 'Development Environment'
        },
      ]
    };
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

.font-signature {
  font-family: 'Pacifico', cursive;
}

.item-tech:hover img {
  transform: scale(1.15);
  transition: transform 0.25s ease;
}

/* Membuat kotak kosong terlihat lebih soft (abu-abu transparan) */
.github-chart-wrapper {
  filter: brightness(0.85) contrast(1.1);
}

.github-chart {
  opacity: 0.95;
}
</style>