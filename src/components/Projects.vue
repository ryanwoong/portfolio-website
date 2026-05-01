<script setup>
import { defineProps } from "vue";
import Project from "./Project.vue";

const props = defineProps({
  projects: Array,
});
</script>

<template>
  <div class="p-6 rounded-lg max-w-3xl">
    <h2 class="text-3xl font-bold mb-8 text-black">Projects & Hackathons</h2>
    <Project
      v-for="(project, index) in projects"
      :key="index"
      :delay="index * 80"
      :title="project.title"
      :img="project.img"
      :description="project.description"
      :link="project.link"
      :skills="project.skills"
    />
  </div>
</template>
