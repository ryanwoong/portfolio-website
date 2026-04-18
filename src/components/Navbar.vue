<script setup>
import { defineProps, ref, onMounted } from "vue";

const props = defineProps({
  activeSection: String,
  sections: Array,
});

// Add section ID mapping to match the one in HomeView
const sectionIds = {
  ABOUT: "about",
  EXPERIENCE: "experience",
  "PROJECTS & HACKATHONS": "projects-hackathons",
  RESUME: "resume",
};

const fullText = "Ryan Wong";
const typingText = ref("");
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
    element.scrollIntoView({ behavior: "smooth" });
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
    <div class="sticky top-12 flex flex-col gap-4">
      <!-- Section 1: Profile -->
      <div class="bg-white rounded-lg p-4">
        <img
          src="@/assets/me.jpg"
          alt="Ryan"
          class="hidden md:block w-60 h-60 object-cover rounded-md mb-4 mx-auto"
        />
        <h1 class="flex text-4xl font-bold mb-2 text-black">
          <span class="text-cyan-600 mr-1">></span>
          {{ typingText }}
        </h1>
        <p class="text-lg mb-2 text-black">Fullstack Developer & Student</p>
        <p class="text-sm text-black">I love bananas.</p>
      </div>

      <!-- Section 2: Menu -->
      <div class="bg-white rounded-lg p-4">
        <!-- Mobile toggle -->
        <div class="md:hidden flex items-center mb-4">
          <button
            @click="toggleMobileMenu"
            class="text-cyan-600 hover:text-cyan-600 transition-colors"
          >
            <i :class="['pi', isMobileMenuOpen ? 'pi-times' : 'pi-bars', 'text-2xl']"></i>
          </button>
        </div>

        <ul :class="['space-y-2', { hidden: !isMobileMenuOpen, 'md:block': true }]">
          <li
            v-for="section in sections"
            :key="section"
          >
            <template v-if="section.toLowerCase() === 'resume'">
              <RouterLink
                to="/resume"
                target="_blank"
                class="text-cyan-600 hover:text-cyan-600 transition-colors text-sm tracking-widest font-bold"
              >
                {{ section }}
                <span class="pi pi-external-link text-xs ml-1"></span>
              </RouterLink>
            </template>
            <template v-else-if="section.toLowerCase() === 'blog'">
              <a
                href="https://blog.ryanwong.ca"
                target="_blank"
                class="text-cyan-600 hover:text-cyan-600 transition-colors text-sm tracking-widest font-bold"
              >
                {{ section }}
              </a>
            </template>
            <template v-else>
              <a
                @click="
                  scrollToSection(section);
                  toggleMobileMenu();
                "
                :class="{
                  'text-cyan-600': activeSection !== sectionIds[section],
                  'text-black': activeSection === sectionIds[section],
                }"
                class="hover:text-cyan-600 transition-colors text-sm tracking-widest font-bold cursor-pointer"
              >
                {{ section }}
              </a>
            </template>
          </li>
        </ul>
      </div>

      <!-- Section 3: Socials -->
      <div class="bg-white rounded-lg p-4 flex justify-center space-x-4">
        <a
          href="https://github.com/ryanwoong"
          target="_blank"
          class="text-black hover:text-cyan-600 transition-all duration-300"
        >
          <span class="sr-only">GitHub</span>
          <i class="pi pi-github text-3xl"></i>
        </a>
        <a
          href="https://twitter.com/ryxnwxng"
          target="_blank"
          class="text-black hover:text-cyan-600 transition-all duration-300"
        >
          <span class="sr-only">Twitter</span>
          <i class="pi pi-twitter text-3xl"></i>
        </a>
        <a
          href="https://www.linkedin.com/in/ryanwongyyc/"
          target="_blank"
          class="text-black hover:text-cyan-600 transition-all duration-300"
        >
          <span class="sr-only">LinkedIn</span>
          <i class="pi pi-linkedin text-3xl"></i>
        </a>
        <a
          href="https://youtube.com/@ryanwoong"
          target="_blank"
          class="text-black hover:text-cyan-600 transition-all duration-300"
        >
          <span class="sr-only">YouTube</span>
          <i class="pi pi-youtube text-3xl"></i>
        </a>
      </div>
    </div>
  </nav>
</template>
