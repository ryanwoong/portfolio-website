<script setup>
import shinchan from "@/assets/shinchan.png";

defineProps({
  message: {
    type: String,
    required: true,
  },
  link: {
    type: String,
    default: null,
  },
  linkText: {
    type: String,
    default: "Learn more",
  },
});
</script>

<template>
  <div
    class="banner flex items-center justify-center gap-3 px-4 py-2.5 mb-6 rounded-lg max-w-3xl text-sm font-medium shadow-md backdrop-blur-md"
    :style="{ backgroundColor: '#ffffff' }"
  >
    <img
      :src="shinchan"
      alt="Shinchan"
      class="shinchan w-8 h-8 object-contain shrink-0"
    />
    <span class="text-black">{{ message }}</span>
    <a
      v-if="link"
      :href="link"
      target="_blank"
      rel="noopener noreferrer"
      class="ml-1 text-cyan-600 font-semibold hover:underline shrink-0"
    >
      {{ linkText }} →
    </a>
  </div>
</template>

<style scoped>
/* Slide down + fade in on mount */
.banner {
  animation: slideDown 0.5s cubic-bezier(0.16, 1, 0.3, 1) both,
             borderGlow 3s ease-in-out 0.5s infinite;
  border: 1.5px solid transparent;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Soft repeating border glow */
@keyframes borderGlow {
  0%, 100% {
    border-color: transparent;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  }
  50% {
    border-color: rgba(6, 182, 212, 0.45);
    box-shadow: 0 2px 16px rgba(6, 182, 212, 0.25);
  }
}

/* Gentle bob on the Shinchan image */
.shinchan {
  animation: bob 2.5s ease-in-out 0.8s infinite;
}

@keyframes bob {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(-4px); }
}
</style>
