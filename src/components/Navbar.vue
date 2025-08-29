<script setup>
  import { defineProps, ref, onMounted } from 'vue';

  const props = defineProps({
      activeSection: String,
      sections: Array
  });

  // Add section ID mapping to match the one in HomeView
  const sectionIds = {
    'ABOUT': 'about',
    'EXPERIENCE': 'experience',
    'PROJECTS & HACKATHONS': 'projects-hackathons',
    'RESUME': 'resume'
  };

  const fullText = 'Ryan Wong';
  const typingText = ref('');
  let isTyping = true;
  let typingIndex = 0;

  // Function to handle typing and deleting animation
  const typeEffect = () => {
      const typingSpeed = 150; // Typing speed (milliseconds)
      const deletingSpeed = 100; // Deleting speed (milliseconds)
      const delayBetweenCycles = 1500; // Pause before typing starts again

      if (isTyping) {
          if (typingIndex < fullText.length) {
              typingText.value += fullText[typingIndex];
              typingIndex++;
              setTimeout(typeEffect, typingSpeed);
          } else {
              isTyping = false;
              setTimeout(typeEffect, delayBetweenCycles); // Pause before deleting
          }
      } else {
          if (typingIndex > 0) {
              typingText.value = typingText.value.slice(0, --typingIndex);
              setTimeout(typeEffect, deletingSpeed);
          } else {
              isTyping = true;
              setTimeout(typeEffect, delayBetweenCycles); // Pause before typing restarts
          }
      }
  };

  // Initialize the typing effect when the component mounts
  onMounted(() => {
      typeEffect();
  });

  // Function to scroll to the specified section
  const scrollToSection = (section) => {
      const sectionId = sectionIds[section] || section.toLowerCase();
      const element = document.getElementById(sectionId);
      if (element) {
          element.scrollIntoView({ behavior: 'smooth' });
      }
  };

  // New ref for mobile menu state
  const isMobileMenuOpen = ref(false);

  // Function to toggle mobile menu
  const toggleMobileMenu = () => {
    isMobileMenuOpen.value = !isMobileMenuOpen.value;
  };
</script>

<template>
  <nav class="w-100 p-12 md:flex md:flex-col md:mt-20 md:ml-[15%]">
    <div class="sticky top-12">
      <!-- Typing animation for Ryan Wong -->
      <h1 class="flex text-4xl font-bold mb-2 text-gray-700">
        <span class="text-sage-100 mr-1">></span> 
        {{ typingText }} <!-- Show full text on small screens -->
      </h1>
      <p class="text-lg mb-4 text-gray-600">Fullstack Developer & Student</p>
      <div class="flex items-center gap-2 mb-14">
        <p class="text-sm text-gray-600">I love bananas.</p>
        <!-- <img src="../assets/banana.png" class="inline-block h-10 w-auto"> -->
      </div>

      <div class="relative">
        <!-- Mobile menu container -->
        <div class="md:hidden flex justify-between items-center mb-4">
          <!-- Mobile menu toggle button -->
          <button
            @click="toggleMobileMenu"
            class="text-sage hover:text-sage-100 transition-colors"
          >
            <i :class="['pi', isMobileMenuOpen ? 'pi-times' : 'pi-bars', 'text-2xl']"></i>
          </button>
          
          <!-- Social links (visible on mobile) -->
          <div class="flex space-x-4">
            <a href="https://github.com/ryanwoong" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
              <span class="sr-only">GitHub</span>
              <i class="pi pi-github text-3xl"></i>
            </a>
            <a href="https://www.linkedin.com/in/ryanwongyyc/" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
              <span class="sr-only">LinkedIn</span>
              <i class="pi pi-linkedin text-3xl"></i>
            </a>
            <a href="https://twitter.com/yourusername" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
              <span class="sr-only">Twitter</span>
              <i class="pi pi-twitter text-3xl"></i>
            </a>
            <a href="https://youtube.com/@yourchannel" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
              <span class="sr-only">YouTube</span>
              <i class="pi pi-youtube text-3xl"></i>
            </a>
          </div>
        </div>

        <!-- Navigation links -->
        <ul :class="['space-y-2 mb-6 md:mb-12', {'hidden': !isMobileMenuOpen, 'md:block': true}]">
          <li v-for="section in sections" :key="section">
            <template v-if="section.toLowerCase() === 'resume'">
              <RouterLink
                to="/resume"
                target="_blank"
                class="text-sage hover:text-sage-100 transition-colors text-sm tracking-widest font-bold"
              >
                {{ section }}
                <span class="pi pi-external-link text-xs ml-1"></span>
              </RouterLink>
            </template>
            <template v-else-if="section.toLowerCase() === 'blog'">
              <a
                href="https://blog.ryanwong.ca"
                target="_blank"
                class="text-sage hover:text-sage-100 transition-colors text-sm tracking-widest font-bold"
              >
                {{ section }}
              </a>
            </template>
            <template v-else>
              <a
                @click="scrollToSection(section); toggleMobileMenu()"
                :class="{ 
                  'text-sage': activeSection !== sectionIds[section], 
                  'text-gray-800': activeSection === sectionIds[section] 
                }"
                class="hover:text-sage-100 transition-colors text-sm tracking-widest font-bold cursor-pointer"
              >
                {{ section }}
              </a>
            </template>
          </li>
        </ul>

        <!-- Social links (hidden on mobile, visible on larger screens) -->
        <div class="hidden md:flex space-x-4">
          <a href="https://github.com/ryanwoong" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
            <span class="sr-only">GitHub</span>
            <i class="pi pi-github text-3xl"></i>
          </a>
          <a href="https://twitter.com/ryxnwxng" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
            <span class="sr-only">Twitter</span>
            <i class="pi pi-twitter text-3xl"></i>
          </a>
          <a href="https://www.linkedin.com/in/ryanwongyyc/" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
            <span class="sr-only">LinkedIn</span>
            <i class="pi pi-linkedin text-3xl"></i>
          </a>
          <a href="https://youtube.com/@ryanwoong" target="_blank" class="text-gray-600 hover:text-sage-100 transition-all duration-300">
            <span class="sr-only">YouTube</span>
            <i class="pi pi-youtube text-3xl"></i>
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>
