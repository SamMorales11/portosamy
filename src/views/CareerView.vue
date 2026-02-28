<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col gap-5 md:px-20 fade-zoom-up">
      
      <header class="mb-4 md:mb-6 fadein-bot">
        <div class="flex flex-col gap-2 text-left">
          <h1 class="text-3xl md:text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-blue-500 inline-block">
            Professional Experience
          </h1>
          <div class="flex items-center gap-4 mt-1">
            <p class="text-sm md:text-base text-gray-400 max-w-lg">
              A timeline of my career journey, past roles, and the impact I've made along the way.
            </p>
            <div class="hidden md:block h-[1px] flex-1 bg-gradient-to-r from-blue-400/50 to-transparent rounded-full"></div>
          </div>
        </div>
      </header>

      <div v-for="job in careers" :key="job.id" class="bg-[#1e1e1f] border border-[#383838] rounded-xl p-5 md:p-6 transition-all duration-300">
        
        <div class="flex flex-col md:flex-row gap-4 md:gap-6">
          <div class="w-16 h-16 md:w-20 md:h-20 bg-white rounded-lg flex items-center justify-center p-2 shrink-0">
            <img :src="job.logo" :alt="job.company" class="w-full h-full object-contain">
          </div>
          
          <div class="flex flex-col flex-1 text-left">
            <h2 class="text-lg md:text-xl font-bold text-white">{{ job.role }}</h2>
            <p class="text-gray-400 text-sm md:text-base mt-1">{{ job.company }} &bull; {{ job.location }}</p>
            <p class="text-gray-500 text-xs md:text-sm mt-2">
              {{ job.period }} &bull; {{ job.duration }} &bull; {{ job.type }} &bull; {{ job.workplace }}
            </p>
            
            <button @click="job.expanded = !job.expanded" class="mt-4 w-fit flex items-center text-sm text-gray-400 hover:text-white transition-colors">
              <svg v-if="!job.expanded" class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
              <svg v-else class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
              {{ job.expanded ? 'Hide details' : 'Show details' }}
            </button>
          </div>
        </div>

        <div v-show="job.expanded" class="mt-6 pt-6 border-t border-[#383838] text-left fadein-bot">
          
          <div class="mb-6">
            <h3 class="text-blue-300 font-bold text-sm md:text-base mb-3 flex items-center uppercase tracking-wider">
              <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 10h16M4 14h16M4 18h16"></path></svg>
              Responsibilities
            </h3>
            <ul class="space-y-2">
              <li v-for="(res, idx) in job.responsibilities" :key="idx" class="flex items-start text-gray-300 text-sm md:text-base">
                <svg class="w-4 h-4 mr-2 mt-1 shrink-0 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                <span>{{ res }}</span>
              </li>
            </ul>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <h3 class="text-blue-300 font-bold text-sm md:text-base mb-3 flex items-center uppercase tracking-wider">
                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path></svg>
                What I Learned
              </h3>
              <ul class="space-y-2">
                <li v-for="(learn, idx) in job.learned" :key="idx" class="flex items-start text-gray-300 text-sm md:text-base">
                  <svg class="w-4 h-4 mr-2 mt-1 shrink-0 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                  <span>{{ learn }}</span>
                </li>
              </ul>
            </div>

            <div>
              <h3 class="text-blue-300 font-bold text-sm md:text-base mb-3 flex items-center uppercase tracking-wider">
                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                Impact
              </h3>
              <ul class="space-y-2">
                <li v-for="(imp, idx) in job.impact" :key="idx" class="flex items-start text-gray-300 text-sm md:text-base">
                  <svg class="w-4 h-4 mr-2 mt-1 shrink-0 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                  <span>{{ imp }}</span>
                </li>
              </ul>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CareerView',
  data() {
    return {
      careers: [
        {
          id: 1,
          role: 'Artificial Intelligence Engineer',
          company: 'Badan Pusat Statistik (Central Bureau of Statistics)',
          location: 'Balikpapan, Indonesia ID',
          period: 'Jul 2025 - Dec 2025',
          duration: '6 Months',
          type: 'Internship',
          workplace: 'Onsite',
          logo: 'img/bps 1.jpg', 
          expanded: false,
          responsibilities: [
            "Spearheaded the development and implementation of a Geotagging-Based Business Data System integrated with an AI Chatbot for the national Economic Census.",
            "Designed and deployed NLP driven chatbot solutions to automate complex workflows, including data collection, validation, and user interaction.",
            "Collaborated closely with cross-functional teams to integrate geospatial data analytics and AI models into cohesive, functional systems."
          ],
          learned: [
            "Deepened practical knowledge of Natural Language Processing (NLP) and AI model deployment within a large scale.",
            "Gained hands-on experience synthesizing geospatial data with machine learning models to generate real-time.",
            "Strengthened cross-functional collaboration skills by working alongside diverse teams to deliver a national-level digital infrastructure project."
          ],
          impact: [
            "Significantly enhanced the efficiency and accuracy of the national Economic Census process by automating data collection and validation.",
            "Delivered real-time business mapping capabilities, empowering policymakers and stakeholders with robust, data-driven decision-making tools."
          ]
        },
        {
          id: 2,
          role: 'Front-End Developer',
          company: ' Penajam Paser Utara Regency Government',
          location: 'Penajam Paser Utara, Indonesia ID',
          period: 'May 2024 - Nov 2024',
          duration: '7 Months',
          type: 'Practical Work',
          workplace: 'Onsite',
          logo: '/img/ppu 1.png', 
          expanded: false,
          responsibilities: [
            "Collaborated in developing a scalable, user-friendly e-commerce platform for local micro, small, and medium enterprises (UMKM).",
            "Applied technical software development skills to build digital solutions aimed at empowering traditional businesses."
          ],
          learned: [
            "Gained practical experience translating technical knowledge into real-world applications during a two-month government internship.",
            "Deepened my understanding of how targeted technological solutions can directly drive local economic growth and community development."
          ],
          impact: [
            "Expanded digital market access for regional UMKMs, successfully bridging the gap between traditional commerce and the digital economy.",
            "Delivered a functional platform that actively supports local government initiatives in driving community economic empowerment."
          ]
        },
        {
          id: 3,
          role: 'Front-End Developer Intern',
          company: ' Media Selaras',
          location: 'Jakarta, Indonesia ID',
          period: 'Jul 2024 - Nov 2024',
          duration: '5 Months',
          type: 'Internship',
          workplace: 'Online',
          logo: '/img/selaras 1.jpg', 
          expanded: false,
          responsibilities: [
            "Developed the front-end interface for an online learning platform focused on thesis consultation and university entrance exam preparation.",
            "Implemented user-centric designs and optimized web functionality to ensure a seamless user experience.",
            "Collaborated within a multidisciplinary team to translate project requirements into accessible and engaging web features."
          ],
          learned: [
            "Enhanced practical skills in applying user-centered design principles within a real-world educational technology environment.",
            "Gained valuable experience in cross-functional collaboration to successfully build and optimize front-end performance."
          ],
          impact: [
            "Improved academic accessibility for students by helping deliver a structured, easy-to-navigate platform for educational support.",
            "Contributed to an intuitive and impactful user experience that directly advanced the platform's goal of enhancing academic delivery."
          ]
        },
        {
          id: 4,
          role: 'Project Management Officer',
          company: ' Ambivers Foundation',
          location: 'Jakarta, Indonesia ID',
          period: 'Apr 2025 - Oct 2025',
          duration: '7 Months',
          type: 'Internship',
          workplace: 'Hybrid',
          logo: '/img/ambivers 1.png', 
          expanded: false,
          responsibilities: [
            "Planned and managed project timelines, ensuring seamless progress tracking and timely updates.",
            "Coordinated actively with stakeholders to identify and mitigate risks while maintaining rigorous quality standards.",
            "Managed project budgets, resources, and key deliverables to ensure completion on time and strictly within scope."
          ],
          learned: [
            "Mastered effective cross-functional communication and stakeholder collaboration to drive continuous project success.",
            "Developed strong expertise in proactive risk management and continuous improvement strategies throughout the project lifecycle."
          ],
          impact: [
            "Consistently delivered high-quality projects that met or exceeded stakeholder expectations.",
            "Enhanced overall project outcomes and long-term stakeholder satisfaction through regular evaluation and process optimization."
          ]
        },
      ]
    }
  }
}
</script>

<style scoped>
@keyframes fadeZoomUp {
  0% {
    opacity: 0;
    transform: scale(0.95);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
.fade-zoom-up {
  animation: fadeZoomUp 0.8s ease-in-out;
}

.fadein-bot {
  opacity: 0;
  animation: fadeInBot 0.5s forwards;
}
@keyframes fadeInBot {
  from {
    opacity: 0;
    transform: translate3d(0, -20px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
</style>