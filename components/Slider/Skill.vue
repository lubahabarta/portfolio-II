<script setup lang="ts">
const { src } = defineProps({
    src: {
        type: String,
        required: true,
    },
    alt: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <div class="flex h-[14vh] aspect-square justify-center items-center bg-white shadow-md rounded-[10%] border-[1.2px] border-gray-400 mr-4 sm:mr-[14vh]">
        <img :src="src" :alt="alt" class="w-[45%] h-[45%]" />
    </div>
</template>