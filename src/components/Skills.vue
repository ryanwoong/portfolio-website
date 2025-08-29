<script setup>
import { defineProps } from 'vue';
import Skill from './Skill.vue';  // Import the Skill component

// Define the props
const props = defineProps({
  languages: Array,
  technologiesFrameworks: Array
});
</script>

<template>
  <div class="p-6 rounded-lg backdrop-blur-md shadow-lg max-w-3xl" :style="{backgroundColor: '#e6e6e9'}">
    <h2 class="text-3xl font-bold mb-8 text-gray-700">Tech Stack</h2>


    <h2 class="text-lg font-bold mb-4 text-gray-700">Languages</h2>
    <div class="flex flex-wrap gap-2 overflow-x-auto">
      <Skill v-for="(language, index) in languages" :key="'language-' + index" :name="language" />
    </div>
    
    <h2 class="text-lg font-bold mt-6 mb-4 text-gray-700">Technologies & Frameworks</h2>
    <div class="flex flex-wrap gap-2 overflow-x-auto">
      <Skill v-for="(tech, index) in technologiesFrameworks" :key="'tech-' + index" :name="tech" />
    </div>
  
  </div>
</template>
