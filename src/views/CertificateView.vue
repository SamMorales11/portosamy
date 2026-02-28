<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col-reverse md:flex-row relative">
      <div class="w-full md:w-2/3">
        <div class="flex flex-col gap-10 md:px-20 fade-zoom-up">
          
          <div v-for="(org, index) in certificatesData" :key="index" :id="'org-' + index" class="flex flex-col scroll-mt-28 md:scroll-mt-32">
            <div class="flex items-center mb-5">
              <div class="h-[1px] w-10 bg-blue-500 mr-2"></div>
              <h2 class="text-xl md:text-2xl text-white font-bold">{{ org.organization }}</h2>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
              <div v-for="cert in org.certificates" :key="cert.id" class="flex flex-col bg-[#1e1e1f] border border-[#383838] rounded-xl text-left text-white p-4 transition-all duration-300 hover:bg-[#282828] hover:scale-105 hover:-translate-y-1">
                <div class="w-full h-48 md:h-40 overflow-hidden rounded-lg mb-4 bg-white/5">
                  <img :src="cert.image" alt="Certificate" class="w-full h-full object-cover">
                </div>
                
                <div class="w-full flex flex-col flex-1">
                  <div class="text-xs mb-2 text-slate-400 flex items-center italic">
                    {{ cert.date }}
                  </div>
                  <h1 class="text-sm md:text-base text-blue-300 font-bold mb-2 paraf">{{ cert.title }}</h1>
                  
                  <div class="flex items-center justify-between mt-auto pt-3">
                    <div class="text-xs text-[#c1c1c1]">
                      {{ cert.credentialId }}
                    </div>
                    
                    <a v-if="cert.link" :href="cert.link" target="_blank" rel="noreferrer"
                       title="View Certificate" class="transition-all text-amber-50 hover:text-white">
                      <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round"
                        height="20" width="20" xmlns="http://www.w3.org/2000/svg">
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
      
      <div class="w-full md:w-1/3 h-fit p-8 md:sticky md:top-24">
        <div class="flex flex-col text-left">
          <div class="bg-clip-text bg-gradient-to-r from-white to-blue-400 text-transparent text-2xl font-bold mb-3">
            My Certificates
          </div>
          <div class="text-slate-400 text-sm">
            A collection of certifications and achievements I've earned from various organizations and platforms.
          </div>
          <div class="h-[1px] mt-7 mb-7 w-20 bg-blue-400 mr-2"></div>
          
          <div class="hidden md:block">
            <div class="text-white text-md font-semibold mb-3">Issuing Organizations</div>
            <div class="mt-3 flex flex-wrap gap-2">
              <span v-for="(org, index) in certificatesData" :key="index"
                @click="scrollToSection(index)"
                class="py-2 px-3 rounded-2xl bg-[#1e1e1f] text-white text-xs cursor-pointer hover:bg-[#282828] hover:text-blue-300 transition-all duration-300">
                {{ org.organization }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CertificateView',
  data() {
    return {
      certificatesData: [
        {
          organization: "Dicoding Indonesia",
          certificates: [
            { 
              id: 1, 
              title: "Basic Data Visualization", 
              date: "Desember 2023", 
              credentialId: "Cred ID: GRX5QLD3YZ0M", 
              image: "/img/dicoding 1.jpeg",
              link: "https://drive.google.com/file/d/1dHRWBehlr9KR_EWiha-5DMj8_C87cWVu/view?usp=sharing" 
            },
            { 
              id: 2, 
              title: "Basic AWS Cloud", 
              date: "Desember 2024", 
              credentialId: "Cred ID: JMZV4K03NXN9", 
              image: "/img/dicoding 3.jpeg",
              link: "https://drive.google.com/file/d/1-k_zAmN5zXoWXxvFjOd30iZDhA-v5_GK/view?usp=sharing"
            },
            { 
              id: 3, 
              title: "Basic IT Project Management", 
              date: "Agustus 2024", 
              credentialId: "Cred ID: 98XWL1660ZM3", 
              image: "/img/dicoding 4.jpeg",
              link: "https://drive.google.com/file/d/1Exvqe21YlljOKQRzG7kgWoPj0zgnzreN/view?usp=sharing"
            },
            { 
              id: 4, 
              title: "Basic Structured Query Language (SQL)", 
              date: "Februari 2024", 
              credentialId: "Cred ID: 1RXY1E8M9PVM", 
              image: "/img/dicoding 5.jpeg",
              link: "https://drive.google.com/file/d/1Uy15YjpvKInhys4OZk1UsBpGy_XceIiW/view?usp=sharing"
            },
            { 
              id: 5, 
              title: "Basic Data Science", 
              date: "September 2024", 
              credentialId: "Cred ID: JLX14G1K6X72", 
              image: "/img/dicoding 6.jpeg",
              link: "https://drive.google.com/file/d/1uXfNT525xrF0RZ2IdwlTLAIJDVi_TPf5/view?usp=sharing"
            },
            { 
              id: 6, 
              title: "Basic Javascript", 
              date: "Januari 2025", 
              credentialId: "Cred ID: RVZKW640NZD5", 
              image: "/img/dicoding 7.jpeg",
              link: "https://drive.google.com/file/d/1PfkYSVfg9q_VtqglzmbGVHgC_AhpDwxf/view?usp=sharing"
            }
          ]
        },
        {
          organization: "Coursera",
          certificates: [
            { 
              id: 7, 
              title: "Game Theory", 
              date: "Februari 2025", 
              credentialId: "Cred ID: HUI28S4JBN99", 
              image: "/img/coursera 1.jpeg",
              link: "https://drive.google.com/file/d/1UOXNUILwI-CeKTvgsJNUVtLHT6B_Awrd/view?usp=sharing"
            },
            { 
              id: 8, 
              title: "Financial Markets", 
              date: "Februari 2025", 
              credentialId: "Cred ID: JJ23RGQYIMM7", 
              image: "/img/coursera 2.jpeg",
              link: "https://drive.google.com/file/d/1raa3Zo-jHf0fJpTajYEnT-8X1mEIL6la/view?usp=sharing"
            },
            { 
              id: 9, 
              title: "Mathematical Thinking", 
              date: "April 2025", 
              credentialId: "Cred ID: F5N4J6Z39PQ0", 
              image: "/img/coursera 3.jpeg",
              link: "https://drive.google.com/file/d/1W9TR10Fi0GsjvzVaudcqvRqaNHu02PVb/view?usp=sharing"
            },
            { 
              id: 10, 
              title: "Cryptography", 
              date: "Februari 2025", 
              credentialId: "Cred ID: TXAAF0VJN9Z1", 
              image: "/img/coursera 4.jpeg",
              link: "https://drive.google.com/file/d/1Jlz8uF47_MVx5RdhPgDZFufWB3MrN87u/view?usp=sharing"
            },
          ]
        },
        {
          organization: "Cisco Academy",
          certificates: [
            { 
              id: 7, 
              title: "Cyber Threat Management", 
              date: "April 2024",  
              image: "/img/cisco 1.jpeg",
              link: "https://drive.google.com/file/d/12lJNyMs2T9HFH4DszbCjk5dZU2v4wGn7/view?usp=sharing"
            },
            { 
              id: 8, 
              title: "Ethical Hacker", 
              date: "Januari 2025", 
              image: "/img/cisco 2.jpeg",
              link: "https://drive.google.com/file/d/1Ukr6NF-AfP5Dwbq3zmFjcYRuWQIk-Jvv/view?usp=sharing"
            },
            { 
              id: 9, 
              title: "English for IT", 
              date: "Maret 2025", 
              image: "/img/cisco 3.jpeg",
              link: "https://drive.google.com/file/d/1Ybq-Eu7wKMEbLSYpGn6Ig4XKulceDIxV/view?usp=sharing"
            },
            { 
              id: 10, 
              title: "Introduction to Cybersecurity", 
              date: "Februari 2025", 
              image: "/img/cisco 4.jpeg",
              link: "https://drive.google.com/file/d/1sY1_Tcw5-Ka4U5g_oSi8akdIHGqi7YfT/view?usp=sharing"
            },
          ]
        },
        {
          organization: "Udemy",
          certificates: [
            { 
              id: 7, 
              title: "AI Engineering Masterclass: From Zero to AI Hero", 
              date: "Juli 2025",  
              image: "/img/udemy 1.jpeg",
              link: "https://drive.google.com/file/d/12AUFSHlN9xPm4oXa9CCTyxpx7wgtQiYk/view?usp=sharing"
            },
            { 
              id: 8, 
              title: "AI & Quantum Computing Mastery Bootcamp", 
              date: "Juli 2025", 
              image: "/img/udemy 2.jpeg",
              link: "https://drive.google.com/file/d/1hrJxirq2BRWSKCxmKB7cUC9VzF8WNlac/view?usp=sharing"
            },
          ]
        },
        {
          organization: "Semrush Academy",
          certificates: [
            { 
              id: 7, 
              title: "International SEO", 
              date: "Juli 2025",
              credentialId: "Cred ID: 6b7a3266cb",
              image: "/img/semrush 1.jpeg",
              link: "https://drive.google.com/file/d/1sQA1gZ-WYbSyKx_iQ0ATLAMJ6wpEsoEG/view?usp=sharing"
            },
            { 
              id: 8, 
              title: "Mastering Youtube Search Trends and SEO Strategis", 
              date: "Juli 2025",
              credentialId: "Cred ID: 8ed676790e",
              image: "/img/semrush 2.jpeg",
              link: "https://drive.google.com/file/d/1GRzNn4WEUlhW6KDvpL-l9waKgQXtDkje/view?usp=sharing"
            },
          ]
        },
        {
          organization: "IBM Skills Build",
          certificates: [
            { 
              id: 7, 
              title: "Classifying Data Using IBM Granite", 
              date: "Agustus 2025",
              image: "/img/ibm 1.jpeg",
              link: "https://drive.google.com/file/d/1JvS5kZi3GMlBkvXC-END3MRhn_IPzpdY/view?usp=sharing"
            },
            { 
              id: 8, 
              title: "Summarizing Data Using IBM Granite", 
              date: "Agustus 2025",
              image: "/img/ibm 1.jpeg",
              link: "https://drive.google.com/file/d/1_lL6KnIdLcJ84znUaH4G73At5ZBP-u4y/view?usp=sharing"
            },
          ]
        },
      ]
    }
  },
  // Tambahkan methods scrollToSection di sini
  methods: {
    scrollToSection(index) {
      const element = document.getElementById('org-' + index);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
}
</script>

<style scoped>
.paraf {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
  overflow: hidden;
}

@keyframes fadeZoomUp {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
.fade-zoom-up {
  animation: fadeZoomUp 1s ease-in-out;
}

svg:hover {
  stroke: #ffdb70;
}
</style>