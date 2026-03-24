<script>
export default {
  data() {
    return {
      activeTab: 1,
      items: [
        {
          id: 1,
          name: 'GEOTAGGING APP',
          imageFile: 'portofolio-geotag bpp.png', 
          status: 'Led the development of an AI Chatbot integrated Geotagging System for the national Economic Census, automating data collection, validation, and user interaction. By combining NLP driven chatbots with geospatial analytics, the solution enabled real-time business mapping and data-driven insights, enhancing efficiency, accuracy, and policymaking.',
          tech: 'Python, Javascript',
          github: 'https://github.com/reno99986/capstone-ai/tree/samy',
          demo: 'null',
          expanded: false // Tambahan untuk deteksi tombol klik
        },
        {
          id: 2,
          name: 'WEBSITE UMKM PPU',
          imageFile: 'potofolio-umkmppu.png', 
          status: 'During my internship at the Penajam Paser Utara Regency Government, I contributed to the development of an e-commerce platform designed to digitize and expand market access for local micro, small, and medium enterprises (MSMEs). This initiative aimed to create a user friendly, scalable solution that bridges traditional businesses with the digital economy, fostering economic growth and community empowerment.',
          tech: 'Javascript, Tailwind',
          github: 'https://github.com/glenngladly26/e-commerce-ppu-kp/tree/samy',
          demo: 'null',
          expanded: false
        },
        {
          id: 3,
          name: 'BERKAH BOX',
          imageFile: 'portofolio-berkahbox.png',
          status: 'The Berkah Box Mosque Platform is an integrated company profile website and donation management system, specifically developed to streamline operations and promote transparency for the Berkah Box Mosque in Balikpapan. In my role as a Front-End Developer, I focused on designing and implementing an intuitive, responsive, and user-friendly interface to enhance accessibility and encourage community engagement. ',
          tech: 'Laravel',
          github: 'https://github.com/Gibran699/CP-BerkahBox/tree/profil',
          demo: 'null',
          expanded: false
        },
        {
          id: 4,
          name: 'Acreage',
          imageFile: 'acreage2.jpeg',
          status: 'Acreage is a real-time real estate analytics dashboard that uses a Random Forest Regression model to estimate property market values. Built with FastAPI, Vue.js 3, and Tailwind CSS v4, the application features Explainable AI (XAI) visualizations through Chart.js to provide transparent, data-driven financial insights. This project showcases a seamless end-to-end integration of predictive modeling and modern web architecture.',
          tech: 'Vue, Python, Vite ',
          github: 'https://github.com/SamMorales11/project-acreage',
          demo: 'https://acreageproject.netlify.app/',
          expanded: false
        },
        {
          id: 5,
          name: 'ARTEMIS : ZERO',
          imageFile: 'portofolio-artemis zero.png',
          status: 'Artemis is a 2D story driven RPG featuring a distinctive retro pixel art style, inspired by the novel Artemis: Zero. The game immerses players in a richly narrative world, offering deep character interactions and strategic monster battles that seamlessly blend exploration, storytelling, and combat. Developed in Unity, Artemis reflects a dedication to indie game craftsmanship and innovative interactive storytelling, delivering a cohesive and engaging gaming experience.',
          tech: 'Unity, Click Up',
          github: 'null',
          demo: 'null',
          expanded: false
        },
        {
          id: 6,
          name: 'Asset Market',
          imageFile: 'portfolio-asset market.png',
          status: 'Pixel Store is a dynamic digital marketplace specializing in the exchange of premium creative assets, such as images, videos, visual effects (VFX), and 3D models. The platform serves as a bridge between talented creators and industry professionals, offering a curated selection of high-quality resources tailored for projects in gaming, film production, and digital media.',
          tech: 'React Js, Firebase',
          github: 'https://github.com/Project-Ippl-Asset-Market',
          demo: 'null',
          expanded: false
        },
        {
          id: 6,
          name: 'AG Connect',
          imageFile: 'ag connect.jpeg',
          status: 'AG Connect is a modern, enterprise-grade church management system designed to streamline congregation administration and boost community engagement through real-time QR attendance tracking, dynamic gamification, and actionable data analytics.',
          tech: 'Vue js, Python',
          github: 'https://github.com/SamMorales11/ag-connect',
          demo: 'https://ag-connect.vercel.app/',
          expanded: false
        },
      ]
    };
  }
}
</script>

<template>
  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-10 fadein-bot title-section flex items-center justify-center flex-col">
          <h4>Past Project Experience</h4>
          <h4 class="text-base font-normal text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-blue-500">
            Explore the projects I've worked on so far
          </h4>
        </div>
      </header>
      <section>
        <div>
          <div class="grid grid-cols-1 gap-6 pb-32 md:grid-cols-3 xl:grid-cols-3 fade-zoom-in">
            <div v-for="item in items" :key="item.id" class="h-full">
              <div class="item-card flex flex-col h-full gap-4 bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] rounded-xl text-amber-50 px-5 py-5 transition-all duration-300">
                
                <div class="w-full h-48 overflow-hidden rounded-lg zoom-in bg-white/5">
                  <img alt="Project Thumbnail" loading="lazy" decoding="async" data-nimg="1" 
                    class="w-full h-full object-cover object-top drop-shadow-xl transition-all duration-300 hover:scale-105"
                    :src="'/img/' + item.imageFile">
                </div>
                
                <div class="w-full flex flex-col flex-1 gap-2 text-sm md:text-base lg:text-lg">
                  <div class="title-text font-bold text-lg text-center md:text-left text-white">
                    {{ item.name }}
                  </div>
                  
                  <div class="flex flex-col gap-1">
                    <div :class="['w-full text-justify text-xs text-[#c1c1c1] md:text-sm transition-all duration-300', item.expanded ? '' : 'desc-clamp']">
                      {{ item.status }}
                    </div>
                    
                    <button @click="item.expanded = !item.expanded" class="text-blue-400 text-xs md:text-sm text-left w-fit hover:text-blue-300 mt-1 focus:outline-none">
                      {{ item.expanded ? 'Show less' : 'Read more' }}
                    </button>
                  </div>
                  
                  <div class="w-full mt-auto pt-4 flex flex-col gap-3">
                    <div class="text-sm text-left text-blue-300">
                      {{ item.tech }}
                    </div>
                    
                    <div class="w-full flex justify-end gap-3 text-primary">
                      <a v-if="item.github !== 'null'" :href="item.github" target="_blank" rel="noreferrer"
                        title="View github repository" class="transition-all hover:text-white">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"
                          height="20" width="20" xmlns="http://www.w3.org/2000/svg">
                          <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22">
                          </path>
                        </svg>
                      </a>
                      <a v-if="item.demo !== 'null'" :href="item.demo" target="_blank" rel="noreferrer"
                        title="View finished project" class="transition-all hover:text-white">
                        <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"
                          height="22" width="22" xmlns="http://www.w3.org/2000/svg">
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
          </div>
        </div>
      </section>
    </article>
  </div>
</template>

<style>
.item-card:hover {
  transition: transform 0.3s ease;
  transform: translateY(-8px);
}
svg:hover {
  stroke: #ffdb70;
}
@keyframes fadeZoomIn {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

.fade-zoom-in {
  animation: fadeZoomIn 1s ease-in-out;
}

/* Custom class untuk memotong teks otomatis */
.desc-clamp {
  display: -webkit-box;
  -webkit-line-clamp: 4; /* Sesuaikan angka ini jika ingin lebih panjang/pendek */
  line-clamp: 4;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>