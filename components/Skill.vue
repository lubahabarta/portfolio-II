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
    <div class="flex h-[14vh] aspect-square justify-center items-center rounded-lg border-[1px] border-gray-400 mr-4 sm:mr-[14vh]">
        <img :src="src" :alt="alt" class="w-2/5 h-2/5" />
    </div>
</template>