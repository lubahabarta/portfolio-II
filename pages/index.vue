<script setup lang="ts">
import { onMounted } from 'vue';

const scrolled = ref(0);
const windowH = ref(0);

const projectsScrolled = computed(() => scrolled.value - windowH.value * 3.5);

onMounted(() => {
    windowH.value = window.innerHeight;

    window.onscroll = () => {
        scrolled.value = window.scrollY;
    }
});
</script>

<template>
    <main class="bg-white">
        <SectionIntro :scrolled="scrolled > 0 ? scrolled : 0" />
        <SectionProjects :scrolled="projectsScrolled > 0 ? projectsScrolled : 0" />
        <SectionSkills />
        <SectionAboutMe />
    </main>
</template>