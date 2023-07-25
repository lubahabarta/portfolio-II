<script setup lang="ts">
const { src, customStyles } = defineProps({
    src: {
        type: String,
        required: true,
    },
    alt: {
        type: String,
        required: true,
    },
    customStyles: {
        type: String,
        required: true,
    }
});
</script>

<template>
    <div class="flex justify-center items-center bg-gray-100 rounded-lg" :class="customStyles">
        <img :src="src" :alt="alt" class="w-2/5 h-2/5" />
    </div>
</template>