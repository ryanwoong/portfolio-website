<script setup>
import Experience from "./Experience.vue";

defineProps({ experiences: Array });
</script>

<template>
  <div>
    <div class="mb-7">
      <p class="eyebrow">Where I’ve contributed</p>
      <h2 class="section-heading mt-2">Experience</h2>
    </div>
    <div class="experience-timeline">
      <Experience
        v-for="experience in experiences"
        :key="experience.position + experience.years"
        v-bind="experience"
      />
    </div>
  </div>
</template>
