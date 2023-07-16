<script setup lang="ts">
import { ref, onMounted } from 'vue';

const trigger = ref<null | HTMLDivElement>(null);
const centeredText = ref<null | HTMLSpanElement>(null);
const bgContainer = ref<null | HTMLDivElement>(null);
const topBg = ref<null | HTMLDivElement>(null);
const bottomBg = ref<null | HTMLDivElement>(null);

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
        rotateStart: windowHeight * 2.5,
        rotateEnd: windowHeight * 3.5,
    };

    window.onscroll = () => {
        const scrolled = trigger.value!.getBoundingClientRect().top * -1;
        let opacity = 1;
        let text = 'Luba Habarta';
        let transformBg = 'rotate(0) scale(1)';
        let transformTop = 'translateY(0)';
        let transformBottom = 'translateY(0)';

        if (scrolled < point.lubaFadeOutEnd) {
            text = 'Luba Habarta';
        } else if (scrolled < point.devFadeOutEnd) {
            text = 'Junior Developer';
        }

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

        if (scrolled < point.rotateStart) {
            transformBg = 'rotate(0) scale(1)';
            transformTop = 'translateY(0)';
            transformBottom = 'translateY(0)';
        } else if (scrolled >= point.rotateStart && scrolled < point.rotateEnd) {
            const percentage = (scrolled - point.rotateStart) / (frame * 2);
            transformBg = `rotate(${90 * percentage}deg) scale(${1 + percentage})`;
            transformTop = `translateY(-${50 * percentage}%)`;
            transformBottom = `translateY(${50 * percentage}%)`;
        } else {
            transformBg = 'rotate(90deg) scale(2)';
            transformTop = 'translateY(-50%)';
            transformBottom = 'translateY(50%)';
        }

        centeredText.value!.style.opacity = `${opacity}`;
        centeredText.value!.innerText = text;

        bgContainer.value!.style.transform = transformBg;
        topBg.value!.style.transform = transformTop;
        bottomBg.value!.style.transform = transformBottom;
    }
});
</script>

<template>
    <section id="intro" class="relative h-[350vh] z-10">
        <div ref="trigger"></div>
        <div class="flex items-center justify-center sticky top-0 w-full h-[100vh]">
            <div ref="bgContainer" class="absolute w-full h-full origin-cente z-20">
                <div ref="topBg" class="h-[100vh] w-[200vw] absolute top-[-50%] bg-gradient-to-r from-white to-gray-300" />
                <div ref="bottomBg" class="h-[100vh] w-[200vw] absolute bottom-[-50%] bg-gradient-to-l from-white to-gray-300" />
            </div>
            <span ref="centeredText" class="z-20 will-change-[opacity] text-[5vw]">Luba Habarta</span>
        </div>
    </section>
</template>