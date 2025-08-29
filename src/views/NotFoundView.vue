<script setup>
    import { RouterLink } from 'vue-router';
</script>

<template>
    <section class="text-center flex flex-col justify-center items-center md:h-screen" :style="{backgroundColor: '#d9d2c7'}">
      <h1 class="text-6xl font-bold mb-4 text-gray-800">oopsie!</h1>
      <p class="text-xl mb-5 text-gray-800">Looks like this page doesn't exist...</p>
      <RouterLink
        to="/"
        class="p-3 rounded-lg group backdrop-blur-md shadow-lg text-gray-800"
        :style="{backgroundColor: '#EDEAE5'}"
        >Go Back
    </RouterLink>
    </section>
</template>