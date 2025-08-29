<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  name: String
});
</script>

<template>
  <span class="bg-sage text-gray-100 px-3 py-1 rounded-full text-sm">
    {{ name }}
  </span>
</template>
