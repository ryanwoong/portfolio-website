<script setup>
import shinchan from "@/assets/shinchan.png";
defineProps({ message: String, link: String, linkText: String });
</script>

<template>
  <a
    v-if="link"
    :href="link"
    target="_blank"
    rel="noopener noreferrer"
    class="banner focusable mb-6 flex w-full items-center gap-3 rounded-lg px-4 py-3 text-sm font-medium"
  >
    <img
      :src="shinchan"
      alt=""
      class="h-9 w-9 object-contain"
    />
    <span>{{ message }}</span>
    <span class="ml-auto shrink-0 font-bold underline underline-offset-4">{{ linkText }} ↗</span>
  </a>
  <aside
    v-else
    class="banner mb-6 flex w-full items-center gap-3 rounded-lg px-4 py-3 text-sm font-medium"
  >
    <img
      :src="shinchan"
      alt=""
      class="h-9 w-9 object-contain"
    />
    <span>{{ message }}</span>
  </aside>
</template>

<style scoped>
.banner {
  background: var(--amber);
  color: #4a2a05;
  transition:
    transform 200ms ease,
    background-color 200ms ease;
}

a.banner:hover {
  background: #ffc37d;
  transform: scale(1.01);
}
</style>
