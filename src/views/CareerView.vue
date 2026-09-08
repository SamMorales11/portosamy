<template>
  <div class="container mx-auto px-4 md:px-8 py-8 md:py-12">
    <div class="max-w-4xl mx-auto">
      
      <!-- Header -->
      <header class="mb-10 fadein-bot">
        <h1 class="text-3xl md:text-4xl font-bold text-white mb-3">
          Professional Experience
        </h1>
        <div class="flex items-center gap-4">
          <p class="text-sm md:text-base text-gray-400 max-w-xl">
            A timeline of my career journey, past roles, and the impact I've made along the way.
          </p>
          <div class="hidden md:block h-[1px] flex-1 bg-gradient-to-r from-[#659cf0]/40 to-transparent rounded-full"></div>
        </div>
      </header>

      <!-- Timeline -->
      <div class="relative space-y-6">
        <!-- Vertical line -->
        <div class="absolute left-[27px] top-4 bottom-4 w-[2px] bg-[#2a2a2a] hidden md:block"></div>

        <div 
          v-for="job in careers" 
          :key="job.id" 
          class="relative group"
        >
          <!-- Timeline dot -->
          <div class="absolute left-[19px] top-8 w-[18px] h-[18px] rounded-full bg-[#0a0a0a] border-[3px] border-[#659cf0] z-10 hidden md:block"></div>

          <!-- Card -->
          <div 
            class="md:ml-16 bg-[#141414] border border-[#2a2a2a] rounded-2xl p-5 md:p-6 transition-all duration-300 hover:border-[#659cf0]/40 hover:shadow-[0_0_30px_rgba(101,156,240,0.08)]"
          >
            <div class="flex flex-col sm:flex-row gap-4 sm:gap-5">
              
              <!-- Logo -->
              <div class="w-14 h-14 md:w-16 md:h-16 bg-white rounded-xl flex items-center justify-center p-2 shrink-0 shadow-sm">
                <img :src="job.logo" :alt="job.company" class="w-full h-full object-contain">
              </div>
              
              <!-- Content -->
              <div class="flex-1 text-left">
                <div class="flex flex-col sm:flex-row sm:items-start sm:justify-between gap-2">
                  <div>
                    <h2 class="text-lg md:text-xl font-bold text-white leading-tight">
                      {{ job.role }}
                    </h2>
                    <p class="text-[#659cf0] text-sm md:text-base mt-0.5 font-medium">
                      {{ job.company }}
                    </p>
                  </div>
                  
                  <!-- Type Badge -->
                  <span class="self-start px-2.5 py-1 rounded-full text-[11px] font-medium bg-[#659cf0]/10 text-[#659cf0] border border-[#659cf0]/20">
                    {{ job.type }}
                  </span>
                </div>

                <p class="text-gray-500 text-xs md:text-sm mt-2 flex flex-wrap items-center gap-x-2 gap-y-1">
                  <span>{{ job.period }}</span>
                  <span class="text-gray-600">•</span>
                  <span>{{ job.duration }}</span>
                  <span class="text-gray-600">•</span>
                  <span>{{ job.workplace }}</span>
                  <span class="text-gray-600">•</span>
                  <span>{{ job.location }}</span>
                </p>
                
                <!-- Toggle Button -->
                <button 
                  @click="job.expanded = !job.expanded" 
                  class="mt-4 flex items-center gap-1.5 text-sm text-gray-400 hover:text-[#659cf0] transition-colors duration-200"
                >
                  <svg 
                    class="w-4 h-4 transition-transform duration-300"
                    :class="{ 'rotate-90': job.expanded }"
                    fill="none" 
                    stroke="currentColor" 
                    viewBox="0 0 24 24"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
                  </svg>
                  {{ job.expanded ? 'Hide details' : 'Show details' }}
                </button>
              </div>
            </div>

            <!-- Expanded Details -->
            <transition name="expand">
              <div v-if="job.expanded" class="mt-6 pt-6 border-t border-[#2a2a2a]">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-left">
                  
                  <!-- Responsibilities -->
                  <div>
                    <h3 class="text-[#659cf0] font-semibold text-sm mb-3 flex items-center gap-2">
                      <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2"/>
                      </svg>
                      Responsibilities
                    </h3>
                    <ul class="space-y-2">
                      <li 
                        v-for="(res, idx) in job.responsibilities" 
                        :key="idx" 
                        class="flex items-start gap-2 text-gray-300 text-sm leading-relaxed"
                      >
                        <span class="mt-1.5 w-1.5 h-1.5 rounded-full bg-[#659cf0] shrink-0"></span>
                        <span>{{ res }}</span>
                      </li>
                    </ul>
                  </div>

                  <!-- What I Learned -->
                  <div>
                    <h3 class="text-[#659cf0] font-semibold text-sm mb-3 flex items-center gap-2">
                      <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/>
                      </svg>
                      What I Learned
                    </h3>
                    <ul class="space-y-2">
                      <li 
                        v-for="(learn, idx) in job.learned" 
                        :key="idx" 
                        class="flex items-start gap-2 text-gray-300 text-sm leading-relaxed"
                      >
                        <span class="mt-1.5 w-1.5 h-1.5 rounded-full bg-[#659cf0] shrink-0"></span>
                        <span>{{ learn }}</span>
                      </li>
                    </ul>
                  </div>

                  <!-- Impact -->
                  <div>
                    <h3 class="text-[#659cf0] font-semibold text-sm mb-3 flex items-center gap-2">
                      <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
                      </svg>
                      Impact
                    </h3>
                    <ul class="space-y-2">
                      <li 
                        v-for="(imp, idx) in job.impact" 
                        :key="idx" 
                        class="flex items-start gap-2 text-gray-300 text-sm leading-relaxed"
                      >
                        <span class="mt-1.5 w-1.5 h-1.5 rounded-full bg-[#659cf0] shrink-0"></span>
                        <span>{{ imp }}</span>
                      </li>
                    </ul>
                  </div>

                </div>
              </div>
            </transition>
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
          location: 'Balikpapan, Indonesia',
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
            "Gained hands-on experience synthesizing geospatial data with machine learning models to generate real-time insights.",
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
          company: 'Penajam Paser Utara Regency Government',
          location: 'Penajam Paser Utara, Indonesia',
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
            "Gained practical experience translating technical knowledge into real-world applications during a government internship.",
            "Deepened understanding of how targeted technological solutions can drive local economic growth."
          ],
          impact: [
            "Helped digitize and expand market access for local UMKM through a modern e-commerce platform.",
            "Contributed to a more inclusive digital economy in the region."
          ]
        },
        {
          id: 3,
          role: 'Front-End Developer Intern',
          company: 'Media Selaras',
          location: 'Jakarta, Indonesia',
          period: 'Jul 2024 - Nov 2024',
          duration: '5 Months',
          type: 'Internship',
          workplace: 'Online',
          logo: '/img/selaras 1.jpg', 
          expanded: false,
          responsibilities: [
            "Developed and maintained front-end components for an educational technology platform.",
            "Collaborated with designers and backend developers to deliver responsive and accessible interfaces."
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
          company: 'Ambivers Foundation',
          location: 'Jakarta, Indonesia',
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

/* Expand transition */
.expand-enter-active,
.expand-leave-active {
  transition: all 0.3s ease;
  overflow: hidden;
}

.expand-enter-from,
.expand-leave-to {
  opacity: 0;
  max-height: 0;
  transform: translateY(-8px);
}

.expand-enter-to,
.expand-leave-from {
  opacity: 1;
  max-height: 1000px;
  transform: translateY(0);
}
</style>