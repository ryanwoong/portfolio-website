<script setup>
  import Experiences from '@/components/Experiences.vue';
  import { ref, onMounted, onUnmounted } from 'vue';
  import jsonData from '@/data.json';
  import Navbar from '@/components/Navbar.vue';
  import Projects from '@/components/Projects.vue';
  import Skills from '@/components/Skills.vue';

  // Define sections with correct capitalization and ID mapping
  const sections = ['ABOUT', 'EXPERIENCE', 'PROJECTS & HACKATHONS', 'BLOG', 'RESUME'];
  // Map section titles to their IDs for accurate navigation
  const sectionIds = {
    'ABOUT': 'about',
    'EXPERIENCE': 'experience',
    'PROJECTS & HACKATHONS': 'projects-hackathons',
    'RESUME': 'resume'
  };
  
  const languages = [
    'C#',
    'C++', 
    'Dart', 
    'HTML / CSS', 
    'Java', 
    'JavaScript', 
    'Kotlin', 
    'Python', 
    'SQL', 
    'TypeScript'
  ];

  const technologiesFrameworks = [
    '.NET',
    'Android Studio', 
    'AWS', 
    'Docker', 
    'Express.js', 
    'Firebase', 
    'Flutter', 
    'Git/GitHub', 
    'Linux', 
    'MongoDB', 
    'MySQL', 
    'Node.js', 
    'Postgres', 
    'React', 
    'Vue'
  ];

  const activeSection = ref('about');
  const mainContent = ref(null);
  const { projects, experiences } = jsonData;

  const updateActiveSection = () => {
    if (!mainContent.value) return;
    
    const scrollPosition = mainContent.value.scrollTop;
    const windowHeight = window.innerHeight;
    const offset = windowHeight * 0.3; // Adjust this value to change when the highlight triggers

    // Create an array to hold section elements and their positions
    const sectionPositions = sections.map(section => {
      const id = sectionIds[section];
      const element = document.getElementById(id);
      if (!element) return { id, top: Infinity, bottom: Infinity };
      
      return {
        id,
        top: element.offsetTop,
        bottom: element.offsetTop + element.offsetHeight
      };
    }).filter(section => section.top !== Infinity);

    // Sort sections by position to ensure we select the correct active section
    sectionPositions.sort((a, b) => a.top - b.top);
    
    // Find the active section
    for (const section of sectionPositions) {
      if (scrollPosition >= section.top - offset && scrollPosition < section.bottom - offset) {
        activeSection.value = section.id;
        break;
      }
    }
  };

  onMounted(() => {
    if (mainContent.value) {
      mainContent.value.addEventListener('scroll', updateActiveSection);
      // Initial call to set the active section on page load
      setTimeout(updateActiveSection, 100); // Small delay to ensure DOM is fully rendered
    }
  });

  onUnmounted(() => {
    if (mainContent.value) {
      mainContent.value.removeEventListener('scroll', updateActiveSection);
    }
  });
</script>

<template>
  <div class="md:flex md:h-screen text-gray-300" :style="{ backgroundColor: '#f4f4f6' }">

    <Navbar :active-section="activeSection" :sections="sections"/>

    <main class="flex-1 overflow-y-auto py-6 px-4 md:py-12 md:px-24 md:mt-20" ref="mainContent">
      <section id="about" class="p-6 mb-2 md:mb-4 rounded-lg group backdrop-blur-md shadow-lg max-w-3xl" :style="{backgroundColor: '#e6e6e9'}">
        <p class="mb-4 text-gray-800">
          Hey! My name is <span class="text-sage font-bold">Ryan</span>, a <span class="text-sage font-bold">student</span> and <span class="text-sage font-bold">passionate developer</span> with the desire to expand my knowledge and learn new things. 
        </p>
        <p class="mb-4 text-gray-800">
          I'm currently a third year student attending the <span class="text-sage font-bold">University of Calgary</span> pursing a major in <span class="text-sage font-bold">Computer Science</span> and minoring in <span class="text-sage font-bold">Management and Society</span>.
        </p>
        <p class="mb-4 text-gray-800">
          As a child the world of technology always fascinated me, fast-forward to the present, and I now continue to strive to explore and learn everything I can. I have been fortunate enough to be able to own some amazing pieces of technology throughout my life which has allowed me to explore many different opportunites. From <span class="text-sage font-bold">Raspberry Pi's</span>, <span class="text-sage font-bold">VR Technology</span>, <span class="text-sage font-bold">AI & Machine Learning</span>, I have dove into the endless possibilities of technology, constantly expanding my technology stack.
        </p>
      </section>

      <section id="experience" class="mb-6 mt-6 md:mb-12">
        <Experiences :experiences="experiences" />
      </section>

      <section id="projects-hackathons" class="mb-6 md:mb-12">
        <Projects :projects="projects" />
      </section>

      <section id="skills" class="mb-6 md:mb-12">
        <Skills :languages="languages" :technologiesFrameworks="technologiesFrameworks" />
      </section>

    </main>
  </div>
</template>

