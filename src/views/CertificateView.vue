<template>
  <div class="container mx-auto px-4 md:px-8 py-8 md:py-12">
    <div class="max-w-6xl mx-auto">

      <!-- Header -->
      <header class="mb-10 fadein-bot">
        <h1 class="text-3xl md:text-4xl font-bold text-white mb-2">
          {{ t().certificate.title }}
        </h1>
        <p class="text-sm md:text-base text-gray-400 max-w-xl">
          {{ t().certificate.subtitle }}
        </p>
      </header>

      <div class="flex flex-col lg:flex-row gap-8">
        
        <!-- Sidebar Filter -->
        <aside class="lg:w-64 shrink-0">
          <div class="sticky top-24 bg-[#141414] border border-[#2a2a2a] rounded-2xl p-5">
            <h3 class="text-sm font-semibold text-gray-400 uppercase tracking-wider mb-4">
              {{ t().certificate.organizations }}
            </h3>
            <div class="flex flex-wrap lg:flex-col gap-2">
              <button
                v-for="(org, index) in certificatesData"
                :key="index"
                @click="scrollToSection(index)"
                class="text-left px-3 py-2 rounded-lg text-sm transition-all duration-200"
                :class="activeOrg === index 
                  ? 'bg-[#659cf0]/15 text-[#659cf0] border border-[#659cf0]/30' 
                  : 'text-gray-400 hover:text-white hover:bg-[#1a1a1a]'"
              >
                {{ org.organization }}
              </button>
            </div>
          </div>
        </aside>

        <!-- Certificates List -->
        <div class="flex-1 space-y-12">
          <section
            v-for="(org, index) in certificatesData"
            :key="index"
            :id="'org-' + index"
            class="scroll-mt-28"
          >
            <div class="flex items-center gap-3 mb-6">
              <div class="h-[2px] w-8 bg-[#659cf0] rounded-full"></div>
              <h2 class="text-xl md:text-2xl font-bold text-white">
                {{ org.organization }}
              </h2>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
              <div
                v-for="cert in org.certificates"
                :key="cert.id"
                class="group bg-[#141414] border border-[#2a2a2a] rounded-2xl overflow-hidden transition-all duration-300 hover:border-[#659cf0]/40 hover:shadow-[0_0_25px_rgba(101,156,240,0.08)] hover:-translate-y-1"
              >
                <div class="aspect-[4/3] overflow-hidden bg-[#1a1a1a]">
                  <img
                    :src="cert.image"
                    :alt="cert.title"
                    class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
                    loading="lazy"
                  />
                </div>

                <div class="p-4 flex flex-col">
                  <p class="text-xs text-gray-500 mb-1">
                    {{ cert.date }}
                  </p>
                  <h3 class="text-sm md:text-base font-semibold text-white leading-snug mb-2 line-clamp-2">
                    {{ cert.title }}
                  </h3>

                  <div class="flex items-center justify-between mt-auto pt-3 border-t border-[#2a2a2a]">
                    <span class="text-xs text-gray-500 truncate max-w-[70%]">
                      {{ cert.credentialId || 'Certificate' }}
                    </span>

                    <a
                      v-if="cert.link"
                      :href="cert.link"
                      target="_blank"
                      rel="noreferrer"
                      class="text-gray-400 hover:text-[#659cf0] transition-colors"
                      title="View Certificate"
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
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CertificateView',
  inject: ['t'],
  data() {
    return {
      activeOrg: 0,
      certificatesData: [
        {
          organization: "Dicoding Indonesia",
          certificates: [
            { id: 1, title: "Basic Data Visualization", date: "Desember 2023", credentialId: "Cred ID: GRX5QLD3YZ0M", image: "/img/dicoding 1.jpeg", link: "https://drive.google.com/file/d/1dHRWBehlr9KR_EWiha-5DMj8_C87cWVu/view?usp=sharing" },
            { id: 2, title: "Basic AWS Cloud", date: "Desember 2024", credentialId: "Cred ID: JMZV4K03NXN9", image: "/img/dicoding 3.jpeg", link: "https://drive.google.com/file/d/1-k_zAmN5zXoWXxvFjOd30iZDhA-v5_GK/view?usp=sharing" },
            { id: 3, title: "Basic IT Project Management", date: "Agustus 2024", credentialId: "Cred ID: 98XWL1660ZM3", image: "/img/dicoding 4.jpeg", link: "https://drive.google.com/file/d/1Exvqe21YlljOKQRzG7kgWoPj0zgnzreN/view?usp=sharing" },
            { id: 4, title: "Basic Structured Query Language (SQL)", date: "Februari 2024", credentialId: "Cred ID: 1RXY1E8M9PVM", image: "/img/dicoding 5.jpeg", link: "https://drive.google.com/file/d/1Uy15YjpvKInhys4OZk1UsBpGy_XceIiW/view?usp=sharing" },
            { id: 5, title: "Basic Data Science", date: "September 2024", credentialId: "Cred ID: JLX14G1K6X72", image: "/img/dicoding 6.jpeg", link: "https://drive.google.com/file/d/1uXfNT525xrF0RZ2IdwlTLAIJDVi_TPf5/view?usp=sharing" },
            { id: 6, title: "Basic Javascript", date: "Januari 2025", credentialId: "Cred ID: RVZKW640NZD5", image: "/img/dicoding 7.jpeg", link: "https://drive.google.com/file/d/1PfkYSVfg9q_VtqglzmbGVHgC_AhpDwxf/view?usp=sharing" }
          ]
        },
        {
          organization: "Coursera",
          certificates: [
            { id: 7, title: "Game Theory", date: "Februari 2025", credentialId: "Cred ID: HUI28S4JBN99", image: "/img/coursera 1.jpeg", link: "https://drive.google.com/file/d/1dHRWBehlr9KR_EWiha-5DMj8_C87cWVu/view?usp=sharing" }
          ]
        },
        {
          organization: "Cisco Academy",
          certificates: [
            { id: 8, title: "Junior Cybersecurity Analyst Career Path", date: "Januari 2025", image: "/img/cisco 1.jpeg", link: "https://drive.google.com/file/d/1Ukr6NF-AfP5Dwbq3zmFjcYRuWQIk-Jvv/view?usp=sharing" },
            { id: 9, title: "Ethical Hacker", date: "Januari 2025", image: "/img/cisco 2.jpeg", link: "https://drive.google.com/file/d/1Ukr6NF-AfP5Dwbq3zmFjcYRuWQIk-Jvv/view?usp=sharing" },
            { id: 10, title: "English for IT", date: "Maret 2025", image: "/img/cisco 3.jpeg", link: "https://drive.google.com/file/d/1Ybq-Eu7wKMEbLSYpGn6Ig4XKulceDIxV/view?usp=sharing" },
            { id: 11, title: "Introduction to Cybersecurity", date: "Februari 2025", image: "/img/cisco 4.jpeg", link: "https://drive.google.com/file/d/1sY1_Tcw5-Ka4U5g_oSi8akdIHGqi7YfT/view?usp=sharing" }
          ]
        },
        {
          organization: "Udemy",
          certificates: [
            { id: 12, title: "AI Engineering Masterclass: From Zero to AI Hero", date: "Juli 2025", image: "/img/udemy 1.jpeg", link: "https://drive.google.com/file/d/12AUFSHlN9xPm4oXa9CCTyxpx7wgtQiYk/view?usp=sharing" },
            { id: 13, title: "AI & Quantum Computing Mastery Bootcamp", date: "Juli 2025", image: "/img/udemy 2.jpeg", link: "https://drive.google.com/file/d/1hrJxirq2BRWSKCxmKB7cUC9VzF8WNlac/view?usp=sharing" }
          ]
        },
        {
          organization: "Semrush Academy",
          certificates: [
            { id: 14, title: "International SEO", date: "Juli 2025", credentialId: "Cred ID: 6b7a3266cb", image: "/img/semrush 1.jpeg", link: "https://drive.google.com/file/d/1sQA1gZ-WYbSyKx_iQ0ATLAMJ6wpEsoEG/view?usp=sharing" },
            { id: 15, title: "Mastering Youtube Search Trends and SEO Strategis", date: "Juli 2025", credentialId: "Cred ID: 8ed676790e", image: "/img/semrush 2.jpeg", link: "https://drive.google.com/file/d/1GRzNn4WEUlhW6KDvpL-l9waKgQXtDkje/view?usp=sharing" }
          ]
        },
        {
          organization: "IBM Skills Build",
          certificates: [
            { id: 16, title: "Classifying Data Using IBM Granite", date: "Agustus 2025", image: "/img/ibm 1.jpeg", link: "https://drive.google.com/file/d/1JvS5kZi3GMlBkvXC-END3MRhn_IPzpdY/view?usp=sharing" },
            { id: 17, title: "Summarizing Data Using IBM Granite", date: "Agustus 2025", image: "/img/ibm 1.jpeg", link: "https://drive.google.com/file/d/1_lL6KnIdLcJ84znUaH4G73At5ZBP-u4y/view?usp=sharing" }
          ]
        }
      ]
    }
  },
  methods: {
    scrollToSection(index) {
      this.activeOrg = index;
      const element = document.getElementById('org-' + index);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
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

.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>