<script setup>
import Skill from "./Skill.vue";
defineProps({ languages: Array, frameworks: Array, developerTools: Array, databases: Array });
</script>
<template>
  <div>
    <div class="mb-7">
      <p class="eyebrow">Toolkit</p>
      <h2 class="section-heading mt-2">Tech stack</h2>
    </div>
    <div class="grid gap-3 md:grid-cols-2">
      <article
        v-for="group in [
          { title: 'Languages', items: languages },
          { title: 'Frameworks', items: frameworks },
          { title: 'Developer tools & platforms', items: developerTools },
          { title: 'Databases & services', items: databases },
        ]"
        :key="group.title"
        class="flat-card"
      >
        <p class="mb-5 text-lg font-bold tracking-[-.02em]">{{ group.title }}</p>
        <div class="flex flex-wrap gap-2">
          <Skill
            v-for="item in group.items"
            :key="item"
            :name="item"
          />
        </div>
      </article>
    </div>
  </div>
</template>
