<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col gap-12 md:px-20 fade-zoom-up">
      
      <div>
        <header>
          <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
            Find me on social media &nbsp;
            <div class="h-[1px] w-32 bg-blue-400 md:w-96 aos-init aos-animate" data-aos="zoom-in-left" data-aos-duration="600"></div>
          </div>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6">
          <a v-for="contact in contacts" :key="contact.id" :href="contact.link" target="_blank" rel="noreferrer"
             :class="['relative overflow-hidden rounded-2xl p-6 flex flex-col justify-between transition-all duration-300 hover:scale-[1.02] hover:shadow-lg group', contact.bgClass, contact.spanClass]">
            
            <div class="absolute -right-6 -bottom-6 w-32 h-32 bg-white opacity-5 rounded-full blur-2xl group-hover:opacity-10 transition-opacity"></div>
            <div class="absolute right-12 top-12 w-24 h-24 bg-white opacity-5 rounded-full blur-xl group-hover:opacity-10 transition-opacity"></div>

            <div class="relative z-10 flex justify-between items-start">
              <div class="flex flex-col text-left max-w-[70%]">
                <h2 class="text-xl md:text-2xl font-bold text-white mb-1">{{ contact.title }}</h2>
                <p class="text-white/80 text-sm md:text-base mb-6">{{ contact.desc }}</p>
                
                <div :class="['w-fit flex items-center gap-2 px-4 py-2 rounded-lg text-sm font-semibold transition-colors', contact.btnClass]">
                  {{ contact.buttonText }}
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <line x1="7" y1="17" x2="17" y2="7"></line>
                    <polyline points="7 7 17 7 17 17"></polyline>
                  </svg>
                </div>
              </div>

              <div class="relative z-10 flex shrink-0 items-center justify-center w-14 h-14 md:w-16 md:h-16 rounded-2xl bg-white/10 border border-white/20 backdrop-blur-sm">
                <svg class="w-8 h-8 md:w-10 md:h-10 text-white" fill="currentColor" viewBox="0 0 24 24" v-html="contact.svgPath"></svg>
              </div>
            </div>
          </a>
        </div>
      </div>

      <div class="text-left fadein-bot">
        <h3 class="text-lg md:text-xl font-bold text-white mb-4">Or send me a message</h3>
        
        <form @submit.prevent="sendMessage" class="flex flex-col gap-4">
          <div class="flex flex-col md:flex-row gap-4">
            <input 
              type="text" 
              v-model="form.name" 
              placeholder="Name" 
              required
              class="w-full bg-transparent border border-[#383838] rounded-xl p-4 text-white placeholder-gray-500 focus:outline-none focus:border-blue-500 focus:bg-[#1e1e1f] transition-all duration-300">
            
            <input 
              type="email" 
              v-model="form.email" 
              placeholder="Email" 
              required
              class="w-full bg-transparent border border-[#383838] rounded-xl p-4 text-white placeholder-gray-500 focus:outline-none focus:border-blue-500 focus:bg-[#1e1e1f] transition-all duration-300">
          </div>
          
          <textarea 
            v-model="form.message" 
            placeholder="Message" 
            rows="5" 
            required
            class="w-full bg-transparent border border-[#383838] rounded-xl p-4 text-white placeholder-gray-500 focus:outline-none focus:border-blue-500 focus:bg-[#1e1e1f] transition-all duration-300 resize-y"></textarea>
          
          <button 
            type="submit"
            class="w-full bg-[#1e1e1f] hover:bg-[#282828] border border-[#383838] text-white font-semibold py-4 rounded-xl transition-all duration-300">
            Send Email
          </button>
        </form>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactView',
  data() {
    return {
      // Data form yang akan diikat (bind) dengan inputan user
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
          link: 'mailto:benedicto.siahaan@gmail.com', // Ganti dengan email asli Anda
          spanClass: 'md:col-span-2',
          bgClass: 'bg-gradient-to-br from-red-600 to-red-900',
          btnClass: 'bg-red-200/90 hover:bg-red-200 text-red-900',
          svgPath: '<path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>'
        },
        {
          id: 2,
          title: 'Follow My Journey',
          desc: 'Follow my creative journey.',
          buttonText: 'Go to Instagram',
          link: 'https://instagram.com/samsiiahaan', // Ganti dengan link Anda
          spanClass: 'md:col-span-1',
          bgClass: 'bg-gradient-to-br from-purple-600 via-pink-600 to-orange-500',
          btnClass: 'bg-pink-100/90 hover:bg-pink-100 text-pink-900',
          svgPath: '<path d="M7.8 2h8.4C19.4 2 22 4.6 22 7.8v8.4a5.8 5.8 0 0 1-5.8 5.8H7.8C4.6 22 2 19.4 2 16.2V7.8A5.8 5.8 0 0 1 7.8 2m-.2 2A3.6 3.6 0 0 0 4 7.6v8.8C4 18.39 5.61 20 7.6 20h8.8a3.6 3.6 0 0 0 3.6-3.6V7.6C20 5.61 18.39 4 16.4 4H7.6m9.65 1.5a1.25 1.25 0 0 1 1.25 1.25A1.25 1.25 0 0 1 17.25 8 1.25 1.25 0 0 1 16 6.75a1.25 1.25 0 0 1 1.25-1.25M12 7a5 5 0 0 1 5 5 5 5 0 0 1-5 5 5 5 0 0 1-5-5 5 5 0 0 1 5-5m0 2a3 3 0 0 0-3 3 3 3 0 0 0 3 3 3 3 0 0 0 3-3 3 3 0 0 0-3-3z"/>'
        },
        {
          id: 3,
          title: "Let's Connect",
          desc: 'Connect with me professionally.',
          buttonText: 'Go to Linkedin',
          link: 'https://www.linkedin.com/in/samuelsiiahaan/', // Ganti dengan link Anda
          spanClass: 'md:col-span-1',
          bgClass: 'bg-gradient-to-br from-cyan-600 to-blue-800',
          btnClass: 'bg-blue-100/90 hover:bg-blue-100 text-blue-900',
          svgPath: '<path d="M19 3a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h14m-.5 15.5v-5.3a3.26 3.26 0 0 0-3.26-3.26c-.85 0-1.84.52-2.32 1.3v-1.11h-2.79v8.37h2.79v-4.93c0-.77.62-1.4 1.39-1.4a1.4 1.4 0 0 1 1.4 1.4v4.93h2.79M6.88 8.56a1.68 1.68 0 0 0 1.68-1.68c0-.93-.75-1.69-1.68-1.69a1.69 1.69 0 0 0-1.69 1.69c0 .93.76 1.68 1.69 1.68m1.39 9.94v-8.37H5.5v8.37h2.77z"/>'
        },
        {
          id: 4,
          title: 'Join the Fun',
          desc: 'Watch engaging and fun content.',
          buttonText: 'Go to Tiktok',
          link: 'https://tiktok.com/@vionanaj', // Ganti dengan link Anda
          spanClass: 'md:col-span-1',
          bgClass: 'bg-gradient-to-br from-gray-700 to-gray-900',
          btnClass: 'bg-gray-200/90 hover:bg-gray-200 text-gray-900',
          svgPath: '<path d="M12.53.02C13.84 0 15.14.01 16.44 0c.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.57-.26-1.1-.59-1.62-.93-.01 2.92.01 5.84-.02 8.75-.08 2.22-1.15 4.35-2.91 5.61-1.74 1.28-4.04 1.64-6.07 1.05-2.48-.71-4.48-2.9-4.88-5.45-.44-2.67.65-5.54 2.82-7.1 1.71-1.24 3.96-1.57 6.01-1.01v4.21c-.51-.12-1.04-.15-1.57-.12-.87.05-1.75.5-2.26 1.19-.62.82-.7 2.05-.17 2.94.52.88 1.62 1.34 2.62 1.25.99-.07 1.91-.71 2.3-1.63.15-.36.22-.75.22-1.15V.02z"/>'
        },
        {
          id: 5,
          title: 'Explore the Code',
          desc: 'Explore my open-source work.',
          buttonText: 'Go to Github',
          link: 'https://github.com/SamMorales11', 
          spanClass: 'md:col-span-1',
          bgClass: 'bg-gradient-to-br from-slate-800 to-black',
          btnClass: 'bg-slate-200/90 hover:bg-slate-200 text-slate-900',
          svgPath: '<path d="M12 2A10 10 0 0 0 8.84 21.5c.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.45-1.15-1.11-1.46-1.11-1.46-.9-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.87 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0 0 12 2z"/>'
        },
      ]
    }
  },
  methods: {
    // Fungsi ini dipanggil ketika user menekan tombol Send Email
    sendMessage() {
      // Sebagai contoh sederhana, kita arahkan ke mailto default komputer user
      // Nanti Anda bisa mengubahnya dengan API (seperti EmailJS atau backend Anda sendiri)
      const mailtoLink = `mailto:samuelbenedicto@gmail.com?subject=New Message from ${this.form.name}&body=${encodeURIComponent(this.form.message)}%0A%0AFrom: ${this.form.email}`;
      window.location.href = mailtoLink;
      
      // Kosongkan form setelah diklik
      this.form.name = '';
      this.form.email = '';
      this.form.message = '';
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
  animation-delay: 200ms;
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

/* Mengatur transisi halus saat form difokuskan */
input:focus, textarea:focus {
  box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.2);
}
</style>