<template>
  <div class="container mx-auto px-4 md:px-8 py-8 md:py-12">
    <div class="max-w-5xl mx-auto space-y-12">

      <!-- Header -->
      <header class="fadein-bot">
        <h1 class="text-3xl md:text-4xl font-bold text-white mb-2">
          {{ t().contact.title }}
        </h1>
        <p class="text-sm md:text-base text-gray-400">
          {{ t().contact.subtitle }}
        </p>
      </header>

      <!-- Social Cards -->
      <div>
        <div class="flex items-center gap-3 mb-6">
          <h2 class="text-lg font-semibold text-white">{{ t().contact.social }}</h2>
          <span class="h-[1px] flex-1 bg-gradient-to-r from-[#659cf0]/40 to-transparent rounded-full"></span>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <a
            v-for="contact in contacts"
            :key="contact.id"
            :href="contact.link"
            target="_blank"
            rel="noreferrer"
            class="group relative overflow-hidden rounded-2xl p-5 border border-[#2a2a2a] bg-[#141414] transition-all duration-300 hover:border-[#659cf0]/40 hover:shadow-[0_0_25px_rgba(101,156,240,0.08)] hover:-translate-y-1"
          >
            <div class="flex items-start justify-between gap-4">
              <div class="flex-1">
                <h3 class="text-lg font-bold text-white mb-1">
                  {{ contact.title }}
                </h3>
                <p class="text-sm text-gray-400 mb-4">
                  {{ contact.desc }}
                </p>
                <span class="inline-flex items-center gap-1.5 text-sm font-medium text-[#659cf0] group-hover:text-blue-400 transition-colors">
                  {{ contact.buttonText }}
                  <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <line x1="7" y1="17" x2="17" y2="7"></line>
                    <polyline points="7 7 17 7 17 17"></polyline>
                  </svg>
                </span>
              </div>

              <div class="w-12 h-12 rounded-xl bg-[#1a1a1a] border border-[#2a2a2a] flex items-center justify-center text-[#659cf0] group-hover:border-[#659cf0]/40 transition-colors">
                <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" v-html="contact.svgPath"></svg>
              </div>
            </div>
          </a>
        </div>
      </div>

      <!-- Contact Form -->
      <div>
        <div class="flex items-center gap-3 mb-6">
          <h2 class="text-lg font-semibold text-white">{{ t().contact.formTitle }}</h2>
          <span class="h-[1px] flex-1 bg-gradient-to-r from-[#659cf0]/40 to-transparent rounded-full"></span>
        </div>

        <div class="bg-[#141414] border border-[#2a2a2a] rounded-2xl p-6 md:p-8">
          <form @submit.prevent="sendMessage" class="space-y-5">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
              <div>
                <label class="block text-sm text-gray-400 mb-1.5">{{ t().contact.name }}</label>
                <input
                  v-model="form.name"
                  type="text"
                  required
                  :placeholder="t().contact.namePlaceholder"
                  class="w-full px-4 py-2.5 rounded-lg bg-[#0a0a0a] border border-[#2a2a2a] text-white text-sm placeholder-gray-600 focus:outline-none focus:border-[#659cf0] transition-colors"
                />
              </div>
              <div>
                <label class="block text-sm text-gray-400 mb-1.5">{{ t().contact.email }}</label>
                <input
                  v-model="form.email"
                  type="email"
                  required
                  :placeholder="t().contact.emailPlaceholder"
                  class="w-full px-4 py-2.5 rounded-lg bg-[#0a0a0a] border border-[#2a2a2a] text-white text-sm placeholder-gray-600 focus:outline-none focus:border-[#659cf0] transition-colors"
                />
              </div>
            </div>

            <div>
              <label class="block text-sm text-gray-400 mb-1.5">{{ t().contact.message }}</label>
              <textarea
                v-model="form.message"
                required
                rows="5"
                :placeholder="t().contact.messagePlaceholder"
                class="w-full px-4 py-2.5 rounded-lg bg-[#0a0a0a] border border-[#2a2a2a] text-white text-sm placeholder-gray-600 focus:outline-none focus:border-[#659cf0] transition-colors resize-none"
              ></textarea>
            </div>

            <button
              type="submit"
              class="inline-flex items-center gap-2 px-6 py-2.5 rounded-lg bg-[#659cf0] text-white text-sm font-medium hover:bg-blue-500 transition-all duration-300 hover:shadow-[0_0_20px_rgba(101,156,240,0.35)]"
            >
              {{ t().contact.send }}
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <line x1="22" y1="2" x2="11" y2="13"></line>
                <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
              </svg>
            </button>
          </form>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactView',
  inject: ['t'],
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      contacts: [
        {
          id: 1,
          title: 'Stay in Touch',
          desc: 'Reach out via email for inquiries or collaborations.',
          buttonText: 'Go to Gmail',
          link: 'mailto:benedicto.siahaan@gmail.com',
          svgPath: '<path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>'
        },
        {
          id: 2,
          title: 'Follow My Journey',
          desc: 'Follow my creative journey.',
          buttonText: 'Go to Instagram',
          link: 'https://www.instagram.com/samsiiahaan',
          svgPath: '<path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/>'
        },
        {
          id: 3,
          title: "Let's Connect",
          desc: 'Connect with me professionally.',
          buttonText: 'Go to LinkedIn',
          link: 'https://www.linkedin.com/in/samuelsiiahaan/',
          svgPath: '<path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>'
        },
        {
          id: 4,
          title: 'Join the Fun',
          desc: 'Watch engaging and fun content.',
          buttonText: 'Go to Tiktok',
          link: 'https://www.tiktok.com/benedictooos',
          svgPath: '<path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1v-3.5a6.37 6.37 0 00-.79-.05 6.33 6.33 0 00-6.33 6.33 6.33 6.33 0 006.33 6.33 6.33 6.33 0 006.33-6.33V9.25a8.16 8.16 0 004.77 1.52V7.33a4.85 4.85 0 01-1.4-.64z"/>'
        },
        {
          id: 5,
          title: 'Explore the Code',
          desc: 'Explore my open-source work.',
          buttonText: 'Go to Github',
          link: 'https://github.com/SamMorales11',
          svgPath: '<path d="M12 2A10 10 0 0 0 8.84 21.5c.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.45-1.15-1.11-1.46-1.11-1.46-.9-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2z"/>'
        }
      ]
    }
  },
  methods: {
    sendMessage() {
      const mailtoLink = `mailto:benedicto.siahaan@gmail.com?subject=New Message from ${this.form.name}&body=${encodeURIComponent(this.form.message)}%0A%0AFrom: ${this.form.email}`;
      window.location.href = mailtoLink;
      
      this.form.name = '';
      this.form.email = '';
      this.form.message = '';
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
</style>