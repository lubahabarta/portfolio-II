<script setup lang="ts">
import { onMounted } from 'vue';

const { scrolled } = defineProps({
    scrolled: {
        type: Number,
        required: true,
    }
});

const windowH = ref(0);

const getIntroText = (s: number) => {
    const point = {
        lubaFadeOutEnd: windowH.value,
    };

    if (s < point.lubaFadeOutEnd) {
        return 'Luba Habarta';
    } else if (s >= point.lubaFadeOutEnd) {
        return 'Junior Developer';
    }
};

const getIntroTextOpacity = (s: number) => {
    const frame = windowH.value * 0.5;
    const point = {
        lubaFadeOutStart: windowH.value * 0.5,
        lubaFadeOutEnd: windowH.value,
        devFadeInStart: windowH.value,
        devFadeInEnd: windowH.value * 1.5,
        devFadeOutStart: windowH.value * 2,
        devFadeOutEnd: windowH.value * 2.5,
    };

    if (s < point.lubaFadeOutStart) {
        return 1;
    } else if (s >= point.lubaFadeOutStart && s < point.lubaFadeOutEnd) {
        const percentage = 1 - (s - point.lubaFadeOutStart) / frame;
        return percentage;
    } else if (s >= point.devFadeInStart && s < point.devFadeInEnd) {
        const percentage = (s - point.devFadeInStart) / frame;
        return percentage;
    } else if (s >= point.devFadeOutStart && s < point.devFadeOutEnd) {
        const percentage = 1 - (s - point.devFadeOutStart) / frame;
        return percentage;
    } else if (s >= point.devFadeOutEnd) {
        return 0;
    }
};

const getBgTransformStyle = (s: number) => {
    const frame = windowH.value * 0.5;
    const point = {
        rotateStart: windowH.value * 2.5,
        rotateEnd: windowH.value * 3.5,
    };

    if (s < point.rotateStart) {
        return {
            bg: `rotate(0deg) scale(1)`,
            top: `translateY(0)`,
            bottom: `translateY(0)`,
        };
    } else if (s >= point.rotateStart && s < point.rotateEnd) {
        const percentage = (s - point.rotateStart) / (frame * 2);
        return {
            bg: `rotate(${90 * percentage}deg) scale(${1 + percentage})`,
            top: `translateY(-${50 * percentage}%)`,
            bottom: `translateY(${50 * percentage}%)`,
        };
    } else {
        return {
            bg: 'rotate(90deg) scale(2)',
            top: 'translateY(-55%)',
            bottom: 'translateY(55%)',
        };
    }
};

onMounted(() => {
    windowH.value = window.innerHeight;
});
</script>

<template>
    <section id="intro" class="relative h-[350vh] z-10">
        <div class="flex items-center justify-center sticky top-0 w-full h-[100vh] overflow-x-clip">
            <div class="absolute w-full h-full origin-cente z-20 will-change-transform"
                :style="{ transform: getBgTransformStyle(scrolled).bg }">
                <div class="h-[100vh] w-[300vw] left-[-100vw] absolute top-[-50%] bg-gradient-to-r from-white from-20% to-gray-300 to-80% will-change-transform"
                    :style="{ transform: getBgTransformStyle(scrolled).top }" />
                <div class="h-[100vh] w-[300vw] left-[-100vw] absolute bottom-[-50%] bg-gradient-to-l from-white from-20% to-gray-300 to-80% will-change-transform"
                    :style="{ transform: getBgTransformStyle(scrolled).bottom }" />
            </div>
            <span class="z-20 will-change-[opacity] text-[5vw]" :style="{ opacity: getIntroTextOpacity(scrolled) }">
                {{ getIntroText(scrolled) }}
            </span>
        </div>
    </section>
</template>