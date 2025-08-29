<script setup>
    import { defineProps } from 'vue';
    import Experience from './Experience.vue';

    const props = defineProps({
        experiences: Array
    });
</script>

<template>
    <div class="p-6 rounded-lg group backdrop-blur-md shadow-lg max-w-3xl" :style="{backgroundColor: '#e6e6e9'}">
        <h2 class="text-3xl font-bold mb-8 text-gray-700">Experience</h2>
        <Experience 
          v-for="(experience, index) in experiences" 
          :key="index" 
          :position="experience.position"
          :company="experience.company"
          :years="experience.years"
          :description="experience.description"
          :skills="experience.skills"
        />
    </div>
</template>
