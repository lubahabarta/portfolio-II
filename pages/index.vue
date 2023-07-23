<script setup lang="ts">
import { onMounted } from 'vue';

const scrolled = ref(0);

onMounted(() => {
    window.onscroll = () => {
        scrolled.value = window.scrollY;
    }
});
</script>

<template>
    <main class="bg-white">
        <SectionIntro />
        <SectionBio :sc="scrolled" />
    </main>
</template>