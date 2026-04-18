<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    position: String,
    company: String,
    years: String,
    description: String,
    skills: Array
});
</script>

<template>
    <div class="mb-6 max-w-3xl">
        <div
            class="p-6"
            :style="{
                transition: 'background 0.3s ease, backdrop-filter 0.3s ease',
            }"
        >
            <h3 class="text-xl font-semibold mb-2 text-cyan-600">
                {{ position }} {{ company !== "" ? "|" : "" }} {{ company }}
            </h3>
            <p class="text-md text-black italic mb-4">{{ years }}</p>
            <p class="text-black max-w-2xl mb-4">{{ description }}</p>
            <div class="flex flex-wrap gap-2">
                <span
                    v-for="skill in skills"
                    :key="skill"
                    class="bg-cyan-600 text-gray-100 px-3 py-1 rounded-full text-sm"
                >
                    {{ skill }}
                </span>
            </div>
        </div>
    </div>
</template>
