<script setup>
import { defineProps } from "vue";
import Experience from "./Experience.vue";

const props = defineProps({
  experiences: Array,
});
</script>

<template>
  <div class="p-6 rounded-lg group max-w-3xl">
    <h2 class="text-3xl font-bold mb-8 text-black">Experience</h2>
    <Experience
      v-for="(experience, index) in experiences"
      :key="index"
      :delay="index * 80"
      :position="experience.position"
      :company="experience.company"
      :years="experience.years"
      :description="experience.description"
      :skills="experience.skills"
    />
  </div>
</template>
