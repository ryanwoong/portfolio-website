<script setup>
import { defineProps } from 'vue';
import Project from './Project.vue';

const props = defineProps({
    projects: Array
});
</script>

<template>
  <div class="p-6 rounded-lg backdrop-blur-md shadow-lg max-w-3xl" :style="{backgroundColor: '#e6e6e9'}">
    <h2 class="text-3xl font-bold mb-2 text-gray-700">Projects & Hackathons</h2>
    <Project 
      v-for="(project, index) in projects" 
      :key="index" 
      :title="project.title"
      :img="project.img"
      :description="project.description"
      :link="project.link"
      :skills="project.skills"
    />
  </div>
</template>
