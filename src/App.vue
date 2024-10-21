<template>
  <div class="min-h-screen bg-black text-white">
    <header class="fixed top-0 left-0 right-0 z-50 bg-black bg-opacity-50 backdrop-blur-md">
      <nav class="container mx-auto px-6 py-4">
        <div class="flex justify-between items-center">
          <div>
            <img
              class="w-10 h-10 md:w-12 md:h-12 rounded-full border-2 border-primary"
              src="./assets/Hadeed-Ul-Haq.png"
              alt="Hadeed Ul Haq"
            />
          </div>
          <div class="hidden md:flex items-center space-x-8">
            <a
              v-for="item in menuItems"
              :key="item"
              :href="`#${item.toLowerCase()}`"
              :class="[
                'text-sm uppercase tracking-wider hover:text-primary transition-colors',
                { 'text-primary': activeSection === item.toLowerCase() }
              ]"
              @click.prevent="scrollToSection(item.toLowerCase())"
            >
              {{ item }}
            </a>
          </div>
          <div class="md:hidden">
            <button
              class="text-white hover:text-primary focus:outline-none"
              @click="isMenuOpen = !isMenuOpen"
              aria-label="Toggle menu"
            >
              <MenuIcon v-if="!isMenuOpen" class="h-6 w-6" />
              <XIcon v-else class="h-6 w-6" />
            </button>
          </div>
        </div>
      </nav>
    </header>

    <Transition name="fade">
      <div v-if="isMenuOpen" class="fixed inset-0 z-40 bg-black bg-opacity-95 flex items-center justify-center">
        <div class="text-center">
          <a
            v-for="item in menuItems"
            :key="item"
            :href="`#${item.toLowerCase()}`"
            class="block py-4 text-2xl uppercase tracking-wider hover:text-primary transition-colors"
            @click.prevent="scrollToSection(item.toLowerCase())"
          >
            {{ item }}
          </a>
        </div>
      </div>
    </Transition>

    <main>
      <section id="home" class="min-h-screen flex items-center relative overflow-hidden">
        <img 
          src="./assets/1.png" 
          alt="Background" 
          class="absolute inset-0 w-full h-full object-cover opacity-30"
          sizes="100vw"
        />
        <div class="container mx-auto px-6 relative z-10">
          <div class="max-w-3xl">
            <h1 class="text-4xl sm:text-5xl md:text-7xl font-bold mb-4">
              Hi, I'm <span class="text-primary">Hadeed Ul Haq</span>
            </h1>
            <h2 class="text-xl sm:text-2xl md:text-3xl font-semibold text-gray-400 mb-6">
              Software Engineer | Automation Testing Specialist
            </h2>
            <p class="text-gray-400 mb-8 text-base sm:text-lg">
              I am a dedicated and passionate software engineer with specialised expertise in automation testing. Proficient in Cypress, I focus on ensuring software applications perform seamlessly with robust and efficient test automation solutions.
            </p>
            <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
              <button
                class="bg-primary hover:bg-primary-dark text-white font-bold py-2 px-4 rounded w-full sm:w-auto"
                @click="scrollToSection('work')"
              >
                View My Work
              </button>
              <button
                class="border border-primary text-primary hover:bg-primary hover:text-white font-bold py-2 px-4 rounded transition-colors w-full sm:w-auto"
                @click="scrollToSection('about')"
              >
                About Me
              </button>
            </div>
          </div>
        </div>
      </section>

      <section id="work" class="min-h-screen flex items-center bg-zinc-900">
        <div class="container mx-auto px-6 py-20">
          <h2 class="text-3xl sm:text-4xl font-bold mb-10">Experience</h2>
          <div class="grid md:grid-cols-2 gap-8">
            <div
              v-for="(job, index) in jobs"
              :key="job.title"
              class="bg-zinc-800 rounded-lg p-6 hover:bg-zinc-700 transition-colors relative overflow-hidden"
            >
              <img src="./assets/2.png"
                class="absolute inset-0 w-full h-full object-cover opacity-10"
                sizes="(min-width: 768px) 50vw, 100vw"
              />
              <div class="relative z-10">
                <h3 class="text-lg sm:text-xl font-semibold mb-2">{{ job.title }}</h3>
                <p class="text-gray-400 mb-4">{{ job.company }} | {{ job.location }}</p>
                <ul class="list-disc list-inside text-gray-400">
                  <li v-for="(responsibility, index) in job.responsibilities" :key="index" class="mb-2 text-sm sm:text-base">
                    {{ responsibility }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="projects" class="min-h-screen flex items-center bg-zinc-800">
        <div class="container mx-auto px-6 py-20">
          <h2 class="text-3xl sm:text-4xl font-bold mb-10">Projects</h2>
          <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="project in projects" :key="project.title" class="bg-zinc-700 rounded-lg overflow-hidden shadow-lg">
              <img :src="project.image" :alt="project.title" class="w-full h-48 object-cover" />
              <div class="p-6">
                <h3 class="text-xl font-semibold mb-2">{{ project.title }}</h3>
                <p class="text-gray-400 mb-4">{{ project.description }}</p>
                <div class="mb-4">
                  <h4 class="text-sm font-semibold mb-2">Key Technologies:</h4>
                  <div class="flex flex-wrap gap-2">
                    <span v-for="tech in project.technologies" :key="tech" class="bg-zinc-600 text-xs text-white px-2 py-1 rounded">
                      {{ tech }}
                    </span>
                  </div>
                </div>
                <a :href="project.link" target="_blank" rel="noopener noreferrer" class="inline-block bg-primary hover:bg-primary-dark text-white font-bold py-2 px-4 rounded transition-colors">
                  Visit Project
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="skills" class="min-h-screen flex items-center relative overflow-hidden">
        <img 
          src="./assets/3.png" 
          alt="Skills background" 
          class="absolute inset-0 w-full h-full object-cover opacity-10"
          sizes="100vw"
        />
        <div class="container mx-auto px-6 py-20 relative z-10">
          <h2 class="text-3xl sm:text-4xl font-bold mb-10">Core Competencies</h2>
          <div class="grid md:grid-cols-2 gap-8">
            <div v-for="(skillGroup, index) in coreCompetencies" :key="index" class="bg-zinc-800 rounded-lg p-6 hover:bg-zinc-700 transition-colors">
              <h3 class="text-lg sm:text-xl font-semibold mb-2">{{ skillGroup.category }}</h3>
              <p class="text-gray-400 text-sm sm:text-base">{{ skillGroup.skills.join(', ') }}</p>
            </div>
          </div>
        </div>
      </section>

      <section id="about" class="min-h-screen flex items-center bg-zinc-900">
        <div class="container mx-auto px-6 py-20">
          <div class="flex flex-col md:flex-row items-center">
            <div class="md:w-1/2 mb-10 md:mb-0">
              <img 
                src="./assets/4.png" 
                alt="About Hadeed Ul Haq" 
                class="rounded-lg shadow-xl w-full h-auto"
                sizes="(min-width: 768px) 50vw, 100vw"
              />
            </div>
            <div class="md:w-1/2 md:pl-10">
              <h2 class="text-3xl sm:text-4xl font-bold mb-6">About Me</h2>
              <p class="text-gray-400 mb-4 text-sm sm:text-base">
                I'm a passionate software engineer based in Northwood, London. With a deep knowledge of automation testing, I ensure software applications run smoothly and flawlessly. My expertise spans both end-to-end and component testing, driven by a commitment to software quality.
              </p>
              <p class="text-gray-400 mb-4 text-sm sm:text-base">
                I hold a Bachelor's degree in Software Engineering from Iqra National University, completed in 2020.
              </p>
              <p class="text-gray-400 text-sm sm:text-base">
                When I'm not coding, I enjoy table tennis, competitive gaming, calisthenics, and experimenting with PC hardware.
              </p>
            </div>
          </div>
        </div>
      </section>

    </main>

    <footer class="bg-zinc-900 py-10">
      <div class="container mx-auto px-6">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-6 md:mb-0">
            <h3 class="text-xl sm:text-2xl font-bold mb-2">Let's work together</h3>
            <div class="flex space-x-4">
              <a href="mailto:hadeedulhaq@gmail.com" class="text-primary hover:text-primary-light transition-colors">
                <MailIcon class="h-6 w-6" />
                <span class="sr-only">Email</span>
              </a>
              <a href="tel:+447774067432" class="text-primary hover:text-primary-light transition-colors">
                <PhoneIcon class="h-6 w-6" />
                <span class="sr-only">Phone</span>
              </a>
              <a href="https://www.linkedin.com/in/hadeed-ul-haq" target="_blank" rel="noopener noreferrer" class="text-primary hover:text-primary-light transition-colors">
                <LinkedinIcon class="h-6 w-6" />
                <span class="sr-only">LinkedIn</span>
              </a>
              <a href="https://github.com/HadeedUlHaq" target="_blank" rel="noopener noreferrer" class="text-primary hover:text-primary-light transition-colors">
                <GithubIcon class="h-6 w-6" />
                <span class="sr-only">GitHub</span>
              </a>
            </div>
          </div>
          <p class="text-gray-400 text-sm sm:text-base">&copy; 2024 Hadeed Ul Haq. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { MenuIcon, XIcon, MailIcon, PhoneIcon, LinkedinIcon, GithubIcon } from 'lucide-vue-next'

const activeSection = ref('home')
const isMenuOpen = ref(false)

const menuItems = ['Home', 'Work', 'Projects', 'Skills', 'About']

const jobs = [
  {
    title: 'Automation Testing Engineer',
    company: 'Zsah Ltd Managed Technology Services',
    location: 'London, UK',
    responsibilities: [
      'Integrated comprehensive automation testing using Cypress for the SDM Registry',
      'Conducted API testing using HTTP methods such as GET, POST, PUT, and DELETE',
      'Integrated Cypress testing into the CI/CD pipeline',
      'Implemented performance evaluation through JMeter',
    ],
    
  },
  {
    title: 'Tech Lead',
    company: 'Business Upscalers',
    location: 'Richmond, TX (Remote)',
    responsibilities: [
      'Developed custom WordPress themes from scratch',
      'Collaborated with SEO and design teams, optimising workflow',
      'Optimised website performance using CDN, lazy loading, and Cloudflare',
    ],
  },
  {
    title: 'SQA Engineer',
    company: 'Bitknox Technologies',
    location: 'Lahore, Pakistan',
    responsibilities: [
      'Performed manual testing in Salesforce Commerce Cloud',
      'Conducted usability testing for enhancing  user interface',
      'Performed load and stress testing',
    ],
  },
  {
    title: 'Front-end Web Developer (Intern)',
    company: 'Systems Limited',
    location: 'Lahore, Pakistan',
    responsibilities: [
      'Developed, tested, and maintained web applications',
      'Used technologies including Flutter, OutSystems, .NET, and Salesforce CRM',
    ],
  }
]

const projects = [
  {
    title: 'My Family Shopping List',
    description: 'A responsive and feature-rich shopping list web application built from scratch using React.js and Firebase. This app allows users to easily create and manage shopping lists, with personalized item suggestions and real-time updates.',
    image: 'https://constguide.app/wp-content/uploads/2024/10/project1.png',
    link: 'https://my-family-shopping-list.pages.dev/app',
    technologies: ['React.js', 'Firebase', 'HTML', 'CSS', 'Cloudflare']
  },
  {
    title: 'Business Upscalers',
    description: 'A professional website developed for Business Upscalers, showcasing services for business growth and development. I designed and implemented a custom WordPress theme from the ground up, focusing on user experience and responsive design.',
    image: 'https://constguide.app/wp-content/uploads/2024/10/project2.png',
    link: 'https://businessupscalers.com/',
    technologies: ['WordPress', 'HTML', 'CSS', 'jQuery', 'SEO Optimisation']
  },
  {
    title: 'Affordable Junk Removal Akron',
    description: 'Developed a clean and efficient website for Affordable Junk Removal Akron, focusing on fast load times and an intuitive user interface. I integrated CDN for optimised delivery, implemented lazy loading for images, and ensured robust security protocols.',
    image: 'https://constguide.app/wp-content/uploads/2024/10/project3.png',
    link: 'https://www.affordablejunkremovalakron.com/',
    technologies: ['WordPress', 'Cloudflare', 'SSL', 'HTML', 'CSS', 'jQuery']
  }
]

const coreCompetencies = [
  {
    category: 'Automation Testing',
    skills: ['Cypress', 'Selenium', 'JMeter']
  },
  {
    category: 'Web Development',
    skills: ['HTML', 'CSS', 'JavaScript', 'React.js', 'jQuery']
  },
  {
    category: 'Cloud & Hosting',
    skills: ['Cloudflare', 'Firebase', 'CI/CD Pipelines']
  },
  {
    category: 'Performance Testing',
    skills: ['API Testing', 'Load & Stress Testing']
  },
  {
    category: 'Agile Methodologies',
    skills: ['Scrum', 'Jira']
  },
  {
    category: 'Security',
    skills: ['Cybersecurity protocols', 'SSL', 'DDoS Protection']
  },
  {
    category: 'Version Control',
    skills: ['Git', 'GitHub', 'GitLab']
  }
]

const scrollToSection = (sectionId) => {
  const section = document.getElementById(sectionId)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
  isMenuOpen.value = false
}

const handleScroll = () => {
  const sections = document.querySelectorAll('section')
  let current = ''

  sections.forEach((section) => {
    const sectionTop = section.offsetTop
    const sectionHeight = section.clientHeight
    if (window.pageYOffset >= sectionTop - sectionHeight / 3) {
      current = section.getAttribute('id') || ''
    }
  })

  activeSection.value = current
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>