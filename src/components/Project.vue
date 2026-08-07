<script setup>
import { computed } from "vue";
const props = defineProps({ title: String, description: String, link: String, video_link: String, skills: Array, featured: Boolean });
const youtubeEmbedUrl = computed(() => {
  if (!props.video_link) return null;
  try {
    const url = new URL(props.video_link);
    const id = url.searchParams.get("v");
    return id ? `https://www.youtube.com/embed/${id}` : null;
  } catch {
    return null;
  }
});
</script>
<template>
  <a
    v-if="link"
    :href="link"
    target="_blank"
    class="project-card focusable flat-card flat-card-interactive group flex flex-col"
    :class="{ 'lg:col-span-2': featured }"
  >
    <div class="flex items-start justify-between gap-4">
      <p class="eyebrow">{{ featured ? "Featured project" : "Project" }}</p>
      <i class="pi pi-arrow-up-right text-lg transition-transform duration-200 group-hover:scale-125"></i>
    </div>
    <h3 class="mt-6 text-2xl font-extrabold tracking-[-.03em]">{{ title }}</h3>
    <div
      v-if="youtubeEmbedUrl"
      class="mt-5 aspect-video overflow-hidden rounded-md bg-black"
    >
      <iframe
        :src="youtubeEmbedUrl"
        class="h-full w-full"
        title="Project video"
        allowfullscreen
      ></iframe>
    </div>
    <p class="mt-4 max-w-3xl leading-relaxed">{{ description }}</p>
    <p class="technology-line">
      <span>Utilized</span>
      {{ skills.join(" · ") }}
    </p>
  </a>
  <article
    v-else
    class="project-card flat-card flex flex-col"
    :class="{ 'lg:col-span-2': featured }"
  >
    <p class="eyebrow">Project</p>
    <h3 class="mt-4 text-2xl font-extrabold tracking-[-.03em]">{{ title }}</h3>
    <p class="mt-4 leading-relaxed">{{ description }}</p>
    <p class="technology-line">
      <span>Utilized</span>
      {{ skills.join(" · ") }}
    </p>
  </article>
</template>
