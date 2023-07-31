<script setup lang="ts">
import { onMounted } from 'vue';

const scrolled = ref(0);
const windowH = ref(0);
const projectsScrolled = ref(0);

// const projectsScrolled = computed(() => scrolled.value - windowH.value * 3.5);

onMounted(() => {
    const projects = document.querySelector('#projects');
    windowH.value = window.innerHeight;

    window.onscroll = () => {
        projectsScrolled.value = projects ? projects.getBoundingClientRect().top * -1 : 0;

        scrolled.value = window.scrollY;
    }
});
</script>

<template>
    <main class="bg-white">
        <SectionIntro :scrolled="scrolled > 0 ? scrolled : 0" />
        <SectionAboutMe />
        <SectionSkills />
        <SectionProjects :scrolled="projectsScrolled > 0 ? projectsScrolled : 0" />
    </main>
</template>