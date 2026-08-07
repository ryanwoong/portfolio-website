<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import jsonData from "@/data.json";
import Navbar from "@/components/Navbar.vue";
import NotificationBanner from "@/components/NotificationBanner.vue";
import Projects from "@/components/Projects.vue";
import Experiences from "@/components/Experiences.vue";
import Skills from "@/components/Skills.vue";

const sections = ["ABOUT", "EXPERIENCE", "PROJECTS & HACKATHONS", "BLOG", "RESUME"];
const sectionIds = { ABOUT: "about", EXPERIENCE: "experience", "PROJECTS & HACKATHONS": "projects-hackathons" };
const { projects, experiences, skills } = jsonData;
const activeSection = ref("about");
const darkMode = ref(false);

const updateActiveSection = () => {
  // The document, rather than <main>, is the scrolling container. Use the
  // sections' viewport positions so this also remains correct after layout
  // changes (for example, responsive text wrapping).
  const triggerLine = window.innerHeight * 0.3;
  let currentSection = "about";

  for (const section of sections) {
    const id = sectionIds[section];
    const element = id && document.getElementById(id);
    if (element && element.getBoundingClientRect().top <= triggerLine) currentSection = id;
  }

  activeSection.value = currentSection;
};
const setTheme = (value) => {
  darkMode.value = value;
  document.documentElement.classList.toggle("dark", value);
};
onMounted(() => {
  // Clear any inline accent left by the retired palette picker, then use the design-system default.
  document.documentElement.style.removeProperty("--primary");
  window.addEventListener("scroll", updateActiveSection, { passive: true });
  window.addEventListener("resize", updateActiveSection);
  updateActiveSection();
});
onUnmounted(() => {
  window.removeEventListener("scroll", updateActiveSection);
  window.removeEventListener("resize", updateActiveSection);
});
</script>

<template>
  <div
    class="min-h-screen"
    :style="{ background: 'var(--canvas)', color: 'var(--text)' }"
  >
    <Navbar
      :active-section="activeSection"
      :sections="sections"
      :dark-mode="darkMode"
      @toggle-theme="setTheme(!darkMode)"
    />
    <main class="mx-auto max-w-7xl px-4 pb-16 pt-5 sm:px-8 lg:pl-80 lg:pt-10">
      <NotificationBanner
        message="Check out my recent video on rymo — my local-first Miro alternative."
        link="https://www.youtube.com/watch?v=MgRekuT9zlw"
        linkText="Watch it"
      />
      <section
        id="about"
        class="relative mb-14 overflow-hidden rounded-lg p-7 sm:p-10"
        :style="{ background: 'var(--primary)', color: 'var(--primary-foreground)' }"
      >
        <div class="absolute -right-12 -top-16 h-56 w-56 rounded-full border-[28px] border-white/30"></div>
        <div class="absolute bottom-[-48px] right-1/4 h-28 w-28 rotate-45 bg-white/25"></div>
        <div class="relative max-w-3xl">
          <p class="eyebrow !text-current opacity-70">Hello, I’m Ryan</p>
          <h1 class="mt-3 text-5xl font-extrabold leading-[.9] tracking-[-.05em] sm:text-7xl">
            Developer.
            <br />
            Curious builder.
          </h1>
          <div class="mt-7 max-w-2xl space-y-4 text-lg leading-relaxed">
            <p>A Computer Science student at the University of Calgary who turns curiosity into useful software. I build full-stack products, explore emerging technology, and enjoy making complex things feel simple.</p>
            <p>I’m pursuing a minor in Management and Society, and I’m driven by the same curiosity that first drew me to technology.</p>
            <p>From Raspberry Pis and VR to AI and machine learning, I enjoy exploring new tools, expanding my stack, and turning what I learn into practical software.</p>
          </div>
          <a
            href="#projects-hackathons"
            class="focusable mt-8 inline-flex rounded-md bg-[#172033] px-5 py-3 text-sm font-bold uppercase tracking-wider text-white transition-transform duration-200 hover:scale-105"
          >
            See selected work
            <span class="ml-3">↓</span>
          </a>
        </div>
      </section>
      <section
        id="skills"
        class="mb-14"
      >
        <Skills v-bind="skills" />
      </section>
      <section
        id="experience"
        class="mb-14"
      >
        <Experiences :experiences="experiences" />
      </section>
      <section id="projects-hackathons"><Projects :projects="projects" /></section>
    </main>
  </div>
</template>
