<script setup>
import { ref } from "vue";
const props = defineProps({ activeSection: String, sections: Array, darkMode: Boolean });
const emit = defineEmits(["toggle-theme"]);
const open = ref(false);
const sectionIds = { ABOUT: "about", EXPERIENCE: "experience", "PROJECTS & HACKATHONS": "projects-hackathons" };
const scrollTo = (section) => {
  const item = document.getElementById(sectionIds[section]);
  item?.scrollIntoView({ behavior: "smooth" });
  open.value = false;
};
</script>
<template>
  <header class="lg:fixed lg:inset-y-0 lg:left-0 lg:z-10 lg:w-72 lg:p-6">
    <div
      class="mx-4 mt-4 rounded-lg p-5 lg:m-0 lg:flex lg:h-full lg:flex-col"
      :style="{ background: 'var(--elevated)' }"
    >
      <div class="flex items-center justify-between lg:block">
        <RouterLink
          to="/"
          class="focusable text-3xl font-extrabold tracking-[-.06em]"
        >
          RYAN
          <br />
          <span :style="{ color: 'var(--primary-strong)' }">WONG.</span>
        </RouterLink>
        <button
          class="focusable rounded-md p-2 text-xl lg:hidden"
          :style="{ background: 'var(--surface)' }"
          @click="open = !open"
          :aria-expanded="open"
        >
          <i :class="['pi', open ? 'pi-times' : 'pi-bars']"></i>
        </button>
      </div>
      <img
        src="@/assets/me.jpg"
        alt="Ryan Wong"
        class="mt-6 hidden h-44 w-full rounded-md object-cover lg:block"
      />
      <p
        class="mt-5 hidden text-sm leading-relaxed lg:block"
        :style="{ color: 'var(--muted-text)' }"
      >
        Full-stack developer
        <br />
        and lifelong learner.
      </p>
      <nav :class="[open ? 'block' : 'hidden', 'mt-6 lg:block']">
        <ul class="space-y-1">
          <li
            v-for="section in sections"
            :key="section"
          >
            <RouterLink
              v-if="section === 'RESUME'"
              to="/resume"
              target="_blank"
              class="focusable nav-link"
            >
              {{ section }}
              <i class="pi pi-external-link text-[10px]"></i>
            </RouterLink>
            <a
              v-else-if="section === 'BLOG'"
              href="https://blog.ryanwong.ca"
              target="_blank"
              class="focusable nav-link"
            >
              {{ section }}
              <i class="pi pi-arrow-up-right text-[10px]"></i>
            </a>
            <button
              v-else
              class="focusable nav-link w-full text-left"
              :class="{ active: activeSection === sectionIds[section] }"
              @click="scrollTo(section)"
            >
              {{ section }}
            </button>
          </li>
        </ul>
      </nav>
      <div class="mt-7 flex items-center gap-4 lg:mt-auto">
        <button
          class="focusable flex h-10 w-10 items-center justify-center rounded-md"
          :style="{ background: 'var(--surface)' }"
          @click="emit('toggle-theme')"
        >
          <i :class="['pi', darkMode ? 'pi-sun' : 'pi-moon']"></i>
          <span class="sr-only">Toggle theme</span>
        </button>
        <a
          href="https://github.com/ryanwoong"
          target="_blank"
          class="social-link focusable text-xl"
        >
          <i class="pi pi-github"></i>
          <span class="sr-only">GitHub</span>
        </a>
        <a
          href="https://www.linkedin.com/in/ryanwongyyc/"
          target="_blank"
          class="social-link focusable text-xl"
        >
          <i class="pi pi-linkedin"></i>
          <span class="sr-only">LinkedIn</span>
        </a>
        <a
          href="https://x.com/ryxnwxng"
          target="_blank"
          class="social-link focusable text-xl"
        >
          <i class="pi pi-twitter"></i>
          <span class="sr-only">X</span>
        </a>
        <a
          href="https://youtube.com/@ryanwoong"
          target="_blank"
          class="social-link focusable text-xl"
        >
          <i class="pi pi-youtube"></i>
          <span class="sr-only">YouTube</span>
        </a>
      </div>
    </div>
  </header>
</template>
<style scoped>
.nav-link {
  display: block;
  border-radius: 6px;
  padding: 0.7rem 0.75rem;
  color: var(--muted-text);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  transition:
    background-color 200ms ease,
    transform 200ms ease,
    color 200ms ease;
}
.nav-link:hover,
.nav-link.active {
  background: var(--primary);
  color: var(--primary-foreground);
  transform: translateX(4px);
}
.social-link {
  transition:
    color 180ms ease-in,
    transform 240ms cubic-bezier(0.16, 1, 0.3, 1);
}
.social-link:hover,
.social-link:focus-visible {
  color: var(--primary-strong);
  transform: translateY(-3px) scale(1.12);
}
</style>
