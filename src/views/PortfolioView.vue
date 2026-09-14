<template>
  <div class="container mx-auto px-4 md:px-8 py-8 md:py-12">
    <div class="max-w-6xl mx-auto">
      
      <!-- Header -->
      <header class="mb-8 text-center md:text-left fadein-bot">
        <h1 class="text-3xl md:text-4xl font-bold text-white mb-2">
          {{ t().portfolio.title }}
        </h1>
        <p class="text-sm md:text-base text-gray-400">
          {{ t().portfolio.subtitle }}
        </p>
      </header>

      <!-- Filter Tabs -->
      <div class="flex flex-wrap gap-2 mb-8">
        <button
          v-for="cat in categories"
          :key="cat.key"
          @click="activeCategory = cat.key"
          class="px-4 py-2 rounded-lg text-sm font-medium transition-all duration-200"
          :class="activeCategory === cat.key 
            ? 'bg-[#659cf0] text-white shadow-[0_0_15px_rgba(101,156,240,0.3)]' 
            : 'bg-[#1a1a1a] text-gray-400 hover:text-white hover:bg-[#252525]'"
        >
          {{ cat.label }}
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="item in filteredItems"
          :key="item.id"
          class="group bg-[#141414] border border-[#2a2a2a] rounded-2xl overflow-hidden transition-all duration-300 hover:border-[#659cf0]/40 hover:shadow-[0_0_30px_rgba(101,156,240,0.1)] hover:-translate-y-1 flex flex-col"
        >
          <!-- Image -->
          <div class="relative overflow-hidden aspect-video bg-[#1a1a1a]">
            <img
              :src="`img/${item.imageFile}`"
              :alt="item.name"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
            />
          </div>

          <!-- Content -->
          <div class="p-5 flex flex-col flex-1">
            <div class="flex items-start justify-between gap-2 mb-2">
              <h3 class="text-lg font-bold text-white">
                {{ item.name }}
              </h3>
              <span class="text-[10px] px-2 py-0.5 rounded-full bg-[#659cf0]/10 text-[#659cf0] border border-[#659cf0]/20 whitespace-nowrap">
                {{ item.category }}
              </span>
            </div>

            <!-- Description -->
            <p
              class="text-sm text-gray-400 leading-relaxed"
              :class="{ 'line-clamp-3': !item.expanded }"
            >
              {{ item.status }}
            </p>

            <!-- Read more / Show less -->
            <button
              @click="item.expanded = !item.expanded"
              class="text-left text-sm text-[#659cf0] hover:text-blue-400 mt-2 mb-1 transition-colors font-medium"
            >
              {{ item.expanded ? t().portfolio.showLess : t().portfolio.readMore }}
            </button>

            <!-- Footer -->
            <div class="flex items-center justify-between mt-auto pt-4 border-t border-[#2a2a2a]">
              <span class="text-xs text-gray-500">
                {{ item.tech }}
              </span>

              <div class="flex items-center gap-3">
                <a
                  v-if="item.github !== 'null'"
                  :href="item.github"
                  target="_blank"
                  rel="noreferrer"
                  class="text-gray-400 hover:text-[#659cf0] transition-colors"
                  title="View GitHub"
                >
                  <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" height="18" width="18">
                    <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path>
                  </svg>
                </a>

                <a
                  v-if="item.demo !== 'null'"
                  :href="item.demo"
                  target="_blank"
                  rel="noreferrer"
                  class="text-gray-400 hover:text-[#659cf0] transition-colors"
                  title="Live Demo"
                >
                  <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" height="18" width="18">
                    <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                    <polyline points="15 3 21 3 21 9"></polyline>
                    <line x1="10" y1="14" x2="21" y2="3"></line>
                  </svg>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Empty State -->
      <div v-if="filteredItems.length === 0" class="text-center py-16 text-gray-500">
        {{ t().portfolio.empty }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PortfolioView',
  inject: ['t'],
  data() {
    return {
      activeCategory: 'All',
      items: [
        {
          id: 1,
          name: 'GEOTAGGING APP',
          imageFile: 'portofolio-geotag bpp.png',
          status: 'Led the development of an AI Chatbot integrated Geotagging System for the national Economic Census, automating data collection, validation, and user interaction. By combining NLP driven chatbots with geospatial analytics, the solution enabled real-time business mapping and data-driven insights, enhancing efficiency, accuracy, and policymaking.',
          tech: 'Python, Javascript',
          github: 'https://github.com/reno99986/capstone-ai/tree/samy',
          demo: 'null',
          category: 'Data Analyst',
          expanded: false
        },
        {
          id: 2,
          name: 'WEBSITE UMKM PPU',
          imageFile: 'potofolio-umkmppu.png',
          status: 'During my internship at the Penajam Paser Utara Regency Government, I contributed to the development of an e-commerce platform designed to digitize and expand market access for local micro, small, and medium enterprises (MSMEs). This initiative aimed to create a user friendly, scalable solution that bridges traditional businesses with the digital economy, fostering economic growth and community empowerment.',
          tech: 'Javascript, Tailwind',
          github: 'https://github.com/glenngladly26/e-commerce-ppu-kp/tree/samy',
          demo: 'null',
          category: 'Full Stack',
          expanded: false
        },
        {
          id: 3,
          name: 'BERKAH BOX',
          imageFile: 'portofolio-berkahbox.png',
          status: 'The Berkah Box Mosque Platform is an integrated company profile website and donation management system, specifically developed to streamline operations and promote transparency for the Berkah Box Mosque in Balikpapan. In my role as a Front-End Developer, I focused on designing and implementing an intuitive, responsive, and user-friendly interface to enhance accessibility and encourage community engagement.',
          tech: 'Laravel',
          github: 'https://github.com/Gibran699/CP-BerkahBox/tree/profil',
          demo: 'null',
          category: 'Full Stack',
          expanded: false
        },
        {
          id: 4,
          name: 'Acreage',
          imageFile: 'acreage2.jpeg',
          status: 'Acreage is a real-time real estate analytics dashboard that uses a Random Forest Regression model to estimate property market values. Built with FastAPI, Vue.js 3, and Tailwind CSS.',
          tech: 'Python, Vue.js, FastAPI',
          github: 'https://github.com/SamMorales11/project-acreage',
          demo: 'https://project-acreage.vercel.app/',
          category: 'Data Analyst',
          expanded: false
        },
        {
          id: 6,
          name: 'Asset Market',
          imageFile: 'portfolio-asset market.png',
          status: 'Pixel Store is a dynamic digital marketplace specializing in the exchange of premium creative assets, such as images, videos, visual effects (VFX), and 3D models. The platform serves as a bridge between talented creators and industry professionals.',
          tech: 'React Js, Firebase',
          github: 'https://github.com/Project-Ippl-Asset-Market',
          demo: 'null',
          category: 'Full Stack',
          expanded: false
        },
        {
          id: 7,
          name: 'AG Connect',
          imageFile: 'ag connect.jpeg',
          status: 'AG Connect is a modern, enterprise grade church management system designed to streamline congregation administration and boost community engagement through real time QR attendance tracking, dynamic gamification, and actionable data analytics.',
          tech: 'Vue js, Python',
          github: 'https://github.com/SamMorales11/ag-connect',
          demo: 'https://ag-connect.vercel.app/',
          category: 'Full Stack',
          expanded: false
        },
        {
          id: 8,
          name: 'Omnihealth',
          imageFile: 'omnihealth.png',
          status: 'OmniHealth Systems is a modern, enterprise grade clinical management suite designed to streamline medical operations and elevate patient care precision through structured SOAP documentation tracking, seamless e-prescribing, and actionable clinical analytics dashboards.',
          tech: 'TypeScript',
          github: 'https://github.com/SamMorales11/Omnihealth',
          demo: 'https://omnihealth-web.vercel.app/',
          category: 'Full Stack',
          expanded: false
        },
        {
          id: 9,
          name: 'Lionel Messi Career Analytics Dashboard',
          imageFile: 'messi.png',
          status: 'The Lionel Messi Career Goal Contributions Dashboard is an interactive analytics platform tracking Messi’s match level goals and assists from 2005 to 2026. It visualizes cumulative career milestones, situational splits, and comparative performance across FC Barcelona, PSG, Inter Miami, and Argentina to spotlight his sustained offensive efficiency and career trajectory.',
          tech: 'Jupyter Notebook, Python',
          github: 'https://github.com/SamMorales11/messi-dashboard',
          demo: 'https://messi-dashboard-az8x6ovyb3xkog8zsjugpu.streamlit.app/',
          category: 'Data Analyst',
          expanded: false
        },
        {
          id: 10,
          name: 'Gen-Z Behavioral Clustering',
          imageFile: 'genz.png',
          status: 'The Gen-Z Social Media Behavioral Archetypes project uses unsupervised clustering (DuckDB, MiniBatchKMeans) across 1M records to identify four usage personas, proving that temporal habits like late night scrolling and fragmented checking rather than platform choice are the primary drivers of digital addiction and lower well being.',
          tech: 'Jupyter Notebook',
          github: 'https://github.com/SamMorales11/gen-z-behavioral-clustering',
          demo: 'https://gen-z-behavioral-clustering-7fbcwkcuehn8qecirmyt4d.streamlit.app/',
          category: 'Data Analyst',
          expanded: false
        },
      ]
    };
  },
  computed: {
    categories() {
      return [
        { key: 'All', label: this.t().portfolio.all },
        { key: 'Full Stack', label: this.t().portfolio.fullStack },
        { key: 'Data Analyst', label: this.t().portfolio.dataAnalyst },
        { key: 'Others', label: this.t().portfolio.others },
      ];
    },
    filteredItems() {
      if (this.activeCategory === 'All') {
        return this.items;
      }
      return this.items.filter(item => item.category === this.activeCategory);
    }
  }
}
</script>

<style scoped>
.fadein-bot {
  opacity: 0;
  animation: fadeInBot 0.5s forwards;
}

@keyframes fadeInBot {
  from {
    opacity: 0;
    transform: translate3d(0, -16px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>