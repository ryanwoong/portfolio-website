<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    title: String,
    img: String,
    description: String,
    link: String,
    skills: Array
});
</script>

<template>
    <!-- When there is a link, wrap the entire box in an <a> -->
    <a v-if="link !== ''" :href="link" target="_blank" class="block">
        <div
            :class="{
                'border border-transparent rounded-lg max-w-3xl md:p-6 pb-6 transition-all duration-300': true,
                'hover:bg-white/10 hover:backdrop-blur-md hover:shadow-lg cursor-pointer': link !== ''
            }"
            :style="{
                transition: 'background 0.3s ease, backdrop-filter 0.3s ease, box-shadow 0.3s ease',
            }"
        >
            <!-- Title will also hover when the entire box is hovered -->
            <h3 class="text-xl font-semibold mb-2 text-sage transition-all duration-300 group-hover:text-sage-100 hover:text-sage-100">
                {{ title }}
                <li class="pi pi-external-link text-xs ml-2"></li>
            </h3>
            <p class="text-gray-800 max-w-2xl mb-4">{{ description }}</p>
            <div class="flex flex-wrap gap-2">
                <span
                    v-for="skill in skills"
                    :key="skill"
                    class="bg-sage text-gray-100 px-3 py-1 rounded-full text-sm"
                >
                    {{ skill }}
                </span>
            </div>
        </div>
    </a>

    <!-- If there's no link, just display the box without any <a> tag -->
    <div
        v-else
        class="border border-transparent rounded-lg mb-2 transition-all duration-300 max-w-3xl md:p-6 pb-6"
    >
        <h3 class="text-xl font-semibold mb-2 text-sage">{{ title }}</h3>
        <p class="text-gray-800 max-w-2xl mb-4">{{ description }}</p>
        <div class="flex flex-wrap gap-2">
            <span
                v-for="skill in skills"
                :key="skill"
                class="bg-sage text-gray-100 px-3 py-1 rounded-full text-sm"
            >
                {{ skill }}
            </span>
        </div>
    </div>
</template>
