<script setup lang="ts">
import { ref, onMounted } from 'vue';

const trigger = ref<null | HTMLDivElement>(null);
const centeredText = ref<null | HTMLSpanElement>(null);

onMounted(() => {
    const windowHeight = window.innerHeight;
    const frame = windowHeight * 0.5;

    const point = {
        lubaFadeOutStart: windowHeight * 0.5,
        lubaFadeOutEnd: windowHeight,
        devFadeInStart: windowHeight,
        devFadeInEnd: windowHeight * 1.5,
        devFadeOutStart: windowHeight * 2,
        devFadeOutEnd: windowHeight * 2.5,
    };

    window.onscroll = () => {
        const scrolled = trigger.value!.getBoundingClientRect().top * -1;
        let opacity = 1;
        let text = 'Luba Habarta';

        if (scrolled < point.lubaFadeOutStart) {
            opacity = 1;
        } else if (scrolled >= point.lubaFadeOutStart && scrolled < point.lubaFadeOutEnd) {
            const percentage = 1 - (scrolled - point.lubaFadeOutStart) / frame;
            opacity = percentage;
        } else if (scrolled >= point.devFadeInStart && scrolled < point.devFadeInEnd) {
            const percentage = (scrolled - point.devFadeInStart) / frame;
            opacity = percentage;
        } else if (scrolled >= point.devFadeOutStart && scrolled < point.devFadeOutEnd) {
            const percentage = 1 - (scrolled - point.devFadeOutStart) / frame;
            opacity = percentage;
        } else if (scrolled >= point.devFadeOutEnd) {
            opacity = 0;
        }

        if (scrolled < point.lubaFadeOutEnd) {
            text = 'Luba Habarta';
        } else if (scrolled < point.devFadeOutEnd) {
            text = 'Junior Developer';
        }

        centeredText.value!.style.opacity = `${opacity}`;
        centeredText.value!.innerText = text;
    }
});
</script>

<template>
    <section id="intro" class="relative h-[350vh]">
        <div ref="trigger"></div>
        <div class="flex items-center justify-center sticky overflow-hidden top-0 w-full h-[100vh]">
            <div class="w-full h-[100vh] absolute top-[-50%] bg-gradient-to-r from-white to-gray-300" />
            <div class="w-full h-[100vh] absolute bottom-[-50%] bg-gradient-to-l from-white to-gray-300" />
            <span ref="centeredText" class="z-10 will-change-[opacity]">Luba Habarta</span>
        </div>
    </section>
</template>