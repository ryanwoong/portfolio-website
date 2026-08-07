<script setup>
defineProps({ position: String, company: String, years: String, location: String, description: String, skills: Array });
</script>

<template>
  <article class="experience-item">
    <div class="experience-date">
      <p>{{ years }}</p>
      <p
        v-if="location"
        class="experience-location"
      >
        {{ location }}
      </p>
    </div>
    <div
      class="experience-marker"
      aria-hidden="true"
    ></div>
    <div class="experience-content">
      <h3>{{ position }}</h3>
      <p class="experience-company">{{ company }}</p>
      <p class="experience-description">{{ description }}</p>
      <p class="technology-line">
        <span>Utilized</span>
        {{ skills.join(" · ") }}
      </p>
    </div>
  </article>
</template>
