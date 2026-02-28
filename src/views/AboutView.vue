<script>
export default {
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
          name: 'WordPress',
          imageUrl: 'https://img.icons8.com/?size=100&id=13664&format=png&color=000000',
          status: 'Beginner'
        },
        {
          id: 14,
          name: 'Vite',
          imageUrl: 'https://img.icons8.com/?size=100&id=dJjTWMogzFzg&format=png&color=000000',
          status: 'Intermediate'
        },
        {
          id: 14,
          name: 'Dart',
          imageUrl: 'https://img.icons8.com/?size=100&id=7AFcZ2zirX6Y&format=png&color=000000',
          status: 'Beginner'
        },
      ],
      tools: [
        {
          id: 1,
          name: 'Git',
          imageUrl: 'https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png',
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
          name: 'Android Studio',
          imageUrl: 'https://img.icons8.com/?size=100&id=1LAX3PYMg2iA&format=png&color=000000',
          status: 'Mobile IDE'
        },
      ]
    };
  }
}
</script>
<template>
  <div
    class="bg-[#1e1e1f] px-5 py-5 md:px-12 md:py-10 text-left border border-[#383838] rounded-3xl text-amber-50 mx-3 mb-5">
    <article data-page="about">

      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          About Me &nbsp;
          <div class="h-[1px] w-32 bg-blue-400 md:w-96 aos-init aos-animate" data-aos="zoom-in-left"
            data-aos-duration="600"></div>
        </div>
      </header>

      <section
        class="text-sm md:text-lg text-justify flex flex-col gap-4 md:flex-row md:gap-8 md:justify-left md:items-center">
        <div class="flex justify-center">
          <img class="w-9/12 rounded-full mb-3 fadein-up"
            src="img\Screenshot 2026-02-20 103528.jpg" alt="Foto">
        </div>
        <div class="md:w-7/12">
          <p class="mb-3 md:mb-5 fadein-left fadeins-1">
            &nbsp; &nbsp; &nbsp; Hi everyone! My name is Samuel Benedicto Siahaan. a Balikpapan-based Software Engineer dedicated to building impactful digital solutions. 
            I have 3 year of experience web development and data science. I really enjoy what I do right now, in my opinion, 
            creating programs is not just a job, but also an art that has aesthetic value.
          </p>
          <p class="mb-3 fadein-left fadeins-2">
            &nbsp; &nbsp; &nbsp; My primary focus is crafting software architecture that doesn't just work but is well-structured, maintainable, and scalable to meet business needs. I believe that high-quality code must go hand-in-hand with system efficiency and logical clarity.
I blend technical expertise with proactive communication, critical thinking, and effective time management. I thrive in collaborative environments and leverage leadership skills to ensure every project delivers optimal results and a real-world impact.
          </p>

          <div class="mt-8 fadein-left fadeins-2 text-left">
            <p class="text-gray-300 text-sm md:text-base">Best regards,</p>
            <h2 class="text-blue-400 text-4xl md:text-5xl mt-2 font-signature">samuel</h2>
          </div>

        </div>

      </section>

    </article>
  </div>

  <div class="px-5 py-5 md:px-12 md:py-10 text-left text-amber-50 mx-3">
    <article data-page="about">
      <header>
        <div class="text-2xl font-bold text-white mb-5 fadein-bot title-section flex items-center">
          <div class="h-[1px] w-10 bg-blue-400 md:w-20 aos-init aos-animate" data-aos="zoom-in-left"
            data-aos-duration="600"></div>
          &nbsp; Technical Arsenal
        </div>
      </header>
      <section>
        <div>
          <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400 mb-5">
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-blue-300 bg-blue-300 bg-opacity-10': activeTab === 1 }" @click="activeTab = 1">Tech Stack</button>
            </li>
            <li class="mr-2">
              <button class="inline-block px-4 py-3 rounded-lg hover:text-white"
                :class="{ 'text-blue-300 bg-blue-300 bg-opacity-10': activeTab === 2 }" @click="activeTab = 2">Tools</button>
            </li>
          </ul>
        </div>
        <div v-show="activeTab === 1">
          <div class="grid grid-cols-2 gap-4 pb-32 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tech" :key="item.id">
              <div
                class="item-tech flex cursor-pointer items-center gap-2 rounded border border-blue-200 px-2 py-2 hover:bg-amber-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img alt="HTML" loading="lazy" width="32" height="32" decoding="async" data-nimg="1"
                    class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]  "
                    :src="item.imageUrl" style="color: transparent;">
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0 ">{{ item.name }}
                  </div>
                  <div
                    class="status-tech opacity-0 absolute mt-5 text-[10px] text-white transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div v-show="activeTab === 2">
          <div class="grid grid-cols-2 gap-4 pb-32 md:grid-cols-3 md:gap-8 xl:grid-cols-4 xl:gap-10 2xl:gap-12">
            <div v-for="item in tools" :key="item.id">
              <div
                class="item-tech flex cursor-pointer items-center gap-2 rounded border border-blue-200 px-2 py-2 hover:bg-amber-200 hover:bg-opacity-10 md:gap-3 lg:px-3">
                <div class="flex h-12 w-12 items-center justify-center p-0 lg:h-16 lg:w-16 lg:p-2 zoom-in">
                  <img alt="HTML" loading="lazy" width="32" height="32" decoding="async" data-nimg="1"
                    class="img-tech drop-shadow-xl transition-all duration-300 h-[65%] w-[65%] lg:h-[85%] lg:w-[85%]  "
                    :src="item.imageUrl" style="color: transparent;">
                </div>
                <div class="flex items-center text-sm md:text-base lg:text-lg">
                  <div class="tech font-medium text-secondary transition-all duration-300 translate-y-0 ">{{ item.name }}
                  </div>
                  <div
                    class="status-tech opacity-0 absolute mt-5 text-[10px] text-white transition-all duration-300 md:text-xs lg:text-sm">
                    {{ item.status }}</div>
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
/* Import Font Pacifico untuk gaya tanda tangan */
@import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

.font-signature {
  font-family: 'Pacifico', cursive;
}

.fadein-left {
  opacity: 0;
  animation: fadeInLeft 0.5s ease-out forwards;
}

@keyframes fadeInLeft {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }

  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadeins-1 {
  animation-delay: 500ms;
}

.fadeins-2 {
  animation-delay: 800ms;
}

.img-tech,
.tech {
  transition: transform 0.3s ease;
}

.item-tech:hover .img-tech {
  transform: scale(1.3);
}

.item-tech:hover .tech {
  transform: translateY(-12px);
}

.item-tech:hover .status-tech {
  opacity: 1;
}
</style>