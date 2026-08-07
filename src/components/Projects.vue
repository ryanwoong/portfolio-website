<script setup>
import Project from "./Project.vue";
defineProps({ projects: Array });
</script>
<template>
  <div>
    <div class="mb-7">
      <p class="eyebrow">What I'm working on</p>
      <h2 class="section-heading mt-2">Selected work</h2>
    </div>
    <div class="grid gap-3 lg:grid-cols-2">
      <Project
        v-for="(project, index) in projects"
        :key="project.title"
        v-bind="project"
        :featured="index === 0"
      />
    </div>
  </div>
</template>
