<script setup>
import { defineProps } from "vue";
import Skill from "./Skill.vue";

const props = defineProps({
  languages: Array,
  frameworks: Array,
  developerTools: Array,
  databases: Array,
});
</script>

<template>
  <div class="p-6 rounded-lg max-w-3xl">
    <h2 class="text-3xl font-bold mb-8 text-black">Tech Stack</h2>

    <div
      class="p-6 rounded-lg backdrop-blur-md shadow-lg border border-transparent mb-4"
      :style="{ backgroundColor: '#ffffff' }"
    >
      <h2 class="text-lg font-bold mb-4 text-black">Languages</h2>
      <div class="flex flex-wrap gap-2 overflow-x-auto">
        <Skill
          v-for="(language, index) in languages"
          :key="'language-' + index"
          :name="language"
        />
      </div>
    </div>

    <div
      class="p-6 rounded-lg backdrop-blur-md shadow-lg border border-transparent mb-4"
      :style="{ backgroundColor: '#ffffff' }"
    >
      <h2 class="text-lg font-bold mb-4 text-black">Frameworks</h2>
      <div class="flex flex-wrap gap-2 overflow-x-auto">
        <Skill
          v-for="(fw, index) in frameworks"
          :key="'fw-' + index"
          :name="fw"
        />
      </div>
    </div>

    <div
      class="p-6 rounded-lg backdrop-blur-md shadow-lg border border-transparent mb-4"
      :style="{ backgroundColor: '#ffffff' }"
    >
      <h2 class="text-lg font-bold mb-4 text-black">Developer Tools & Platforms</h2>
      <div class="flex flex-wrap gap-2 overflow-x-auto">
        <Skill
          v-for="(tool, index) in developerTools"
          :key="'tool-' + index"
          :name="tool"
        />
      </div>
    </div>

    <div
      class="p-6 rounded-lg backdrop-blur-md shadow-lg border border-transparent"
      :style="{ backgroundColor: '#ffffff' }"
    >
      <h2 class="text-lg font-bold mb-4 text-black">Databases & Backend Services</h2>
      <div class="flex flex-wrap gap-2 overflow-x-auto">
        <Skill
          v-for="(db, index) in databases"
          :key="'db-' + index"
          :name="db"
        />
      </div>
    </div>
  </div>
</template>
